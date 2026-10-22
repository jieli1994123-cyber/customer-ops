# /setup — build the product profile and ICP

Goal: turn whatever the user already has (a code repo, a website, or just their answers) into two files the rest of the framework runs on:

- `profile/product.md` — what the product is, who it helps, proof, pricing, competitors
- `profile/icp.md` — 2–3 candidate customer segments + the scoring rules for each

Everything inferred is presented to the user for confirmation **before** it is saved. Nothing in these files may be invented: each field is either read from a source or marked `inferred — please confirm`.

## Step 0 — Offer the three paths

Ask the user which path to take (default to A if they are inside a product repo):

- **A. Read my code repo** — "Point me at the repo (or I'll use the current directory) and I'll draft the profile from the code."
- **B. Read my website** — needs the product URL.
- **C. Interview me** — 6 short questions, no artifacts needed.

Paths can combine: if A or B surfaces gaps, fill them with C-style questions at the end.

## Path A — Repo scan protocol (one-click product understanding)

Run from the repo root. Read in this priority order; stop reading a category once you have enough signal:

1. **Positioning first**
   - `README*` (root) — product description, feature list, target-user language, screenshots' alt text
   - `docs/` — getting-started, use-case and feature pages
   - Landing/marketing copy **in code**: `pages/index.*`, `app/page.*`, `components/hero*`, `components/landing*`, locale files (`en.json`, `*.po`) — hero headline + subheadline are usually the sharpest positioning the founder has written
2. **Product shape**
   - `package.json` / `pyproject.toml` / `Cargo.toml` / `go.mod` — name, description, dependencies (integrations reveal the ecosystem and therefore the buyer)
   - `app.json`, `manifest.json`, `fastlane/metadata/**`, `*.xcconfig` product names — shipped product name if it differs from the repo name
   - Feature flags / route names / main screens — what the product actually does day to day
3. **Commercial signals**
   - Pricing: `**/pricing*` components/pages, plan constants (`plans.ts`, `PLANS`, Stripe price IDs are opaque — note plan *names and tiers*, never guess amounts), `LICENSE`/edition gates (open-core split hints at who pays)
   - Proof: testimonials in code, `customers`/`logos` assets, case-study pages
4. **Direction**
   - `CHANGELOG.md` (latest ~15 entries) — what the product is becoming
   - Public roadmap / issues labels if present in-repo

Then synthesize:

- One-sentence positioning (their words, lightly cleaned — not your paraphrase of what you *wish* it was)
- Feature list mapped to **buyer outcomes** ("exports to X" → "saves the ops person a manual step")
- Ecosystem signals → candidate buyer types (a Shopify app implies store owners; a Figma plugin implies design teams)
- Explicitly list what the repo could **not** tell you (pricing amount, current customers, traction) as questions for the user

Monorepo: if multiple products live in one repo, ask which one this outreach is for before profiling.
No README and thin code comments: fall back to directory/screen names + route structure, mark the whole draft `low confidence`, and lean on interview questions to fill gaps.

## Path B — Website scan

Fetch the homepage, pricing page, and features page(s). Extract the same fields as Path A. If the site names a repo or app-store listing, offer to cross-check with Path A sources — code and marketing disagreeing is itself a finding worth showing the user ("your site says X, your app does Y — which is current?").

## Path C — Interview (also the gap-filler for A and B)

Ask only what's missing, in this order, one at a time:

1. In one sentence: what does your product do, and for whom?
2. Who has already paid (or would pay first)? Describe one real happy customer if you have one.
3. What does a customer use today instead of you? (competitor, spreadsheet, doing nothing…)
4. Price point and how it's charged?
5. Which buyers are a definite **no** for you? (too small, wrong industry, competitors…)
6. Where do your buyers hang out publicly? (platforms, communities, directories)

## Step — Derive candidate ICP segments

From the profile, propose **2–3 segments**, each with:

- Who they are, in findable terms ("Shopify stores selling physical goods, US, 5–50 staff" — not "small businesses")
- Why they'd care (the specific pain your product removes)
- Where they are publicly findable → which playbook applies (or "needs a new playbook")
- Known vetoes (from interview Q5 + profile)

User picks, edits, or replaces segments. Only confirmed segments go into `profile/icp.md`.

## Step — Optional voice sample

Ask for 2–3 samples of the user's own writing (a past email, a launch post). Save to `profile/voice.md`. If skipped, note `voice: default (plain, specific, no hype)` in the profile.

## Step — Save and initialize

1. Write `profile/product.md` and `profile/icp.md` from the templates, with a `Sources:` line per section (repo files / URLs / "interview").
2. Initialize `tracker.md` from `templates/tracker.template.md` and the `leads/` + `outreach/` folders.
3. Print a confirmation summary: product one-liner, segments chosen, fields still marked `inferred`, and the suggested next command (`/discover <segment>`).

Re-running `/setup` refreshes the profile: show a diff against the saved version and let the user accept or reject changes per section — never silently overwrite a user-edited profile.
