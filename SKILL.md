---
name: content-outline
description: Generate structured content outlines from a tabular input (TSV or Markdown table) with columns: id, anchor text 1, anchor text 2, brief, mandatory, title, source. Use this skill whenever the user pastes a table or spreadsheet with article rows and asks to create content outlines, content briefs, article blueprints, or writing guides. Also trigger when the user mentions "content outline", "article outline", or "content points" alongside any structured input. Trigger even if the user just pastes a table without explicit instructions — the presence of these columns is enough.
---

# Content Outline Generator

Generates one structured content outline file per table row. Each file contains Content Points — the semantic payload that writers transform into prose, without doing their own research or angle decisions.

**Output language:** English  
**Output format:** One `.md` file per row, named `{id} - {anchor text 1}.md`

---

## Step 1: Read All Rows First

Read the entire table before doing anything else. For each row, internally note:

- The **focus and angle** of each article to detect topic cannibalization across rows
- Which rows have **empty `source`** and no user-provided data
- What **topic-critical data** each row requires (see Step 2 for definition)
- Any **table anomalies** (shifted columns, empty titles, missing fields)

Do not output anything yet.

---

## Step 2: Pre-Batch Clearance — One Message, No Exceptions

**No row may be written until this step is fully resolved.**

Run two checks across all rows simultaneously. Bundle every finding into a single message to the user. Do not start the batch until the user explicitly confirms all issues are cleared.

### Check A — Source Data

Identify rows where `source` is empty and the user did not paste data alongside the table. For those rows, ask:

> **Rows with no source data:** Row X *(title)*, Row Y *(title)*
>
> Choose one:
> - **A** — I'll research all via web search
> - **B** — You'll provide all data now (paste here)
> - **C** — Mixed: tell me which you'll provide, I'll research the rest

### Check B — Topic-Data Fit

For rows that **do** have source data, evaluate whether the data covers the specific claims the topic requires. Flag a row if the topic demands data that is absent from the source.

Common topic-to-data requirements:

| Topic type | Data that must be present in source |
|---|---|
| Cooling / thermal performance | TDP (watt), cooling system name, fan configuration |
| Build quality / materials | Material name, treatment process, durability test results |
| Security features | Specific feature names, certification names |
| AI features | NPU presence, TOPS rating, AI feature names |
| Battery / endurance | Battery capacity (Wh), claimed runtime |
| Pricing | Actual price figure for the market in scope |
| Warranty / after-sales | Warranty duration, coverage details, service type |

If a row's source lacks topic-critical data, flag it:

> **Rows with insufficient data for their topic:**
> - Row 44 *(Laptop Tidak Cepat Panas)* — thermal/TDP data not found in source
> - Row 60 *(Desain Premium)* — material and surface treatment data not found in source
>
> Choose one per flagged row:
> - **A** — You'll provide the missing data (paste here)
> - **B** — I'll research the missing data via web search
> - **C** — Skip the missing data; I'll note the gap in the file without fabricating

### Bundling Rule

If both Check A and Check B find issues, combine them into **one single message**. Do not send two separate messages. Do not proceed until the user replies and all issues have a resolution.

---

## Step 3: Determine Source Data Per Row

Apply this priority order for each row:

| Priority | Condition | Action |
|---|---|---|
| 1 | User pasted data in the same message as the table | Use as sole reference. Do not add anything from outside. |
| 2 | `source` column contains content (URL, markdown, JSON, plain text) | Use as primary reference. Do not supplement with external data. |
| 3 | `source` is empty | Use web search or data provided in Step 2 reply. |

If `source` is a URL, fetch the page. If it is markdown, JSON, or plain text, use it as-is.

---

## Step 4: Process Rows One by One (Stateless)

Each row is a fully independent unit.

- Complete one row fully before starting the next
- No rule, data, or constraint from one row may carry into another — even if rows share the same client
- Write all context needed for a row inside that row's own file
- Do not write cross-references like "same as row 3" or "continued from previous row"

---

## Step 5: Build the Content Outline

Before writing each row, read:
- `references/structure.md` — section definitions, H2 count rules, paragraph structure
- `references/content-points.md` — Content Point writing rules and anti-patterns
- `references/examples.md` — full output examples (with and without mandatory section)

### 5a. Determine H2 Count from Title

- **Title contains an explicit number** (e.g., "5 Reasons", "7 Criteria"): that number is a hard structural limit. Numbered H2 sections must equal exactly that number.
- **Title contains no number**: determine a logical H2 count based on semantic scope, requested word count, and topical groupings. Do not inflate sections to increase word count.

### 5b. Read Brief and Mandatory

Extract from `brief` and `mandatory` columns:
- Topic boundaries and prohibited content
- Required headings
- Keywords that must be mentioned
- Phrases, sentences, or paragraphs that must appear and their placement
- Specific H2 sections dedicated to a product (mandatory section)

**Mandatory section rules — read carefully:**

| `mandatory` column contains | Action |
|---|---|
| A product name or topic to be discussed (positive requirement) | Create a dedicated H2 mandatory section in the body |
| Only restrictions (e.g., "Do not mention X") | No mandatory H2 in body. Restrictions apply globally. Product promotion goes to CTA section only. |
| Empty | No mandatory section |

If `brief` mentions promoting a product or brand (e.g., "soft selling article untuk mempromosikan X") but `mandatory` only contains restrictions: the promotion belongs **only in the CTA section**, not as a standalone H2 in the article body.

### 5c. Resolve Calculations Before Writing

If the article requires comparisons, calculations, or practical implications, resolve these **before** writing any Content Point. Label theoretical or estimated figures clearly. Only include a comparison if base data has been verified.

### 5d. Write the Outline

Follow this structure (details in `references/structure.md`):

```
H1 Article Title

Introduction Content Points

H2 Section 1
  Content Points

H2 Section 2
  Content Points

[H2 Mandatory Section — only if `mandatory` column is filled]
  Content Points

Conclusion Content Points

H2 CTA Section
  CTA Content Points
```

---

## Step 6: Internal Checklist Before Saving

Run silently before saving each file:

- [ ] Anchor text 1 appears naturally and contextually in the introduction
- [ ] Anchor text 2 appears naturally and contextually in the introduction
- [ ] All instructions in `brief` and `mandatory` have been followed
- [ ] H2 count matches the rule in Step 5a
- [ ] Every number or claim has a verified source; no figure is invented
- [ ] No rules, data, or constraints from other rows have leaked into this file
- [ ] No cross-references to other rows exist in the file
- [ ] The file can be understood by a writer who has never seen the original table

---

## Step 7: Save and Present

Save the file as `{id} - {anchor text 1}.md`. Present it to the user, then proceed to the next row.
