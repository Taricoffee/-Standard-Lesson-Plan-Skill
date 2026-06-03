---
name: standard-lesson-plan
description: Create or revise Chinese art lesson-plan Word documents into the user's standard “两江新区实验中学三段五学六有思维型生命课堂” format. Use when the user asks to turn a courseware file, textbook pages, an existing教案, or a备课指南 document into a standardized lesson plan; when they mention using the final 《花卉的秘密》 version as the template; or when they ask to delete the备课指南 section/AI赋能说明 and output a Word document named by the课题.
---

# Standard Lesson Plan

## Purpose

Convert source material into the user's preferred final deliverable:

- A Word `.docx` named by the lesson topic, e.g. `花卉的秘密.docx`.
- Keep only the lesson-plan table headed `两江新区实验中学“三段五学六有”思维型生命课堂（教案）`.
- Remove the upper `备  课  指  南` matrix/table and any `AI赋能说明`.
- Preserve the writing style of the final `花卉的秘密.docx`: compact but complete, with seven closed-loop sections and explicit 三段五学六有 language.

Use the Documents skill for Word work and render QA when possible.

## Workflow

1. **Read sources**
   - Inspect the provided Word/PPT/PDF/images and any existing lesson plan.
   - If a template is provided, read its paragraphs and tables first.
   - If textbook images are unreadable, say so and use available local/source materials only with a clear note.

2. **Extract the lesson core**
   - Identify: 课题、年级/课时、教材内容、主要作品/案例、核心知识点、学习任务、作业/评价要求.
   - For art lessons, keep discipline language concrete: 形态、结构、色彩、构图、线条、纹样、写生、装饰、图像叙事、审美感知、艺术表现、创意实践、文化理解.

3. **Rewrite into seven sections**
   - 学情分析（起点分析）
   - 教学目标（发展愿景）
   - 方法路径（实施路径）
   - 精准点拨（关键干预）
   - 评测反馈（效果检验）
   - 学力建设（能力奠基）
   - 教学反思（基础知识掌握和思维品质提升方面的主要问题及整改措施）

4. **Use the required writing pattern**
   - In `学情分析`, include `【起点分析】` and `【三段对应】`.
   - In `教学目标`, include numbered goals plus `教学重点：` and `教学难点：`.
   - In `方法路径`, use:
     - `一、情境导入（5-8分钟，导学+自学）`
     - `二、探究建构（20-25分钟，自学+互学+评学）`
     - `三、迁移应用（10-15分钟，创学+评学）`
   - In `精准点拨`, include 情境衔接、探究过程、思维方法、迁移脚手架.
   - In `评测反馈`, include 情境导入、探究建构、迁移应用 and measurable达标要求.
   - In `学力建设`, include 学法训练、学习习惯、分层巩固、作业设计.
   - In `教学反思`, include `课后重点反思：` and `整改措施：`.

5. **Final cleanup**
   - Delete any upper `备  课  指  南` paragraphs and the guide matrix table.
   - Delete all text containing `AI赋能说明`.
   - Save as `<课题>.docx` in the same working/output folder unless the user specifies another folder.

## Style Constraints

- Write in Chinese, teacher-facing, contest-ready language.
- Keep each section dense and practical, like `花卉的秘密`: usually 200-450 Chinese characters per section.
- Make objectives observable and evaluable.
- Explicitly mention 三段、五学、六有 where natural; include 导学、自学、互学、评学、创学.
- Avoid generic AI-sounding filler. Tie all tasks to the actual lesson content and student learning evidence.
- Do not leave `AI赋能说明` in the final topic-named Word unless the user specifically asks for it.

## Script

Use `scripts/clean_topic_docx.py` when a generated/received file still contains the guide section or AI note and only needs final cleanup:

```bash
python scripts/clean_topic_docx.py input.docx --out-dir /path/to/output
```

The script removes the first table when the document contains multiple tables, removes `备课指南` title paragraphs, removes `AI赋能说明`, infers the topic from the first row of the remaining lesson table, and saves `<课题>.docx`.
