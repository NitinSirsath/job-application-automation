# LinkedIn Application Strategy

## Objective
Apply to roles matching the target job titles in `personal_data/profile.md`.

## Search Strategy
1. Navigate to LinkedIn Jobs.
2. Enter the target job titles defined in `personal_data/profile.md`.
3. Filter by **Date Posted**: "Past 24 hours" (preferred) or "Past week".
4. Filter by **Easy Apply**.

## Execution Flow
1. Read the job posting and run the fit check, scoped duplicate check, daily-limit check, today's site-stop check, and pacing check in `AGENTS.md`.
2. Click a matching job posting and then **Easy Apply**.
3. Auto-fill the required fields using the authoritative saved data.
4. Compare every prefilled/parsed factual value with the saved profile before submission; correct mismatches.
5. If a required question is not covered by a matching saved answer, stop this job and log it as `needs_user`. Do not guess.
6. If the resume upload is unsupported, ask the user to upload `personal_data/resume.pdf` in the current tab, wait for `done`, and verify the attachment.
7. Before the first submit of the session, show the filled answers and resume state and wait for `ok`.
8. Untick the "Follow [company]" checkbox before submitting.
9. Submit the application.
10. Verify that LinkedIn shows an application confirmation before recording `Status: applied`.
11. Append the outcome immediately to today's `applied/YYYY-MM-DD/applications.md`.
12. Wait at least 2 minutes before another LinkedIn submit.

## Exclusions
- Do not apply to roles that strictly require years of experience exceeding the user's profile.
- Skip applications that redirect to complex third-party external sites unless another supported workflow applies.
