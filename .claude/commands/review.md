# /review — the funnel, honestly, and what to change

Usage: `/review` (weekly by default; `/review <segment>` to scope it).

Goal: turn the tracker into decisions. Not a vanity report — a calibration session.

## The funnel report

From `tracker.md`, for the period:

| Stage | Count | Conversion from previous |
|---|---|---|
| Discovered | | |
| Scored → shortlisted | | |
| Drafted → approved → sent | | |
| Replied (any) | | |
| Interested | | |
| Meetings | | |

Plus: reply classification breakdown (interested / not-now / no-budget / wrong-person / has-solution / negative / opt-out), and follow-up performance (did follow-up 1 or 2 produce replies the first touch didn't?).

Small numbers rule: under ~30 sends, present counts without percentages theatre — say "too early to conclude" where that's the truth.

## The calibration pass

Answer three questions with evidence from the data:

1. **Which segment is actually converting?** Compare reply/interested rates per segment in `profile/icp.md`. Recommend: double down / keep testing / drop — with the counts behind the recommendation.
2. **Which scoring signals predicted replies?** Cross-tab: did `pain-public` leads reply more? Did high-Timing leads? Propose concrete rubric changes (weight up/down, new veto) as edits to `profile/icp.md` overrides — **propose, don't apply**: the user approves each change.
3. **Which draft angles worked?** Group sent drafts by their opening specific (launch / complaint / stack / hire). Note which openings earned replies; feed the winner pattern back into `/draft` guidance for the user's workspace (a short `profile/angle-notes.md`).

## Output

A one-page report saved to `outreach/review-<YYYY-MM-DD>.md` and summarized in chat: funnel table, the three answers, and the list of proposed changes awaiting approval. If the tracker is empty or nearly so, say the honest thing: run more of the funnel first, here's the smallest useful next batch.
