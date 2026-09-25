# LinkedIn Application Strategy

## Objective
Apply to roles matching the target job titles in `personal_data/profile.md`.

## Search Strategy
1. Navigate to LinkedIn Jobs.
2. Enter the target job titles defined in `personal_data/profile.md`.
3. Filter by **Date Posted**: "Past 24 hours" (preferred) or "Past week".
4. Filter by **Easy Apply**.

## Execution Flow
1. Check whether the job is already logged as **Applied** in `tracking/applied_jobs.csv`. If it is, skip it.
2. Read the job posting and run the fit check in `AGENTS.md`.
3. Click on a matching job posting.
4. Click the **Easy Apply** button.
5. Auto-fill the required fields using data from `personal_data/`.
6. For questions, answer from `personal_data/form_answers.md`; otherwise skip and log.
7. Before the first submit of the session, show the filled answers and wait for `ok`.
8. Untick **Follow <company>** before submitting.
9. Submit the application.
10. Log the application to `tracking/applied_jobs.csv`.
11. Wait at least 2 minutes before another submit on LinkedIn.
12. Move to the next job in the list.

## Exclusions
- Do not apply to roles that strictly require years of experience exceeding the user's profile.
- Skip applications that redirect to complex third-party external sites unless specified otherwise.
