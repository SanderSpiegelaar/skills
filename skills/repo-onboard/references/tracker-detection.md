# Tracker Detection

Open this when deciding the supported issue-tracker target for onboarding.

## Supported Targets

| Signal | Recommended tracker |
| --- | --- |
| GitHub remote exists | GitHub issues |
| `.github/` exists without a remote | Ask before assuming GitHub issues |
| `.scratch/` contains issue or feature markdown | Local markdown under `.scratch/<feature>/` |
| No supported signal | Recommend local markdown unless the user chooses GitHub |

Only GitHub issues and local markdown are supported in v1.

## GitHub Detection

Check:
- `git remote -v`
- `.git/config`
- `.github/ISSUE_TEMPLATE/`
- `.github/workflows/`

Treat a GitHub remote as the strongest signal. Do not assume publishing is allowed; note that downstream skills publish only when the user explicitly asks.

## Local Markdown Detection

Check:
- `.scratch/`
- `.scratch/*/*.md`
- existing local issue lists in docs when explicitly named by the user

Recommend local markdown when no GitHub remote exists or when the repo already uses `.scratch/` for planning.

## Unsupported Trackers

If Jira, Linear, GitLab, Azure DevOps, or another tracker appears:
- record it as an unsupported signal
- do not map it into `docs/agents/issue-tracker.md` as an active target
- ask whether to use GitHub or local markdown for workflow publication

## Output Wording

State:
- detected signal
- recommended supported tracker
- whether publication is automatic or only on explicit request

Example: `Detected GitHub remote; recommend GitHub issues as the supported tracker. Downstream skills should publish only when the user explicitly requests it.`
