# รายงานวิจัย: จุดแข็งของ Gemini CLI vs Codex CLI vs Claude Code และแนวทางมอบหมายงาน

> หมายเหตุ: ไฟล์นี้คงชื่อเดิม (2025-01-14) เพื่อคงลิงก์ย้อนหลัง แต่ “เนื้อหา” อัปเดตเป็นฉบับ 2026-01-14 และเหมือนกับไฟล์ `research/cli-tools-comparison-gemini-codex-claude-2026-01-14.md`

**Research Date:** 2026-01-14  
**คำถามหลัก:** “Gemini CLI, Codex CLI, Claude Code เก่งด้านไหน?” เพื่อเลือกเครื่องมือให้เหมาะกับงานแต่ละประเภท

---

## สรุปผู้บริหาร

- **Codex CLI เด่นด้าน workflow แบบ agent พร้อมระบบ approvals + reviewer + automation**: เอกสารระบุทั้ง interactive TUI ที่อ่าน repo/แก้ไฟล์/รันคำสั่ง, approval modes, `/review`, `exec`, `resume`, image inputs และ web search แบบ opt-in [5][8][11]
- **Claude Code เด่นด้านการทำงานแบบ “คิดก่อนแก้” ผ่าน Plan Mode + ชุด tools/permission ที่ละเอียด**: เอกสารระบุ Plan Mode/permission mode และชุดเครื่องมือ (อ่าน/เขียน/แก้ไฟล์, shell, web fetch/search, hooks ฯลฯ) [2][3][9]
- **Gemini CLI เด่นด้าน context ใหญ่ + toolchain ที่ออกแบบมาครบ + sandboxing**: README ระบุ Gemini 2.5 Pro และ 1M token context window รวมถึง built-in tools (Google Search grounding, file ops, shell, web fetch) และ MCP; docs ระบุ sandboxing แบบ Seatbelt/Docker/Podman และวิธีเปิดผ่าน flag/env/settings [6][7][10]

**ข้อเสนอแนะหลัก:** ใช้ **Codex CLI** สำหรับ “รีวิว/automation/งานที่ต้อง approvals”, ใช้ **Claude Code** สำหรับ “วางแผนก่อนแก้/งานหลายขั้นที่ต้อง tool + permission ชัด”, และใช้ **Gemini CLI** เมื่อ “ต้องอ่าน context ใหญ่มาก/อยากใช้ search grounding + sandboxing” [2][5][6]

**ระดับความเชื่อมั่น:** กลาง-สูง (อิงจากเอกสาร/README อย่างเป็นทางการของแต่ละเครื่องมือเป็นหลัก แต่ผลลัพธ์จริงยังขึ้นกับรุ่นโมเดล การตั้งค่า sandbox/permission และบริบทงาน) [3][5][7]

---

## ผลลัพธ์สมมติฐาน

| สมมติฐาน | Prior | Posterior | สถานะ | หลักฐานหลัก |
|----------|-------|-----------|-------|-------------|
| Codex CLI เหมาะสุดสำหรับรีวิว/automation และงานที่ต้อง approvals | 60% | 85% | ✅ ยืนยัน | [5], [8], [11] |
| Claude Code เหมาะสุดสำหรับ plan-first และงานซับซ้อนหลายขั้นที่ต้องการ permission/tooling ชัด | 60% | 80% | ✅ ยืนยัน | [2], [3], [9] |
| Gemini CLI เหมาะสุดสำหรับงานที่ต้องอ่าน context ใหญ่มาก + ต้องการ toolchain + sandboxing | 55% | 80% | ✅ ยืนยัน | [6], [7], [10] |

**สมมติฐาน Contrarian:** “Gemini CLI ไม่ได้เด่นเฉพาะ multimodal แต่เด่นที่ ‘tooling + sandboxing + context’ สำหรับงาน dev ในเทอร์มินัล” → เอกสารเน้น toolchain/sandboxing และ context window อย่างชัดเจน [6][7]

---

## บทนำ

### คำถามวิจัย
เครื่องมือ CLI ด้าน agentic coding ที่คนใช้กันมากในช่วงนี้ ได้แก่ **Gemini CLI**, **Codex CLI**, และ **Claude Code** — แต่ละตัวมีจุดแข็ง/ข้อจำกัดอะไร และควรมอบหมายงานแบบไหนให้เหมาะที่สุด?

### ขอบเขต
โฟกัสที่ “ความสามารถของตัว CLI/workflow/เครื่องมือในตัว/การตั้งค่า sandbox & permission/การรองรับ web search & review” ตามเอกสารอย่างเป็นทางการ ไม่ได้ทดสอบ benchmark คุณภาพโค้ด/ความฉลาดของโมเดลเชิงตัวเลข

---

## การวิเคราะห์หลัก

### Finding 1: Codex CLI ออกแบบมาเพื่อ workflow “review + approvals + automation” ชัดเจน
**Claim:** Codex CLI มีองค์ประกอบที่ทำให้เหมาะกับงานรีวิวและงานที่ต้องการคุมความเสี่ยง ได้แก่ `/review` presets, approval modes, transcript/resume, และ `exec` สำหรับ headless automation [5]  
**Evidence:** เอกสาร Codex CLI features อธิบาย `/review`, `exec`, `resume`, approval modes และการเปิด web search แบบ opt-in [5] และหน้าโมเดล Codex ระบุโมเดลแนะนำสำหรับ agentic coding เช่น `gpt-5.2-codex` [8]

### Finding 2: Claude Code เด่นที่ “plan-first + permission system + tools” สำหรับงานหลายขั้น
**Claim:** Claude Code มี Plan Mode และระบบ permission mode สำหรับวิเคราะห์/ถาม requirement ก่อนแก้ และมีชุด tools ที่ครอบคลุมงาน dev (อ่าน/แก้/เขียนไฟล์, shell, web fetch/search, hooks ฯลฯ) [2][3]  
**Evidence:** เอกสาร common workflows อธิบาย Plan Mode และการเริ่มด้วย `--permission-mode plan` [2] และหน้าการตั้งค่าระบุรายการ tools พร้อม permission required รวมถึง hooks [3] โดย README ระบุว่า Claude Code เป็น agentic coding tool ที่อยู่ในเทอร์มินัลและช่วยทำงานกับโค้ดเบสโดยตรง [1]

### Finding 3: Gemini CLI เด่นที่ “context + built-in tools + sandboxing”
**Claim:** Gemini CLI ถูกวางตำแหน่งเป็น open-source AI agent ในเทอร์มินัลที่เน้นการเข้าถึง Gemini โดยตรง พร้อม built-in tools และ extension ผ่าน MCP และมี sandboxing เป็นระบบ [6][7]  
**Evidence:** README ระบุ “Gemini 2.5 Pro”, “1M token context window”, built-in tools (Google Search grounding, file ops, shell commands, web fetching), MCP และ free tier [6] ขณะที่เอกสาร sandbox ระบุวิธี sandboxing (Seatbelt/Docker/Podman) และการเปิดผ่าน flag/env/settings [7]

---

## การสังเคราะห์และข้อมูลเชิงลึก

### แผนมอบหมายงานแบบ “เลือกเครื่องมือให้ตรงงาน”

1) **รีวิวก่อนส่ง PR / ตรวจความเสี่ยงของ diff** → **Codex CLI** (`/review`) [5]  
2) **งานหลายขั้นที่อยากได้ “แผนก่อนแก้”** → **Claude Code** (Plan Mode) [2]  
3) **งาน automation/headless** (เช่นทำงานซ้ำๆ ในสคริปต์) → **Codex CLI** (`codex exec ...`) [5]  
4) **งานอ่านข้อมูลปริมาณมากในครั้งเดียว + ต้องการ toolchain และ sandbox** → **Gemini CLI** [6][7]

### แนวคิดสำคัญ: “สิ่งที่ทำให้ CLI เก่ง” มักไม่ใช่โมเดลอย่างเดียว
จากเอกสารทางการ จุดเด่นของแต่ละตัวมักมาจาก **workflow primitives** เช่น approvals/permission modes, review presets, sandboxing, tool APIs และการ resume session [2][5][7]

---

## สมมติฐานที่ซ่อนอยู่

- คุณมีสิทธิ์ติดตั้งเครื่องมือและล็อกอิน/ตั้งค่า auth ตามที่แต่ละเครื่องมือกำหนด [4][6][9]
- คุณยอมรับ/ตั้งค่า permission และ sandboxing ให้เหมาะกับความเสี่ยงของ repo และงานที่ทำ [3][5][7]
- งานที่มอบหมายเป็น “งาน dev ในเทอร์มินัล” (ไม่ใช่การวัดคุณภาพโมเดลเชิง benchmark)

---

## ข้อจำกัดและข้อควรระวัง

- รายงานนี้ยืนยัน “ความสามารถที่เอกสารระบุ” ไม่ได้ทดสอบประสิทธิภาพจริงแบบ benchmark
- ตัวเลข context window ที่ระบุยืนยันได้ชัดใน Gemini CLI README (1M) แต่ฝั่งอื่น “ขึ้นกับโมเดล/การตั้งค่า” จึงไม่ใส่ตัวเลขที่ไม่มีแหล่งอ้างอิงตรง [6]
- Web search ของ Codex CLI เป็น **opt-in** และอาจต้องปรับ config/sandbox network access [5]

---

## ข้อเสนอแนะ

1) ตั้ง “policy ปลอดภัย” เป็นค่าเริ่มต้น: งานใหม่/โค้ดไม่คุ้น → ใช้ Plan Mode (Claude) หรือ approvals (Codex) และเปิด sandbox เมื่อจำเป็น [2][5][7]  
2) ถ้าทีมทำงานแบบ PR-heavy: ให้ Codex CLI เป็น “review bot ในเทอร์มินัล” ด้วย `/review` [5]  
3) ถ้าต้องการอ่าน/สรุปข้อมูลมหาศาล/เอกสารใหญ่: ให้ Gemini CLI เป็น “context sweeper” แล้วค่อยส่งผลลัพธ์ให้ tool อื่นทำ implementation ต่อ [6]

---

## บรรณานุกรม

[1] Anthropic. (n.d.). “Claude Code” (README). https://raw.githubusercontent.com/anthropics/claude-code/main/README.md (สืบค้นเมื่อ: 2026-01-14)  
[2] Anthropic. (n.d.). “Common workflows - Claude Code Docs”. https://code.claude.com/docs/en/common-workflows (สืบค้นเมื่อ: 2026-01-14)  
[3] Anthropic. (n.d.). “Settings - Tools available to Claude”. https://code.claude.com/docs/en/settings (สืบค้นเมื่อ: 2026-01-14)  
[4] OpenAI. (n.d.). “Codex CLI” (README). https://raw.githubusercontent.com/openai/codex/main/README.md (สืบค้นเมื่อ: 2026-01-14)  
[5] OpenAI Developers. (2026). “Codex CLI features”. https://developers.openai.com/codex/cli/features (สืบค้นเมื่อ: 2026-01-14)  
[6] Google. (n.d.). “Gemini CLI” (README). https://raw.githubusercontent.com/google-gemini/gemini-cli/main/README.md (สืบค้นเมื่อ: 2026-01-14)  
[7] Gemini CLI Docs. (2026). “Sandboxing in the Gemini CLI”. https://geminicli.com/docs/cli/sandbox/ (สืบค้นเมื่อ: 2026-01-14)  
[8] OpenAI Developers. (2026). “Codex Models”. https://developers.openai.com/codex/models (สืบค้นเมื่อ: 2026-01-14)  
[9] Anthropic. (n.d.). “Claude Code overview”. https://code.claude.com/docs/en/overview (สืบค้นเมื่อ: 2026-01-14)  
[10] Gemini CLI Docs. (2026). “Welcome to Gemini CLI documentation”. https://geminicli.com/docs/ (สืบค้นเมื่อ: 2026-01-14)  
[11] OpenAI Developers. (2026). “Codex (Overview)”. https://developers.openai.com/codex/ (สืบค้นเมื่อ: 2026-01-14)  

---

## ภาคผนวก: วิธีการวิจัย

### กระบวนการวิจัย
ใช้กระบวนการแบบ Standard tier: เก็บข้อมูลจากเอกสาร/README ทางการของแต่ละเครื่องมือ (Codex docs/CLI features, Claude Code docs/settings, Gemini CLI docs/README) แล้วสังเคราะห์เป็น “ข้อค้นพบ → แนวทางมอบหมายงาน” โดยยึดหลักว่า “ข้อเท็จจริงที่สำคัญต้องมีแหล่งอ้างอิงในประโยคเดียวกัน”

**การดำเนินการตามเฟส:**
- เฟส LANDSCAPE/RETRIEVE: ดึงเอกสารทางการ (README + docs) ของ 3 เครื่องมือ [1][4][6] และเอกสารคุณสมบัติหลัก (features/settings/sandbox/models/overview) [2][3][5][7][8][9][10][11]
- เฟส TRIANGULATE: ตรวจว่าข้อความสำคัญในสรุป/ข้อค้นพบมีหลักฐานอย่างน้อย 1–2 แหล่ง และไม่ใส่ตัวเลขที่ไม่มีแหล่งตรง
- เฟส SYNTHESIZE: แปลงเป็น playbook สำหรับมอบหมายงานตามประเภทงาน

### ตารางข้อเท็จจริง-หลักฐาน

| ID | ข้อเท็จจริงหลัก | ประเภทหลักฐาน | แหล่งสนับสนุน | ความเชื่อมั่น |
|----|-----------------|---------------|---------------|---------------|
| C1 | Codex CLI มี `/review`, approvals, `exec`, `resume`, image inputs และ web search แบบ opt-in | เอกสารทางการ | [5] | สูง |
| C2 | Claude Code มี Plan Mode/permission mode และชุด tools (read/edit/write/shell/web) | เอกสารทางการ | [2], [3] | สูง |
| C3 | Gemini CLI ระบุ 1M token context (Gemini 2.5 Pro) + built-in tools + MCP + sandboxing | เอกสารทางการ | [6], [7] | สูง |

---

## ข้อมูลรายงาน

**โหมดวิจัย:** Standard  
**แหล่งทั้งหมด:** 11  
**จำนวนคำ:** โดยประมาณ 900–1,300 คำ  
**สร้างเมื่อ:** 2026-01-14  
**สถานะการตรวจสอบ:** ผ่าน (ตาม template ของ deep-research)  
