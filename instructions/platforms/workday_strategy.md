# Workday Application Strategy

## Objective
Successfully navigate and complete the often tedious Workday ATS multi-step application processes.

## Understanding Workday
Workday requires a unique account to be created for *every single company* you apply to. This requires managing credentials and pushing through multi-page forms.

## Execution Flow
1. **Account Creation:**
   - When redirected to a Workday portal, click "Apply" and then "Create Account".
   - Use the standard email from `/personal_data/profile.md`.
   - Pull the standard password from `/personal_data/credentials.md`.
   - Accept terms and create the account.
   - **IMMEDIATELY log these details to `/tracking/created_accounts.csv`.**

2. **Form Navigation (The Multi-Step Process):**
   - **Upload Resume:** Upload `/personal_data/resume.pdf` to allow Workday to parse it.
   - **My Information:** Review parsed data. Fix any glaring errors using `/personal_data/profile.md`.
   - **My Experience:** Ensure at least the most recent job and education are present.
   - **Application Questions:** This is the most crucial part. Map questions regarding sponsorship, veteran status, disability, and gender to `/personal_data/form_answers.md`.
   - **Voluntary Disclosures:** Complete using the standard template answers.

3. **Submission:**
   - Review and submit the application.
   - Log the successful application to `/tracking/applied_jobs.csv`.

## Exclusions / Rules
- Do not get stuck in a loop correcting minor parsing errors on old experiences. Ensure the required fields are filled and proceed.
- If a Workday portal requires email verification *before* allowing the application to proceed, skip it (unless you have access to the user's inbox).
