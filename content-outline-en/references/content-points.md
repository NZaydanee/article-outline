# Content Points Reference

Content Points are the list of information that **must be conveyed** in one article section. They are the semantic payload of the outline — not instructions to the writer.

A writer receiving Content Points performs *surface realization* only: turning points into natural, readable prose. The writer does not search for information, determine angles, or develop new topics.

---

## Content Point Labels

Every Content Point must carry a label indicating its **relationship to the previous point within the paragraph**:

| Label | Question it answers | Position |
|---|---|---|
| `[main]` | What is the fact? What happened? | Always first |
| `[supporting]` | How does it work? Why is that? | After `[main]` |
| `[reinforcing]` | How much? What is the evidence? What is a concrete example? | After `[main]` or `[supporting]` |
| `[additional]` | What else is relevant? (without explaining mechanism or providing evidence) | Last in the group |

**How to distinguish the four labels — one complete paragraph example:**

```
- [main]        Trans Studio Bandung operates 20 active attractions across seven themed zones.
- [supporting]  Each zone is designed with a distinct visual theme, so visitors experience
                a new atmosphere every time they move to a different area.
- [reinforcing] The Hollywood and Cartoon Network zones recorded the longest average queues
                based on 2024 operational data.
- [additional]  Some attractions have a minimum height requirement for safety reasons.
```

**Label rules:**
- Every paragraph group must have **exactly one** `[main]`
- `[main]` is always the first point in the group
- You do not need to use all four labels — choose the label that best fits the information

---

## Coherence Rule Between Points (Mandatory)

Every non-`[main]` point must be written with full awareness of the point above it — as if the previous point is already on the screen and this point continues from it. Not adding a new standalone fact, but **extending the narrative thread** already started.

**How to write each label correctly:**

`[supporting]` — write as if the `[main]` sentence was just read. This sentence elaborates on *why* or *how* the main claim works. May use an explicit reference word ("This...," "The system...," "This condition...") or a natural logical sequence without explicit reference.

`[reinforcing]` — write as if the claim or explanation above already exists. This sentence provides a number, name, or concrete proof. Do not repeat information from `[main]` — go straight to the evidence.

`[additional]` — write as if the reader already knows all previous points in this group. This sentence completes the picture without explaining a mechanism or providing evidence. Avoid starting with a fact that has no connection to the points above.

**Example of correct coherence:**

```
- [main]        The consultant holds a database of buildings far larger than
                what independent searches through general portals return.
- [reinforcing] SewaKantorCBD lists over 500 buildings, including 225 in CBD Jakarta
                with a total available area of 7.8 million m².
- [supporting]  This figure far exceeds what appears in general searches, and the data
                is grouped by subarea so preliminary comparisons can be made before any site visit.
```

**Coherence test before saving a group:**
Read the entire group from top to bottom as one paragraph. If any point can be moved or removed without breaking the reading flow of the others, that point is not sufficiently connected and needs to be rewritten.

---

## How to Write Non-[main] Points: Awareness of the Previous Point

Every non-`[main]` point must be written as if the `[main]` point above it is already on the screen. The next point is not a new standalone fact — it is a continuation of what was just claimed.

**Two valid ways to connect:**

Explicit connection — use a reference word or phrase that directly points back to the previous point: "This figure...", "That condition...", "This feature...", "Compared to...", "As a result..."

Implicit connection — a logical sequence of facts that naturally follows the previous point. Valid as long as a reader instinctively knows both sentences are about the same thing.

**Coherence test before saving:** Take two consecutive points in one group. Could they be separated and used in different paragraphs without losing meaning? If yes — the second point is too standalone and needs to be rewritten to "look upward."

Wrong — second point stands alone:
```
**Paragraph 1**
- [main] SewaKantorCBD lists more than 500 office buildings across Jakarta.
- [supporting] Building data is grouped by grade, price, and subarea location.
```

Right — second point continues from the first:
```
**Paragraph 1**
- [main] SewaKantorCBD lists more than 500 office buildings across Jakarta.
- [supporting] That data is grouped by grade, price, and subarea, so buildings can be compared before any physical survey.
```

---

## 6 Core Rules

### 1. Every Content Point Must Be Concrete

Write as information to be displayed, not as a task for the writer.

**Prohibited verbs:** explain, discuss, elaborate, mention, compare, highlight, talk about, give examples, show why.

### 2. Connect Facts to Their Meaning

Do not present raw data without context.

| Wrong | Right |
|---|---|
| Seat height: 750 mm | `[main]` A 750 mm seat height makes it easier for the rider to reach the ground when stopping. |

### 3. One Semantic Meaning Per Point

**Special case — lists of items (features, options, steps):**

Do not pack all items into one supporting point. Instead:
1. Use the point after `[main]` to **name and introduce** the group
2. Use subsequent paragraph groups to explain each item

**Wrong:**
```
**Paragraph 2**
- [main]        Three booster features shorten the path to completing the puzzle.
- [supporting]  Invite Teman works when a recruited user completes one transfer;
                Oper Puzzle converts duplicates into a spin via a same-level friend;
                Kejar Puzzle rewards five transfers to different users on a Friday.
```

**Right:**
```
**Paragraph 2**
- [main]        Three booster features shorten the path: Invite Teman, Oper Puzzle,
                and Kejar Puzzle.
- [additional]  Each targets a different transfer behavior and can be used independently
                or combined in the same week.

**Paragraph 3**
- [main]        Invite Teman activates when a recruited user completes at least one transfer;
                Oper Puzzle converts a duplicate piece into a Putar Roda spin via a same-level friend.
- [reinforcing] Kejar Puzzle rewards completing five transfers to five different users on a Friday.
```

### 4. Complete Analysis Before Writing

Resolve comparisons, calculations, and implications before writing any Content Point.

### 5. No Invented Information

Content Points must be based on provided data or verified research. If it cannot be verified, do not write it.

### 6. Label Theoretical and Calculated Figures

| Wrong | Right |
|---|---|
| Covering 1,000 km costs IDR 250,000. | `[reinforcing]` At IDR 10,000 per liter and a theoretical consumption of 40 km/L, covering 1,000 km requires approximately 25 liters, or about IDR 250,000. |

---

## Section Format (Non-Negotiable)

```
## [SECTION TITLE]

**Paragraph 1**
- [main] Main idea of this paragraph.
- [supporting/reinforcing/additional] Continues from the point above.

**Paragraph 2**
- [main] Main idea of the second paragraph.
- [supporting/reinforcing/additional] Continues from the point above.
```
