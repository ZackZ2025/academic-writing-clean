# Target-Journal Style Skill Extraction

Use this reference when the user names a target journal and asks to learn from published papers or create a reusable writing guide.

## Trigger

- User names a target journal and wants manuscript style adapted to that journal.
- User asks to study one or two similar papers and turn the pattern into a reusable skill or guide.
- The manuscript has a local workspace where project-specific style guidance should live beside the manuscript sources.

## Workflow

1. Confirm the target journal and manuscript class.
   - Identify whether the goal is main journal, companion journal, short report, research article, review, etc.
   - Retrieve author guidelines for required components: abstract format, highlights, Research in Context, word limits, reporting expectations.
2. Search for 1–3 close source articles in the target journal.
   - Prefer full research articles over conference abstracts when learning prose structure.
   - Choose one article close in mechanism/model and one close in data type when possible.
   - Record DOI/PMID/PMCID and why each article was selected.
3. Extract writing patterns, not just scientific facts.
   - Article-level sequence: problem → intervention/exposure → phenotype → omics/pathway → validation → implication.
   - Section-level moves: Introduction funnel, Results figure order, Discussion limitations, Research in Context claims.
   - Evidence-boundary language: association vs causality, candidate vs validated, in vitro vs in vivo.
4. Create a class-level project skill or style guide.
   - Use a directory such as `<journal-slug>-writing-style/` with `SKILL.md` and `references/source-articles.md`.
   - Keep the skill reusable for future revisions, not a one-off summary of the session.
   - Include templates for Abstract, Highlights, Research in Context, Results transitions, and Discussion limitations.
5. Verify the skill file.
   - Frontmatter starts at byte 0 with `---`.
   - `name` and `description` exist and description is under 1024 characters.
   - Source articles and journal guideline URLs/DOIs are recorded in `references/source-articles.md`.
   - Active manuscript source directories are not modified unless the user asked for actual manuscript revision.

## Selection Heuristics

- Prefer an article from the exact target journal over a more scientifically similar article from another journal.
- If no perfect match exists, combine patterns: one exact-journal article for house style and one near-topic article for scientific framing.
- Avoid using conference abstracts as the main style model unless the user's deliverable is also an abstract.

## Common Pitfalls

1. **Summarizing the papers instead of extracting style.** The deliverable is a reusable writing protocol.
2. **Ignoring author guidelines.** Target-journal style includes required sections, not only prose tone.
3. **Overfitting to one paper.** Extract class-level patterns and mark which lessons are article-specific.
4. **Creating a narrow session artifact.** Name the skill after the writing class or journal style, not today's manuscript step.
5. **Accidentally editing the manuscript.** If the user asked only for a skill/style guide, do not touch `02_正文/`, figure files, or the Word draft.
