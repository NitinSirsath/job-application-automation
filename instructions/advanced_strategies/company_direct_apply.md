# Company Direct Apply Strategy

## Objective
Apply directly on company career pages, specifically targeting common, streamlined ATS platforms like Greenhouse, Lever, and Ashby.

## Execution Flow
1. Open each URL under Company Career Page URLs in `personal_data/profile.md`. If there are none, skip company_direct.
2. Locate the "Apply" or "View Roles" button.
3. Identify the ATS type (look at the URL, e.g., `boards.greenhouse.io`, `jobs.lever.co`).
4. Run the fit and duplicate checks in `AGENTS.md`.
5. **For Greenhouse / Lever / Ashby:**
   - These are usually single-page forms.
   - Attach `personal_data/resume.pdf`.
   - Fill in Basic Info (Name, Email, Phone, Location).
   - Fill in Links (LinkedIn, GitHub, Portfolio) from `personal_data/profile.md`.
   - Answer standard EEO questions from `personal_data/form_answers.md`; otherwise skip and log.
   - For any other question, answer from `form_answers.md`; otherwise skip and log.
   - Before the first submit of the session, show the filled answers and wait for `ok`.
   - Submit.
6. **For Custom / Proprietary ATS:**
   - If forced to create an account, do so using credentials from `personal_data/credentials.md` and log to `tracking/created_accounts.csv`.
   - Answer from `form_answers.md`; otherwise skip and log.
7. Log successful applications to `tracking/applied_jobs.csv`.
8. Wait at least 2 minutes before another submit in the company-direct/discovery workflow.

## Exclusions
- If a custom ATS requires answering essay-style behavioral questions not covered in the user's data, skip it.
