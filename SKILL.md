---
name: academic-writing-clean
description: "Use when coordinating English-language academic writing and revision for medical or biomedical manuscripts. Acts as the router for abstract, background, methods, results, and discussion skills while enforcing evidence boundaries, source-of-truth rules, and anti-AI style checks."
version: 2.0.0
author: Hermes Agent
license: MIT
metadata:
  hermes:
    tags: [academic-writing, manuscript, biomedical, imrad, editing]
    related_skills: [manuscript-abstract-writing, manuscript-background-writing, manuscript-methods-writing, manuscript-results-writing, manuscript-discussion-writing, evidence-first-research, academic-deep-search, docx-editing, humanizer]
---

# Academic Writing Clean

## Overview

Use this as the **medical/biomedical manuscript writing router**. It keeps the whole manuscript coherent, then dispatches section-specific work to narrower skills:

| Task | Load this skill |
|---|---|
| Abstract, highlights, structured abstract | `manuscript-abstract-writing` |
| Introduction / Background / gap / rationale | `manuscript-background-writing` |
| Methods, reproducibility, statistics, ethics, placeholders | `manuscript-methods-writing` |
| Results, figure-flow, evidence-chain narration, minimal revision | `manuscript-results-writing` |
| Discussion, limitations, implications, citation-backed interpretation | `manuscript-discussion-writing` |
| Word `.docx` inspection/editing/verification | `docx-editing` |
| Literature support and evidence quality | `evidence-first-research`, `academic-deep-search` |
| Anti-AI prose cleanup | `humanizer` plus the checks below |

Do **not** keep expanding this file into a monster. If the work belongs to one IMRaD section, load the relevant section skill.

## When to Use

Use this skill when:

- The user asks for general manuscript writing, polishing, or revision without naming a section.
- Multiple sections must stay synchronized.
- A manuscript has split Markdown sources plus an integrated Word candidate.
- You need to decide which section-specific skill should own the task.
- The user asks for academic prose that is concrete, restrained, and not AI-like.

Do not use this as the only skill when:

- The task is clearly only Abstract / Background / Methods / Results / Discussion. Load the specific skill too.
- The task is file-level `.docx` manipulation. Load `docx-editing`.
- The task requires new literature support. Load `evidence-first-research` or `academic-deep-search` before drafting.

## Global Manuscript Rules

1. **Separate evidence levels.** Keep own data, literature, reasonable inference, and speculation visibly distinct.
2. **Do not invent.** Never fabricate P values, fold changes, sample sizes, approval numbers, supplier/catalog information, figure panels, or citations.
3. **Preserve evidence boundaries.** Do not collapse in vitro into in vivo, candidate into verified, association into causality, or asymmetric model arms into a single strong mechanism.
4. **Respect source of truth.** If split Markdown files exist, treat them as authoritative unless workspace rules say otherwise. Word-only edits must be backfilled into Markdown and verified section by section.
5. **Prefer candidates over overwrites.** Generate a clearly named candidate Word file unless the user explicitly asks to overwrite.
6. **Keep active directories clean.** Archive scripts, logs, audits, backups, and temporary extracts under `00_inbox/agent_artifacts`, `00_inbox`, or the workspace's artifact directory.
7. **Honor minimal revision requests.** When the user says “最小修改原则”, preserve the original paragraph architecture and repair only what the stated correction requires.

## Default Workflow

1. Identify manuscript type, target audience, target journal if known, and the requested section.
2. Inspect local workspace rules (`AGENTS.md`, split Markdown sources, figure maps, terminology tables) before writing.
3. Choose the section skill from the dispatch table.
4. If claims depend on external literature, run an evidence-first search before drafting.
5. Draft or revise only the requested scope.
6. Run an anti-AI and overclaim pass.
7. If producing Word output, use `docx-editing` validation rules: ZIP integrity, text extraction, relationship sanity when needed, and residual-marker search.
8. Report what changed, what was assumed, and what remains unresolved.

## Anti-AI Style Check

Before finalizing any paragraph, ask:

- Is every sentence doing work, or is it just sounding formal?
- Did I replace vague abstractions with data, actors, actions, or consequences?
- Did I avoid stock phrases such as “In the current era”, “It is worth noting”, “plays a crucial role”, and “future studies are needed” when they add no information?
- Did I vary sentence structure without making the prose theatrical?
- Did I keep the tone confident but not inflated?
- Did I remove invented certainty?

## Target-Journal Style Extraction

When the user names a target journal and asks you to learn from similar published papers, do not merely summarize the papers. Build a reusable style guide or project-local skill that captures the journal's required components, article structure, evidence-boundary language, and section templates. Prefer 1–3 close articles from the exact journal plus the journal author guidelines. Keep source notes in a project-local file such as `source-articles.md` under that project's references directory, or an equivalent support file. See `references/target-journal-style-skill.md` for the full workflow.

## Verification Checklist

- [ ] Correct section-specific skill loaded for the actual task.
- [ ] Workspace rules and source-of-truth files inspected when relevant.
- [ ] If a target journal is named, author guidelines and 1–3 close source articles were checked before writing a style guide.
- [ ] No invented statistics, citations, methods metadata, or figure/panel labels.
- [ ] Evidence strength matches wording strength.
- [ ] Markdown/Word synchronization handled or explicitly not in scope.
- [ ] Unresolved items marked as `【待确认：...】` or reported separately rather than silently guessed.
