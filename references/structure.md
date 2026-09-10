# Content Outline Structure Reference

## High-Level Structure

```
H1 Article Title
│
├── Introduction Content Points
│
├── H2 Section 1
│   └── Content Points
│
├── H2 Section 2
│   └── Content Points
│
├── [H2 Mandatory Section — only if mandatory column has a positive requirement]
│   └── Content Points
│
├── <kesimpulan> Conclusion Content Points </kesimpulan>
│
└── CTA (no H2)
    ├── Narrative bridge
    └── CTA Content Points
```

**Note on Conclusion and CTA format:** Neither the conclusion nor the CTA uses an H2 heading. The conclusion is wrapped in `<kesimpulan>...</kesimpulan>` tags. The CTA follows directly after, always opened by a narrative bridge.

---

## H2 Count Rules

| Condition | Rule |
|---|---|
| Title contains an explicit number | That number is a hard structural limit for numbered H2 sections |
| Title contains no number | Determine a logical count based on semantic scope, word count, and topical groupings |

Additional rules:
- Introduction, mandatory section, and closing/CTA **do not count** toward the numbered total
- A single point may **not** be split across multiple H2 sections
- Do **not** add bonus, extra, or tip sections unless the `brief` explicitly requests content outside the numbered list
- To add depth without adding H2 sections: add more Content Points within an existing section (max 100 words per section)
- If the requested word count cannot be reached under a numbered title constraint, do not fabricate sections or invent content — maintain structural accuracy

---

## Section Types

### Introduction

**Paragraph count:** 2–3 paragraphs, 2–3 sentences each.

| Paragraph | Role |
|---|---|
| First | Broad context relevant to the general topic |
| Second | Narrower context focused on the article's specific topic |
| Third | Bridge that guides the reader into the main content |

**Anchor text rule:** Both `anchor text 1` and `anchor text 2` must appear **naturally and contextually** in the introduction. Bold `anchor text 1` in the introduction.

---

### Standard H2 Section

**Paragraph count:** 2–3 paragraphs, 2–3 sentences each. Each paragraph focuses on one main idea to avoid dense stacking.

---

### Mandatory Section

Present only when the `mandatory` column is filled. This section discusses a specific product as a concrete solution to the challenges raised in the article.

**Structure:**
- **First paragraph:** Product context and primary specs
- **Second paragraph:** Primary USP of the product
- **Third paragraph:** Additional USP or further elaboration

---

### Conclusion

The conclusion is **not** an H2 heading. It appears as a `<kesimpulan>` block directly before the CTA section.

**Format:**
```
<kesimpulan>
- [Conclusion content point]
- [Conclusion content point]
</kesimpulan>
```

Content: 2–3 bullet points summarizing the article's key takeaway. Do not introduce new information.

---

### CTA Section

The CTA section has **no H2 heading**. It appears as plain paragraphs directly after the `<kesimpulan>` block.

**Structure:**
- **Narrative bridge** — always present. Connects the conclusion to the product or service being promoted. Can be a standalone paragraph or the opening sentence of the first CTA paragraph, depending on what flows more naturally.
- **CTA Content Points** — 2–3 points presenting the product/service as the solution, ending with a clear, direct action (visit a URL, contact via WhatsApp, browse a catalogue, etc.)

**Content Points format for CTA (use `**CTA**` as label, not `##`):**
```
**CTA**

**Content Points:**

- Narrative bridge: [one sentence connecting conclusion to product]

- [Point presenting product/service as solution]

- [Point with specific action — URL, WhatsApp, email, etc.]
```