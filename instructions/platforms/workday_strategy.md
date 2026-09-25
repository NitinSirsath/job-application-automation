# Workday Application Strategy

## Objective
Successfully navigate and complete the Workday ATS multi-step application processes.

## Understanding Workday
Workday may require a unique account for every company you apply to. Check the existing account record before creating anything new.

## Search Strategy
1. Web search `site:myworkdayjobs.com "<target job title from profile.md>" "<location from profile.md>"` and open matching posts.

## Execution Flow
1. Read the job post and run the fit, duplicate and daily-limit checks from `AGENTS.md`. If any fails, skip and log before creating or signing in to an account.
2. **Check for an existing account:**
   - Open `tracking/created_accounts.csv` first.
   - If an account for the company already exists, use **Sign In** and use the stored login email/password from the tracking record and `personal_data/credentials.md` as applicable.
   - If no account exists, continue with account creation.
3. **Account Creation:**
   - When redirected to a Workday portal, click "Apply" and then "Create Account".
   - Use the standard email from `personal_data/profile.md`.
   - Pull the standard password from `personal_data/credentials.md`.
   - Accept terms and create the account.
   - **IMMEDIATELY log these details to `tracking/created_accounts.csv`.**
4. **Form Navigation (The Multi-Step Process):**
   - **Upload Resume:** Upload `personal_data/resume.pdf` to allow Workday to parse it.
   - **My Information:** Review parsed data. Fix any glaring errors using `personal_data/profile.md`.
   - **My Experience:** Ensure the required job and education information is present using the saved personal data.
   - **Application Questions:** Answer from `personal_data/form_answers.md`; otherwise skip and log the job as required by `AGENTS.md`.
   - **Voluntary Disclosures:** Answer from `personal_data/form_answers.md`.
5. **Submission:**
   - Run the answer check from `AGENTS.md`.
   - Before the first submit of the session, show the filled answers and wait for `ok`.
   - Review and submit the application.
   - Log the successful application to `tracking/applied_jobs.csv`.
   - Wait at least 2 minutes before another Workday submit.
6. **Email or account verification fallback:**
   - If Workday requires email verification before the app can proceed and the agent cannot open the user's inbox, pause and say:
     "Please sign in / create the account / click the email verification link in this tab, then reply done"
   - Continue after the user replies `done`.

## Exclusions / Rules
- Do not get stuck in a loop correcting minor parsing errors on old experiences. Ensure the required fields are filled and proceed.
