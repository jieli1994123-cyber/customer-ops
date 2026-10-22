# /contacts — find the right person for each shortlisted lead

Usage: `/contacts` (all `shortlisted` leads lacking a contact) or `/contacts <company-slug>`.

Goal: for each lead, the **right person** (the role that owns the problem the user's product solves) and a **public business contact point** — or an honest `no public contact` verdict.

## Steps

1. **Pick the target role** from the segment in `profile/icp.md` (e.g. founder for <10-person companies; Head of Ops / owner for SMB; the creator themselves for creator businesses). Note the role choice in the lead's `research.md`.
2. **Find the person** from public sources, in order: company About/Team page → public professional profiles surfaced by search → press/podcast/launch posts naming them. Capture name, role, and the source URL for each.
3. **Find the contact point**, in order of preference:
   - Published work email (on their site, in a directory listing, in a public post) — mark `published`
   - Company contact page / contact form URL — mark `form`
   - Public social profile suitable for a DM — mark `social` (draft only; sending stays manual and off-platform automation is out of scope)
   - Pattern-guessed email — mark `guessed — unverified`, **excluded from send lists by default**; tell the user it's a guess
4. **Update the lead's `research.md`** with a `Contact` section (person, role, contact point, type, source) and set the tracker status to `contacted` (meaning: contact identified — the name is historical; sending is tracked by `/outcome`).

## Rules

- Public business contact points only (CLAUDE.md rule 3). No personal emails, no data brokers, no leaked lists.
- If two people plausibly own the problem, list both with a recommendation — don't silently pick.
- `no public contact` is a valid, useful result: it moves the lead back to the pool with a note, instead of forcing a guessed email.
