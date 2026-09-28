# LinkedIn Application Strategy

## Objective
Apply to roles matching the target job titles in `personal_data/profile.md`.

## Search Strategy
1. Navigate to LinkedIn Jobs.
2. Enter the target job titles from `personal_data/profile.md`.
3. Apply the shared freshness rule in `AGENTS.md`: select visible Newest / Most recent and Past 24 hours controls when available, verify them, and do not widen to Past week or older ranges automatically.
4. Filter by Easy Apply.

## Execution Flow
1. Read today's `applied/YYYY-MM-DD/applications.md` and legacy history when available. If the scoped job is already `applied` or `skipped`, skip it.
2. Read the job posting and run the fit check in `AGENTS.md`.
3. Click a matching job posting.
4. Click **Easy Apply**.
5. Auto-fill required fields from the authoritative saved data.
6. Compare prefilled factual values with `profile.md` and correct material discrepancies.
7. For questions, answer from `form_answers.md`; for contextual questions, reuse only matching context.
8. If the first submit-capable action of the session has not yet been approved, show the exact job and filled answers/pitch and wait for `ok`.
9. Untick **Follow company** before submitting.
10. Submit the application.
11. Wait for confirmation shown by LinkedIn.
12. Append one record immediately to today's daily Markdown file.
13. Follow the shared cooldown/rotation rule in `AGENTS.md`; do not add a separate fixed wait here.

## Exclusions
- Do not apply when required experience exceeds the user's profile.
- Skip complex external third-party flows unless they are intentionally handled by another selected strategy.
- Stop LinkedIn for the day on a LinkedIn daily-limit, unusual-activity, CAPTCHA, security, or restriction message and record the dated site stop.
