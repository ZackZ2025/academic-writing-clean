# Citation-Backed Discussion Drafting

Use this reference when drafting or rewriting the Discussion section of a biomedical or medical original research manuscript.

## Lesson Captured

A Discussion section that has a coherent internal logic but no sources is not acceptable for biomedical manuscript work. The section must connect the study findings to traceable literature and make clear which claims are project data, which are established background, and which are cautious inference.

## Minimum Standard

Before writing the Discussion:

0. Treat a source-free biomedical Discussion as immature, even if its internal logic is coherent. If the user asks for a Discussion rewrite and sources are missing, pause drafting, run evidence-first search, then rewrite around checked sources rather than merely polishing prose.

1. Identify the Discussion claims that require external support.
   - disease/background links
   - model relevance
   - mechanism plausibility
   - prior evidence for molecules, pathways, assays, or interventions
   - limitations that depend on field expectations

2. Search sources before drafting.
   - Prefer PubMed/PMC for biomedical topics.
   - Use `evidence-first-research` for strategy and evidence quality.
   - Use `academic-deep-search` for PubMed/PMC execution and source extraction.

3. Use traceable citations in the draft.
   - Prefer DOI + PMID or PMCID when available.
   - Inline format can be `【DOI; PMID:xxxx】` when the project uses Chinese-style citation placeholders.
   - Do not cite from memory when the DOI/PMID can be checked.

4. Match claim strength to source strength.
   - Systematic review/meta-analysis: suitable for disease association/background.
   - Primary animal/cell papers: suitable for mechanism plausibility, not human efficacy.
   - Reviews: suitable for pathway definitions and framing, not novel causal claims.
   - Project data: use for the manuscript’s own findings, but do not invent external consensus.

5. State evidence boundaries explicitly.
   - Separate in vitro intervention evidence from in vivo animal intervention evidence.
   - Do not write candidate metabolites as proven unique mediators.
   - Do not write pathway candidates as the sole or complete mechanism.
   - Flag asymmetry when one disease/model arm has stronger mechanism evidence than the other.

## Practical Paragraph Pattern

For each major Discussion paragraph:

1. Open with the manuscript’s finding.
2. Add 1–3 source-backed context sentences.
3. Interpret what the manuscript adds beyond those sources.
4. State the boundary or alternative explanation if the claim is indirect.

Example skeleton:

```text
Our data show [project finding]. Prior work has shown [source-backed field context]【DOI; PMID】. This supports the plausibility that [bounded interpretation]. However, [specific limitation], so the current evidence supports [careful claim] rather than [overclaim].
```

## Verification Checklist

Before finalizing:

- Every paragraph that depends on field background has at least one traceable source.
- DOI/PMID/PMCID identifiers were checked through PubMed/PMC or another reliable source.
- No unsupported citations were fabricated.
- The draft distinguishes project findings from literature context.
- Sensitive overclaims were searched and removed: `prove`, `fully mediates`, `only mediator`, `directly causes`, `directly promotes`, `demonstrate conclusively`.
- Verification searches target the active manuscript file, not backup folders that may contain stale forbidden terms.
