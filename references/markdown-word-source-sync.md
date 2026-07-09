# Markdown-source / Word-candidate synchronization for manuscript workspaces

Use this when a project keeps split Markdown manuscript sections (for example `Abstract.md`, `Methods.md`, `Results.md`) plus an integrated `.docx` candidate.

## Core rule
If the workspace defines Markdown as the source of truth, never treat a direct Word edit as complete. Any Word edit must be reconciled back into the corresponding Markdown section before final delivery.

## Required workflow
1. Read the workspace rules (`AGENTS.md`, `CLAUDE.md`, or equivalent) before editing.
2. Identify source-of-truth files and integrated Word candidates.
3. If multiple `.docx` candidates exist, avoid destructive overwrite unless the user explicitly confirms the active file.
4. Back up active Markdown source files and relevant `.docx` files to the workspace-approved archive/backup location.
5. Extract Word section text and compare it against each Markdown source section.
6. If Chinese comments/visible notes were resolved in Word first, backfill those edits into Markdown immediately. This is not optional cleanup; it is the actual correction.
7. Convert unresolved Chinese metadata placeholders into English placeholders rather than inventing facts, e.g.:
   - `[supplier information to be confirmed]`
   - `[approval number to be inserted]`
   - `[catalog number to be inserted]`
   - `[dose to be inserted]`
8. Translate manuscript section headings to English in both Markdown and Word when requested.
9. Preserve citation/reference placeholder style unless the task explicitly asks to reformat references.
10. Verify the final `.docx` against Markdown section-by-section, not just by timestamp or filename.
11. Write a change report stating which source files changed, whether the Word candidate is synchronized, and what remains as unresolved metadata.

## Verification checklist
- Active Markdown source files contain no visible editorial marker text such as `<span class="mark">`, `占位`, `这里`, `需要描述`, or `太绝对` unless deliberately preserved.
- Active Markdown source files and the verified Word body contain no unintended Chinese text after comment cleanup.
- Section headings match requested language (usually Abstract, Introduction, Methods, Results, Discussion).
- Terminology drift checks target active files only, not backups or logs.
- For Word Discussion sections, body paragraphs do not inherit list/numbering properties.
- Section-level comparison reports no missing or extra paragraphs between Markdown and the verified Word candidate.

## Pitfall
A Word candidate can look clean while the split Markdown sources still contain old comments/placeholders. That is a workflow failure: the next regeneration will resurrect the bad text. Fix the source files first, then verify the Word candidate.
