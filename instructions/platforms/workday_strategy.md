# Workday Application Strategy

## Objective
Successfully navigate and complete the Workday ATS multi-step application processes.

## Understanding Workday
Workday may require a unique account for every company you apply to. Check the existing account record before creating anything new.

## Execution Flow
1. **Check for an existing account:**
   - Open \`tracking/created_accounts.csv\` first.
   - If an account for the company already exists, use **Sign In** and use the stored login email/password from the tracking record and \`personal_data/credentials.md\` as applicable.
   - If no account exists, continue with account creation.
2. **Account Creation:**
   - When redirected to a Workday portal, click "Apply" and then "Create Account".
   - Use the standard email from \`personal_data/profile.md\`.
   - Pull the standard password from \`personal_data/credentials.md\`.
   - Accept terms and create the account.
   - **IMMEDIATELY log these details to \`tracking/created_accounts.csv\`.**
3. **Form Navigation (The Multi-Step Process):**
   - **Upload Resume:** Upload \`personal_data/resume.pdf\` to allow Workday to parse it.
   - **My Information:** Review parsed data. Fix any glaring errors using \`personal_data/profile.md\`.
   - **My Experience:** Ensure the required job and education information is present using the saved personal data.
   - **Application Questions:** Answer from \`personal_data/form_answers.md\`; otherwise skip and log the job as required by \`AGENTS.md\`.
   - **Voluntary Disclosures:** Answer from \`personal_data/form_answers.md\`.
4. **Submission:**
   - Run the fit, duplicate, daily-limit, and answer checks from \`AGENTS.md\`.
   - Before the first submit of the session, show the filled answers and wait for \`ok\`.
   - Review and submit the application.
   - Log the successful application to \`tracking/applied_jobs.csv\`.
   - Wait at least 2 minutes before another Workday submit.
5. **Email or account verification fallback:**
   - If Workday requires email verification before the app can proceed and the agent's app blocks it, pause and say:
     "Please sign in / create the account / click the email verification link in this tab, then reply done"
   - Continue after the user replies \`done\`.

## Exclusions / Rules
- Do not get stuck in a loop correcting minor parsing errors on old experiences. Ensure the required fields are filled and proceed.
