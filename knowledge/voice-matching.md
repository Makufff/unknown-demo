# GrayMate — Voice Agent Personality Matching System
## "คุยกับ AI แล้วให้ AI หาคู่ให้"

---

## 💡 Core Concept

แทนที่จะให้ผู้ใช้กรอก questionnaire แบบ form ธรรมดา  
GrayMate ใช้ **AI Voice Agent สัมภาษณ์** ทั้ง Host และ Guest ผ่านการพูดคุยสั้นๆ 5–7 นาที  
แล้ว AI วิเคราะห์คำตอบเพื่อสร้าง **"Kizuna Profile"** — ค่า stats ที่ใช้ matching

> เหมือน MBTI แต่ไม่ต้องกรอกฟอร์ม แค่คุย แล้ว AI อ่านออก

---

## 🎭 Kizuna Profile — 6 มิติ

```
มิติที่ 1  🌅  Rhythm Score        จังหวะชีวิต (กลางวัน vs กลางคืน)
มิติที่ 2  🤝  Bond Style          ชอบสังสรรค์ vs ต้องการความเป็นส่วนตัว
มิติที่ 3  🏠  Home Vibe           บ้านเงียบ vs บ้านมีชีวิตชีวา
มิติที่ 4  🍽️  Table Culture       ชอบทานด้วยกัน vs ต่างคนต่างทาน
มิติที่ 5  💬  Communication Style  พูดตรงๆ vs ใช้ความเกรงใจ
มิติที่ 6  🌱  Care Orientation    ชอบดูแลคนอื่น vs ชอบให้คนอื่นดูแล
```

แต่ละมิติมีค่า **0.0 – 1.0**  
เช่น `Rhythm Score: 0.2` = คนตื่นเช้ามาก, `0.8` = คนนอนดึก

---

## 🗣️ Voice Agent Flow

### ขั้นตอนที่ 1: เปิดบทสนทนา (30 วินาที)
```
AI:  "สวัสดีครับ ผมชื่อ เก็น เป็น AI ของ GrayMate 
      วันนี้จะขอพูดคุยกับคุณสักครู่นะครับ 
      ไม่มีคำตอบถูกหรือผิด แค่เล่าให้ฟังตามความเป็นจริงก็พอครับ
      พร้อมแล้วก็เริ่มได้เลยนะครับ — วันนี้ตื่นมาทำอะไรเป็นอย่างแรกครับ?"
```

### ขั้นตอนที่ 2: บทสนทนา adaptive (5–7 นาที)
AI ถามคำถามปลายเปิด **ไม่มีสคริปต์ตายตัว** แต่ครอบคลุม 6 มิติ

```
หัวข้อที่ต้องผ่าน:
□  ตอนเช้าของคุณเป็นยังไง? (→ Rhythm)
□  บ้านในฝันของคุณเป็นยังไง? (→ Home Vibe + Bond Style)
□  ถ้าอยู่บ้านกับคนอื่น อะไรที่คุณให้ความสำคัญที่สุด? (→ Communication)
□  เล่าความทรงจำดีๆ กับครอบครัวให้ฟังหน่อย (→ Table Culture + Care)
□  ถ้าคนที่อยู่ด้วยทำอะไรที่ไม่ถูกใจ คุณจัดการยังไง? (→ Communication Style)
```

### ขั้นตอนที่ 3: AI Analysis (เบื้องหลัง)
```
Input:   transcript ของบทสนทนา
Process: GPT-4o วิเคราะห์และสกัด Kizuna Profile
Output:  JSON ของค่า 6 มิติ + confidence score + personality summary
```

### ขั้นตอนที่ 4: แสดงผล Kizuna Profile
```
ผู้ใช้เห็น radar chart หรือ profile card
พร้อม personality summary 2–3 ประโยค
เช่น: "คุณเป็นคนจังหวะชีวิตกลางวัน ชอบความเงียบ 
       แต่มีน้ำใจอยากดูแลคนรอบข้าง เหมาะกับบ้านที่มีบรรยากาศอบอุ่นเงียบสงบ"
```

---

## 🧮 Matching Algorithm

### Compatibility Formula

```python
def calculate_compatibility(host: KizunaProfile, guest: KizunaProfile) -> float:
    
    weights = {
        "rhythm":        0.30,  # สำคัญที่สุด — ถ้าตื่นเวลาต่างกัน = ปัญหาแน่
        "home_vibe":     0.20,  # สำคัญมาก — บ้านควรตรงกัน
        "table_culture": 0.20,  # กินข้าวด้วยกันคือ core value ของโครงการ
        "bond_style":    0.15,  # ระดับ social ที่ต้องการ
        "communication": 0.10,  # ปรับเข้าหากันได้ถ้าอื่นๆ ตรง
        "care":          0.05,  # Host ดูแล Guest ได้บ้าง
    }
    
    score = 0
    for dim, weight in weights.items():
        # ยิ่งค่าใกล้กัน ยิ่ง compatible
        diff = abs(host[dim] - guest[dim])
        similarity = 1 - diff
        score += similarity * weight
    
    return round(score * 100, 1)  # คืนค่า 0–100%
```

### Hard Filters (ก่อน calculate score)
```
🚫  smoke: host=False AND guest=True → exclude ทันที
🚫  pet_allergy: host มีแมว AND guest แพ้แมว → exclude ทันที  
🚫  rhythm diff > 0.6 → เตือนว่า "ความเสี่ยงสูง" แม้ score รวมสูง
```

### Match Result Output
```json
{
  "compatibility_score": 94.2,
  "verdict": "เข้ากันได้ดีมาก",
  "dimension_breakdown": {
    "rhythm": {"host": 0.2, "guest": 0.25, "match": 97},
    "home_vibe": {"host": 0.3, "guest": 0.35, "match": 95},
    "table_culture": {"host": 0.8, "guest": 0.75, "match": 95},
    "bond_style": {"host": 0.4, "guest": 0.5, "match": 90},
    "communication": {"host": 0.3, "guest": 0.45, "match": 85},
    "care": {"host": 0.7, "guest": 0.4, "match": 70}
  },
  "strengths": ["จังหวะชีวิตใกล้เคียงกันมาก", "ทั้งคู่ชอบทานข้าวด้วยกัน"],
  "watch_out": ["Guest อาจต้องการพื้นที่ส่วนตัวบ้าง"],
  "ai_insight": "คู่นี้มีโอกาสสร้างความสัมพันธ์แบบ 'ยายกับหลาน' ได้จริงๆ"
}
```

---

## 🛠️ Technical Implementation

### Stack สำหรับ Voice Agent

```
Option A — ง่ายที่สุด (แนะนำสำหรับ 18h)
├── Frontend: Web Audio API (record) → Blob
├── Transport: POST to backend
├── STT: OpenAI Whisper API (whisper-1)
├── AI Agent: GPT-4o (conversational turn-by-turn)
├── Analysis: GPT-4o (extract Kizuna Profile from transcript)
└── Output: JSON → store in Supabase

Option B — ว้าวกว่า (ถ้ามีเวลา)
├── OpenAI Realtime API (voice-to-voice แบบ real-time)
├── ไม่มี delay, AI ตอบกลับทันที
└── Demo ได้สวยมากแต่ setup ซับซ้อนกว่า
```

### API Calls ที่ต้องใช้

```python
# Step 1: Transcribe audio
transcript = openai.audio.transcriptions.create(
    model="whisper-1",
    file=audio_file,
    language="th"
)

# Step 2: Conversational turn
response = openai.chat.completions.create(
    model="gpt-4o",
    messages=[
        {"role": "system", "content": AGENT_SYSTEM_PROMPT},
        {"role": "user", "content": transcript.text}
    ]
)

# Step 3: Extract Kizuna Profile from full transcript
profile = openai.chat.completions.create(
    model="gpt-4o",
    messages=[{
        "role": "user", 
        "content": f"""
        จากบทสนทนานี้: {full_transcript}
        
        วิเคราะห์และตอบเป็น JSON เท่านั้น:
        {{
          "rhythm": float (0-1, 0=ตื่นเช้า, 1=นอนดึก),
          "bond_style": float (0-1, 0=introvert, 1=extrovert),
          "home_vibe": float (0-1, 0=เงียบ, 1=賑やか),
          "table_culture": float (0-1, 0=ทานคนเดียว, 1=ทานด้วยกันเสมอ),
          "communication": float (0-1, 0=พูดตรงๆ, 1=เกรงใจสูง),
          "care": float (0-1, 0=ต้องการการดูแล, 1=ชอบดูแลคนอื่น),
          "summary": "สรุปบุคลิก 2 ประโยค",
          "confidence": float (0-1)
        }}
        """
    }]
)
```

### System Prompt สำหรับ Voice Agent

```
คุณชื่อ "เก็น" เป็น AI ของ GrayMate
หน้าที่: สัมภาษณ์ผู้ใช้เพื่อทำความเข้าใจบุคลิกและ lifestyle

กฎการสนทนา:
1. พูดภาษาไทยสุภาพ อบอุ่น เหมือนเพื่อนคุย ไม่เป็นทางการ
2. ถามทีละคำถาม ไม่ถามรวดเดียวหลายข้อ
3. ถ้าคำตอบกว้างเกินไป ให้ถามเจาะลึกต่อ
4. อย่าบอกว่ากำลัง "วัดค่า" อะไร ให้รู้สึกเหมือนคุยเล่น
5. ต้องครอบคลุม: จังหวะชีวิต, บ้านในฝัน, การกิน, การสื่อสาร
6. ใช้เวลา 5-7 นาที จบด้วยการขอบคุณอบอุ่นๆ
7. ห้ามถามเรื่องเงิน, สุขภาพ, หรือข้อมูลส่วนตัวที่ sensitive
```

---

## 🎯 Why This Wins the Hackathon

### เหนือกว่า Questionnaire อย่างไร?

| | Questionnaire | Voice Agent |
|---|---|---|
| User experience | น่าเบื่อ, กดเลือก | เหมือนคุยกับเพื่อน |
| Data richness | ตอบแค่ที่ถาม | AI จับ nuance ที่คนไม่รู้ตัว |
| Authenticity | คนตอบ "ดูดี" | พูดสดๆ สะท้อนตัวตนจริง |
| Demo factor | ไม่น่าตื่นเต้น | Judge ได้ลองจริงๆ ต่อหน้า |
| Post-AGI angle | ไม่มี | ✅ AI สัมภาษณ์มนุษย์ = Post-AGI จริงๆ |

### Demo Script สำหรับ Pitch
```
"ขอเชิญ judge ลองพูดคุยกับ AI ของเราสัก 2 นาที"
→ Judge พูดกับ voice agent สด
→ ระบบแสดง Kizuna Profile ของ judge บนจอ
→ "นี่คือสิ่งที่ AI เข้าใจเกี่ยวกับคุณ — และนี่คือคนที่เราคิดว่าเข้ากับคุณได้"
```

> ไม่มีทีมไหนใน hackathon นี้ที่จะทำแบบนี้ได้

---

## ⚠️ Risks & Mitigation

| Risk | โอกาส | Mitigation |
|---|---|---|
| Whisper แปลภาษาไทยผิด | กลาง | เตรียม mock transcript สำรองไว้ demo |
| เสียงรบกวนในงาน hackathon | สูง | ใช้ text input เป็น fallback แทน voice |
| GPT วิเคราะห์ผิดเพี้ยน | ต่ำ | ทดสอบ prompt กับ transcript จริงก่อน |
| เวลาไม่พอ build voice UI | กลาง | ทำ text-based version ก่อน แล้วเพิ่ม voice ทีหลัง |

---

## 📋 Build Priority

```
Hour 01–03  ✅ P0  Text-based interview → extract Kizuna Profile (core logic)
Hour 03–05  ✅ P0  Matching algorithm + compatibility score display
Hour 05–08  ✅ P1  Web Audio record → Whisper transcription
Hour 08–10  ✅ P1  Conversational turn-by-turn with GPT-4o
Hour 10–12  🎯 P2  Radar chart visualization ของ Kizuna Profile
Hour 12–14  🎯 P2  Demo-ready UI + polish
```
