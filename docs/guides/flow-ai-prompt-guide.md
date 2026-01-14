# Flow.ai (Veo) Prompt Guide สำหรับ TikTok Shop

> คู่มือการเขียน Prompt สร้างวิดีโอด้วย Flow.ai / Google Veo เพื่อติดตะกร้าสินค้า TikTok Shop
>
> อัปเดต: 2026-01-13

---

## Table of Contents

1. [Flow.ai & Veo คืออะไร?](#flowai--veo-คืออะไร)
2. [หลักการเขียน Prompt พื้นฐาน](#หลักการเขียน-prompt-พื้นฐาน)
3. [Prompt Templates สำหรับ TikTok Shop](#prompt-templates-สำหรับ-tiktok-shop)
4. [Canvas Prompting Technique](#canvas-prompting-technique)
5. [JSON Prompt Format](#json-prompt-format)
6. [Thai-Specific Prompts](#thai-specific-prompts)
7. [Best Practices](#best-practices)
8. [แหล่งข้อมูลอ้างอิง](#แหล่งข้อมูลอ้างอิง)

---

## Flow.ai & Veo คืออะไร?

**Flow** คือแพลตฟอร์มสร้างวิดีโอด้วย AI ของ Google ที่ใช้โมเดล **Veo** (ปัจจุบันเวอร์ชัน 3.1)

### ความสามารถหลัก

| ฟีเจอร์ | คำอธิบาย |
|---------|-----------|
| **Text-to-Video** | สร้างวิดีโอจากข้อความ prompt |
| **Image-to-Video** | แปลงรูปภาพสินค้าเป็นวิดีโอ |
| **Canvas Prompting** | ใช้ภาพหลายๆ ภาพมาประกอบเป็นวิดีโอ |
| **9:16 Vertical** | รองรับวิดีโอแนวตั้งสำหรับ TikTok |
| **Native Audio** | สร้างเสียงประกอบได้อัตโนมัติ |
| **Consistent Characters** | สร้าง AI influencer ที่มีใบหน้าเดิมได้ |

---

## หลักการเขียน Prompt พื้นฐาน

### โครงสร้าง Prompt ที่ดี

```
[Subject] + [Action] + [Setting/Environment] + [Style] + [Technical Specs]
```

### องค์ประกอบสำคัญ

| องค์ประกอบ | ตัวอย่าง | หมายเหตุ |
|-------------|----------|---------|
| **Subject** | "A young Thai woman", "The skincare product" | ระบุชัดเจน |
| **Action** | "applying cream", "holding product", "demostrating" | กริยาชัดเจน |
| **Setting** | "modern Thai living room", "clean white studio" | บริบทแวดล้อม |
| **Style** | "UGC-style", "authentic", "cinematic", "casual" | โทนของวิดีโอ |
| **Camera** | "close-up shot", "slow motion", "360 rotation" | มุมกล้อง |
| **Lighting** | "soft natural lighting", "studio lighting" | แสง |
| **Technical** | "vertical 9:16", "30 seconds", "high quality" | ข้อกำหนดเทคนิค |

### ข้อห้ามในการเขียน Prompt

- ❌ อย่าใช้เครื่องหมายคำพูด (quotation marks)
- ❌ อย่าใช้ prompt ยาวเกินไป (สั้น กระชับ ชัดเจนดีกว่า)
- ❌ อย่ารวมหลาย scene ไว้ใน prompt เดียว (เน้น 1 scene ต่อ 1 video)

---

## Prompt Templates สำหรับ TikTok Shop

### Template 1: Product Reveal (เปิดตัวสินค้า)

```
A 30-second vertical TikTok video (9:16) featuring [PRODUCT NAME].
Camera slowly zooms in on the product placed on a clean white surface.
Soft studio lighting with subtle shadows. Professional product photography style.
The product rotates 360 degrees to show all angles.
Minimalist background, focus entirely on the product.
High quality, 4K resolution.
```

### Template 2: UGC Style Review (รีวิวแบบเป็นกันเอง)

```
A 25-second vertical TikTok video (9:16).
A young Thai woman with Southeast Asian features, warm skin tone, holding [PRODUCT NAME] in her hand.
She is smiling naturally and showing the product to camera.
Casual authentic setting, looks like user-generated content.
Natural window lighting, handheld camera movement.
She demonstrates using the product.
Friendly and genuine expression, like recommending to a friend.
```

### Template 3: Before/After Transformation

```
A 35-second vertical TikTok video (9:16) split screen effect.
Left side: Before using [PRODUCT], right side: After using [PRODUCT].
Smooth transition between states.
Clear visual difference showing product effectiveness.
Professional lighting, clean background.
Text overlay space at bottom for caption.
Optimistic and inspiring mood.
```

### Template 4: Lifestyle Scenario (การใช้ชีวิตประจำวัน)

```
A 30-second vertical TikTok video (9:16).
A person in a modern Thai home setting using [PRODUCT NAME] in their daily routine.
Warm cozy atmosphere, natural lighting.
Genuine candid moments, not staged.
Multiple quick shots showing product in different contexts.
Authentic lifestyle photography style.
Soft background music vibe.
```

### Template 5: Feature Highlight (เน้นฟีเจอร์)

```
A 20-second vertical TikTok video (9:16).
Extreme close-up shot of [PRODUCT NAME]'s key feature.
Slow motion to highlight detail.
Macro lens style, crystal clear focus.
Minimalist dark background for contrast.
Text-friendly space for bullet points.
Premium luxury aesthetic.
```

### Template 6: Unboxing Experience

```
A 40-second vertical TikTok video (9:16).
First-person POV opening [PRODUCT] packaging.
Hands carefully unboxing, showing excitement.
Clean well-lit table surface.
Authentic unboxing experience.
Product reveal moment with dramatic lighting.
Package design details visible.
Satisfying unboxing ASMR vibe.
```

### Template 7: Multiple Product Showcase

```
A 30-second vertical TikTok video (9:16).
Three [PRODUCT CATEGORY] items arranged artistically on a modern surface.
Each product gets spotlight: camera pans from one to another.
Dynamic transitions between products.
Cohesive color scheme and styling.
Professional flat lay photography style.
Clean, organized aesthetic.
```

### Template 8: Problem-Solution Format

```
A 35-second vertical TikTok video (9:16).
First 10 seconds: Show the problem [PAIN POINT].
Next 20 seconds: Introduce [PRODUCT] as the solution.
Last 5 seconds: Satisfied result with product.
Relatable scenarios, authentic emotions.
Clear visual narrative arc.
Engaging storytelling approach.
```

---

## Canvas Prompting Technique

### Canvas Prompting คืออะไร?

**Canvas Prompting** เป็นเทคนิคที่ใช้ภาพหลายๆ ภาพมา "วาด" โครงสร้างวิดีโอ แทนการพิมพ์ prompt ยาวๆ

### ขั้นตอน Canvas Prompting

```
Step 1: เตรียมภาพต้นฉบับ
   ├─ ภาพสินค้า (Product Image)
   ├─ ภาพคน/Model (Person Image)
   └─ ภาพพื้นหลัง (Background Image)

Step 2: Upload ภาพทั้งหมดลงใน Flow.ai

Step 3: จัดวางตำแหน่งใน Canvas
   ├─ ระบุว่าภาพไหนอยู่ตรงไหน
   ├─ กำหนดขนาดและสัดส่วน
   └─ กำหนดความสัมพันธ์ระหว่าง elements

Step 4: เขียน prompt สั้นๆ เสริม
   └─ "Combine these elements naturally"

Step 5: Generate Video
```

### ตัวอย่าง Canvas Prompting สำหรับสินค้า

**Input Images:**
1. Product photo (ภาพสินค้าบนพื้นขาว)
2. Thai model photo (ภาพคนไทยถ่ายแบบ)
3. Lifestyle background (ภาพห้องนั่งเล่นสไตล์ไทย)

**Prompt:**
```
Combine these images into a natural product demonstration video.
The Thai woman should hold the skincare product naturally in the modern living room setting.
Seamless integration, authentic feel, UGC-style.
Vertical 9:16 format, 25 seconds.
```

### ข้อดีของ Canvas Prompting

| ข้อดี | คำอธิบาย |
|-------|-----------|
| **Control มากขึ้น** | กำหนด layout และ composition ได้ละเอียด |
| **Consistent** | สินค้า/คน/พื้นหลังเหมือนต้นฉบับ |
| **Professional** | เหมาะกับ brand videos |
| **Flexible** | ปรับ layout ได้ง่าย |

---

## JSON Prompt Format

### JSON Prompt คืออะไร?

สำหรับการใช้ Flow.ai ผ่าน API หรือ n8n automation สามารถใช้ JSON format ได้

### JSON Structure พื้นฐาน

```json
{
  "prompt": "A Thai woman holding skincare product",
  "aspect_ratio": "9:16",
  "duration_seconds": 30,
  "style": "UGC-style authentic",
  "camera": "handheld natural movement",
  "lighting": "soft natural window light"
}
```

### JSON Prompt สำหรับ Product Video

```json
{
  "prompt": "A young Thai woman demonstrating facial cleanser in modern bathroom",
  "product_name": "Gentle Foam Cleanser",
  "aspect_ratio": "9:16",
  "duration_seconds": 25,
  "resolution": "1080x1920",
  "style": {
    "overall": "authentic UGC",
    "lighting": "natural bright",
    "camera": "handheld slightly shaky",
    "mood": "friendly and genuine"
  },
  "subject": {
    "appearance": "Southeast Asian Thai features",
    "age": "25-30 years old",
    "expression": "natural smile"
  },
  "action": "applying product to face, showing result",
  "setting": "modern Thai bathroom with natural light",
  "audio": {
    "type": "background_music",
    "mood": "upbeat trending"
  }
}
```

### ใช้กับ n8n Automation

```json
{
  "nodes": [
    {
      "type": "Webhook",
      "name": "Receive Product Info"
    },
    {
      "type": "OpenAI Chat Model",
      "name": "Generate Prompt",
      "prompt": "Create a Veo video prompt for {{product_name}} targeting Thai audience"
    },
    {
      "type": "HTTP Request",
      "name": "Call Flow API",
      "url": "https://api.flow.ai/generate",
      "body": {
        "prompt": "{{$json.prompt}}",
        "aspect_ratio": "9:16"
      }
    }
  ]
}
```

---

## Thai-Specific Prompts

### Prompts สำหรับคนไทย (Thai Audience)

### Beauty & Skincare (ความงาม)

```
A 30-second vertical TikTok video (9:16).
A young Thai woman with Southeast Asian features, warm skin tone, applying face serum.
Gentle patting motion on cheeks and forehead.
Modern Thai bathroom background with natural sunlight.
Soft, glowing complexion visible.
Authentic UGC style, handheld camera.
She smiles satisfied with the result.
Text overlay friendly.
```

### Fashion (แฟชั่น)

```
A 25-second vertical TikTok video (9:16).
Thai fashion model walking in a trendy Bangkok cafe area.
Wearing a casual white dress, twirling to show the outfit.
Natural confident walk, candid moments.
Trendy cafe background, blurred depth of field.
Golden hour lighting, warm tones.
Fashion photography style but authentic.
Multiple quick outfit showcase shots.
```

### Food Supplements (อาหารเสริม)

```
A 30-second vertical TikTok video (9:16).
Collagen supplement bottle on a clean white surface.
Camera circles around the product elegantly.
Next to a glass of water and fresh fruits.
Fresh, healthy aesthetic.
Soft studio lighting, premium feel.
Slow motion pour of supplement into water.
Clean and minimal design.
```

### Electronics (อิเล็กทรอนิกส์)

```
A 35-second vertical TikTok video (9:16).
Close-up of wireless earbuds in a Thai person's ear.
Modern Bangkok skyline background at night.
Person listening to music, enjoying the moment.
Cinematic city lights bokeh effect.
Premium tech aesthetic.
Multiple angle shots of product features.
Lifestyle demonstration.
```

### Home & Living (ของใช้ในบ้าน)

```
A 30-second vertical TikTok video (9:16).
Modern Thai living room with smart home device.
Person using voice command to control device.
Cozy warm lighting, plants in background.
Contemporary Thai interior design.
Authentic daily life moment.
Natural and relaxed atmosphere.
Product fits seamlessly into home.
```

### Keywords สำหรับ Thai Market

เพิ่ม keywords เหล่านี้ใน prompt ถ้าต้องการให้เหมาะกับคนไทย:

| Keyword | ใช้เมื่อ |
|---------|----------|
| "Southeast Asian appearance" | ต้องการหน้าตาคนไทย/เอเชีย |
| "Thai features" | คนไทยโดยเฉพาะ |
| "warm skin tone" | สีผิวเหมาะกับคนไทย |
| "Bangkok urban setting" | ฉากเมืองกรุงเทพฯ |
| "Thai modern home" | บ้านสไตล์ไทยยุคใหม่ |
| "tropical vibe" | บรรยากาศเขตร้อน |
| "Thai cafe aesthetic" | คาเฟ่สไตล์ไทย |

---

## Best Practices

### 1. เริ่มต้นด้วย Prompt ที่ละเอียด

- ✅ ใช้คำอธิบายที่ชัดเจนและเฉพาะเจาะจง
- ✅ ระบุ subject, action, setting อย่างชัดเจน
- ✅ ใส่ technical specs (9:16, 30s, quality)

### 2. ใช้ Gemini ช่วยเขียน Prompt

ตามคำแนะนำจาก Google:
- ถ้าไม่รู้จะเขียน prompt ยังไง ให้ขอความช่วยเหลือจาก Gemini
- Prompt: "Help me write a Veo prompt for [product] targeting Thai audience"

### 3. อิงรายละเอียดจากหน้าร้าน (กันเคลมลอย/พูดผิดสเปก)

ก่อนเขียนบทพูด/voiceover ให้ดึงข้อมูลจากหน้าเว็บขายของมาเป็น reference แล้วใช้ข้อมูลนั้นเป็น “กรอบ” สำหรับบทพูด:

- Workflow: `docs/workflows/product-description-to-dialogue-workflow.md`
- Template: `docs/templates/product-details-sheet.md`

### 4. Focus on Transformation ไม่ใช่แค่ Product

ตามที่ผู้เชี่ยวชาญแนะนำ:
> "A good Veo prompt doesn't show off the product. It shows off the transformation."

- ❌ "Show the skincare bottle"
- ✅ "A woman's skin becoming glowing and radiant after applying the serum"

### 4. เน้น Scene เดียวต่อ 1 Video

- ✅ 1 scene = 1 video (30-45 วินาที)
- ❌ หลาย scene ผสมกัน (จะสับสน)

### 5. ทดสอบหลายๆ Version

สร้าง 3-5 versions ของ prompt เดียวกัน:
- Version 1: UGC style
- Version 2: Cinematic style
- Version 3: Lifestyle scenario
- Version 4: Feature focus
- Version 5: Before/after

แล้วดูว่าอันไหน perform ดีสุด

### 6. ใช้ Canvas Prompting สำหรับ Brand Video

ถ้าต้องการ:
- สินค้าตรงกับรูป 100%
- ใบหน้า model เหมือนต้นฉบับ
- Brand consistency

ให้ใช้ **Canvas Prompting** ไม่ใช่ text prompt เท่านั้น

### 7. เพิ่ม Audio Specifications

ใน prompt ให้ระบุ audio ด้วย:
```
...with upbeat trending background music
...with soft satisfying ASMR sounds
...with Thai voiceover narration
```

### 8. ปล่อยให้ AI สร้างสรรค์

อย่า micro-manage ทุกอย่าง:
- ✅ "Natural camera movement"
- ❌ "Camera pans left 15 degrees, then right 20 degrees..."

---

## แหล่งข้อมูลอ้างอิง

### Official Google Resources

- [5 Tips for Getting Started with Flow](https://blog.google/innovation-and-ai/products/flow-video-tips/) - Google Blog
- [Veo on Vertex AI Prompt Guide](https://docs.cloud.google.com/vertex-ai/generative-ai/docs/video/video-gen-prompt-guide) - Official Docs
- [Best Practices for Veo on Vertex AI](https://docs.cloud.google.com/vertex-ai/generative-ai/docs/video/best-practice) - Official Guidelines
- [Ultimate Prompting Guide for Veo 3.1](https://cloud.google.com/blog/products/ai-machine-learning/ultimate-prompting-guide-for-veo-3-1) - Google Cloud Blog

### Prompt Examples & Templates

- [Best Veo 3 Prompts (2025)](https://skywork.ai/blog/best-veo-3-prompts-2025/) - 18 Copy-Paste Prompts
- [Veo 3 Video Prompt Examples](https://www.powtoon.com/blog/veo-3-video-prompt-examples/) - Powtoon Guide
- [30+ Viral-Ready Veo 3 Prompt Examples](https://filmora.wondershare.com/ai-prompt/veo3-prompt.html) - Filmora
- [50+ Veo Prompt Ideas for Marketing](https://aifreeforever.com/blog/50-veo-prompt-ideas-for-marketing-videos-ready-to-use-templates/) - Ready Templates

### Product Videos & E-commerce

- [Veo 3.1 for Product Demo Videos](https://skywork.ai/blog/ai-video/veo-3-1-for-product-demo-videos/) - Product Demo Guide
- [How to Create Product Videos with AI](https://www.veo3ai.io/blog/how-to-create-product-videos) - Veo3 AI Blog
- [Best AI Prompts for Image-to-Video](https://productvideo.ai/blog/best-ai-prompts-for-image-to-video) - Product Video AI

### Canvas Prompting Tutorials

- [Put Real Products into AI Video Ads](https://www.youtube.com/watch?v=2Yh2borU9Bs) - YouTube Tutorial
- [How to Put Products Into Google Veo 3](https://www.youtube.com/watch?v=hSqznXKbp9Y) - Full Tutorial
- [How To Create Cinema-Quality UGC with Canvas Prompting](https://www.linkedin.com/posts/mike-futia-108709126_veo-3-canvas-prompting-is-soooo-good-activity-7363966216723472386-zFij) - LinkedIn Post

### Vertical Video for TikTok

- [VEO 3 9:16: Everything You Need to Know](https://pixpretty.tenorshare.ai/ai-insights/veo-3-9-16.html) - Vertical Guide
- [How to Create Vertical Videos with Google Veo 3](https://www.youtube.com/watch?v=CPa72s1kvRg) - YouTube Tutorial
- [Generate AI Viral Videos with VEO 3 for TikTok](https://n8n.io/workflows/8642-generate-ai-viral-videos-with-veo-3-and-upload-to-tiktok/) - n8n Workflow

### GitHub & Community

- [Veo-3-Prompting-Guide](https://github.com/snubroot/Veo-3-Prompting-Guide) - GitHub Guide
- [veo3-prompt-generator](https://github.com/shijincai/veo3-prompt-generator) - Prompt Generator Tool
- [Google VEO 3 Prompt Playbook](https://www.scribd.com/document/918677202/Google-VEO-3-Prompt-Playbook) - PDF Playbook

### JSON & API

- [Veo 3 JSON Prompt Format](https://www.architjn.com/blog/veo-3-json-prompt-format-beats-generic-prompts) - JSON Guide
- [JSON Prompting Guide for Veo 3](https://www.imagine.art/blogs/veo-3-json-prompting-guide) - ImagineArt
- [Creating Viral Ads with JSON Prompts](https://key-g.com/blog/how-to-create-viral-ads-with-json-prompts-using-google-veo-3/) - JSON Tutorial

---

## Quick Reference

### Prompt Structure Formula

```
[Subject] + [Action] + [Setting] + [Style] + [Technical Specs]
```

### Example for Thai Skincare Product

```
A young Thai woman applying face serum in modern bathroom,
gentle patting motion on cheeks, natural sunlight,
authentic UGC style, handheld camera,
vertical 9:16, 30 seconds, high quality
```

### Thai Keywords Checklist

- [ ] Southeast Asian appearance
- [ ] Thai features
- [ ] Warm skin tone
- [ ] Bangkok/Thai setting
- [ ] Tropical vibe

### Technical Checklist

- [ ] Vertical 9:16 format
- [ ] 1080x1920 resolution
- [ ] 20-45 seconds duration
- [ ] MP4 format output
- [ ] No quotation marks
- [ ] Single scene focus

---

*เอกสารนี้รวบรวมข้อมูลจากแหล่งข้อมูลอย่างเป็นทางการของ Google และชุมชนผู้ใช้งาน ณ มกราคม 2026*
