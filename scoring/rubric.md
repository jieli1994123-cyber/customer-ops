# Scoring rubric

Every candidate is scored on three dimensions. Scores are worthless without reasons: each dimension gets a one-line justification tied to a source in the lead's `research.md`.

## Fit — 0 to 5 (does this company need what the user sells?)

| Score | Meaning |
|---|---|
| 5 | Textbook ICP: right segment, right size, visibly has the exact problem |
| 4 | Strong match; one criterion assumed rather than proven |
| 3 | Plausible match; the problem is inferred, not evidenced |
| 2 | Adjacent segment; would need a different pitch or product tweak |
| 1 | Weak; only a generic "they're a business" connection |
| 0 | No fit |

## Contact-ability — 0 to 2 (can we reach a decision-maker publicly?)

| Score | Meaning |
|---|---|
| 2 | Named right-role person + published contact point |
| 1 | Named person, or only a company contact point |
| 0 | Neither — research more or drop |

## Timing — 0 to 2 (is there a reason to talk *now*?)

| Score | Signal |
|---|---|
| 2 | Active pain or change: public complaint about an incumbent, relevant hire in progress, launch/expansion, recent funding earmarked for this area |
| 1 | Soft signal: growth, new location/product line, seasonal peak approaching |
| 0 | No signal — could be any time, which usually means no time |

## Total and thresholds

`Total = Fit × 2 + Contact + Timing` (Fit dominates; max 14)

- **Shortlist:** Total ≥ 10 **and** Fit ≥ 4 **and** Contact ≥ 1 — a lead nobody can be reached through is not a lead; it stays in the pool, not the shortlist
- **Maybe:** Total 7–9 — kept in pool, rescored when a new signal appears
- **Skip:** below that, with the reason recorded

Per-segment overrides (thresholds, weights, extra signals) live in `profile/icp.md` and beat these defaults.

## Vetoes (override any score — straight to `skipped` or `do_not_contact`)

- Competitor of the user, or a company the user already sells to / is negotiating with
- Defunct, acquired-and-absorbed, or no public activity in 12+ months
- `pain-public` in reverse: they publicly *love* their incumbent and just renewed/expanded it
- Segment mismatch the user declared a hard no in `/setup`
- Already in the tracker as `do_not_contact`

## Honesty clauses

- Unverifiable = Fit capped at 2 until verified.
- A score is a research summary, not a prediction. `/review` recalibrates weights from real reply data; until then, treat Timing claims with suspicion — yours included.
