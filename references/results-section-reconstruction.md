# Results section reconstruction from messy manuscript notes

Use this reference when a user asks to turn a rough Results outline, figure-by-figure notes, or a `.docx` draft into a polished Results section and optional visual reading aid.

## Trigger

- Rough Results text is organized as figure notes, assay lists, mixed Chinese/English bullets, or lab-log chronology.
- User asks for a more "advanced", cinematic, logical, or publication-ready Results narrative.
- The task is to output Markdown/HTML rather than directly overwrite the source Word file.

## Safe workflow

1. Extract the source text from `.docx` without editing the original file.
2. Identify the evidence chain before rewriting:
   - phenomenon/model validation;
   - candidate target;
   - pathway or downstream node;
   - mechanism/interaction;
   - cell-to-cell consequence;
   - intervention/delivery system;
   - in vivo or translational validation.
3. Convert figure notes into finding-based Results subheadings.
4. For each section, write in the sequence: purpose -> observed finding -> supporting assays/readouts -> narrow result-level conclusion -> bridge to the next section.
5. Preserve evidence boundaries. Do not invent sample sizes, P values, fold changes, figure panels, reagent details, animal details, citations, or causal certainty.
6. If the source has contradictions or placeholders, keep the main narrative conservative and list the unresolved items at the end.
7. If making an HTML visual aid, use it to show the narrative architecture, not to replace the manuscript text. A useful structure is: one-line thesis, pathway chain, act/scene summary, figure-by-figure timeline, and a hard-issues box.
8. Verify generated files exist and contain the expected major sections before final response.

## Style rule

"Cinematic" scientific Results writing does not mean decorative prose. It means each result behaves like the necessary next shot in a sequence. The polish comes from clean causality, proportionate emphasis, and disciplined transitions, not from adjectives.

## Common hard-issue checklist

Flag these explicitly rather than smoothing them over:

- conflicting direction of the same result in different parts of the draft;
- figure numbering collisions;
- pathway terms or chemical symbols that appear mistyped;
- sudden appearance of a major upstream molecule without prior data;
- empty citation markers or literature-dependent mechanistic background inside Results;
- use of "significant" without visible statistics;
- claims that jump from association to mechanism or treatment implication.

## Hard-issue resolution pass

When the user starts resolving the hard-issue list after a reconstruction, treat it as a second editing pass, not just a chat discussion:

1. Re-open the reconstructed Markdown and visual HTML if present, plus the original extracted notes when needed.
2. Separate issues into:
   - user-confirmed corrections that can be applied immediately;
   - evidence-supported corrections from authoritative lookup;
   - items that still require figure panels, raw statistics, Methods, or author confirmation.
3. Apply user-confirmed corrections across all generated deliverables, not only the prose file. Typical examples:
   - unify gene/protein nomenclature exactly as requested;
   - correct result directionality (e.g., up/down in a specific cell type);
   - correct phosphosite or pathway notation;
   - remove a molecule/pathway from the narrative if the user says it should not appear.
4. Add or update a short `*_硬伤处理记录.md` / issue-resolution note when several corrections were made. Keep it a decision table: issue -> action -> current wording -> still needed.
5. Verify the corrected files no longer contain banned old terms or stale contradictions by searching the generated Markdown, HTML, and issue log. Do not leave old terms alive inside the "resolved issues" section unless the user explicitly wants a before/after audit; use neutral wording like "旧位点" or "错误钙符号" instead.
6. Preserve unresolved items as explicit remaining checks. Do not fake figure numbering, P values, reagent details, targeting peptide names, or BBB evidence.

## Output pattern

For this class of task, produce at least:

- `*_结果部分重构稿.md` for the manuscript-ready Results narrative;
- optional `*_结果部分重构可视化.html` for human review of the evidence chain;
- a concise final note listing files created and unresolved evidence gaps.
