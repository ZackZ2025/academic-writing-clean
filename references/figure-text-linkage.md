# Figure-to-text linkage workflow for biomedical manuscript edits

Use this when a user says a figure or panel changed (e.g., "Fig.5 panel M added 4-HNE staining") and the manuscript has separate figure files, knowledge-base control files, Markdown source sections, and an integrated Word candidate.

## Trigger

- New or removed figure panel, changed panel label/order, changed assay/staining marker, changed model arm, or changed conclusion scope.
- User asks to "启动联动修改程序" or otherwise expects figure/text synchronization.

## Minimal safe workflow

1. Read the workspace workflow file first (`AGENTS.md` or equivalent) and identify the controlling files for figures, terminology, unresolved issues, evidence mapping, manuscript source, and Word draft.
2. Inspect the current figure asset when available. Do not rely only on the user's short description if the image can be checked.
3. Determine scope before editing:
   - figure legend source;
   - figure role/logic file;
   - figure-to-text evidence map;
   - affected Results paragraph and embedded legend;
   - integrated Word candidate if Markdown source changed;
   - change log.
4. Back up every active source file that will be edited into the project backup/archive location, not beside the active file.
5. Make narrow edits only. Preserve the main storyline and do not convert a new panel into a stronger causal claim than the experiment supports.
6. If the changed panel only covers one model arm, say so explicitly. Example: a 4-HNE panel in 5×FAD tissue supports 5×FAD-side in vivo lipid peroxidation, not an IH-side molecular closure.
7. Keep model/assay asymmetry visible: in vitro M3G evidence and in vivo ND646 evidence must not be merged into a single closed causal chain unless direct data exist.
8. Synchronize the integrated Word draft after Markdown source edits when workspace rules require it. Prefer XML-level targeted replacement for a small `.docx` text change; verify ZIP integrity and extract the affected paragraphs afterward.
9. Verify intentionally:
   - old figure title/legend text no longer appears in active sources;
   - terminology drift such as `5xFAD`, `5XFAD`, or casual `FAD mice` is absent from active manuscript/figure files, ignoring terminology tables that list deprecated variants;
   - no inline editorial residue (`<span class="mark">`, Chinese TODO notes) was introduced;
   - active source directories contain only intended source/deliverable files; scripts/logs live under `00_inbox/agent_artifacts` or equivalent.
10. Update the change log with changed files, reason, synchronization status, and Word status.

## Wording patterns

- Safer title when Fig.5 has in vitro M3G plus in vivo ND646 evidence:
  `M3G suppresses ... in vitro, while ND646 reduces ... in vivo`
- Safer panel wording:
  `Representative 4-HNE staining images in hippocampal tissues from WT, 5×FAD, and 5×FAD+ND646 mice, showing reduced lipid peroxidation after ND646 treatment.`
- Avoid:
  - `M3G suppresses ... in vitro and in vivo` when in vivo data are ND646-only.
  - `4-HNE demonstrates IH-side mechanism closure` when the panel only contains 5×FAD tissue.

## Verification notes

For docx text-only synchronization without python-docx, unzip/rewrite `word/document.xml` with Python stdlib (`zipfile` + `xml.etree.ElementTree`), replace exact paragraph text, rezip, then run `ZipFile.testzip()` and extract the affected paragraphs. Keep the script/report under the artifact directory, never in active manuscript directories.
