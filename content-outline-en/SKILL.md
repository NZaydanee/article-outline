---
name: content-outline-en
description: Generate structured content outlines from a tabular input (TSV or Markdown table) with columns: id, anchor text 1, anchor text 2, brief, mandatory, title, source. Use this skill whenever the user pastes a table or spreadsheet with article rows and asks to create content outlines, content briefs, article blueprints, or writing guides. Also trigger when the user mentions "content outline", "article outline", or "content points" alongside any structured input. Trigger even if the user just pastes a table without explicit instructions — the presence of these columns is enough.
---

# Content Outline Generator — English

Generates one structured content outline file per table row. Each file contains labeled Content Points ready for a writing agent to turn into a final article.

**Output language:** English  
**File naming:** `{id} - {anchor text 1}.md`

---

## Step 1: Batch Settings

Before reading the table, ask the user two questions in one message:

> "Before we start, two quick settings:
>
> 1. **Target word count per article?** (Default: 700 words)
> 2. **CTA section heading?**
>    - **No H2** — CTA appears as plain paragraphs after the conclusion
>    - **Yes, H2** — provide the exact heading text you want (e.g., *"Find Your AIS Receiver at IAPS"*)"

Wait for one reply, then:
- Store word count as `target_words`. Default is **700** if not specified.
- Store CTA preference as `cta_heading`. If heading text is provided, use it verbatim for every row. If no H2, format CTA as plain paragraphs using `**CTA**` label (no `##`) in the outline.

---

## Step 2: Read Reference Files and All Rows

Read these two reference files **once** before processing any row:
- `references/content-points.md` — Content Point rules, label definitions, format
- `references/structure.md` — section definitions, H2 count rules, paragraph structure

Keep them in context — do not re-read for each row.

Then read the entire table and internally note:
- Which rows have empty `source` and no user-provided data
- What topic-critical data each row requires
- Any table anomalies (shifted columns, empty titles, missing fields)

Do not output anything yet.
Do not output anything yet.

---

## Step 3: Pre-Batch Clearance — One Message, No Exceptions

**No row may be written until this step is fully resolved.**

Run two checks simultaneously across all rows. Bundle every finding into one message. Do not start until the user confirms all issues are cleared.

### Check A — Source Data

Identify rows where `source` is empty and the user did not paste data alongside the table. Ask once, all affected rows listed together:

> **Rows with no source data:** Row X *(title)*, Row Y *(title)*
>
> - **A** — I'll research all via web search
> - **B** — You'll provide all data now (paste here)
> - **C** — Mixed: tell me which you'll provide, I'll research the rest

### Check B — Topic-Data Fit

For rows with source data, evaluate if the data covers what the topic requires. Flag rows where topic-critical data is absent from the source.

| Topic type | Required data |
|---|---|
| Cooling / thermal | TDP (watt), cooling system name, fan configuration |
| Build quality / materials | Material name, treatment process, durability test results |
| Security features | Feature names, certification names |
| AI features | NPU presence, TOPS rating, AI feature names |
| Battery / endurance | Capacity (Wh), claimed runtime |
| Pricing | Actual price for the market in scope |
| Warranty / after-sales | Duration, coverage, service type |

If any rows are flagged, ask per flagged row: provide data / research / skip with gap note.

**Bundling rule:** Check A and Check B go in one message — never two separate messages.

---

## Step 4: Determine Source Data Per Row

| Priority | Condition | Action |
|---|---|---|
| 1 | User pasted data in same message as table | Sole reference. Nothing added from outside. |
| 2 | `source` has content (URL, markdown, JSON, plain text) | Primary reference. No external supplement. |
| 3 | `source` empty | Use web search or Step 3 reply data. |

If `source` is a URL, fetch the page. If markdown/JSON/plain text, use as-is.

---

## Step 5: Process Rows One by One (Stateless)

Each row is a fully independent unit.
- Complete one row fully before starting the next
- No rule, data, or constraint from one row may carry into another
Use the understanding from reference files read in Step 2.
## Step 6: Build the Content Outline

Before writing each row, read:
- `references/content-points.md` — Content Point writing rules, label definitions, format
- `references/structure.md` — section definitions, H2 count rules, paragraph structure
- `references/examples.md` — full output examples

### 6a. Determine H2 Count from Title

- **Title contains an explicit number** (e.g., "5 Reasons", "7 Criteria"): hard structural limit. Numbered H2 sections must equal exactly that number.
- **Title contains no number**: determine logically from semantic scope and topical groupings.

H2 count does not change based on word count.

### 6b. Calculate Paragraph Budget Per Section

```
available_words    = target_words - 150
per_section_budget = available_words ÷ H2_count
paragraphs_per_section = max(2, round(per_section_budget ÷ 55))
```

Where 150 = estimated intro + CTA word budget, and 55 = approximate words per paragraph.

Quick reference:

| target_words | 4 H2 | 5 H2 | 6 H2 |
|---|---|---|---|
| 700 | 2–3 paragraphs | 2 paragraphs | 2 paragraphs |
| 900 | 3 paragraphs | 2–3 paragraphs | 2 paragraphs |
| 1100 | 3–4 paragraphs | 3 paragraphs | 2–3 paragraphs |

Each paragraph = 1 `[main]` + 1 or more other labels. Same formula applies to mandatory section.

### 6c. Read Brief and Mandatory

| `mandatory` column contains | Action |
|---|---|
| A product name or topic to discuss (positive requirement) | Create dedicated H2 mandatory section in body |
| Only restrictions (e.g., "Do not mention X") | No H2 in body. Restrictions apply globally. Product promotion goes to CTA only. |
| Empty | No mandatory section |

If `brief` mentions promoting a product but `mandatory` only contains restrictions: promotion belongs **only in the CTA section**.

### 6d. Resolve Calculations Before Writing

Resolve all comparisons, calculations, and implications before writing any Content Point. Label theoretical or estimated figures clearly.

### 6e. Output Structure

```
H1 Article Title

Introduction Content Points (labeled)

## H2 Section 1
  Content Points (labeled, per paragraph group)

## H2 Section 2
  Content Points (labeled, per paragraph group)

[## H2 Mandatory Section — only if mandatory has positive requirement]
  Content Points (labeled, per paragraph group)

<kesimpulan>
- Conclusion point
- Conclusion point
</kesimpulan>

[## CTA heading from user] or [**CTA** no heading]
CTA Content Points
```

---

## Step 7: Internal Checklist Before Saving

Run silently before saving each file:

- [ ] Anchor text 1 appears naturally in introduction, bolded
- [ ] Anchor text 2 appears naturally in introduction
- [ ] All instructions in `brief` and `mandatory` followed
- [ ] H2 count matches Step 6a rule
- [ ] Paragraph count per section matches Step 6b budget
- [ ] Every paragraph group has exactly one `[main]` as the first point
- [ ] Every number or claim has a verified source; no figure is invented
- [ ] No rules, data, or constraints from other rows have leaked into this file
- [ ] No cross-references to other rows
- [ ] File can be understood by a writer who has never seen the original table

---

## Output Prohibition

Do not include a metadata block, writer notes, or technical parameter summary in the output. The file must contain only the content outline — from the H1 title through the CTA.

---

## Step 8: Save and Present

Save as `{id} - {anchor text 1}.md`, present to user, then proceed to the next row.
