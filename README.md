# 📚 Study Tracker

แอปติดตามการเรียนและคุยกับ AI ช่วยติวตลอดสัปดาห์ รองรับทั้ง Desktop และ Mobile (PWA)

![Study Tracker](https://img.shields.io/badge/PWA-ready-4f8ef7?style=flat-square) ![License](https://img.shields.io/badge/license-MIT-green?style=flat-square)

---

## ✨ ฟีเจอร์

- 📅 **ตารางครบ 7 วัน** — จันทร์–ศุกร์ (วันทบทวน) + เสาร์–อาทิตย์ (วันเรียนจริง)
- ✅ **Checkbox ติ๊ก session** — บันทึกว่าทำอะไรไปแล้วบ้าง
- 📝 **บันทึกหัวข้อที่เรียน** — วันเสาร์/อาทิตย์มีช่องกรอกว่าเรียนถึงไหน
- 💬 **Chat กับ AI** — ถามเรื่องที่เรียน ขอสรุป หรือให้ช่วยติวได้เลย
- 🔄 **Scroll snap แนวตั้ง** — เลื่อนนิ้วขึ้น-ลงเพื่อเปลี่ยนวัน
- 💾 **บันทึกอัตโนมัติ** — ข้อมูลเก็บใน localStorage ปิดแล้วเปิดใหม่ข้อมูลยังอยู่
- 📱 **PWA** — ติดตั้งบนมือถือได้เหมือน app จริง ใช้ offline ได้ด้วย

---

## 📁 โครงสร้างไฟล์

```
study-tracker/
├── index.html      ← ตัวแอปหลัก
├── manifest.json   ← PWA manifest
├── sw.js           ← Service Worker (offline support)
├── icon.svg        ← ไอคอนแอป
└── README.md       ← ไฟล์นี้
```

---

## 🚀 วิธี Deploy บน GitHub Pages

### ขั้นตอนที่ 1 — สร้าง Repository

1. ไปที่ [github.com](https://github.com) → กด **New repository**
2. ตั้งชื่อ repo เช่น `study-tracker`
3. เลือก **Public**
4. กด **Create repository**

### ขั้นตอนที่ 2 — อัปโหลดไฟล์

1. กด **Add file → Upload files**
2. ลากไฟล์ทั้ง 4 ไฟล์เข้าไปพร้อมกัน:
   - `index.html`
   - `manifest.json`
   - `sw.js`
   - `icon.svg`
3. กด **Commit changes**

### ขั้นตอนที่ 3 — เปิด GitHub Pages

1. ไปที่ **Settings → Pages**
2. ตรง Source เลือก **Deploy from a branch**
3. เลือก branch **main** → folder **/ (root)**
4. กด **Save**
5. รอ 1–2 นาที จะได้ลิงก์:

```
https://<username>.github.io/study-tracker
```

---

## 📱 วิธีติดตั้งบนมือถือ (PWA)

### iPhone / iPad (Safari)
1. เปิดลิงก์ GitHub Pages ใน **Safari** (ไม่ใช่ Chrome)
2. กดปุ่ม **Share** 🔗 (กล่องมีลูกศรขึ้น ด้านล่างหน้าจอ)
3. เลือก **Add to Home Screen**
4. กด **Add**
5. แอปจะปรากฏบน Home Screen เปิดได้เลยแบบ fullscreen

### Android (Chrome)
1. เปิดลิงก์ใน **Chrome**
2. กดเมนู **⋮** มุมขวาบน
3. เลือก **Add to Home screen** หรือ **Install app**
4. กด **Add**

> หลังติดตั้งแล้วใช้งาน offline ได้ด้วย เพราะมี Service Worker cache ไว้

---

## 🔑 วิธีตั้งค่า API Key (OpenRouter)

แอปใช้ [OpenRouter](https://openrouter.ai) สำหรับ AI chat ซึ่งมี free tier ให้ใช้ฟรี

1. สมัครที่ [openrouter.ai](https://openrouter.ai) ด้วย Google หรือ Email
2. ไปที่ [openrouter.ai/keys](https://openrouter.ai/keys) → กด **Create Key**
3. Copy key ที่ได้ (ขึ้นต้นด้วย `sk-or-...`)
4. เปิดแอป → กดปุ่ม 🔑 มุมขวาบน → วาง key → กด **บันทึก**

> Key จะบันทึกใน localStorage ของเบราว์เซอร์บนเครื่องคุณเท่านั้น ไม่มีการส่งไปที่อื่น

---

## 📖 วิธีใช้งานแอป

| การกระทำ | วิธี |
|----------|------|
| เปลี่ยนวัน | Scroll ขึ้น-ลง หรือกดจุดด้านขวา |
| ติ๊ก session เสร็จแล้ว | คลิกที่รายการ |
| บันทึกหัวข้อที่เรียน (เสาร์/อาทิตย์) | ติ๊ก session แล้วพิมพ์ในช่องที่โผล่ขึ้นมา |
| ถาม AI | พิมพ์ในช่องด้านขวา แล้วกด Enter |
| ใช้ quick prompt | กดปุ่มลัดเหนือช่องพิมพ์ |

---

## 🛠 วิธีแก้ไขตารางเรียน

เปิดไฟล์ `index.html` แล้วหาส่วน `const DAYS = [...]` จะเห็นโครงสร้างแบบนี้:

```javascript
{ name:'วันจันทร์', short:'จันทร์', isClassDay:false, sessions:[
    { id:'mon-1', label:'MATH0101 — ทบทวนโจทย์เสาร์', sub:'derivative / limit', tag:'math' },
    ...
]}
```

แก้ `label` และ `sub` ให้ตรงกับตารางเรียนของคุณได้เลย

---

## 📜 License

MIT — ใช้งานได้ฟรี แก้ไขได้ตามต้องการ
