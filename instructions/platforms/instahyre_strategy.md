# Instahyre Application Strategy

## Objective
Apply to relevant roles on Instahyre while keeping the workflow deliberately conservative.

## Search Strategy
1. Open Instahyre and inspect the actual current job/search UI at runtime.
2. Use target titles, locations, and work modes from `personal_data/profile.md`.
3. Do not assume a particular button name, form sequence, or quick-apply behavior unless the current page shows it.
4. Run fit, duplicate, and daily-limit checks before applying.

## Execution Flow
1. Instahyre has a hard maximum of 10 applications per local day, regardless of a larger user request.
2. Read today's daily file and available legacy history for scoped duplicates and today's count.
3. If Instahyre is signed out or the application simply asks for login, ask the user to sign in in the current tab and reply `done`; verify sign-in and continue the current flow. Do not stop the platform.
4. Read the complete current job post.
5. Compare any prefilled factual values with `profile.md`.
6. Answer questions only from the saved data and matching contextual answers.
7. Before the session's first submit-capable action, show the exact filled details and wait for `ok`.
8. Complete the actual current-page application flow.
9. Record `applied` only after the site shows confirmation. Otherwise record `skipped` or `needs_user` with the exact reason.
10. Append the outcome immediately to today's daily Markdown file.
11. Wait at least 2 minutes before another Instahyre submit.

## Exclusions
- Do not invent guaranteed Instahyre UI behavior.
- Stop Instahyre for the day only on a daily-limit, CAPTCHA, unusual-activity warning, security restriction, or equivalent access restriction, and record the dated site stop.
