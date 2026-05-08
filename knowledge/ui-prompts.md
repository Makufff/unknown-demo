# GrayMate UI Design Prompts for Claude

ใช้ prompt เหล่านี้กับ Claude แยกกันทีละหน้า เพื่อให้ได้ UI ที่ละเอียดที่สุด

---

## 🟢 PROMPT 1: LINE LIFF — หน้าสำหรับผู้สูงอายุ

```
Design a mobile UI screen (375px wide, Thai language) for a LINE LIFF app called "GrayMate" (เกรย์เมท).

This screen is for elderly Thai users aged 65+. Design for maximum accessibility.

Screen: "My Home Dashboard" — what the elderly host sees after opening the app.

Layout requirements:
- Warm color palette: cream white (#FFF8F0) background, coral accent (#FF6B6B), soft gold (#FFB347)
- Font size minimum 20px for all text, 28px for headings
- Large tap targets (minimum 60px height for all buttons)
- Thai language throughout

Content to include:
1. Top greeting card: "สวัสดีตอนเช้า คุณยายสมศรี 🌅" with today's date in Thai
2. Housemate status card showing: profile photo placeholder of student "ต้น", status badge "อยู่ในบ้าน ✅", last check-in time "เช้านี้ 07:23 น."
3. Three large icon buttons in a grid:
   - "ส่งข้อความหาต้น" (chat bubble icon, blue)
   - "นัดทานข้าวด้วยกัน" (fork icon, orange)  
   - "แจ้งเหตุฉุกเฉิน SOS" (warning icon, red, slightly larger)
4. Today's "moment" card at bottom: soft background, text "ต้นฝากบอกว่า: เย็นนี้จะกลับบ้านหลัง 3 ทุ่มนะครับคุณยาย 🙏"

Style: Warm, friendly, like a family app. Rounded corners everywhere (16px+). Drop shadows. No sharp edges. Feels like WhatsApp meets a greeting card.

Output as a complete HTML file with inline CSS. Make it pixel-perfect and production-ready.
```

---

## 🔵 PROMPT 2: LINE LIFF — หน้าสำหรับนักศึกษา

```
Design a mobile UI screen (375px wide, Thai language) for a LINE LIFF app called "GrayMate".

This screen is for Thai university students aged 18-25. Modern, clean, slightly playful.

Screen: "Student Home Dashboard" — main screen the student sees.

Layout requirements:
- Modern color palette: white background, deep teal (#1A535C) primary, mint green (#4ECDC4) accent
- Clean sans-serif typography, 16px base
- Card-based layout with subtle shadows

Content to include:
1. Top nav bar: "GrayMate" logo left, notification bell right with red dot
2. Hero status card (rounded, teal gradient):
   - "บ้านของคุณ" label
   - Address: "ซ.ลาดพร้าว 15, กรุงเทพฯ"
   - Rent saved badge: "ประหยัดได้ ฿4,500/เดือน 💚"
3. "คุณยายสมศรี" card with:
   - Avatar circle with elderly woman emoji
   - Status: "อยู่ที่บ้าน 🏠"
   - Mood indicator: "😊 อารมณ์ดีวันนี้" (from AI check-in)
   - Button: "ส่งข้อความ"
4. "กิจกรรมวันนี้" section:
   - Checklist item checked: "✅ ทักทายตอนเช้า"
   - Checklist item unchecked: "⬜ ทานข้าวเย็นด้วยกัน (18:00 น.)"
5. Bottom: Soft nudge card with light yellow background: 
   "💡 คุณยายกำลังทำข้าวต้มอยู่นะ ลองแวะคุยสักแป๊บไหม?"

Style: Clean and modern like Grab or Line MAN but warmer. Tab bar at bottom with 4 icons: Home, Match, Messages, Profile.

Output as a complete HTML file with inline CSS. Fully interactive feel with hover states.
```

---

## 🟡 PROMPT 3: Kizuna Hub — Tablet Interface

```
Design a tablet UI (768px × 1024px, landscape mode optional) for "GrayMate Kizuna Hub" — a shared tablet placed in the living room of an elderly Thai person's home.

This is an ambient, always-visible display. It should feel warm and welcoming, like a digital family board.

Layout: Two-column layout

LEFT COLUMN (40%):
- Large clock: current time in Thai format "14:32 น." 
- Date in Thai: "พุธ ที่ 7 พฤษภาคม 2568"
- Weather widget: Bangkok, 34°C, sunny icon
- Photo frame widget showing a placeholder family photo with caption "ภาพความทรงจำ"

RIGHT COLUMN (60%):
- Section header: "สวัสดีคุณยายสมศรี 👋"
- AI daily greeting (speech bubble style): "วันนี้อากาศร้อน อย่าลืมดื่มน้ำเยอะๆ นะคะ และต้นจะกลับบ้านตอน 3 ทุ่มค่ะ"
- Housemate status: Student "ต้น" — "กำลังเรียนอยู่ที่มหาวิทยาลัย 📚" with estimated return time
- Shared meal schedule card: "🍽️ นัดทานข้าวเย็นด้วยกัน — วันนี้ 18:30 น."
- Large "พูดคุยกับ AI" voice button (microphone icon, very large, center-aligned, coral color)

BOTTOM BAR:
- 3 large buttons: "📞 โทรหาต้น" | "🆘 ฉุกเฉิน" | "📋 บันทึกประจำวัน"

Color palette: Warm cream (#FFF8F0), coral (#FF6B6B), soft orange, natural wood textures as border accents. 
Font: Very large — clock 72px, main text 24px minimum.
Style: Like a family smart display (Google Nest Hub) but Thai-flavored and warmer.

Output as a complete HTML file with inline CSS. Should look beautiful on a tablet screen.
```

---

## 🟣 PROMPT 4: Admin Dashboard — สำหรับ Judge และ MHESI

```
Design a web dashboard (1440px wide, desktop) for "GrayMate Admin Dashboard" — shown to government officials and hackathon judges to demonstrate national-scale impact.

This is the control center that shows AI matching data and wellness analytics across Thailand.

Layout: Standard dashboard with sidebar

SIDEBAR (dark teal #1A535C, 240px):
- GrayMate logo + tagline "เชื่อมสองวัย สร้างไทยอบอุ่น"
- Nav items with icons: Overview, Matches, Wellness Analytics, Safety Alerts, Settings

MAIN CONTENT — 4 sections:

1. TOP STATS ROW (4 cards):
   - "คู่ที่จับคู่สำเร็จ" — 1,247 คู่ (↑12% this month)
   - "ผู้สูงอายุในโครงการ" — 1,891 คน
   - "นักศึกษาที่ประหยัดค่าเช่า" — avg ฿4,200/เดือน  
   - "คะแนนความสุขเฉลี่ย" — 4.7/5.0 ⭐

2. MATCHING VISUALIZATION (left 60%):
   - Network graph showing AI match connections between students and elderly
   - Each node: student (blue circle) connected to elderly (orange circle)
   - Lines labeled with compatibility score: "93% match"
   - Title: "AI Matching Engine — เหตุผลในการจับคู่"
   - Below graph: Tag pills showing match reasons: "ตื่นเวลาเดียวกัน ✓" "ชอบดูข่าวเหมือนกัน ✓" "ไม่สูบบุหรี่ ✓"

3. WELLNESS ANALYTICS (right 40%):
   - Line chart: "ดัชนีความสุขผู้สูงอายุ" over 6 months, trending upward
   - Donut chart: Loneliness reduction: "87% รายงานว่าเหงาน้อยลง"
   - Small map of Thailand with dots showing active GrayMate locations

4. BOTTOM: AI Activity Feed
   - Live feed of anonymized AI actions: 
   - "🤖 AI จับคู่ใหม่: นักศึกษาจากมหิดล ↔ คุณยายในลาดพร้าว (95% compatibility)"
   - "💚 Check-in: คุณยายสมศรีรายงานว่าวันนี้อารมณ์ดี"
   - "🍽️ ทานข้าวด้วยกัน: 342 คู่ทานอาหารร่วมกันเมื่อคืน"

Color: Professional — white background, teal sidebar, data viz in coral/mint/gold.
Charts: Use CSS/SVG for charts, no external libraries needed.

Output as a complete HTML file with inline CSS and JavaScript for any interactions. Make it look like a real government dashboard — credible and impressive.
```

---

## 🔴 PROMPT 5: AI Co-Living Contract Generator — Codex Demo Screen

```
Design a mobile UI screen (375px) showing the "GrayMate Smart Contract" feature — the moment after AI matching is complete and Codex generates a personalized co-living agreement.

This is the DEMO MOMENT for the hackathon — judges need to see OpenAI Codex doing real work.

Screen title: "สัญญาการอยู่ร่วมกัน (AI Generated) ✨"

TOP SECTION — Match Result Card:
- Two avatars side by side with a heart connection: 
  - Left: elderly woman icon, "คุณยายสมศรี อายุ 72 ปี"
  - Right: student icon, "ต้น นักศึกษา ม.มหิดล"
- Compatibility score: large "96%" with circular progress bar in coral
- 3 match reason tags: "🌅 ตื่นเช้าเหมือนกัน" "🚭 ไม่สูบบุหรี่" "🌿 ชอบปลูกต้นไม้"

MIDDLE SECTION — "สัญญาที่ AI สร้างให้คุณ":
Styled like a formal document but warm. Show 5 agreement clauses with icons:
1. 🕕 "ต้นจะแจ้งล่วงหน้าหากกลับบ้านหลัง 22:00 น. ผ่าน LINE"
2. 🍽️ "ทานข้าวเย็นร่วมกันอย่างน้อย 3 ครั้ง/สัปดาห์"
3. 🔇 "เวลาเงียบ: 22:00–07:00 น. (ตามที่ทั้งสองฝ่ายต้องการ)"
4. 🌱 "ต้นจะช่วยรดน้ำต้นไม้เมื่อคุณยายไม่สะดวก"
5. 💚 "ทักทายกันทุกวันอย่างน้อย 1 ครั้ง"

Small label below each clause: "สร้างโดย OpenAI Codex จากข้อมูลของคุณ"

BOTTOM SECTION:
- "ปรับแก้สัญญา" button (outlined, teal)
- "ยืนยันและเริ่มต้นการอยู่ร่วมกัน 🏠" button (filled, coral, large)
- Small text: "สัญญานี้จัดเก็บอย่างปลอดภัย รับรองโดย GrayMate"

Style: Clean white with warm accents. Document-like but friendly. The "AI Generated" badge should glow slightly to emphasize tech.

Output as complete HTML with inline CSS. This screen should look impressive enough to demo to OpenAI judges.
```

---

## 📋 วิธีใช้ Prompts เหล่านี้

1. **เปิด Claude.ai** ใหม่แต่ละ conversation สำหรับแต่ละ prompt
2. **Copy prompt ทั้งหมด** วางใน message
3. **Claude จะ generate HTML** ที่รันได้ทันที
4. ถ้าต้องการปรับ บอก Claude เช่น "เปลี่ยนสีเป็น..." หรือ "เพิ่ม animation..."
5. **Save HTML file** แต่ละไฟล์ไว้ใช้ demo

## ⚡ Tips สำหรับ Hackathon

- ทำ PROMPT 5 (Contract Generator) ก่อน — นี่คือ WOW moment สำหรับ judge OpenAI
- ทำ PROMPT 4 (Dashboard) เป็นที่สอง — สำหรับ judge MHESI
- PROMPT 1 และ 2 ใช้เป็น user flow demo ระหว่าง pitch
