# Abstract Markdown-to-Word Sync Notes

Use this when a biomedical manuscript workspace has split Markdown source files and an integrated Word draft, and the user says they edited `摘要.md` / `Abstract` in Markdown.

## Workflow

1. Treat the Markdown abstract as the source of truth unless the user explicitly says the Word draft has newer manual edits.
2. Before editing, inspect the control layer for evidence boundaries and terminology:
   - `论文总纲.md`
   - `术语统一表.md`
   - `待确认问题.md`
3. Make only narrow abstract edits unless the user asked for a rewrite.
4. Back up both the Markdown source and the active Word draft before writing.
5. Synchronize the Word Abstract and Highlights from the Markdown source.
6. Verify section-by-section, not by filename or timestamp:
   - Extract the Word Abstract paragraphs up to `Introduction`.
   - Convert Markdown abstract lines to comparable plain paragraphs by removing Markdown bold markers and the `# Abstract` heading.
   - Compare exact paragraph count and exact paragraph text.
7. Update the project change log for meaningful edits.

## Evidence-boundary checks that matter in this project class

- Use `obstructive sleep apnea (OSA)` and `intermittent hypoxia (IH)` rather than informal hybrids such as `OSA/IH` when defining terms.
- Use `5×FAD mice`, not `5xFAD`, `5XFAD`, or casual `FAD mice`.
- Define `broad-spectrum antibiotics (ABX)` at first abstract mention if ABX appears.
- Prefer cautious causal language when the abstract compresses a multi-step mechanism:
  - Safer: `is linked to an M3G–EGLN3/ferroptosis-associated pathway`
  - Riskier: `through an M3G–EGLN3/ferroptosis pathway` if direct in vivo closure is incomplete.
- For brain M3G changes, prefer `preservation` or `availability` when the data do not prove increased synthesis/generation.
- Do not promote supplementary validation models or unresolved omics plans into headline abstract claims.

## Word implementation note

If the number of Highlights changes, do not just patch existing paragraphs. Insert or remove Word paragraphs before the next section heading, usually `Introduction`, while preserving paragraph properties. Then verify the extracted Word abstract exactly matches Markdown.