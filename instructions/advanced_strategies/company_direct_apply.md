# Company Direct Apply Strategy

## Objective
Apply directly on company career pages, specifically targeting common, streamlined ATS platforms like Greenhouse, Lever, and Ashby.

## Execution Flow
1. Navigate to the provided company career page URL.
2. Locate the "Apply" or "View Roles" button.
3. Identify the ATS type (look at the URL, e.g., `boards.greenhouse.io`, `jobs.lever.co`).
4. **For Greenhouse / Lever / Ashby:**
   - These are usually single-page forms.
   - Attach `/personal_data/resume.pdf`.
   - Fill in Basic Info (Name, Email, Phone, Location).
   - Fill in Links (LinkedIn, GitHub, Portfolio) from `/personal_data/profile.md`.
   - Answer standard EEO questions (Sponsorship, Gender, Veteran, Disability) using `/personal_data/form_answers.md`.
   - Submit.
5. **For Custom / Proprietary ATS:**
   - If forced to create an account, do so using credentials from `/personal_data/credentials.md` and log to `/tracking/created_accounts.csv`.
   - Do your best to map form questions to the provided personal data.
6. Log successful applications to `/tracking/applied_jobs.csv`.

## Exclusions
- If a custom ATS requires answering essay-style behavioral questions not covered in the user's data, skip it.
