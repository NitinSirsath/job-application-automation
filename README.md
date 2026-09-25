# AI-Native Job Application Framework

This repository contains zero executable code. It is a small set of Markdown instructions, local personal-data files, setup state, account records, and daily application records for an AI agent with browser automation.

## 🚀 Workflow

1. Download the repository folder.
2. Open the folder in Codex, Claude Code, Antigravity, or another supported AI app with browser access.
3. Type \`start\`.
4. The agent creates missing personal-data files from the committed templates and guides setup one topic at a time.
5. Setup is resumable: answers are saved immediately, skipped optional values are stored as \`None\`, and a local \`setup_checklist.md\` is only a progress aid.
6. The agent verifies the real files before allowing applications.
7. After setup, choose today's platforms and requested application counts. Supported choices are LinkedIn, Indeed, Naukri, Wellfound, Instahyre, Workday, company career pages, and web discovery.
8. Today's plan and every outcome are stored in exactly one file: \`applied/YYYY-MM-DD/applications.md\`.
9. The agent applies one job at a time, uses the platform strategy files, respects the hard daily limits, pauses for the first-submit \`ok\` approval, and records confirmation only after the site shows it.
10. A later session on the same local date resumes the same daily file instead of creating another tracker.
11. When a real model handoff is needed, all progress is already saved in the local files.

The legacy \`tracking/applied_jobs.csv\`, when present, is read-only history. The separate \`tracking/created_accounts.csv\` remains the account record for reusable company-portal accounts. New applications are never written back to the CSV tracker.

## 📁 Key files

- \`AGENTS.md\` — authoritative workflow and safety rules.
- \`CLAUDE.md\` — imports \`AGENTS.md\`.
- \`personal_data/profile_template.md\` — authoritative profile/job-preference template.
- \`personal_data/form_answers_template.md\` — reusable and contextual screening-answer template.
- \`personal_data/credentials_template.md\` — company-portal credential template.
- \`instructions/platforms/\` — platform strategies, including Instahyre.
- \`instructions/advanced_strategies/\` — company-direct and discovery flows.
- \`setup_checklist.md\` — local ignored setup progress created at runtime.
- \`applied/YYYY-MM-DD/applications.md\` — one local-date application record created at runtime.
- \`tracking/created_accounts.csv\` — local company account record.
- \`tracking/applied_jobs.csv\` — legacy read-only history, if present.

## 🧭 Daily limits

- LinkedIn: 20
- Indeed: 20
- Naukri: 25
- Wellfound: 10
- Instahyre: 10
- Workday: 5
- company_direct + discovery combined: 10
- all platforms combined: 50

User-requested counts and lower user limits are respected. Counts reset by local date, while duplicate history remains available across earlier daily files and any legacy CSV.

## 🤖 Model guidance

Model names and versions are intentionally not hard-coded.

- **Strongest/current-vendor tier:** setup.
- **Light/current-vendor tier:** LinkedIn, Indeed, Naukri, Wellfound, Instahyre quick applications.
- **Medium/current-vendor tier:** Workday, company direct, and discovery.

The agent recommends a tier from the same vendor and asks the user to select it when a change is needed. It should not pretend to switch models itself or force a new chat unless a real handoff is necessary.

## 🔒 Practical safeguards

The workflow keeps fit checks, scoped duplicate checks, no-guessing rules, prefilled-data verification, first-submit approval, additional host-app approvals, two-minute same-platform pacing, CAPTCHA/security stop rules, unsupported-upload handling, account-record reuse, and confirmation-before-success.

No live application testing is claimed by this repository update.
