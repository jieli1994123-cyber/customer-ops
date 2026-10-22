# /outcome — record what happened, classify replies, draft the next move

Usage: `/outcome` — then either tell it what you sent ("sent all 12 from Tuesday's list"), or paste the replies you received.

Goal: keep the funnel truthful. The tracker only learns what the user reports; this command turns messy real-world results into statuses, classifications, and next-step drafts.

## Mode 1 — Mark sends

When the user reports sends (all / some / specific leads from `outreach/send-list.md`):

- Set those leads to `sent` with the send date in the tracker.
- Compute follow-up due dates (+3d, +7d from the draft) and list what's coming due in the next 3 days.

## Mode 2 — Process replies

For each pasted reply:

1. **Match it to the lead** (sender, company, thread content). If the match is ambiguous, ask — never guess.
2. **Classify** into exactly one:
   - `interested` — wants to talk / learn more → draft a reply proposing 2–3 concrete times + a one-line agenda
   - `not-now` — timing objection → draft a graceful exit + propose a re-contact date (default +60 days); tracker status stays `replied`, add `revisit: <date>`
   - `no-budget` — price objection → draft a short reply (acknowledge, leave a lower-friction door open); do not discount unless the user's profile defines a fallback offer
   - `wrong-person` — not their area → draft a referral ask: who owns this, and may I mention your name? Referral replies are the highest-converting path in B2B — treat them as gold, log the referred name as a new lead when provided
   - `has-solution` — happy with an incumbent → draft a one-question reply ("what would have to break for you to look around?") unless they asked to stop
   - `negative` — annoyed / not interested → no draft; status `lost`
   - `opt-out` — any form of "stop / unsubscribe / don't contact" → status `do_not_contact`, permanent, no draft, no exceptions
   - `auto` — OOO / auto-reply → note the return date if stated; shift follow-ups past it
3. **Save** the reply text + classification in the lead's folder (`leads/<slug>/replies.md`), update the tracker, and present reply drafts for the user's approval (drafts only — the user sends).

## Mode 3 — Follow-up drafting

When follow-ups come due for `sent` leads with no reply:

- Serve the pre-written follow-up from `draft.md`, refreshed against anything new in `research.md` (e.g. they just launched something — the follow-up may cite it, with source).
- After follow-up 2 with no reply: status `lost — silent`, and the lead may only re-enter via a new discovery signal after 90 days.

## Rules

- Never mark anything sent that the user didn't confirm sending. An approved draft is not a sent email.
- Every classification shows its reason in one line; `opt-out` and `negative` classifications are never argued with.
