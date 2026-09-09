# content-outline

A Claude skill that generates structured content outlines from a tabular input. Each row in the table becomes one `.md` file containing **Content Points** — the semantic payload that writers transform into prose, without doing their own research or angle decisions.

## Input Format

The skill accepts a TSV or Markdown table with the following columns:

| Column | Description |
|---|---|
| `id` | Unique row identifier |
| `anchor text 1` | Primary anchor text (bolded in introduction) |
| `anchor text 2` | Secondary anchor text (appears in introduction) |
| `brief` | Article instructions, constraints, required keywords |
| `mandatory` | Required product section, if any |
| `title` | Article title (H1) |
| `source` | Source data — URL, markdown, JSON, or plain text |

## Output

One `.md` file per row, named `{id} - {anchor text 1}.md`.

Each file follows this structure:

```
H1 Article Title
├── Introduction
├── H2 Section 1
├── H2 Section 2
├── H2 Mandatory Section (if applicable)
├── Conclusion
└── H2 CTA Section
```

## File Structure

```
├── SKILL.md                      # Main workflow
└── references/
    ├── content-points.md         # Content Point writing rules
    ├── structure.md              # Section and H2 count rules
    └── examples.md               # Full output examples
```

## License

MIT © NZaydanee
