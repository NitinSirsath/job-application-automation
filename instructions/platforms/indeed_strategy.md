# Indeed Application Strategy

## Objective
Apply to relevant roles on Indeed using its current quick-apply flow.

## Search Strategy
1. Go to Indeed.
2. Search for target job titles from `personal_data/profile.md`.
3. Prefer postings from the last 24 hours.
4. Prefer jobs marked Easily apply when that is the current UI label.

## Execution Flow
1. Read today's daily file and applicable history for scoped duplicates.
2. Read the complete job posting and run the fit check in `AGENTS.md`.
3. If Indeed is signed out or the application simply asks for login, ask the user to sign in in the current tab and reply `done`; verify sign-in and continue the current flow. Do not stop the platform.
4. Start the current Indeed application flow.
5. Use prefilled data only after comparing factual values with `profile.md`.
6. For employer questions, use matching answers from `form_answers.md`; do not guess.
7. Before the session's first submit-capable action, show the exact filled answers and wait for `ok`.
8. Submit.
9. Confirm success from the site.
10. Append the application outcome immediately to today's daily Markdown file.
11. Wait at least 2 minutes before another Indeed submit.

## Exclusions
- Skip an application that requires a mandatory custom skills test or assessment before submission unless the user has an explicit saved answer/workflow for it.
- Stop Indeed for the day only on a daily-limit, CAPTCHA, unusual-activity warning, security restriction, or equivalent access restriction, and record the dated site stop.
