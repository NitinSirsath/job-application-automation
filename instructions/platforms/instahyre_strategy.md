# Instahyre Application Strategy

## Objective
Apply to relevant roles on Instahyre while preserving the framework's common checks and confirmation rules.

## Search Strategy
1. Navigate to Instahyre and inspect the actual current search/filter controls at runtime.
2. Use target job titles, locations, work modes, and experience from `personal_data/profile.md`.
3. Prefer recent, relevant matches.

## Execution Flow
1. Open one job and read the complete posting.
2. Run the fit, scoped duplicate, daily-limit, site-stop, and pacing checks in `AGENTS.md`.
3. Inspect the actual form and use only fields/controls that are present. Do not assume a saved UI flow.
4. Compare prefilled facts with saved profile data before submission.
5. Answer custom questions only from matching saved data; otherwise log `needs_user` and stop the job.
6. If resume upload is unsupported, ask the user to upload `personal_data/resume.pdf` in the current tab, wait for `done`, then verify the attachment.
7. Before the first submit of the session, show the fields/answers that will be submitted and wait for `ok`.
8. Submit only after approval and verify the resulting site confirmation/status.
9. Append the outcome immediately to today's `applied/YYYY-MM-DD/applications.md`.
10. Wait at least 2 minutes before another Instahyre submit.

## Daily limit
Instahyre has a hard maximum of 10 applications per local day. Never exceed it.

## Exclusions
- Do not claim or rely on guaranteed UI behavior that has not been observed on the live page.
