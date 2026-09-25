# Wellfound Application Strategy

## Objective
Apply to relevant startup roles on Wellfound using its pitching flow.

## Search Strategy
1. Navigate to the Wellfound jobs section.
2. Apply the role, location, and work-mode preferences from `personal_data/profile.md`.
3. Sort by Newest.
4. Run the fit check from `AGENTS.md` before applying.

## Execution Flow
1. Select a job match and read the complete job post.
2. Run the scoped duplicate, daily-limit, site-stop, and pacing checks.
3. Wellfound may request a short Note/Pitch. Build it only from `profile.md` and the actual job post.
4. Compare any prefilled facts with saved data before submission.
5. For any unanswered required question, stop this job and log `needs_user`.
6. If the resume upload is unsupported, ask the user to upload `personal_data/resume.pdf` in the current tab, wait for `done`, and verify the attachment.
7. Before the first submit of the session, show the filled pitch and other submitted answers and wait for `ok`.
8. Submit and verify the site confirmation before recording `Status: applied`.
9. Append the outcome immediately to today's `applied/YYYY-MM-DD/applications.md`.
10. Wait at least 2 minutes before another Wellfound submit.

## Pitch rules
- Use the target job title from the actual posting.
- Use the saved current title, experience, and core tech stack only.
- Tailor the pitch to the company and role using only job-post facts.
- Do not invent facts, guarantees, or placeholders.
- Keep the pitch to 2-3 sentences.

## Exclusions
- Do not write long, generic cover letters.
