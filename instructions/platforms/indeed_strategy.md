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
3. Start the current Indeed application flow.
4. Use prefilled data only after comparing factual values with `profile.md`.
5. For employer questions, use matching answers from `form_answers.md`; do not guess.
6. Before the session's first submit-capable action, show the exact filled answers and wait for `ok`.
7. Submit.
8. Confirm success from the site.
9. Append the application outcome immediately to today's daily Markdown file.
10. Wait at least 2 minutes before another Indeed submit.

## Exclusions
- Skip an application that requires a mandatory custom skills test or assessment before submission unless the user has an explicit saved answer/workflow for it.
- Stop Indeed for the day on a site restriction, CAPTCHA, unusual-activity, authentication, or daily-limit message and record the dated site stop.
