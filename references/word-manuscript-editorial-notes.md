# Word manuscript editorial notes and Chinese inline comments

Use this reference when revising a `.docx` manuscript that contains Chinese editorial notes, inline placeholders, or reviewer-style instructions embedded in the body.

## Key distinction

A Word file may contain either:

1. Standard Word comments: stored under `word/comments.xml` and anchored by `w:commentRangeStart`, `w:commentRangeEnd`, or `w:commentReference` in `word/document.xml`.
2. Visible inline notes: ordinary body paragraphs or substrings, often in Chinese, such as `这里先保留现象，不提前展开机制`, `【货号】`, or `需要描述...`.

Do not assume visible Chinese notes are standard Word comments. Inspect the `.docx` package first.

## Safe workflow

1. Create a backup and a working copy before editing.
2. Unzip/read the `.docx` package and check for `word/comments.xml`.
3. Extract all paragraphs containing CJK characters plus 1-2 neighboring paragraphs of context.
4. Classify each Chinese item:
   - Section heading to translate (`摘要` -> `Abstract`, `前言` -> `Introduction`, etc.).
   - Editorial instruction to incorporate into prose.
   - Placeholder that needs author data (`【货号】`, `【批准号】`, `【剂量】`).
   - Overclaim warning that requires hedging rather than deletion.
5. Apply revisions in the working copy:
   - Incorporate the instruction into manuscript text before removing the visible note.
   - Translate manuscript headings to journal English.
   - Convert unknown missing details to English placeholders; do not invent supplier names, approval numbers, doses, catalog numbers, or ethics IDs.
6. Generate a modification report mapping original Chinese note -> action taken.
7. Verify the revised `.docx`:
   - ZIP structure passes `testzip()`.
   - No standard Word comments remain unless intentionally unresolved.
   - No CJK-containing paragraphs remain, except deliberate author-facing placeholders if requested.
   - Headings are in English.

## Editing principles

- A Chinese comment is not automatically disposable. Treat it as editorial intent.
- If a note says “do not over-explain mechanism,” remove mechanism inflation and keep the claim at the phenotype/function-validation level.
- If a note says a claim is too absolute, add an evidence-boundary clause: e.g., “although the present data do not establish that X directly causes Y.”
- If a note asks to move a result earlier, restructure the paragraph rather than appending another sentence.
- For biomedical manuscripts, preserve distinctions among in vitro, in vivo, candidate metabolite, association, mediation, and direct causality.

## Minimal Python probes

Use `zipfile.ZipFile` and `xml.etree.ElementTree` to inspect `word/document.xml` and `word/comments.xml`; this avoids depending on Word automation or GUI access.

Core checks:

```python
from zipfile import ZipFile
from xml.etree import ElementTree as ET
import re

NS = {'w': 'http://schemas.openxmlformats.org/wordprocessingml/2006/main'}
W = '{%s}' % NS['w']

def text_of(elem):
    return ''.join(t.text or '' for t in elem.iter(W+'t'))

def has_cjk(s):
    return bool(re.search(r'[\u4e00-\u9fff]', s or ''))

with ZipFile('manuscript.docx') as z:
    print([n for n in z.namelist() if 'comment' in n.lower()])
    root = ET.fromstring(z.read('word/document.xml'))
    for idx, p in enumerate(root.iter(W+'p'), 1):
        txt = text_of(p).strip()
        if has_cjk(txt):
            print(idx, txt)
```
