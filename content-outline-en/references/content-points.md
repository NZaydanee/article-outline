# Content Points Reference

Content Points are the list of information that **must be conveyed** in one article section. They are the semantic payload of the outline — not instructions to the writer.

A writer receiving Content Points performs *surface realization* only: turning points into natural, readable prose. The writer does not search for information, determine angles, add examples, or develop new topics.

---

## Content Point Labels

Every Content Point must carry a label indicating its role in the paragraph:

| Label | Definition | Position in paragraph |
|---|---|---|
| `[main]` | The main idea of the paragraph; becomes the topic sentence | Always first |
| `[supporting]` | Explains or elaborates on the main idea | After `[main]` |
| `[reinforcing]` | Strengthens with data, numbers, or specific facts | After `[main]` or `[supporting]` |
| `[additional]` | Relevant information that completes without repeating | Last in the group |

**Label rules:**
- Every paragraph group must have **exactly one** `[main]`
- `[main]` is always the first point in the group
- One or more other labels follow after `[main]`
- Order after `[main]`: explain first → reinforce with data → add context

---

## 6 Core Rules

### 1. Every Content Point Must Be Concrete

Write as information to be displayed, not as a task for the writer.

**Prohibited verbs:** explain, discuss, elaborate, mention, compare, highlight, talk about, give examples, show why.

| Wrong | Right |
|---|---|
| Explain the seat height. | `[main]` A 750 mm seat height makes it easier for the rider to reach the ground when stopping. |
| Discuss why the 4.2-liter tank is useful. | `[supporting]` A 4.2-liter fuel tank provides a larger fuel reserve before the next refueling stop. |

### 2. Connect Facts to Their Meaning

Do not present raw data without context.

| Wrong | Right |
|---|---|
| Seat height: 750 mm | `[main]` A 750 mm seat height makes it easier for the rider to reach the ground when stopping. |

### 3. One Semantic Meaning Per Point

Split complex information across separate points.

**Wrong:** The 750 mm seat height and 95 kg weight make the motorcycle comfortable, easy to control, beginner-friendly, practical to park, and ideal for city riding.

**Right:**
- `[main]` A 750 mm seat height makes it easier for the rider to reach the ground when stopping.
- `[supporting]` The motorcycle's 95 kg weight supports low-speed maneuverability.

**Special case — lists of items (features, options, steps):**

If a section contains multiple named items, do not pack all of them into one supporting point. Instead:
1. Use the point after `[main]` to **name and introduce** the group of items.
2. Use subsequent paragraph groups to explain each item — one group per item or per logical cluster.

**Wrong:**
```
**Paragraph 2**
- [main] Three booster features shorten the path to completing the puzzle.
- [supporting] Invite Teman works when a recruited user completes one transfer; Oper Puzzle converts duplicates into a Putar Roda spin via a same-level friend; Kejar Puzzle rewards five transfers to different users on a Friday.
```

**Right:**
```
**Paragraph 2**
- [main] Three booster features shorten the path: Invite Teman, Oper Puzzle, and Kejar Puzzle.
- [additional] Each targets a different transfer behavior, so they can be used independently or combined in the same week.

**Paragraph 3**
- [main] Invite Teman activates when a recruited user completes at least one transfer; Oper Puzzle converts a duplicate piece into a Putar Roda spin via a same-level friend.
- [reinforcing] Kejar Puzzle rewards completing five transfers to five different users on a Friday with additional puzzle pieces.
```

### 4. Complete Analysis Before Writing

Resolve comparisons, calculations, and implications before writing any Content Point. Only include a comparison if base data has been verified.

| Wrong | Right |
|---|---|
| Compare the fuel tank capacity with competitors. | `[reinforcing]` The 4.2-liter tank is larger than Competitor A's 3.5-liter tank, providing 0.7 liters of additional capacity. |

### 5. No Invented Information

Content Points must be based on provided data or verified research. Do not fill research gaps with plausible-sounding claims. If a claim cannot be verified, do not write it.

### 6. Label Theoretical and Calculated Figures

Use clear language when a number is theoretical, estimated, or the result of a calculation.

| Wrong | Right |
|---|---|
| Covering 1,000 km costs IDR 250,000. | `[reinforcing]` At IDR 10,000 per liter and a theoretical consumption of 40 km/L, covering 1,000 km requires approximately 25 liters, or about IDR 250,000. |

---

## Section Format (Non-Negotiable)

```
## [SECTION TITLE]

**Paragraph 1**
- [main] The main idea of this paragraph.
- [supporting] Detail that elaborates on the main idea.

**Paragraph 2**
- [main] The main idea of the second paragraph.
- [reinforcing] Specific data or fact that strengthens the claim.

**Paragraph 3** *(only if paragraph budget allows)*
- [main] The main idea of the third paragraph.
- [additional] Relevant information that completes without repeating.
```
