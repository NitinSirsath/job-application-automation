# Wellfound (AngelList) Application Strategy

## Objective
Apply to relevant startup roles on Wellfound using the current application and pitching UI.

## Search Strategy
1. Navigate to Wellfound jobs.
2. Apply role and location filters from `personal_data/profile.md`.
3. Sort by newest when the current UI supports it.
4. Run the fit check before applying.

## Execution Flow
1. Read today's daily file and history for scoped duplicates.
2. Read the complete job post.
3. If Wellfound is signed out or the application simply asks for login, ask the user to sign in in the current tab and reply `done`; verify sign-in and continue the current flow. Do not stop the platform.
4. Prepare the short Note/Pitch from facts in `profile.md` plus role/company details shown on the current job post.
5. Compare any prefilled facts with the authoritative profile.
6. Use contextual answers only when their context matches.
7. Before the session's first submit-capable action, show the pitch and filled answers and wait for `ok`.
8. Submit.
9. Confirm success from Wellfound.
10. Append the application outcome immediately to today's daily Markdown file.
11. Wait at least 2 minutes before another Wellfound submit.

## Exclusions
- Do not write a long generic cover letter.
- Do not invent startup-specific facts.
- Stop Wellfound for the day only on a daily-limit, CAPTCHA, unusual-activity warning, security restriction, or equivalent access restriction, and record the dated site stop.
