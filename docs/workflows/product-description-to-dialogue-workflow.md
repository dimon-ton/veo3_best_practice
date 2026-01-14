# Workflow: ดึงรายละเอียดสินค้าจาก “คำอธิบายสินค้า” → ปรับบทพูด (Dialogue) ใน Video Prompt

เป้าหมาย: เอาข้อมูลจากหน้าเว็บขายของ (หัวข้อสินค้า / bullet / description / วิธีใช้ / สเปก) มาเป็น “หลักฐาน” เพื่อเขียนบทพูดภาษาไทยที่ **ตรงสินค้า** และ “ขายของแบบ UGC” ได้ดีขึ้น

---

## ใช้เมื่อไหร่

- สินค้ามีรายละเอียดเยอะ (ส่วนผสม, จุดเด่น, วิธีใช้, รุ่น/สี/ขนาด)
- อยากให้บทพูด “ไม่ลอย” และไม่เผลอพูดเกินจริง
- ต้องการทำหลายเวอร์ชันจากหน้าเดียวกัน (hook ต่างกัน แต่ facts เดิม)

---

## Step 1: เก็บข้อมูลจากหน้าเว็บขายของ

1. เปิดหน้าสินค้า (TikTok Shop / Shopee / Lazada / เว็บแบรนด์)
2. คัดลอกข้อมูลที่เกี่ยวข้อง:
   - Title / ชื่อสินค้า (ตามหน้าร้าน)
   - Bullet จุดเด่น
   - Description เต็ม
   - สเปก/สิ่งที่ได้/ขนาด/วัสดุ
   - วิธีใช้
   - คำเตือน/ข้อควรระวัง
   - เคลมจากร้าน (copy ตามจริง)
3. วางลงในชีต: `docs/templates/product-details-sheet.md`

---

## Step 2: สรุปเป็น “Product Facts” ที่ใช้พูดได้จริง

เลือก “สิ่งที่คนควรรู้เพื่อเชื่อและซื้อ” ภายใน 16 วินาที:

- Key features 3 ข้อ (เป็นรูปธรรม: วัสดุ/ฟังก์ชัน/ดีไซน์/จุดต่าง)
- Benefits 2 ข้อ (ผลลัพธ์ที่ผู้ใช้รู้สึก/เห็นได้ แต่ไม่เกินจริง)
- How to use 1–2 ขั้นตอน (ให้คนทำตามได้)
- Differentiator 1 ข้อ (เหตุผลที่ต้องเลือกอันนี้)
- CTA 1 ประโยค (เช่น ดูโปร/กดตะกร้า/เลือกสี)

Tip: ถ้า “หาในหน้าร้านไม่เจอ” ให้ใส่ `N/A` แล้วอย่าเอาไปพูด

---

## Step 3: สร้างบทพูด (Thai) ให้พอดี 2 scenes × 8 วินาที

หลักคิด: 1 scene = 1 ไอเดียหลัก + 1 action

### โครงสร้างแนะนำ (16 วินาที)

**Scene 1 (Hook → ปัญหา → เปิดตัว)**
- Hook 1 ประโยค (1–2 วิ)
- ปัญหา/บริบท 1 ประโยค (2–3 วิ)
- แนะนำสินค้า + จุดเด่น 1 ข้อ (3–4 วิ)

**Scene 2 (วิธีใช้ → ผลลัพธ์ → CTA)**
- วิธีใช้ 1 ขั้นตอน (2–3 วิ)
- Benefit 1–2 ข้อ (3–4 วิ)
- CTA 1 ประโยค (1–2 วิ)

### ตัวอย่าง “บทพูดแบบเติมช่อง” (คุมความยาว)

**Scene 1**
- “มีใคร [PAIN POINT] เหมือนเรามั้ย?”
- “เราเลยลอง [PRODUCT NAME]…”
- “จุดที่ชอบคือ [KEY FEATURE 1]”

**Scene 2**
- “วิธีใช้คือ [HOW TO USE STEP]”
- “แล้วมัน [BENEFIT 1] แบบ [SENSORY PROOF]”
- “ใครอยากลอง ไปกดที่ตะกร้า/ดูโปรได้เลย”

---

## Step 4: เอาบทพูดไปใส่ใน Veo / Flow Prompt (Image-to-Video)

ถ้าคุณใช้ workflow แบบ 2 scenes ให้ใส่บทพูดใน prompt ของแต่ละ scene โดยยึดแนวทางจาก `docs/workflows/image-to-video-workflow.md`

ข้อความที่ควรมี (แนะนำ):

- “Thai dialogue: …” (ใส่เป็นประโยคสั้นๆ)
- “Lips sync naturally to Thai dialogue”
- จำกัดเสียง: “Only [speaker] voice. No background music or sound effects.” (ถ้าต้องการให้พูดชัด)

---

## Step 5: QA ก่อน generate (กันพลาดเรื่องเคลม)

- บทพูดทุกประโยคอ้างอิงได้จากหน้าเว็บ (หรือเป็นคำพูดเชิงความรู้สึกที่ไม่ยืนยันผลลัพธ์เกินจริง)
- หลีกเลี่ยงคำที่เสี่ยง: “รักษา/หายขาด/การันตีผล/เห็นผล 100%/ภายใน X วัน” (ถ้าไม่มีในหน้าร้านหรือเสี่ยงนโยบาย)
- ถ้ามีส่วนผสม/สเปก ต้องพูดให้ตรง (ตัวเลข, หน่วย, รุ่น)
- ความยาวรวมต้องพอดี 8 วินาทีต่อ scene (พูดธรรมชาติ)

---

## Prompt ช่วยสรุป (Copy-Paste ให้ AI ช่วยแตกข้อมูล)

นำ “Raw text” จากหน้าร้านมาแปะ แล้วใช้ prompt นี้กับโมเดลที่คุณใช้เขียนสคริปต์:

```
Extract product facts from the shopping page text below.
Return:
1) Product Facts (JSON): product_name, category, key_features (3-5), benefits (2-3), differentiator (1), how_to_use (2-4 steps), specs, warnings, promo.
2) Thai dialogue for 2 scenes x 8 seconds:
   - Scene 1: hook + problem + introduce product + 1 feature
   - Scene 2: how-to + benefits + CTA
Rules:
- Only use facts present in the text. If missing, write N/A and do not mention it in dialogue.
- Keep Thai lines short and natural (UGC).
- Avoid medical/guaranteed claims unless explicitly present in the text.

Shopping page text:
<PASTE HERE>
```

