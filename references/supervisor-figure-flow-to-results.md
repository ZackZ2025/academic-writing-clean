# Turning supervisor figure-flow comments into polished Results prose

Use this reference when a user provides PI/supervisor comments about Figure logic, panel placement, experimental indicators, or supplement/main-figure allocation, but asks for a manuscript Results narrative.

## Core lesson

Do not deliver a Figure-flow plan when the requested output is a Results section. Figure logistics are scaffolding; the manuscript deliverable is paragraph-style evidence narration.

A common failure mode:

1. The supervisor asks practical questions: where to place primary cells, LPS validation, OE conditions, non-target cell controls.
2. The agent answers those questions as bullets and then writes a Figure-by-Figure planning document.
3. The user wanted the previous polished Results style: finding-based headings and continuous paragraphs.

Avoid this. Answer placement questions only as needed to determine the evidence chain, then rewrite the manuscript text.

## Recommended workflow

1. Extract the supervisor's intended Figure logic.
2. Resolve placement questions briefly:
   - Which data belong in main figures vs supplements?
   - Which indicators are core vs optional?
   - Which branches are validation only and should not steal the main story?
3. Convert the flow into finding-based Results subheadings, not `Fig1/Fig2` logistics.
4. Write each subsection in continuous prose:
   - rationale/purpose;
   - key observation;
   - supporting assays/readouts;
   - local conclusion;
   - transition to the next evidence layer.
5. Put unresolved figure-placement or evidence gaps at the end as a short checklist.
6. If making a DOCX, keep the DOCX clean: manuscript prose first, planning notes only if the user explicitly wants them included.

## Style rules

- "High-level" or "高级感" means controlled evidence progression, not decorative adjectives.
- Avoid bullet-heavy main output unless the user specifically asks for an outline.
- Avoid writing `建议内容`, `推荐指标`, `核心问题` as the body of a Results draft. Those are planning labels.
- If the user asks for **最小修改原则**, keep the original paragraph frame and only make the changes required to satisfy the correction. Do not redesign the section, renumber the whole story, or insert a display checklist unless requested.
- If the user asks to output **directly in chat**, do not create a file just because the previous step involved DOCX editing.
- Use finding-based subheadings:
  - Good: `抑制 SMS2 可恢复 ALP 功能并减轻 IH 诱导的小胶质细胞炎症反应`
  - Weak for manuscript prose: `Fig2. 抑制 SMS2 改善 ALP、氧化应激和炎症`
- If the user says "参考上一个版本的写法", re-open or recall the previous Results narrative and match its prose structure.

## Pitfall: mechanism prose vs mechanism checklist

When a user supplies a target such as "溶酶体鞘脂组学并入机制，检测 Ca²⁺、扰动 CaN/TRPML1，观察 p-TFEB、TFEB 核转位、ALP、ROS、炎症", convert it into continuous Results prose:

1. State why the next experiment was done.
2. Report the main direction of the result.
3. Name only the key assays/readouts as support.
4. Conclude narrowly.

Do **not** write a paragraph ending with "结果展示：①...②...③..." unless the user specifically wants figure-planning notes. That is useful scaffolding but bad manuscript Results prose.

## Evidence-boundary reminders

- Do not invent p values, fold changes, sample sizes, panel numbers, or completed experiments.
- If supervisor comments include proposed experiments not yet done, either omit from Results or write them as pending checks outside the Results text.
- Validation branches such as LPS, primary microglia, OE condition choice, or 3T3 controls should be folded into the narrative only if the data exist; otherwise list as figure-planning notes.
- Keep banned/removed molecules or corrected nomenclature out of both the prose and the audit notes unless the user explicitly asks for a before/after record.

## Mini-template

```markdown
### [Finding-based heading]

为明确[question]，我们首先/进一步[assay/model]. 结果显示，[main direction]. [Supporting readouts]共同提示[bounded finding].

为了判断该变化是否具有[necessity/sufficiency/cell specificity]，我们进一步[intervention/rescue/control]. [Result]. 这一结果说明，[narrow conclusion], 并为后续[mechanism/translation]提供依据。
```
