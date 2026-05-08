# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository status

This repo currently contains **planning artifacts only** — no source code, no build system, no tests. The single top-level directory `knowledge/` holds the PRD, research, and design briefs for an 18-hour hackathon build of **GrayMate** (เกรย์เมท), an intergenerational home-sharing platform for the OpenAI Codex × AIAT Hackathon (Wellness AI in the Post-AGI Era, May 2026).

When the user starts implementation, scaffold into the conventional layout implied by the PRD (see "Planned tech stack" below) — there is no existing repo structure to conform to.

## What GrayMate is

AI-matched home sharing between Thai elderly hosts (60–80, with a spare room) and university student guests (18–25, priced out of Bangkok rentals). Three surfaces:

- **LINE OA + LIFF** — onboarding, matching, contract signing, daily wellness for Host and Guest. LINE is non-negotiable: it's the only interface elderly Thai users already know.
- **Kizuna Hub** — an always-on tablet display in the elderly host's living room (clock, AI greeting, housemate status, SOS, shared meal schedule).
- **Admin Dashboard** — desktop web view for MHESI / government stakeholders showing match counts, wellness analytics, and a real-time AI activity feed.

## Planned tech stack (from `knowledge/prd.md` §6)

```
Frontend:   Next.js 14 (App Router) + Tailwind + LINE LIFF SDK
Backend:    FastAPI (Python) + OpenAI SDK (GPT-4o + Codex) + Supabase
Deploy:     Vercel (frontend) + Railway/Render (backend) + LINE Developers
Voice:      OpenAI Whisper for STT; optionally Realtime API for voice-to-voice
```

## Architecture decisions already locked in

These are spec-level choices in the knowledge docs — don't relitigate them without reason:

- **Two-sided matching with mutual opt-in.** Both Host and Guest must accept. A "compatibility score" (0–100) plus tag-pill reasons is the core demo artifact.
- **"Kizuna Profile" — 6 dimensions** (rhythm, bond_style, home_vibe, table_culture, communication, care), each `0.0–1.0`. Compatibility is a weighted similarity over these dims; full formula and weights in `knowledge/voice-matching.md` §"Matching Algorithm". Rhythm has the highest weight (0.30); rhythm-diff > 0.6 is a soft warning even if total score is high.
- **Hard filters before scoring**: smoke mismatch and pet-allergy mismatch exclude pairs outright (`voice-matching.md`). Implement these as a pre-pass, not as score penalties.
- **Voice agent over questionnaire** for personality capture. The agent ("เก็น") runs a 5–7 min open-ended Thai conversation, then a separate GPT-4o call extracts the Kizuna JSON from the transcript. Build the text-based version first; voice is P1 (`voice-matching.md` §"Build Priority"). Keep mock transcripts ready as a demo fallback — Whisper Thai accuracy plus venue noise are the top demo risks.
- **Codex contract generator** must produce ≥5 Thai-language clauses (curfew, meals, quiet hours, chores, greeting) personalized from both profiles, and display a visible "สร้างโดย OpenAI Codex จากข้อมูลของคุณ" badge. This is the headline demo moment for OpenAI judges.
- **Nudge tone is "ความเกรงใจ-aware"**, not alarm-style. Phrasing like "คุณยายทำขนมอยู่นะ ลองแวะคุยไหม?" — invitational, never imperative. This is a hard product requirement (F-19), not a stylistic preference.
- **Data models** (`prd.md` §7): `User`, `Match`, `Contract`, `WellnessLog`. Match status is `pending | accepted | active | ended`. Contract tracks `host_signed` and `guest_signed` separately.
- **API surface** sketched in `prd.md` §8 — follow those paths (`/match/analyze`, `/contract/generate`, `/wellness/checkin`, `/admin/stats`, etc.) so frontend and backend stay in sync without re-deriving them.

## Hard UX constraints (do not relax)

These come from `knowledge/deep-research-report.md` and `knowledge/ui-prompts.md`:

- **Host UI (LINE LIFF)**: minimum 20px body text, 28px headings, 60×60px tap targets, WCAG AA contrast (≥4.5:1). Warm palette — cream `#FFF8F0`, coral `#FF6B6B`, soft gold `#FFB347`. No hamburger menus (Thai elderly users don't recognize them). Thai language throughout; avoid English technical labels.
- **Guest UI (LINE LIFF)**: modern teal/mint palette — primary `#1A535C`, accent `#4ECDC4`. Standard 16px base, bottom-tab nav OK.
- **Kizuna Hub (tablet)**: 768×1024, two-column layout, clock at 72px, body ≥24px. Same warm palette as Host UI.
- **Admin Dashboard**: 1440px desktop, dark teal sidebar `#1A535C`, white content area. Charts in CSS/SVG only — no chart libs (`ui-prompts.md` PROMPT 4).

When asked to "build the [page] UI", the prompts in `knowledge/ui-prompts.md` are the canonical brief — copy from them rather than re-deriving the layout.

## Demo/acceptance criteria (`prd.md` §10)

The 18-hour build is judged against six concrete scenarios. AC-02 (matching < 3s) and AC-03 (contract generation < 5s) are perf-critical; budget OpenAI calls accordingly and have mock responses wired in for rate-limit fallback (`prd.md` §13 risk register).

## Knowledge directory map

| File | Use when |
|---|---|
| `knowledge/prd.md` | Source of truth for scope, modules, data models, API endpoints, timeline |
| `knowledge/voice-matching.md` | Implementing matching logic, voice agent, or Kizuna Profile extraction |
| `knowledge/ui-prompts.md` | Building any of the 5 screens — has full design briefs per screen |
| `knowledge/problem-statements.md` | Pitch deck, README copy, or any user-facing narrative framing |
| `knowledge/deep-research-report.md` | Detailed UX/accessibility specs for elderly + student users |
| `knowledge/global-comparison.md` | Competitive context (Kyoto Solidaire, Humanitas, Nesterly, etc.) |
| `knowledge/compass_artifact_*.md` | Long-form Japan→Thailand transfer playbook; background, not spec |

## Working language

The product is Thai-first — copy, contracts, AI prompts, and UI strings should be in Thai unless they're technical labels. Code comments, identifiers, commit messages, and conversation with the user can be in English or Thai per the user's lead.
