# AI-Native Job Application Framework

This repository contains zero executable code. It is a small Markdown prompt pack plus local personal files, a setup checklist, and one daily application record per date.

## 🚀 Workflow

1. Download the repository folder.
2. Open the folder in Codex, Claude Code, Antigravity, or another agent with browser/search access.
3. Type `start`.
4. The agent checks both the setup checklist and the actual required local files/answers.
5. If setup is unfinished, it resumes one topic at a time without overwriting completed information and does not apply for jobs.
6. After setup, choose the supported application platforms and requested counts.
7. The agent creates/resumes one daily record at `applied/YYYY-MM-DD/applications.md`.
8. The agent uses saved information, fit checks, scoped duplicate checks, hard daily limits, two-minute pacing, and explicit first-submit review.
9. After each outcome, the agent appends the job result immediately. New unanswered questions are saved with their employer/country/role/portal context.
10. At the end of the session, the agent reports applied/skipped/needs-user outcomes and preserves enough progress for the next chat.

Setup never starts applications until all required setup checks pass.

## 📁 Local data and records

```text
personal_data/
  resume.pdf
  profile.md
  form_answers.md
  credentials.md

applied/
  YYYY-MM-DD/
    applications.md

tracking/
  created_accounts.csv
  applied_jobs.csv   # legacy, read-only when present
```

Only the templates and instruction files are committed. Real personal data, account records, runtime setup checklists, and daily application files are ignored by Git.

`tracking/applied_jobs.csv` is a legacy read-only input if it already exists. New application records are written only to the dated Markdown file.

## 🧭 Supported application sources

- LinkedIn
- Indeed
- Naukri
- Wellfound
- Instahyre
- Workday
- Company career pages (`company_direct`)
- Web discovery (`discovery`)

For `company_direct`, provide career URLs during setup. Discovery does not need saved career URLs.

Any form hosted by Workday is counted as Workday, regardless of where the job was found.

## 🔢 Hard daily limits

- LinkedIn: 20
- Indeed: 20
- Naukri: 25
- Wellfound: 10
- Instahyre: 10
- Workday: 5
- `company_direct` + `discovery`: 10 combined
- All platforms: 50 combined

The user may request lower counts. The agent must recount before every application, including after a local-midnight change and when resuming a previous session.

## 🤖 Model guidance

Model names and versions are intentionally not hard-coded.

- Setup: strongest/higher tier.
- Quick-apply platforms: light tier.
- Workday, company-direct, discovery: medium tier.

The agent asks the user to select the appropriate tier when needed; it does not pretend to switch models. A new chat is not mandatory merely because a model change would be useful. When a handoff is genuinely needed, all progress is saved first.

## ✅ Safety and practical safeguards

The framework keeps the existing practical protections: fit checks, scoped duplicate checks, no guessed answers, first-submit `ok`, host-app approvals, confirmation before success, two-minute pacing, site-stop/CAPTCHA/authentication rules, and retry limits.

The LinkedIn strategy uses the GitHub-safe wording `Follow [company]` rather than angle-bracket HTML.

The setup checklist is a helper, not proof of readiness. The agent must inspect the actual files and saved values every time `start` is used.
