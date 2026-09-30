# AI-Native Job Application Framework

This repository contains zero executable code. It is a small set of Markdown instructions, local personal-data files, setup state, account records, and daily application records for an AI agent with browser automation.

## ⚠️ Before you start — read this

**STOP. Read this before the run starts.**
This run can take up to the configured session time limit (default 4 hours).
If your computer sleeps, the browser disconnects and the run fails.
Applications already recorded in today's file are safe. Unfinished ones are lost.
Before replying `ready`, make sure ALL of these are true:
1. The laptop or PC is plugged into power. Do not run on battery.
2. Sleep is turned OFF for this run:
   - macOS: System Settings → Lock Screen → "Turn display off when inactive" → Never.
     Also System Settings → Battery → Options (or Displays → Advanced) →
     "Prevent automatic sleeping on power adapter when the display is off" → On.
   - Windows 11: Settings → System → Power & battery → Screen and sleep →
     "When plugged in, put my device to sleep after" → Never, and
     "When plugged in, turn off my screen after" → Never.
3. The laptop lid stays open for the whole run.
5. Chrome (or the browser your AI app controls) is already open with ONE window.
6. Do not use this computer for other work while the run is active.
If the machine sleeps, the browser disconnects and the run fails. Recorded applications are safe; the unfinished one is lost.

## 🚀 Workflow

1. Download the repository folder.
2. Open the folder in Codex, Claude Code, Antigravity, or another supported AI app with browser access.
3. Type `start`.
5. The agent shows the power/sleep checklist and waits for `ready`.
5. The agent creates missing personal-data files from the committed templates and guides setup one topic at a time.
6. Setup is resumable: answers are saved immediately, skipped optional values are stored as `None`, and a local `setup_checklist.md` is only a progress aid.
7. The agent verifies the real files before allowing applications.
8. After setup, choose today's platforms and requested application counts. Supported choices are LinkedIn, Indeed, Naukri, Wellfound, Instahyre, Workday, company career pages, web discovery, The Reliable Jobs, TEKsystems, Teksands, D4hire, Supersourcing, and We Work Remotely.
9. Today's plan and every outcome are stored in exactly one file: `applied/YYYY-MM-DD/applications.md`.
10. The agent applies one job at a time, uses the platform strategy files, respects the hard daily limits, pauses for the first-submit `ok` approval, and records confirmation only after the site shows it.
11. A later session on the same local date resumes the same daily file instead of creating another tracker.
12. When a real model handoff is needed, all progress is already saved in the local files.

The legacy `tracking/applied_jobs.csv`, when present, is read-only history. The separate `tracking/created_accounts.csv` remains the account record for reusable company-portal accounts. New applications are never written back to the CSV tracker.

## 📁 Key files

- `AGENTS.md` — authoritative workflow and safety rules.
- `CLAUDE.md` — imports `AGENTS.md`.
- `personal_data/profile_template.md` — authoritative profile/job-preference template.
- `personal_data/form_answers_template.md` — reusable and contextual screening-answer template.
- `personal_data/credentials_template.md` — company-portal credential template.
- `instructions/platforms/` — platform strategies, including Instahyre.
- `instructions/advanced_strategies/` — company-direct and discovery flows.
- `setup_checklist.md` — local ignored setup progress created at runtime.
- `applied/YYYY-MM-DD/applications.md` — one local-date application record created at runtime.
- `tracking/created_accounts.csv` — local company account record.
- `tracking/applied_jobs.csv` — legacy read-only history, if present.

## 🧭 Daily limits

- LinkedIn: 20
- Indeed: 20
- Naukri: 25
- Wellfound: 10
- Instahyre: 10
- Workday: 5
- company_direct + discovery combined: 10

The Reliable Jobs, TEKsystems, Teksands, D4hire, Supersourcing, and We Work Remotely are source selectors only; they do not create additional daily-limit buckets. Their applications are counted under the existing actual-destination limits.
- all platforms combined: 50

User-requested counts and lower user limits are respected. Counts reset by local date, while duplicate history remains available across earlier daily files and any legacy CSV.

## 🤖 Model guidance

Model names and versions are intentionally not hard-coded.

- **Strongest/current-vendor tier:** setup.
- **Light/current-vendor tier:** LinkedIn, Indeed, Naukri, Wellfound, Instahyre quick applications.
- **Medium/current-vendor tier:** Workday, company direct, and discovery.

The agent recommends a tier from the same vendor and asks the user to select it when a change is needed. It should not pretend to switch models itself or force a new chat unless a real handoff is necessary.

## 🔎 Selectable job sources

- The Reliable Jobs — `https://thereliablejobs.com/`
- TEKsystems — `https://www.teksystems.com/en/careers`
- Teksands — `https://teksands.ai/`
- D4hire — `https://d4hire.in/`
- Supersourcing — `https://supersourcing.com/`
- We Work Remotely — `https://weworkremotely.com/`

Source selection records where the job was found; the daily record also stores the actual application destination. The existing discovery, company-direct, and Workday flows are reused according to that destination. Unsupported or email-only routes are reported rather than invented, and source-site auto-apply services/recruiter emails are not enabled.

## 🧭 Session length and browser

- Default session limit is 4 hours, set in `personal_data/profile.md`.
- Use one browser window, one anchor tab per platform, and a tab cap of selected platforms + 2.
- `company_direct`, `discovery`, and Workday may trigger a browser-permission prompt per company.

## 🔒 Practical safeguards

The workflow keeps fit checks, scoped duplicate checks, no-guessing rules, prefilled-data verification, first-submit approval, additional host-app approvals, 120-second same-platform/workflow cooldowns with platform rotation, CAPTCHA/security stop rules, unsupported-upload handling, account-record reuse, and confirmation-before-success. Freshness follows the visible-controls rule in `AGENTS.md`.

No live application testing is claimed by this repository update.
