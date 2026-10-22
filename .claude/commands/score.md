# /score — deep-dive the pool, rank it, talk the user out of the weak ones

Usage: `/score` (scores everything `discovered` in the tracker) or `/score <pool-file>`.

Goal: a ranked shortlist the user can approve in one read — plus an explicit skip list with reasons. Scoring follows `scoring/rubric.md`; overrides in `profile/icp.md` win.

## Steps

1. **Deep-dive each candidate** (parallelize with subagents for pools > 10; each agent gets one company and the rubric):
   - Their site: what they sell, who to, size signals (team page, locations, catalog depth)
   - Current stack / incumbents: what they use today for the problem the user's product solves (built-with signals, app/plugin footprints, job posts naming tools)
   - Timing signals: recent funding, hiring for the relevant role, a launch, expansion, a public complaint about an incumbent (`pain-public` from discovery weighs heavily)
   - Decisive visual check: when a single observable fact decides fit (e.g. "does their launch page already have a video", "is there a pricing page"), open the page in a real browser and look — text scraping cannot see media sections, hero videos, or screenshots. A shortlist candidate must have this check done
   - Vetoes from the rubric and the user's ICP (wrong segment, competitor, defunct, existing customer of the user, `do_not_contact`)
   Write findings to `leads/<company-slug>/research.md` — **every fact with its source URL**.
2. **Score** per the rubric: Fit (0–5) × Contact-ability (0–2) × Timing (0–2), vetoes override totals. Record the one-line reason per dimension — a score without a reason is not a score.
3. **Split the output:**
   - **Shortlist** (score ≥ the segment's threshold, default in rubric): ranked, best first
   - **Skip list**: everyone else, each with the reason (`too small`, `uses competitor deeply`, `no timing signal`, `unverifiable`…)
   Update the tracker: shortlisted → `shortlisted`, skipped → `skipped` (reason in notes).
4. **Present for approval.** Show the shortlist as a compact table (company, score, the single best reason to contact them now). The user can remove entries or rescue skips; apply their edits to the tracker before finishing.

## Rules

- If you cannot verify what a company does from public sources, score it `unverifiable` and skip it — never fill gaps with plausible guesses.
- Be the skeptic: when evidence is thin, say the shortlist is weak rather than inflating scores. A shortlist of 8 strong leads beats 30 maybes.
- Research is read-only. Do not contact, follow, or interact with any lead's properties.
