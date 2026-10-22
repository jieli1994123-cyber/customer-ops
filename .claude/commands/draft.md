# /draft — one researched email per lead, written by one agent and critiqued by another

Usage: `/draft` (all shortlisted leads with a contact) or `/draft <company-slug>`.

Goal: for each lead, a final first-touch email + a 2-step follow-up sequence, saved to `leads/<company-slug>/draft.md`, plus an entry in `outreach/send-list.md` once the user approves.

## The drafter–reviewer protocol

For each lead, run two passes. **The reviewer must be a separate subagent with fresh context.** It receives only the draft and the lead's `research.md` — never the drafter's reasoning.

### Pass 1 — Drafter

Inputs: `profile/product.md`, `profile/voice.md` (if present), the lead's `research.md`.

Write the first-touch email:

- **Under 120 words.** One idea per email.
- **Open with the researched specific**: something true about *them* (a launch, a complaint they posted, a tool they use, a hire) — sourced from `research.md`. If no specific exists, stop: this lead isn't draftable yet, send it back for more research instead of writing a generic email.
- **One clear relevance bridge**: their situation → the outcome the user's product produces. No feature lists.
- **One low-friction ask**: a question or a 15-minute look — not a demo pitch deck.
- **Voice**: match `profile/voice.md`; default is plain and specific, zero hype words ("revolutionary", "game-changing", "synergy" are banned).
- 2–3 subject lines, each ≤ 6 words, no clickbait.

Then write the follow-up sequence (sent only if no reply):

- **Follow-up 1 (+3 days)**: ≤ 60 words, new angle or new proof point, not "just bumping this".
- **Follow-up 2 (+7 days)**: ≤ 50 words, the polite break-up: make it easy to say no, leave the door open.

### Pass 2 — Reviewer (fresh subagent)

Check the draft against this list and return verdicts, not vibes:

1. **Fact check**: every specific claim traces to `research.md`? Flag any that doesn't — it gets cut, not softened.
2. **Generic test**: could this email be sent to 100 other companies unchanged? If yes, fail it back to the drafter with the missing specific.
3. **Tone check**: anything that reads as mass-mail, flattery-padding, or AI-slop? Flag the exact phrases.
4. **Ask check**: is there exactly one ask, and is it small?
5. **Length check**: over the word limits? Trim, don't summarize.

The drafter revises once against the reviewer's notes. Both versions and the reviewer notes stay in `draft.md` — the paper trail is how the user learns to trust (or fix) the system.

## Approval and the send list

Present finals to the user in a compact list (lead, subject, first line). The user approves all, approves selectively, or edits. Only approved finals are appended to `outreach/send-list.md` with: recipient, contact point, subject, body, follow-up 1/2 with their send-after dates.

**Reminder to print at the end of every run:** "These are drafts. Nothing has been sent. You send from your own mailbox — suggested pace ≤ 30 first-touches/day."

## Rules

- Check `do_not_contact` before drafting anyone (CLAUDE.md rule 5).
- A lead whose contact is `guessed — unverified` is drafted but held out of the send list unless the user explicitly includes it.
- Never draft for a competitor of the user, or for a company the user already has a relationship with (check tracker notes).
