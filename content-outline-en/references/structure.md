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

- Introduction, mandatory section, and CTA **do not count** toward the numbered total
- A single point may not be split across multiple H2 sections
- Do not add bonus, extra, or tip sections unless `brief` explicitly requests content outside the numbered list
- To add depth without adding H2 sections: add more paragraph groups within an existing section

---

## Section Types

### Introduction

**Paragraph count:** 2–3 groups, each with 1 `[main]` + 1 or more other labels.

| Paragraph | Role |
|---|---|
| First | Broad context relevant to the general topic |
| Second | Narrower context focused on the article's specific topic |
| Third | Bridge that guides the reader into the main content |

Anchor text 1 is bolded and appears naturally in the introduction. Anchor text 2 appears naturally in the same or adjacent paragraph.

---

### Standard H2 Section

Paragraph count determined by the budget from Step 6b in SKILL.md.

Each paragraph group follows this format:
```
**Paragraph N**
- [main] Main idea.
- [supporting/reinforcing/additional] Elaboration.
```

---

### Mandatory Section

Only present when the `mandatory` column contains a **positive requirement** (product name or topic to discuss).

Paragraph count follows the same budget as regular sections (Step 6b).

---

### Conclusion

No H2 heading. Wrapped in `<kesimpulan>...</kesimpulan>` tags.

```
<kesimpulan>
- First conclusion point.
- Second conclusion point.
- Third conclusion point.
</kesimpulan>
```

2–3 points summarizing the article's key takeaways. No new information.

---

### CTA Section

Heading is determined by the user's answer in Step 1 (`cta_heading`):

- **User provided heading text** → use verbatim as H2 for every row
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
