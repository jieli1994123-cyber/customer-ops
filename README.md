# customer-ops

*The customer search that runs on your machine.*

An open-source AI outreach framework built on Claude Code. Point it at your product's code repo, and it figures out what you're selling, finds the companies most worth contacting, scores them against your ICP, and drafts outreach emails a second agent has already critiqued.

**It never sends anything. You press send.**

```
Companies use AI to filter vendors.
This gives founders AI to *choose* customers.
```

## Does it actually work?

<!-- DOGFOOD STORY GOES HERE: replace with your real funnel numbers before launch.
     Format that worked for career-ops: "N companies scanned. M shortlisted. K emails sent. J replies. H meetings." -->

*This section is reserved for the maintainer's own funnel — scanned → shortlisted → sent → replies → meetings — with real numbers, updated as they change.*

## What this is

A structured workflow that turns Claude Code into a front-end sales researcher + SDR assistant for indie hackers and small teams:

```
/setup            /discover           /score             /draft
   |                  |                   |                  |
   v                  v                   v                  v
Read your repo    Search public      Score & rank       Drafter writes
(or URL, or       channels per       against your       Reviewer critiques
 interview)       playbook           ICP rubric         Revise -> final
   |                  |                   |                  |
   v                  v                   v                  v
Product profile   Candidate pool     Shortlist you      Send list you
+ ICP segments    with sources       approve            approve
```

Then `/outcome` classifies the replies you paste back and drafts follow-ups, and `/review` turns the funnel into calibration: which segments and angles actually convert.

## What customer-ops will not do

- **Send email, DMs, or form submissions.** Ever. It produces drafts and send lists; the human sends.
- **Scrape behind logins or automate LinkedIn.** Discovery uses public channels only.
- **Invent facts.** Every specific claim in a draft must trace to a source captured during research. If it can't be sourced, it doesn't get written.
- **Collect private contact data.** Public business contact points only (company contact pages, published work emails, public profiles).

## Quick start

### 1. Get the framework

```bash
git clone https://github.com/jieli1994123-cyber/customer-ops.git
cd customer-ops
```

> ⚠️ **Privacy:** `/setup` writes *your* product and outreach data into local files. Those folders are git-ignored by default (see `.gitignore`), but if you plan to push your copy anywhere, use a **private** repository. GitHub does not allow private forks of public repos — clone into a fresh private repo instead if in doubt.

### 2. Set up your product (one command)

```bash
claude
# Inside Claude Code:
/setup
```

`/setup` offers three paths:

- **A — Read my code repo (recommended).** Point it at the repo of the product you built (or run it from inside the repo). It reads your README, docs, landing-page copy in code, pricing pages, app metadata and changelog, and drafts your product profile automatically. You confirm and edit — nothing is taken on faith.
- **B — Read my website.** Give it your landing page URL; it builds the profile from your public positioning.
- **C — Interview me.** No repo, no site yet: answer a short interview instead.

Output: `profile/product.md`, `profile/icp.md` (2–3 candidate customer segments + your scoring rules), optional `profile/voice.md` (your writing samples, so drafts sound like you).

### 3. Run the funnel

```bash
/discover <segment>     # candidate pool with sources, deduped against your tracker
/score                  # ranked shortlist + who to skip, and why
/contacts               # the right person + public contact point per shortlisted lead
/draft                  # one outreach email + follow-up sequence per lead, drafter-reviewed
```

You approve the shortlist, approve the drafts, export the send list (`outreach/send-list.md`), and send from your own mailbox.

### 4. Close the loop

```bash
/outcome                # paste replies -> classified, reply drafts, follow-ups for silent leads
/review                 # weekly funnel report + ICP calibration suggestions
```

## Commands

| Command | What it does |
|---|---|
| `/setup` | Build your product profile + ICP from your repo, your website, or an interview |
| `/discover` | Find candidate companies for a segment, using the matching discovery playbook |
| `/score` | Deep-dive and score candidates against your ICP rubric; ranked shortlist + skip list |
| `/contacts` | Find the right person and public business contact point for each shortlisted lead |
| `/draft` | Drafter–reviewer outreach email + follow-up sequence per lead |
| `/outcome` | Record sends, paste replies, get classifications + reply/follow-up drafts |
| `/review` | Funnel report and calibration: what converts, what to drop |

## Discovery playbooks

Discovery is playbook-driven: each playbook documents where a customer type is publicly findable, which queries to run, and which signals matter. Ships with:

- `playbooks/startups.md` — early-stage startups (launch platforms, directories, communities)
- `playbooks/online-stores.md` — e-commerce / online stores (store directories, platform signals)
- `playbooks/creators.md` — creators & newsletter/podcast operators (platform pages, public sponsorship/contact info)
- `playbooks/local-smb.md` — local service businesses (directories, maps data, review signals)

New playbooks are the easiest way to contribute — start from `playbooks/_template.md`.

## File structure

```
.claude/commands/     the seven workflow commands
playbooks/            where each customer type hides, and how to search it
scoring/rubric.md     the scoring framework (fit x contact x timing, vetoes)
templates/            product profile, ICP, tracker templates
examples/demo-run/    one complete fictional run, end to end
profile/              YOUR product profile + ICP        (git-ignored)
leads/                per-lead research + drafts        (git-ignored)
tracker.md            your outreach funnel              (git-ignored)
```

## Staying honest (and out of spam folders)

- Drafts are written for **one recipient at a time**, grounded in researched specifics — the opposite of blast email.
- Suggested pace: **≤ 30 first-touch emails per day per mailbox**, warmed up gradually. This tool will warn you above that.
- Anyone who replies "stop" is marked do-not-contact permanently, across all future runs.
- Quality gate: a lead you can't say something *specific and true* about is a lead you don't email.

## Roadmap

- More discovery playbooks (agencies, SaaS micro-tools, course sellers…)
- Reply-intent benchmarks per segment
- Optional CRM/Notion export of the tracker
- More languages for this README

## License

MIT. Fork it and own it.
