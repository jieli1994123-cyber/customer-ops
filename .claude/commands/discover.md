# /discover — build the candidate pool for one segment

Usage: `/discover <segment>` (segment name from `profile/icp.md`, or a free-text description which you then match to a segment or treat as a one-off).

Goal: a **sourced** candidate pool — companies that plausibly fit the segment, each with the public evidence that made them a candidate. Discovery optimizes for recall-with-evidence, not precision: `/score` does the filtering.

## Steps

1. **Load the playbook.** Read the playbook named in the segment (`playbooks/<name>.md`). It defines: where this customer type is publicly listed, the search queries to run, the qualifying signals, and the disqualifiers. If the segment has no playbook, say so and offer to draft one from `playbooks/_template.md` before continuing.
2. **Run the playbook's searches.** Web search + the directories/platforms it names. Work in batches of ~25 results. For each candidate capture:
   - Company name + website
   - One-line what-they-do (from their own site, not your guess)
   - The **signal** that surfaced them (directory listing, a complaint about an incumbent, a hiring post, a launch…)
   - Source URL(s) — mandatory; no source, no candidate
3. **Dedupe against the tracker.** Skip anything already in `tracker.md` (any status, including `skipped` and `do_not_contact`). Report how many were dropped as duplicates.
4. **Apply playbook disqualifiers only** (hard mismatches: wrong country, wrong platform, clearly defunct). Do not score yet.
5. **Write the pool** to `leads/_pool/<YYYY-MM-DD>-<segment>.md` and add each kept candidate to `tracker.md` as `discovered`.

## Output summary

`Discovered: N raw → M after dedupe → K kept. Pool: leads/_pool/<file>. Next: /score`

## Rules

- Public channels only; no login-walled scraping, no data-broker lists (see CLAUDE.md).
- Thin listing → resolve first: when a directory, marketplace, or crowdfunding listing is too thin to judge (no description, no clear product), resolve it to the company's own website before deciding to keep it. Judge the company, never the listing. If there is no verifiable own site, flag it `thin` and keep it in the pool — `/score` skips thin-flagged candidates until the site is confirmed.
- A complaint/pain post about an incumbent competitor is the highest-value signal — flag those candidates with `signal: pain-public` so `/score` can weight them.
- Stop conditions: the playbook's query set is exhausted, or the user-set cap is hit (default 100 new candidates per run). More is not better — say when returns thin out.
