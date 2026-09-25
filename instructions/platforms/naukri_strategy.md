# Naukri Application Strategy

## Objective
Apply to relevant technical roles on Naukri.com.

## Search Strategy
1. Navigate to Naukri search.
2. Use skills and target titles from `personal_data/profile.md`.
3. Set experience filters from the saved profile.
4. Prefer recent postings.

## Execution Flow
1. Read today's daily file and history for scoped duplicates.
2. Read the full job post and run fit, duplicate, and daily-limit checks from `AGENTS.md`.
3. If Naukri is signed out or the application simply asks for login, ask the user to sign in in the current tab and reply `done`; verify sign-in and continue the current flow. Do not stop the platform.
4. Review the exact profile/details that Naukri will send.
5. **Before the first Apply click that could submit immediately, show the user the job and submitted details and wait for `ok`.**
6. Click **Apply**.
7. If additional questions appear, answer only from the authoritative saved data and matching contextual answers.
8. Compare any prefilled factual values before final submission.
9. Confirm success from Naukri.
10. Append the result immediately to today's daily Markdown file.
11. Wait at least 2 minutes before another Naukri submit.

## Exclusions
- Skip roles whose location or work mode does not match the authoritative values in `profile.md`.
- Stop Naukri for the day only on a daily-limit, CAPTCHA, unusual-activity warning, security restriction, or equivalent access restriction, and record the dated site stop.
