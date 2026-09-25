# Indeed Application Strategy

## Objective
Apply to relevant roles on Indeed using its Quick Apply system.

## Search Strategy
1. Go to Indeed.com.
2. Search for the target job titles from `personal_data/profile.md`.
3. Filter results by **Date Posted**: Last 24 hours.
4. Filter by **Easily apply**.

## Execution Flow
1. Open a result, read the job posting, and run the fit, scoped duplicate, daily-limit, site-stop, and pacing checks in `AGENTS.md`.
2. Click **Apply now** and use the Indeed easy-apply flow.
3. Compare prefilled/parsed factual information with the saved profile before submission; correct mismatches.
4. Answer custom employer questions only from matching saved answers. Otherwise log `needs_user` and do not guess.
5. If the resume upload is unsupported, ask the user to upload `personal_data/resume.pdf` in the current tab, wait for `done`, and verify the attachment.
6. Before the first submit of the session, show the filled answers and wait for `ok`.
7. Submit and verify the site result.
8. Append the outcome immediately to today's `applied/YYYY-MM-DD/applications.md`. Record `applied` only when the site confirms success.
9. Wait at least 2 minutes before another Indeed submit.

## Exclusions
- If an Indeed application requests a mandatory custom skills test or assessment before submission, skip it.
