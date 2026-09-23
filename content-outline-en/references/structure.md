# Content Outline Structure Reference

## High-Level Structure

```
H1 Article Title
│
├── Introduction (labeled Content Points)
│
├── ## H2 Section 1
│   └── Content Points (labeled paragraph groups)
│
├── ## H2 Section 2
│   └── Content Points (labeled paragraph groups)
│
├── [## H2 Mandatory Section — only if mandatory has positive requirement]
│   └── Content Points (labeled paragraph groups)
│
├── <kesimpulan>
│   └── Conclusion points
│
└── [## CTA heading] or [**CTA**]
    └── CTA Content Points
```

---

## H2 Count Rules

| Condition | Rule |
|---|---|
| Title contains explicit number | That number is a hard limit for numbered H2 sections |
| Title contains no number | Determine logically from semantic scope |

- Introduction, mandatory section, and CTA do not count toward the numbered total
- Do not add bonus, extra, or tip sections unless `brief` explicitly requests them

---

## Section Types

### Introduction

**Paragraph count:** 2–3 groups, each with 1 `[main]` + 1 or more other labels.

The introduction has no locked role per paragraph. Its content is determined by the facts available in the source for this specific article — not by a category template.

**Anti-template rule (mandatory):**

Every `[main]` in the introduction must pass this test: *could this sentence be moved to another article in the same topic without changing its meaning?* If yes → replace it with a specific fact from the source.

Not allowed — sentences that could appear in any article in the same category:
- "Indoor attractions have become a favorite choice for families regardless of the weather."
- "There are many family travel destinations, but not all remain popular for decades."
- "Modern flagship smartphones offer increasingly competitive specs every year."

Correct — specific facts that only apply to the subject of this article:
- Specific names, numbers, dates, prices, or details that cannot be moved to another article

**Anchor text rules:**
- Anchor text 1 is bolded and appears naturally in the introduction
- Anchor text 2 appears naturally in the same or adjacent paragraph
- Anchor text placement must not force a sentence to become generic

---

### Standard H2 Section

Paragraph count determined by the budget from Step 6b in SKILL.md.

Each paragraph group follows the format and coherence rules in `content-points.md`.

---

### Mandatory Section

Only present when the `mandatory` column contains a positive requirement. Paragraph count follows the same budget as regular sections.

---

### Conclusion

No H2 heading. Wrapped in `<kesimpulan>...</kesimpulan>` tags.

```
<kesimpulan>
- First conclusion point.
- Second conclusion point.
</kesimpulan>
```

2–3 points summarizing key takeaways. No new information.

---

### CTA Section

Heading determined by user's answer in Step 1:

- **User provided heading text** → use verbatim as H2
- **User chose no H2** → use `**CTA**` label (no `##`)

**Format with H2:**
```
## [Heading text from user]

**Content Points:**
- Narrative bridge: [one sentence connecting conclusion to product]
- [Point presenting product/service as solution]
- [Point with specific action — URL, WhatsApp, email, etc.]
```

**Format without H2:**
```
**CTA**

**Content Points:**
- Narrative bridge: [one sentence connecting conclusion to product]
- [Point presenting product/service as solution]
- [Point with specific action — URL, WhatsApp, email, etc.]
```
