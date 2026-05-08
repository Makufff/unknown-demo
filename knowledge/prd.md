# GrayMate — Product Requirements Document (PRD)
**Version:** 1.0 (Hackathon MVP)  
**Date:** May 2026  
**Event:** OpenAI Codex × AIAT Hackathon — Wellness AI in the Post-AGI Era  
**Build Time:** 18 hours  

---

## 1. Overview

### 1.1 Product Vision
GrayMate คือ AI-powered intergenerational home-sharing platform ที่จับคู่ผู้สูงอายุไทย (มีห้องว่าง ต้องการเพื่อน) กับนักศึกษาต่างจังหวัด (ต้องการที่พักราคาสมเหตุสมผล) โดยใช้ OpenAI API วิเคราะห์ความเข้ากัน และ Codex สร้างสัญญาการอยู่ร่วมกันแบบ personalized

### 1.2 Mission Statement
> "ใช้ AI เพื่อสร้างสิ่งที่ AI ทดแทนไม่ได้ — ความสัมพันธ์ระหว่างมนุษย์"

### 1.3 Target Users

| Role | คำอธิบาย | Pain Point หลัก |
|---|---|---|
| **Host** | ผู้สูงอายุ 60–80 ปี มีห้องว่าง อยู่คนเดียวหรือกับคู่สมรส | เหงา ขาดรายได้เสริม กลัวอยู่คนเดียว |
| **Guest** | นักศึกษาอายุ 18–25 ปี มาจากต่างจังหวัด | ค่าห้องแพง ขาด "บ้าน" ในเมือง |
| **Admin** | เจ้าหน้าที่ MHESI / กรมกิจการผู้สูงอายุ / มหาวิทยาลัย | ต้องการข้อมูล impact ระดับนโยบาย |

---

## 2. Scope

### 2.1 In Scope (Hackathon MVP — 18 ชั่วโมง)
- ✅ LINE OA + LIFF สำหรับ Host และ Guest
- ✅ AI Compatibility Matching (questionnaire-based)
- ✅ Codex Co-Living Contract Generator
- ✅ AI Wellness Check-in + Nudge System
- ✅ Kizuna Hub (Tablet ambient display)
- ✅ Admin Dashboard (analytics + matching visualization)

### 2.2 Out of Scope (Post-Hackathon)
- ❌ Payment gateway / escrow
- ❌ Background check integration (PDPA compliance)
- ❌ Real-time fall detection (hardware)
- ❌ Multi-language support
- ❌ TM30 immigration reporting automation

---

## 3. User Stories

### 3.1 Host (ผู้สูงอายุ)

```
US-H01  ในฐานะผู้สูงอายุ ฉันต้องการลงทะเบียนผ่าน LINE
        โดยไม่ต้องโหลดแอปใหม่ เพื่อให้ฉันเข้าถึงได้ง่าย

US-H02  ในฐานะผู้สูงอายุ ฉันต้องการดูสถานะของนักศึกษา
        ว่าอยู่บ้านหรือไม่ เพื่อให้ฉันรู้สึกปลอดภัย

US-H03  ในฐานะผู้สูงอายุ ฉันต้องการส่งข้อความหานักศึกษา
        ผ่านปุ่มใหญ่ที่กดง่าย เพื่อสื่อสารได้โดยไม่ต้องพิมพ์มาก

US-H04  ในฐานะผู้สูงอายุ ฉันต้องการกดปุ่ม SOS ฉุกเฉิน
        เพื่อแจ้งนักศึกษาและครอบครัวได้ทันที

US-H05  ในฐานะผู้สูงอายุ ฉันต้องการบอก AI ว่าวันนี้รู้สึกอย่างไร
        เพื่อให้ระบบส่งต่อข้อมูลให้นักศึกษาดูแลได้

US-H06  ในฐานะผู้สูงอายุ ฉันต้องการนัดทานข้าวกับนักศึกษา
        ผ่านระบบ เพื่อให้มีเวลาพูดคุยร่วมกัน
```

### 3.2 Guest (นักศึกษา)

```
US-G01  ในฐานะนักศึกษา ฉันต้องการกรอกแบบสอบถาม lifestyle
        เพื่อให้ AI วิเคราะห์ว่าฉันเข้ากับผู้สูงอายุคนไหนได้ดีที่สุด

US-G02  ในฐานะนักศึกษา ฉันต้องการดูคะแนน compatibility
        พร้อมเหตุผลที่ชัดเจน เพื่อตัดสินใจได้อย่างมั่นใจ

US-G03  ในฐานะนักศึกษา ฉันต้องการเห็น checklist กิจกรรมประจำวัน
        เพื่อรักษาสัญญาที่ทำไว้กับผู้สูงอายุ

US-G04  ในฐานะนักศึกษา ฉันต้องการรับ nudge จาก AI
        แบบนุ่มนวล ไม่บังคับ เพื่อให้ฉันอยากไปคุยด้วยเอง

US-G05  ในฐานะนักศึกษา ฉันต้องการดูสรุปค่าเช่าที่ประหยัดได้
        เพื่อรู้สึกว่าการอยู่ที่นี่คุ้มค่า

US-G06  ในฐานะนักศึกษา ฉันต้องการอ่านและเซ็นสัญญา
        ที่ AI สร้างมาเฉพาะสำหรับฉันกับบ้านนี้
```

### 3.3 Admin

```
US-A01  ในฐานะ admin ฉันต้องการดู dashboard ภาพรวม
        จำนวน match, wellness score, และ regional distribution

US-A02  ในฐานะ admin ฉันต้องการเห็น AI activity feed
        แบบ real-time เพื่อ monitor ระบบ

US-A03  ในฐานะ admin ฉันต้องการดูกราฟ Wellness Impact
        เพื่อนำเสนอต่อหน่วยงานรัฐและ partner
```

---

## 4. Functional Requirements

### 4.1 Module 1: Onboarding & Profile

| ID | Requirement | Priority | Notes |
|---|---|---|---|
| F-01 | ระบบ LINE OA รองรับ message-based onboarding | P0 | ไม่ต้องโหลดแอป |
| F-02 | Questionnaire สำหรับ Host: เวลาตื่น, สูบบุหรี่, สัตว์เลี้ยง, งานอดิเรก, ความไวต่อเสียง | P0 | ≤10 คำถาม |
| F-03 | Questionnaire สำหรับ Guest: เหมือน Host + สถานะนักศึกษา, มหาวิทยาลัย, เหตุผลที่สมัคร | P0 | ≤10 คำถาม |
| F-04 | ระบบ verify นักศึกษา: upload รูปบัตรนักศึกษา | P1 | MVP ใช้ manual review |
| F-05 | Photo upload สำหรับ profile | P1 | ใช้ placeholder ได้ใน hackathon |

### 4.2 Module 2: AI Matching Engine

| ID | Requirement | Priority | Notes |
|---|---|---|---|
| F-06 | คำนวณ compatibility score 0–100% จากคำตอบ questionnaire | P0 | ใช้ OpenAI API |
| F-07 | แสดง top 3 match พร้อม reasoning (เหตุผลที่ AI เลือก) | P0 | |
| F-08 | แสดง match reasons เป็น tag pills ที่อ่านง่าย | P0 | เช่น "ตื่นเวลาเดียวกัน ✓" |
| F-09 | Flag คู่ที่มี hard mismatch (เช่น คนหนึ่งสูบบุหรี่ อีกคนไม่ยอมรับ) | P0 | hard filter |
| F-10 | Host และ Guest ต้อง "accept" match ทั้งสองฝ่าย | P1 | mutual opt-in |

### 4.3 Module 3: Codex Contract Generator

| ID | Requirement | Priority | Notes |
|---|---|---|---|
| F-11 | Generate co-living contract ภาษาไทยจาก profile ทั้งสองฝ่าย | P0 | OpenAI Codex API |
| F-12 | Contract มีอย่างน้อย 5 clause: เวลากลับบ้าน, มื้ออาหาร, quiet hours, งานบ้าน, การทักทาย | P0 | |
| F-13 | แสดง "สร้างโดย AI จากข้อมูลของคุณ" badge อย่างชัดเจน | P0 | สำหรับ demo |
| F-14 | Guest และ Host กด "ยืนยันสัญญา" ได้ | P1 | |
| F-15 | สามารถ "สร้างสัญญาใหม่" ได้ถ้าไม่พอใจ | P1 | |

### 4.4 Module 4: Daily Wellness & Nudge System

| ID | Requirement | Priority | Notes |
|---|---|---|---|
| F-16 | AI ส่ง check-in message ถาม Host ทุกเช้าผ่าน LINE | P0 | 1 คำถามสั้นๆ |
| F-17 | บันทึก mood/wellness data ของ Host แต่ละวัน | P0 | |
| F-18 | ส่ง nudge ให้ Guest เมื่อ Host อยู่ในสถานการณ์ที่เหมาะ | P0 | ไม่บังคับ, ใช้ภาษาเชิญชวน |
| F-19 | Nudge ต้องใช้ "ความเกรงใจ-aware language" ไม่ใช่ reminder แบบ alarm | P0 | เช่น "คุณยายทำขนมอยู่นะ ลองแวะคุยไหม?" |
| F-20 | Alert Guest ถ้า Host ไม่ตอบ check-in เกิน 24 ชั่วโมง | P1 | |

### 4.5 Module 5: Kizuna Hub (Tablet Display)

| ID | Requirement | Priority | Notes |
|---|---|---|---|
| F-21 | แสดงนาฬิกาและวันที่ภาษาไทยแบบ real-time | P0 | |
| F-22 | แสดงสถานะ Guest (อยู่บ้าน / ไม่อยู่ / เวลากลับโดยประมาณ) | P0 | |
| F-23 | แสดง AI greeting message ที่ปรับตามเวลาและสภาพอากาศ | P0 | เรียก OpenAI API |
| F-24 | ปุ่ม "พูดคุยกับ AI" (voice input) | P1 | MVP ใช้ text input แทนได้ |
| F-25 | ปุ่ม SOS ขนาดใหญ่ที่มองเห็นได้ชัดเจน | P0 | |
| F-26 | แสดง shared meal schedule วันนี้ | P0 | |

### 4.6 Module 6: Admin Dashboard

| ID | Requirement | Priority | Notes |
|---|---|---|---|
| F-27 | KPI cards: total matches, hosts, avg rent saved, happiness score | P0 | ใช้ mock data ได้ |
| F-28 | Bar chart แสดง wellness impact metrics | P0 | CSS/SVG based |
| F-29 | Regional distribution chart | P0 | |
| F-30 | Real-time AI activity feed | P0 | |
| F-31 | Matching visualization (network graph concept) | P1 | |

---

## 5. Non-Functional Requirements

### 5.1 Performance
| Requirement | Target |
|---|---|
| AI matching response time | < 3 วินาที |
| Contract generation time | < 5 วินาที |
| LINE LIFF load time | < 2 วินาที |
| Dashboard load time | < 3 วินาที |

### 5.2 Usability
| Requirement | Detail |
|---|---|
| Minimum font size (Host UI) | 20px |
| Minimum tap target | 60 × 60px |
| ภาษา | ไทยเป็นหลัก, อังกฤษเฉพาะ label เทคนิค |
| Color contrast | WCAG AA (4.5:1 minimum) |

### 5.3 Security & Privacy (MVP Level)
| Requirement | Detail |
|---|---|
| ไม่เก็บข้อมูลส่วนตัวบน client | ใช้ server-side storage |
| API key | ไม่ expose บน frontend |
| PDPA awareness | แสดง consent notice ในหน้า onboarding |

---

## 6. Tech Stack

```
Frontend
├── Next.js 14 (App Router)
├── Tailwind CSS
└── LINE LIFF SDK

Backend
├── FastAPI (Python)
├── OpenAI SDK (GPT-4o + Codex)
└── Supabase (PostgreSQL + Auth)

Infrastructure
├── Vercel (Frontend deploy)
├── Railway / Render (Backend deploy)
└── LINE Developers (OA + LIFF)
```

---

## 7. Data Models

### 7.1 User Profile
```json
{
  "user_id": "uuid",
  "role": "host | guest",
  "name": "string",
  "age": "integer",
  "line_id": "string",
  "location": "string",
  "profile": {
    "wake_time": "string",
    "smoke": "boolean",
    "pet": "string",
    "hobby": ["string"],
    "noise_sensitivity": "low | medium | high",
    "meal_preference": "integer (meals/week together)"
  },
  "created_at": "timestamp"
}
```

### 7.2 Match
```json
{
  "match_id": "uuid",
  "host_id": "uuid",
  "guest_id": "uuid",
  "compatibility_score": "float (0-100)",
  "match_reasons": ["string"],
  "status": "pending | accepted | active | ended",
  "contract_id": "uuid",
  "start_date": "date",
  "monthly_rent": "integer",
  "created_at": "timestamp"
}
```

### 7.3 Contract
```json
{
  "contract_id": "uuid",
  "match_id": "uuid",
  "clauses": ["string"],
  "ai_message": "string",
  "generated_by": "claude-sonnet-4 | codex",
  "host_signed": "boolean",
  "guest_signed": "boolean",
  "created_at": "timestamp"
}
```

### 7.4 Wellness Log
```json
{
  "log_id": "uuid",
  "user_id": "uuid",
  "date": "date",
  "mood_score": "integer (1-5)",
  "response": "string",
  "ai_analysis": "string",
  "nudge_sent": "boolean",
  "created_at": "timestamp"
}
```

---

## 8. API Endpoints

```
Authentication
POST   /auth/line          ← LINE OAuth login

Users
POST   /users/register     ← สร้าง profile
GET    /users/:id          ← ดู profile
PUT    /users/:id          ← แก้ไข profile

Matching
POST   /match/analyze      ← AI วิเคราะห์ compatibility
GET    /match/:id          ← ดูผลการ match
POST   /match/:id/accept   ← ยืนยัน match

Contract
POST   /contract/generate  ← Codex สร้างสัญญา
GET    /contract/:id       ← ดูสัญญา
POST   /contract/:id/sign  ← เซ็นสัญญา

Wellness
POST   /wellness/checkin   ← บันทึก daily check-in
POST   /wellness/nudge     ← trigger nudge to guest
GET    /wellness/:user_id  ← ดู wellness history

Dashboard
GET    /admin/stats        ← KPI overview
GET    /admin/feed         ← AI activity feed
GET    /admin/matches      ← all active matches
```

---

## 9. Screen Flow

```
[HOST FLOW]
LINE OA → Onboarding Questionnaire → Profile Created
→ Notified of Match → Review Student Profile
→ Accept Match → Sign Contract → Kizuna Hub Active
→ Daily Check-in (AI) → Ongoing Wellness Monitoring

[GUEST FLOW]
LINE OA → Onboarding Questionnaire → Profile Created
→ View Match Recommendations → Select Host
→ Accept Match → Review + Sign Contract
→ Daily Checklist → Receive AI Nudges

[ADMIN FLOW]
Web Dashboard Login → Overview KPIs
→ Match Activity Feed → Wellness Analytics
→ Regional Map → Export Report
```

---

## 10. Acceptance Criteria (Hackathon Demo)

สิ่งที่ต้อง demo ได้จริงในวันที่ 9 พฤษภาคม:

| # | Scenario | Expected Result |
|---|---|---|
| AC-01 | Judge เปิด LINE OA แล้วกรอก questionnaire | ระบบบันทึกและแสดง "รับข้อมูลแล้ว" |
| AC-02 | กด "วิเคราะห์ความเข้ากัน" | AI แสดง compatibility score + เหตุผล ภายใน 3 วินาที |
| AC-03 | กด "สร้างสัญญา" | Codex generate สัญญาภาษาไทยเฉพาะคู่นั้น ภายใน 5 วินาที |
| AC-04 | เปิด Kizuna Hub บน tablet | แสดงนาฬิกา, สถานะ Guest, AI greeting แบบ real-time |
| AC-05 | เปิด Admin Dashboard | แสดง KPI, กราฟ, และ activity feed ครบถ้วน |
| AC-06 | กด "ขอ Nudge จาก AI" | AI สร้างข้อความชวนคุยแบบใช้ความเกรงใจ |

---

## 11. Timeline (18 ชั่วโมง)

```
Hour 00–01  Project setup: repo, env, Supabase schema, LINE OA config
Hour 01–03  Backend: FastAPI skeleton + OpenAI integration + API endpoints
Hour 03–06  Frontend: LINE LIFF (Host + Guest) onboarding + questionnaire
Hour 06–09  AI Matching Engine + Contract Generator (core features)
Hour 09–12  Kizuna Hub tablet UI + Wellness check-in + Nudge system
Hour 12–15  Admin Dashboard + mock data + charts
Hour 15–17  Integration testing + bug fixes + demo flow polish
Hour 17–18  Pitch deck final check + rehearse demo script
```

---

## 12. Team Roles (4–5 คน)

| Role | จำนวน | รับผิดชอบ |
|---|---|---|
| **AI/Backend Lead** | 1 คน | FastAPI + OpenAI API + Matching logic + Contract generator |
| **Frontend Lead** | 1 คน | Next.js + LINE LIFF + Kizuna Hub |
| **Full-stack / Integration** | 1 คน | Supabase + API wiring + Admin Dashboard |
| **Design / Frontend Support** | 1 คน | UI polish + Tailwind + Demo data |
| **PM / Pitch** | 1 คน | Slide deck + Demo script + Story + Presentation |

---

## 13. Risk Register

| Risk | ระดับ | Mitigation |
|---|---|---|
| LINE LIFF setup ใช้เวลานาน | 🔴 High | เตรียม LINE account + channel ก่อนงาน |
| OpenAI API rate limit | 🟡 Medium | ใช้ mock response สำรองไว้ |
| Demo ค้างตอน live | 🔴 High | บันทึกวิดีโอ demo ไว้เป็น backup |
| Contract generation ภาษาไทยผิดเพี้ยน | 🟡 Medium | เตรียม prompt engineering อย่างดี |
| Supabase setup ช้า | 🟡 Medium | ใช้ in-memory / JSON file แทนได้ |
| ไม่มีเวลาทำ Kizuna Hub | 🟢 Low | เป็น P1 ตัดออกได้ถ้าเวลาไม่พอ |
