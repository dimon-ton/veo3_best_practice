# Image-to-Video Workflow สำหรับ Veo 3

> Workflow: อัปโหลด Reference Images → สร้างภาพนิ่งด้วย Canvas → สร้างวิดีโอ
>
> ปรับสำหรับ TikTok Shop 16 วินาที (2 scenes × 8 วินาที)

---

## Workflow Overview

```
Step 1: เตรียม Reference Images
├─ รูปนางแบด Character Sheet (หลายมุม)
└─ รูปสินค้า Product Photo (คมชัด)

Step 2: ใช้ Canvas Prompting สร้างภาพนิ่ง
├─ อัปโหลด Reference Images ลง Canvas
├─ วางตำแหน่งรูปใน Canvas
├─ Generate Scene 1 Image (8 วินาที)
└─ (แนะนำ) Animate Scene 1 → จับภาพ “Last Frame” → ใช้เป็นภาพตั้งต้น/อ้างอิงสำหรับ Animate Scene 2

Step 3: สร้างวิดีโอจากภาพ (Image-to-Video)
├─ Scene 1 Video (Image → 8s Video)
└─ Scene 2 Video (Image → 8s Video)

Step 4: รวมวิดีโอใน SceneBuilder
└─ ได้ MP4 16 วินาที
```

---

## Step 1: เตรียม Reference Images

### รูปที่ต้องการ:

| รูป | คำอธิบาย | ข้อควรระวัง | จำนวนแนะนำ |
|-----|----------|-------------|-------------|
| **Model Character Sheet** | รูปนางแบดหลายมุม (ด้านหน้า, ด้านข้าง, แสงต่างกัน) | ใบหน้าชัด, แสงดี, หลายมุม | 3-5 ภาพ |
| **Product Photo** | รูปสินค้าบนพื้นขาว/พื้นสะอาด | คมชัด, packaging ชัด, branding ชัด | 1-3 ภาพ |
| **Background Photo** (optional) | รูปพื้นหลังที่ต้องการ | 9:16 ratio, แสงดี | 0-2 ภาพ |

### รายละเอียด Character Sheet (รูปนางแบด):

**ควรมีภาพหลายมุม:**
- ✅ ด้านหน้า (front view) - ใบหน้าชัดเจน
- ✅ ด้านข้าง (side profile) - โครงหน้าชัด
- ✅ 3/4 view - มุมที่ใช้บ่อยในวิดีโอ
- ✅ แสงต่างกัน (natural light, studio light) - เผื่อใช้ใน setting ต่างกัน
- ✅ ส่วนประกอบเด่น (close-up eyes, smile, hands) - เผื่อต้องการ focus

**รูปอย่าง:**
```
Character Sheet ภาพเดียวที่รวมหลายมุม:
┌─────────┬─────────┬─────────┐
│  หน้า    │  3/4    │  ข้าง   │
│ ตรง     │  view   │  profile │
├─────────┼─────────┼─────────┤
│  ยิ้ม   │  มือ   │  ท่า   │
│         │  closeup│  pose   │
└─────────┴─────────┴─────────┘
```

### รายละเอียด Product Photo (รูปสินค้า):

- ✅ **บนพื้นขาว** - ตัด background ง่าย
- ✅ **High resolution** - 1080x1080 ขึ้นไป
- ✅ **Branding ชัด** - logo, ชื่อสินค้า, colors ชัดเจน
- ✅ **หลายด้าน** - ด้านหน้า, ด้านข้าง, ด้านบน (ถ้าจำเป็น)

---

## Step 2: ใช้ Canvas Prompting สร้างภาพนิ่ง

### วิธีการใน Flow.ai Canvas:

#### Phase 1: อัปโหลด Reference Images

1. **เปิด Flow.ai** → เลือก "Canvas" หรือ "Image Generation"

2. **อัปโหลด Reference Images:**
   ```
   Upload:
   ├─ Model Character Sheet (หรือเลือกภาพที่ต้องการจาก sheet)
   ├─ Product Photo (รูปสินค้า)
   └─ Background Photo (ถ้ามี)
   ```

3. **วางใน Canvas:**
   ```
   Canvas Layout สำหรับ Scene 1:
   ┌─────────────────────────┐
   │                         │
   │   [Model Reference]     │
   │      (มุมบนซ้าย)       │
   │                         │
   │         +               │
   │                         │
   │   [Product Reference]   │
   │      (มุมล่างขวา)     │
   │                         │
   └─────────────────────────┘
   ```

#### Phase 2: Generate Scene 1 Image

**Canvas Prompt Template:**

```
Combine these reference images into a single vertical 9:16 image for TikTok video generation.

[CHARACTER]
Use the face and features from [MODEL REFERENCE IMAGE].
Maintain: facial structure, skin tone, hair texture, expression style.
The character should be wearing [SPECIFY OUTFIT: describe clothing clearly].

[PRODUCT]
The product should look EXACTLY like [PRODUCT REFERENCE IMAGE].
All packaging details, colors, branding, and design elements must match.

[SCENE COMPOSITION]
Create a natural scene where:
- The [model character] is holding the [product] in a natural pose
- Setting: [DESCRIBE SETTING: modern bathroom / living room / cafe]
- Lighting: [DESCRIBE LIGHTING: natural morning / warm golden / soft studio]
- Product and model face clearly visible

[STYLE]
Photorealistic, high quality, DSLR camera style.
Authentic UGC aesthetic, not overly polished.
Vertical 9:16 format.

[OUTPUT]
Generate a single still image combining these elements naturally.
```

**ตัวอย่าง Canvas Prompt (Scene 1):**

```
Combine these reference images into a single vertical 9:16 image.

[CHARACTER]
Use the Thai woman's face from the Model Reference image.
She has Southeast Asian features, warm medium skin tone, shoulder-length straight black hair.
Wearing a casual white cotton t-shirt.

[PRODUCT]
Use the serum bottle from Product Reference image.
Glass bottle with gold pump, premium packaging, branding clearly visible.

[SCENE]
The woman is holding the serum bottle in her right hand, lifting it toward the camera.
Setting: Modern Thai bathroom with white tiles and natural morning light.
Soft shadows, bright clean aesthetic.

[STYLE]
Photorealistic, UGC authentic style, vertical 9:16 format.
```

#### Phase 3: Capture “Last Frame” จาก Scene 1 (แนะนำ)

หลังจาก Animate Scene 1 แล้ว ให้จับภาพเฟรมท้าย (หรือเฟรมช่วงท้ายที่ pose สวยที่สุด) เพื่อใช้เป็นภาพตั้งต้นสำหรับ Animate Scene 2

**วิธีทำ (สั้นๆ):**
- เปิด Scene 1 video → pause ที่เฟรมท้าย
- Capture/Screenshot เฟรมนั้นเป็นไฟล์ภาพ (แนะนำ PNG/JPG, 9:16)
- ใช้ไฟล์ภาพนี้เป็น input ของการ Animate Scene 2 (แทนการสร้าง Scene 2 image ใหม่)

#### Phase 4 (Optional): Generate Scene 2 Image (Canvas)

**เตรียม Reference Images:**
- ใช้ Model Reference เดิม
- ใช้ Product Reference เดิม
- เพิ่ม Scene 1 Frame (จับภาพจาก Scene 1 video) เป็น reference สำหรับ continuity
- (fallback) ใช้ Scene 1 Generated Image เป็น reference แทนได้

**Canvas Prompt Template (Scene 2):**

```
Create a vertical 9:16 image continuing from Scene 1, using the SAME references.

[SAME CHARACTER - CRITICAL]
Use the EXACT SAME face from [MODEL REFERENCE IMAGE].
All features must match Scene 1:
- Same Southeast Asian features
- Same warm medium skin tone
- Same shoulder-length straight black hair
- SAME outfit: [repeat from Scene 1]

[SAME PRODUCT]
Use the EXACT SAME product from [PRODUCT REFERENCE IMAGE].
Product appearance must match Scene 1 perfectly.

[NEW ACTION]
Now the character is [DESCRIBE NEW ACTION]:
- [Option A] Applying product to face with gentle motions
- [Option B] Showing result with satisfied expression
- [Option C] Demonstrating usage clearly

[SAME SETTING or PROGRESSION]
Same [SETTING from Scene 1] or logically progressed (e.g., same bathroom, light slightly changed).
Lighting should feel continuous with Scene 1.

[STYLE]
Same photorealistic UGC style as Scene 1.
Vertical 9:16 format.

[CONSISTENCY NOTE]
This must look like a CONTINUATION of Scene 1.
Same person, same outfit, same setting, different action moment.
```

**ตัวอย่าง Canvas Prompt (Scene 2):**

```
Create vertical 9:16 image continuing from Scene 1, using SAME references.

[SAME CHARACTER]
Use the EXACT SAME Thai woman from Model Reference.
Southeast Asian features, warm medium skin tone, shoulder-length black hair.
Wearing the SAME white cotton t-shirt.

[SAME PRODUCT]
Use the EXACT SAME serum bottle from Product Reference.

[NEW ACTION]
Now she is applying the serum to her cheek with gentle patting motions.
She looks in the mirror with a satisfied smile.
Her skin shows a subtle healthy glow.

[SAME SETTING]
Same modern Thai bathroom with morning light as Scene 1.
Serum bottle visible on the counter.

[SAME STYLE]
Photorealistic UGC authentic style, vertical 9:16 format.
This is a CONTINUATION scene - must match Scene 1 perfectly.
```

---

## Step 3: สร้างวิดีโอจากภาพ (Image-to-Video)

### วิธีการใน Flow.ai:

#### Option A: Image-to-Video Direct (แนะนำ)

1. **เลือก Scene 1 Generated Image**
2. **คลิก "Animate" หรือ "Create Video"**
3. **ใส่ Video Prompt:**

**Scene 1 Video Prompt Template:**

```
Animate this image into an 8-second vertical video with Thai dialogue.

[DIALOGUE - Thai]
Woman speaks naturally in Thai:
"[1–2 short Thai sentences]"

[MOVEMENT DIRECTIONS]
The character should make subtle natural movements:
- Gentle hand/finger motion related to [action in image]
- Slight head movement or facial expression shift
- Subtle breathing motion, natural stance
- Small body sway for authenticity

[CAMERA WORK]
Handheld camera with gentle natural movement.
Slight zoom in or out (5-10%) to create depth.
Authentic UGC-style motion, not robotic or smooth.

[TECHNICAL]
8 seconds duration, vertical 9:16 format, 24 fps.
High quality animation.

[DIALOGUE LENGTH]
Keep the total spoken Thai dialogue short enough for 8 seconds (natural pace).

[NO GRAPHICS / NO TEXT OVERLAY]
No on-screen text, subtitles, captions, stickers, logos, watermarks, UI elements, graphic overlays, or animated typography.

[AUDIO]
Only the woman's voice speaking the Thai dialogue. No background music or sound effects.
```

**Scene 2 Video Prompt Template:**

```
Animate this image (captured last frame from Scene 1) into an 8-second vertical video with Thai dialogue, continuing from Scene 1.

[DIALOGUE - Thai]
Woman speaks naturally in Thai:
"[1–2 short Thai sentences]"

[SAME CHARACTER ANIMATION - CRITICAL]
The EXACT SAME person from Scene 1 with identical appearance.
Maintain: face, outfit, hair, product appearance.

[NEW MOVEMENT]
Character should demonstrate the action naturally:
- [If applying] Gentle patting/rubbing motion on face
- [If showing result] Satisfied smile emerging, admiring result
- [If demonstrating] Clear usage movements

[CONTINUOUS CAMERA]
Same handheld camera style and energy as Scene 1.
Natural movement that feels connected to Scene 1.

[TECHNICAL]
8 seconds, vertical 9:16, 24 fps.

[DIALOGUE LENGTH]
Keep the total spoken Thai dialogue short enough for 8 seconds (natural pace).

[NO GRAPHICS / NO TEXT OVERLAY]
No on-screen text, subtitles, captions, stickers, logos, watermarks, UI elements, graphic overlays, or animated typography.

[AUDIO]
Only the woman's voice speaking the Thai dialogue. No background music or sound effects.

[VISUAL CONSISTENCY]
Must visually match Scene 1 perfectly.
Same person, same outfit, same setting quality.
```

#### Option B: Canvas Video Generation

ถ้าต้องการความ consistent สูงสุด:

1. **อัปโหลด Scene 1 Generated Image**
2. **อัปโหลด Scene 2 Generated Image**
3. **ใช้ Canvas สร้างวิดีโอพร้อมกัน**
4. **Prompt:** `Animate both images with consistent style and movement. No on-screen text or graphic overlays.`

---

## Step 4: รวมวิดีโอ (Combine in SceneBuilder)

### ขั้นตอน:

1. **เปิด Flow SceneBuilder** (labs.google/flow)

2. **Add both videos:**
   - Drag Scene 1 Video to timeline
   - Drag Scene 2 Video after it

3. **Trim if needed:**
   - Scene 1: exactly 8 seconds
   - Scene 2: exactly 8 seconds
   - Total: 16 seconds

4. **Preview transition:**
   - Check consistency between scenes
   - Ensure smooth visual flow

5. **Download:**
   - Export as single MP4 file
   - File size should be under 500MB

---

## Complete Example: Cat Food Package with Canvas Prompting

### Input Reference Images:
- **Model Character Sheet:** Thai woman, 25 years old, shoulder-length hair, multiple angles (front, side, 3/4 view)
- **Product Photo:** Cat food package (bag or pouch), premium packaging, branding visible, cat imagery on package

### Step 1: Canvas Setup for Scene 1

**อัปโหลด:**
- Model Reference Image (เลือก front view)
- Product Reference Image (cat food package)

**Canvas Layout:**
```
┌─────────────────────┐
│  [Model Ref]    +    │
│  (ซ้ายบน)           │
│                     │
│       [Product]      │
│   (cat food package) │
└─────────────────────┘
```

### Step 2: Canvas Prompt - Scene 1 Image

```
Combine these reference images into a single vertical 9:16 image.

[CHARACTER]
Use the Thai woman's face from the Model Reference image.
She has Southeast Asian features, warm medium skin tone, shoulder-length straight black hair.
Wearing a casual cozy pastel-colored sweater or soft blouse.

[PRODUCT]
Use the cat food package from Product Reference image.
Premium packaging with branding clearly visible.
Package design, colors, and all details must match exactly.

[SCENE]
The woman is holding the cat food package in both hands, presenting it toward the camera with a warm friendly smile.
A cute cat is partially visible near her or looking at the package.
Setting: Cozy Thai living room with warm natural light, cat accessories visible in background.
Soft shadows, warm home aesthetic.

[STYLE]
Photorealistic, UGC authentic style, vertical 9:16 format.
Pet lover, trustworthy vibe.
```

**Generate:** สร้างภาพ 3-5 versions → เลือกที่ดีที่สุด

### Step 3: Scene 2 (แนะนำ: ใช้ Last Frame จาก Scene 1)

**เปลี่ยนเป็นวิธีใหม่ (แนะนำ): ใช้ Last Frame จาก Scene 1 แทนการสร้าง Scene 2 Image**

1. **Animate Scene 1** จากภาพ Scene 1 ที่เลือกไว้ → ได้ Scene 1 video (8s)
2. **จับภาพ Last Frame** (หรือเฟรมช่วงท้ายที่ pose สวยที่สุด) ออกมาเป็นไฟล์ภาพ (9:16)
3. **ใช้ไฟล์ภาพ Last Frame นี้เป็น input** ตอนกด Animate เพื่อสร้าง Scene 2 (ต่อเนื่องจาก Scene 1)

**(Optional) ถ้าต้องเปลี่ยน action/pose มากๆ ค่อยสร้าง Scene 2 image ด้วย Canvas**

**อัปโหลด (สำหรับ Optional Canvas):**
- Model Reference Image (เดิม)
- Product Reference Image (เดิม)
- Scene 1 Frame (captured from Scene 1 video) (เพิ่มเข้ามาเพื่อ continuity)

**Canvas Prompt (Optional):**

```
Create vertical 9:16 image continuing from Scene 1, using SAME references.

[SAME CHARACTER]
Use the EXACT SAME Thai woman from Model Reference.
Southeast Asian features, warm medium skin tone, shoulder-length black hair.
Wearing the SAME pastel-colored sweater or soft blouse.

[SAME PRODUCT]
Use the EXACT SAME cat food package from Product Reference.
Packaging must match Scene 1 perfectly.

[NEW ACTION]
Now she is pouring the cat food into a cute bowl while a cat looks excited and happy nearby.
She has a satisfied smile, showing she trusts this product for her pet.
The cat appears healthy and eager to eat.

[SAME SETTING]
Same cozy Thai living room with warm natural light as Scene 1.
Cat bowl and accessories visible.
The cat food package is open, showing the food inside.

[SAME STYLE]
Photorealistic UGC authentic style, vertical 9:16 format.
This is a CONTINUATION scene - must match Scene 1 perfectly.
Happy pet owner moment.
```

**Generate:** สร้างภาพ 3-5 versions → เลือกที่ดีที่สุด

### Step 4: Animate to Videos

**Scene 1 Video Prompt:**

```
Animate this image into an 8-second vertical video with Thai dialogue.

[DIALOGUE - Thai]
Woman speaks naturally in Thai:
"ทาสแมวต้องลอง! แมวรักอาหารนี้มากค่ะ"

[MOVEMENT]
The Thai woman should make subtle natural movements:
- Gentle hand motion holding up the cat food package
- Warm friendly smile with slight head nod
- Lips sync naturally to Thai dialogue
- Cat (if visible) makes subtle movements like tail wagging or head tilting
- Subtle breathing motion, natural stance

[CAMERA]
Handheld camera with gentle movement.
Slight zoom in to create depth.

[TECHNICAL]
8 seconds, vertical 9:16, 24 fps.

[NO GRAPHICS / NO TEXT OVERLAY]
No on-screen text, subtitles, captions, stickers, logos, watermarks, UI elements, graphic overlays, or animated typography.

[AUDIO]
Only the woman's voice speaking the Thai dialogue. No background music or sound effects.
```

**Scene 2 Video Prompt:**

```
Animate this image (captured last frame from Scene 1) into an 8-second vertical video with Thai dialogue, continuing from Scene 1.

[DIALOGUE - Thai]
Woman speaks naturally in Thai:
"ดูสิคะ แมวกินอิ่มขนาดนี้เลย วัตถุดิบดีจริงๆ ค่ะ"

[SAME CHARACTER]
The EXACT SAME woman with identical appearance and outfit.

[MOVEMENT]
She should demonstrate the food pouring naturally:
- Gentle pouring motion from package to bowl
- Lips sync naturally to Thai dialogue
- Cat makes excited movements (tail up, approaching bowl)
- Slight satisfied smile as she pours
- Natural hand and arm movements

[CAMERA]
Same handheld camera style as Scene 1.
Maybe slight movement to follow the pouring action.

[TECHNICAL]
8 seconds, vertical 9:16, 24 fps.

[NO GRAPHICS / NO TEXT OVERLAY]
No on-screen text, subtitles, captions, stickers, logos, watermarks, UI elements, graphic overlays, or animated typography.

[AUDIO]
Only the woman's voice speaking the Thai dialogue. No background music or sound effects.
```

### Step 5: Combine in SceneBuilder

1. Add Scene 1 Video (8s)
2. Add Scene 2 Video (8s)
3. Preview transition
4. Export as single MP4 (16 seconds)

---

## Canvas Prompt Templates พร้อมใช้

### Template 1: Cat Food Package Presentation (แนะนำอาหารแมว)

**Scene 1 Canvas Prompt:**

```
Combine these reference images into a single vertical 9:16 image.

[CHARACTER]
Use the face from [MODEL REFERENCE IMAGE].
Thai woman with Southeast Asian features, warm skin tone, black hair.
Wearing [SPEC OUTFIT: e.g., cozy pastel sweater, casual soft blouse].
Warm friendly, trustworthy pet owner appearance.

[PRODUCT]
Use cat food package from [PRODUCT REFERENCE IMAGE].
All packaging details, branding, colors, and design must match exactly.
Package should look premium and appealing.

[SCENE]
Woman holding [CAT FOOD PACKAGE] in both hands, presenting toward camera.
A cute cat is visible nearby, looking interested at the package.
Setting: [DESCRIBE: cozy living room / warm home space with cat accessories].
Natural bright warm lighting.

[STYLE]
Photorealistic, UGC authentic style, vertical 9:16 format.
Pet lover aesthetic, trustworthy vibe.
```

**Scene 2 Canvas Prompt:**

```
Create vertical 9:16 continuing image, using SAME references.

[SAME CHARACTER]
EXACT SAME woman from [MODEL REFERENCE].
SAME features, SAME [OUTFIT from Scene 1].

[SAME PRODUCT]
EXACT SAME cat food package from [PRODUCT REFERENCE].
Packaging must match Scene 1 perfectly.

[NEW ACTION]
Now [DESCRIBE ACTION]: pouring food into bowl / showing cat eating / demonstrating portion.
Cat looks excited, happy, and healthy.
Woman shows satisfied smile, indicating trust in product.

[SAME SETTING]
Same [SETTING] as Scene 1.
Cat bowl and accessories visible.
Lighting consistent with Scene 1.

[SAME STYLE]
Photorealistic UGC style, vertical 9:16.
CONTINUATION of Scene 1.
Happy pet owner moment.
```

**Scene 1 Video Prompt with Thai Dialogue:**

```
Animate this image into an 8-second vertical video with Thai dialogue.

[DIALOGUE - Thai]
Woman speaks naturally in Thai:
"ทาสแมวต้องลอง! แมวรักอาหารนี้มากค่ะ"

[MOVEMENT]
- Gentle hand motion holding up the cat food package
- Lips sync naturally to Thai dialogue
- Warm friendly smile with slight head nod
- Cat makes subtle movements
- Natural breathing motion

[CAMERA]
Handheld camera with gentle movement.
Slight zoom in to create depth.

[TECHNICAL]
8 seconds, vertical 9:16, 24 fps.

[NO GRAPHICS / NO TEXT OVERLAY]
No on-screen text, subtitles, captions, stickers, logos, watermarks, UI elements, graphic overlays, or animated typography.

[AUDIO]
Only the woman's voice speaking the Thai dialogue. No background music or sound effects.
```

**Scene 2 Video Prompt with Thai Dialogue:**

```
Animate this image (captured last frame from Scene 1) into an 8-second vertical video with Thai dialogue, continuing from Scene 1.

[DIALOGUE - Thai]
Woman speaks naturally in Thai:
"ดูสิคะ แมวกินอิ่มขนาดนี้เลย วัตถุดิบดีจริงๆ ค่ะ"

[MOVEMENT]
- Gentle pouring motion from package to bowl
- Lips sync naturally to Thai dialogue
- Cat makes excited movements (tail up, approaching)
- Slight satisfied smile as she pours

[CAMERA]
Same handheld camera style as Scene 1.

[TECHNICAL]
8 seconds, vertical 9:16, 24 fps.

[NO GRAPHICS / NO TEXT OVERLAY]
No on-screen text, subtitles, captions, stickers, logos, watermarks, UI elements, graphic overlays, or animated typography.

[AUDIO]
Only the woman's voice speaking the Thai dialogue. No background music or sound effects.
```

---

### Template 2: Product Introduction (แนะนำสินค้าทั่วไป)

**Scene 1 Canvas Prompt:**

```
Combine these reference images into a single vertical 9:16 image.

[CHARACTER]
Use the face from [MODEL REFERENCE IMAGE].
Thai woman with Southeast Asian features, warm skin tone, black hair.
Wearing [SPEC OUTFIT: e.g., casual white top].

[PRODUCT]
Use product from [PRODUCT REFERENCE IMAGE].
All packaging details and branding must match.

[SCENE]
Woman holding [PRODUCT NAME] in hand toward camera.
Setting: [DESCRIBE: modern bathroom / clean living room].
Natural bright lighting.

[STYLE]
Photorealistic, UGC authentic style, vertical 9:16 format.
```

**Scene 2 Canvas Prompt:**

```
Create vertical 9:16 continuing image, using SAME references.

[SAME CHARACTER]
EXACT SAME woman from [MODEL REFERENCE].
SAME features, SAME [OUTFIT from Scene 1].

[SAME PRODUCT]
EXACT SAME product from [PRODUCT REFERENCE].

[NEW ACTION]
Now [DESCRIBE ACTION]: applying/using/showing product.
Satisfied expression, demonstrating result.

[SAME SETTING]
Same [SETTING] as Scene 1.
Lighting consistent with Scene 1.

[SAME STYLE]
Photorealistic UGC style, vertical 9:16.
CONTINUATION of Scene 1.
```

---

### Template 2: Before → After (ปัญหา → ผลลัพธ์)

**Scene 1 Canvas Prompt:**

```
Combine reference images into vertical 9:16 image.

[CHARACTER]
Use face from [MODEL REFERENCE IMAGE].
Thai woman, Southeast Asian features.
Skin shows [PROBLEM: dullness / dryness / concern visible].

[SCENE]
Woman looking concerned in [SETTING].
Touching [problem area] gently.
Natural lighting, muted tones.

[STYLE]
Photorealistic, relatable moment, vertical 9:16.
```

**Scene 2 Canvas Prompt:**

```
Create vertical 9:16 continuing image, using SAME references.

[SAME CHARACTER]
EXACT SAME woman from [MODEL REFERENCE].
SAME features, SAME appearance.

[TRANSFORMATION]
Now skin shows [RESULT: glowing / smooth / radiant].
Confident satisfied smile.
[PRODUCT from PRODUCT REFERENCE] visible nearby.

[SAME SETTING]
Same [SETTING] as Scene 1.
Lighting now brighter and warmer.

[SAME STYLE]
Photorealistic, optimistic mood, vertical 9:16.
Transformative CONTINUATION scene.
```

---

### Template 3: Lifestyle Integration (การใช้ชีวิตประจำวัน)

**Scene 1 Canvas Prompt:**

```
Combine reference images into vertical 9:16 image.

[PRODUCT FOCUS]
Use product from [PRODUCT REFERENCE IMAGE].
Product close-up on clean surface.
Rotated to show branding and details.

[STYLE]
Professional lighting, minimalist background.
Premium aesthetic, vertical 9:16 format.
```

**Scene 2 Canvas Prompt:**

```
Create vertical 9:16 lifestyle image, using SAME references.

[CHARACTER]
Use face from [MODEL REFERENCE IMAGE].
Thai woman with Southeast Asian features.
Wearing [STYL OUTFIT].

[INTEGRATION]
[PRODUCT from PRODUCT REFERENCE] naturally in scene.
Woman in [LIFESTYLE SETTING: cafe / balcony / living room].
She's [USING PRODUCT naturally].

[STYLE]
Lifestyle aesthetic, authentic moment.
Natural lighting, vertical 9:16 format.
```

---

## Quick Reference Canvas Commands

### Canvas Layout Tips:

```
┌──────────────────────────┐
│                          │
│   [Model Ref]  [Prod]   │  ← Scene 1: Character intro
│                          │
└──────────────────────────┘

┌──────────────────────────┐
│                          │
│   [Model]  [S1 Frame]    │  ← (Optional) Scene 2 still (Canvas)
│   [Prod]                 │     add Scene 1 frame for continuity
│                          │
└──────────────────────────┘
```

### Canvas Prompt Keywords:

| ส่วนประกอบ | Keywords สำคัญ |
|------------|---------------|
| **Character** | "Use face from [MODEL REFERENCE]", "EXACT SAME", "Maintain features" |
| **Product** | "Match [PRODUCT REFERENCE]", "All details must match", "Branding visible" |
| **Consistency** | "SAME outfit", "CONTINUATION scene", "Must match Scene 1" |
| **Setting** | "Same [location]", "Lighting consistent", "Natural progression" |

---

## Tips สำหรับ Canvas Prompting Workflow

### ข้อดีของ Canvas Prompting:

| ข้อดี | คำอธิบาย |
|-------|-----------|
| **Perfect Product Match** | สินค้าเหมือนรูป reference 100% |
| **Consistent Character** | ใบหน้าเหมือน Character Sheet ทุกครั้ง |
| **Better Control** | ควบคุม composition ผ่านการวางรูปใน Canvas |
| **Easy Iteration** | แก้ภาพง่าย สร้างใหม่ได้เร็ว |
| **Professional Results** | คุณภาพสูงกว่า text-only prompt |

### Canvas Prompting Best Practices:

#### 1. Prepare Quality References

**Character Sheet Requirements:**
- ✅ 3-5 ภาพขั้นต่ำ (front, side, 3/4 view, smile, serious)
- ✅ แสงดี ใบหน้าชัด (no harsh shadows on face)
- ✅ High resolution (1080p ขึ้นไป)
- ✅ หลายมุมมองเผื่อเลือกใช้

**Product Photo Requirements:**
- ✅ บนพื้นขาวหรือพื้นสะอาด
- ✅ Branding ชัด (logo, ชื่อสินค้า, colors)
- ✅ หลายด้านถ้าจำเป็น (ด้านหน้า, ด้านข้าง)
- ✅ คมชัดไม่ภูมิ

#### 2. Generate Multiple Versions

```
Scene 1: Generate 3-5 images
   ├─ Version 1: Best match to reference
   ├─ Version 2: Alternative angle
   ├─ Version 3: Different lighting
   └─ Select BEST for video generation

Scene 2: Generate 3-5 images
   ├─ Use Scene 1 generated image as reference
   ├─ Match outfit and setting exactly
   └─ Select BEST for continuity
```

#### 3. Save Intermediate Assets

**Save Strategy:**
```
Project Folder/
├─ References/
│   ├─ model_character_sheet.jpg
│   └─ product_photo.png
├─ Scene_1_Generated/
│   ├─ scene1_v1.png (selected)
│   ├─ scene1_v2.png
│   └─ scene1_v3.png
├─ Scene_2_Generated/
│   ├─ scene2_v1.png (selected)
│   └─ scene2_v2.png
└─ Final_Videos/
    ├─ scene1_video.mp4
    └─ scene2_video.mp4
```

#### 4. Consistency Checking

**Before animating to video, check:**

| Check Point | Scene 1 | Scene 2 | Match? |
|------------|---------|---------|--------|
| Face structure | ✓ | ✓ | ✅ |
| Skin tone | ✓ | ✓ | ✅ |
| Hair style | ✓ | ✓ | ✅ |
| Outfit | White t-shirt | White t-shirt | ✅ |
| Setting | Bathroom | Bathroom | ✅ |
| Product details | Gold pump | Gold pump | ✅ |

**ถ้าไม่ match:** Regenerate ด้วย prompt ที่เน้น consistency มากขึ้น

#### 5. Use Reference Images Effectively

**Canvas Layout Strategy:**

```
Scene 1 (Character Introduction):
┌─────────────────────────┐
│  [Model Ref]    +       │
│                         │
│        [Product]        │
└─────────────────────────┘

Scene 2 (Action/Result):
┌─────────────────────────┐
│  [Model Ref] [S1 Frame] │  ← Add Scene 1 frame!
│                         │
│  [Product]              │
└─────────────────────────┘
```

**Key (Optional):** ถ้าสร้าง Scene 2 image ด้วย Canvas ให้เพิ่ม Scene 1 Frame (จับภาพจาก Scene 1 video) เข้าไปใน Canvas เพื่อให้ AI เห็น continuity (fallback: ใช้ Scene 1 Generated Image)

---

## Common Canvas Prompting Issues & Solutions

### Issue 1: Character looks different between scenes

**Symptoms:**
- Face structure changes
- Skin tone different
- Hair style doesn't match

**Solutions:**

1. **Use SAME reference image for both scenes**
   ```
   Scene 1: Use Model_Ref_Front.jpg
   Scene 2: Use SAME Model_Ref_Front.jpg (NOT different angle)
   ```

2. **(Optional) If generating Scene 2 image in Canvas: add Scene 1 frame (captured from Scene 1 video) to Scene 2 canvas**
   ```
   Scene 2 Canvas:
   - Model Reference (original)
   - Product Reference (original)
    - Scene 1 Frame (captured from Scene 1 video) (NEW - for continuity)
      (fallback: Scene 1 Generated Image)
   ```

3. **Use stronger consistency keywords**
   ```
   Prompt: "EXACT SAME face", "IDENTICAL features",
   "MUST match Scene 1", "CONTINUATION scene"
   ```

### Issue 2: Product doesn't match reference

**Symptoms:**
- Packaging details wrong
- Colors off
- Branding missing

**Solutions:**

1. **Use high-quality product photo**
   - 1080x1080 ขึ้นไป
   - บนพื้นขาว
   - Branding ชัดเจน

2. **Mention product details explicitly**
   ```
   [PRODUCT]
   Glass bottle with gold pump (from Product Reference).
   Blue label with white text visible.
   "Radiance Serum" branding clearly shown.
   ```

3. **Place product prominently in Canvas**
   - วางไว้ตำแหน่งที่เด่น
   - ไม่บังอยู่หลัง character

### Issue 3: Scene transition feels abrupt

**Symptoms:**
- Jump cut feeling
- Setting looks different
- Lighting doesn't match

**Solutions:**

1. **Use "CONTINUATION" keywords**
   ```
   "CONTINUATION of Scene 1"
   "Must feel connected to previous scene"
   "Natural progression from Scene 1"
   ```

2. **Specify lighting continuity**
   ```
   Scene 1: "Natural morning light from left window"
   Scene 2: "SAME morning light, slightly brighter"
   ```

3. **Add bridging action**
   ```
   Scene 1 ends: "...holding product, about to use"
   Scene 2 starts: "continuing from holding, now applying..."
   ```

### Issue 4: Generated images have artifacts

**Symptoms:**
- Extra fingers
- Distorted product
- Glitchy areas

**Solutions:**

1. **Generate multiple versions**
   - สร้าง 3-5 versions
   - เลือกที่สะอาดสุด

2. **Use cleaner references**
   - รูป reference ไม่ควรมี artifact อยู่แล้ว
   - Crop ส่วนที่ใช้งานได้ออก

3. **Regenerate with modified prompt**
   - เน้น "clean", "no distortion", "natural appearance"

---

## Checklist ก่อน Generate

### Pre-Generation (ก่อนเริ่ม):

**Reference Images:**
- [ ] Model Character Sheet พร้อม (3-5 ภาพ: front, side, 3/4 view)
- [ ] Product Photo พร้อม (บนพื้นขาว, branding ชัด, คมชัด)
- [ ] Background Photo (ถ้าต้องการ) - 9:16 ratio

**Canvas Setup:**
- [ ] Model Reference อัปโหลดแล้ว
- [ ] Product Reference อัปโหลดแล้ว
- [ ] Canvas layout วางเรียบร้อย

**Scene 1 Prompt:**
- [ ] Canvas prompt เขียนเสร็จ (ใช้ Model Ref + Product Ref)
- [ ] Outfit ระบุชัดเจน
- [ ] Setting ระบุชัดเจน
- [ ] Action ระบุชัดเจน

### Scene 1 Generation:

**Generate & Review:**
- [ ] สร้างภาพ 3-5 versions
- [ ] เลือกภาพที่ดีที่สุด
- [ ] Save Scene 1 selected image
- [ ] Check: Character face เหมือน reference?
- [ ] Check: Product เหมือน reference?
- [ ] Check: Overall quality ดี?

### Scene 2 Generation:

**Canvas Setup:**
- [ ] Model Reference (เดิม) อัปโหลดแล้ว
- [ ] Product Reference (เดิม) อัปโหลดแล้ว
- [ ] Scene 1 Generated Image เพิ่มเข้ามาเพื่อ continuity

**Scene 2 Prompt:**
- [ ] Canvas prompt เขียนเสร็จ
- [ ] "EXACT SAME" keywords ใช้แล้ว
- [ ] "CONTINUATION" keywords ใช้แล้ว
- [ ] Outfit ซ้ำจาก Scene 1
- [ ] Setting ซ้ำจาก Scene 1

**Generate & Review:**
- [ ] สร้างภาพ 3-5 versions
- [ ] เลือกภาพที่ดีที่สุด
- [ ] Save Scene 2 selected image
- [ ] Check: Character เหมือน Scene 1 หรือไม่?
- [ ] Check: Product เหมือน Scene 1 หรือไม่?
- [ ] Check: Setting เหมือน Scene 1 หรือไม่?

**Consistency Check:**
| Element | Scene 1 | Scene 2 | Match? |
|---------|---------|---------|--------|
| Face | [ ] | [ ] | [ ] ✅ |
| Skin tone | [ ] | [ ] | [ ] ✅ |
| Hair | [ ] | [ ] | [ ] ✅ |
| Outfit | [ ] | [ ] | [ ] ✅ |
| Setting | [ ] | [ ] | [ ] ✅ |
| Product | [ ] | [ ] | [ ] ✅ |

**ถ้าไม่ match → Regenerate ด้วย prompt ที่เน้น consistency มากขึ้น**

### Video Generation:

**Scene 1 Video:**
- [ ] Scene 1 image selected
- [ ] Video prompt: "Animate into 8-second video"
- [ ] Movement directions specified
- [ ] Camera style specified
- [ ] Generate 8s video
- [ ] Review quality

**Scene 2 Video:**
- [ ] Scene 2 image selected
- [ ] Video prompt: "Animate continuing from Scene 1"
- [ ] "EXACT SAME" keywords used
- [ ] Camera continuity specified
- [ ] Generate 8s video
- [ ] Review quality

**Video Quality Check:**
- [ ] Scene 1: 8 seconds ✅
- [ ] Scene 2: 8 seconds ✅
- [ ] Both scenes: 9:16 vertical ✅
- [ ] Character consistent between videos ✅
- [ ] Smooth transition feel ✅

### Final Export:

**SceneBuilder Assembly:**
- [ ] Scene 1 Video added to timeline
- [ ] Scene 2 Video added after Scene 1
- [ ] Trim to exactly 8s each (16s total)
- [ ] Preview transition
- [ ] Check flow and continuity
- [ ] Export as single MP4

**Final Quality Check:**
- [ ] Total duration: 16 seconds ✅
- [ ] Aspect ratio: 9:16 vertical ✅
- [ ] File size: < 500MB ✅
- [ ] Format: MP4 ✅
- [ ] Product visible and clear ✅
- [ ] Thai cultural elements (if applicable) ✅

**Ready for TikTok Shop:**
- [ ] พร้อมอัปโหลด TikTok Shop ✅

---

## Quick Summary Workflow

```
┌─────────────────────────────────────────────────────────┐
│ STEP 1: Prepare References                              │
│ ├─ Model Character Sheet (3-5 images)                   │
│ └─ Product Photo (white background, clear branding)     │
└─────────────────────────────────────────────────────────┘
                          ↓
┌─────────────────────────────────────────────────────────┐
│ STEP 2: Generate Scene 1 Image (Canvas)                 │
│ ├─ Upload: Model Ref + Product Ref                      │
│ ├─ Prompt: "Combine these references..."                │
│ └─ Generate 3-5 → Select BEST                           │
└─────────────────────────────────────────────────────────┘
                          ↓
┌─────────────────────────────────────────────────────────┐
│ STEP 3: Animate Scene 1 → Capture Frame                 │
│ ├─ Animate Scene 1 image → 8s video                     │
│ └─ Capture 1 frame (screenshot/export) for continuity   │
└─────────────────────────────────────────────────────────┘
                          ↓
┌─────────────────────────────────────────────────────────┐
│ STEP 4: Animate Scene 2 (from Scene 1 last frame)       │
│ ├─ Select Scene 1 last-frame image as input             │
│ └─ Animate → 8s video (continuation)                    │
└─────────────────────────────────────────────────────────┘
                          ↓
┌─────────────────────────────────────────────────────────┐
│ STEP 5: Combine in SceneBuilder                         │
│ ├─ Add both videos (8s + 8s)                            │
│ ├─ Preview & Trim to 16s total                          │
│ └─ Export MP4 → Ready for TikTok Shop                   │
└─────────────────────────────────────────────────────────┘
```

---

## Key Takeaways

### Canvas Prompting Workflow Advantages:

1. **รูปสินค้าเหมือน 100%** - ใช้ Product Reference โดยตรง
2. **ใบหน้านางแบบเหมือน 100%** - ใช้ Character Sheet โดยตรง
3. **Consistency สูง** - ใช้ Scene 1 frame (จับภาพจากวิดีโอ) เป็น reference ตอนสร้าง Scene 2
4. **คุมได้ดีกว่า** - วางรูปใน Canvas เพื่อกำหนด composition
5. **แก้ไขง่าย** - Regenerate ภาพได้เร็ว ไม่ต้องเริ่มใหม่ทั้งหมด

### Critical Success Factors:

| Factor | Best Practice |
|--------|---------------|
| **Reference Quality** | High-res, clear face, clear branding |
| **Multiple Versions** | Generate 3-5 images per scene |
| **Consistency Keywords** | "EXACT SAME", "CONTINUATION", "MUST match" |
| **Scene 1 last frame** | Use a captured Scene 1 last-frame image as the input for Scene 2 animate |
| **Check Before Animate** | Verify consistency before video generation |

---

*Canvas Prompting Workflow Guide สำหรับ Veo 3 Image-to-Video*
*Optimized สำหรับ TikTok Shop Thailand Market*
*Updated: January 14, 2025*
