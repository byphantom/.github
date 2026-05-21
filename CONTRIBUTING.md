# Contributing to byphantom

Welcome. byphantom is the org behind **PHANTOM**, an AI-powered luxury concierge platform for HDFC Bank's top 500K cardholders, operated by R360 / Reward360 Global Services Pvt. Ltd.

## Before your first commit

Each repo has an `ONBOARDING.md` with a day-1 reading list tailored to that codebase. Read it first.

| Repo | Onboarding |
|---|---|
| [hdfc-concierge-platform](https://github.com/byphantom/hdfc-concierge-platform) | [ONBOARDING.md](https://github.com/byphantom/hdfc-concierge-platform/blob/main/ONBOARDING.md) |
| [knowledge-archive](https://github.com/byphantom/knowledge-archive) | [ONBOARDING.md](https://github.com/byphantom/knowledge-archive/blob/main/ONBOARDING.md) |
| [phantom-crawler](https://github.com/byphantom/phantom-crawler) | [ONBOARDING.md](https://github.com/byphantom/phantom-crawler/blob/main/ONBOARDING.md) |
| [phantom-console-legacy](https://github.com/byphantom/phantom-console-legacy) | reference only — no active development |

## Universal rules (apply to every repo)

These live in `CLAUDE.md` at the root of `hdfc-concierge-platform` and govern every change:

- **NEVER-DELETE** — no `rm`, no `git push --force`, no `gh repo delete` without per-instance founder approval. Pocket aside, rename, or annotate instead.
- **Universal data-write rule** — any DB write affecting >100 rows must use the [kb-safe-write](https://github.com/byphantom/hdfc-concierge-platform/blob/main/scripts/kb-pipeline/kb-safe-write.js) wrapper. No direct PATCH/POST/PUT to a table.
- **Maker-checker governance** — every customer-facing content change (templates, KB entries, copy) flows through DRAFT → APPROVED with `approver_id != maker_id` and a God-Rails check at create + approve.
- **Window-coordination** — before any code/migration/deploy, run the pre-flight (git fetch, log, worktree list, open PRs, ps aux, cron jobs).
- **Auto-archive** — every Claude Code session on Amit's machines archives its conversation transcript (redacted) to `byphantom/knowledge-archive` via a Stop hook. Don't bypass.

## Pull requests

- One feature/fix per PR. No bundled work.
- PR title under 70 chars. Body explains the why, not just the what.
- Tests required for any new functionality. UI changes require a screenshot or a Vercel preview link.
- CODEOWNERS routes reviewers automatically — wait for them.
- NEVER merge to `main` with `--no-verify`. If a pre-commit hook fails, fix the underlying issue.

## Questions

amit.chawla@reward360.co
