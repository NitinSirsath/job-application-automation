# General Rules for AI Job Application Agent

**CRITICAL SYSTEM INSTRUCTIONS. YOU MUST FOLLOW THESE RULES AT ALL TIMES.**

## 1. CAPTCHAs & 2FA
- **NEVER attempt to solve complex CAPTCHAs or 2FA (Two-Factor Authentication).**
- If you encounter a blocking CAPTCHA or a 2FA prompt, skip the application immediately. 
- Log the failure in your session notes and move on to the next job. Do not waste time trying to bypass them.

## 2. Duplicate Prevention
- **Always check `/tracking/applied_jobs.csv` before applying to a job.**
- Search the CSV for the Company name and Role. If a match exists, SKIP the application to avoid spamming the employer.

## 3. Tracking & Logging
- **Always log successful applications.**
- Immediately after successfully submitting an application, append a new row to `/tracking/applied_jobs.csv`.
- **Always log newly created accounts.**
- If you are forced to create an account on a company portal (e.g., Workday, direct career sites), log the details in `/tracking/created_accounts.csv` containing the Portal URL, Email Used, and Password.

## 4. Data Usage & Hallucination
- **Only reference data from the `/personal_data/` folder.**
- Do NOT hallucinate skills, experiences, or answers that are not present in `/personal_data/profile.md`, `/personal_data/form_answers.md`, or the user's resume.
- If a required question on a form cannot be confidently answered using the provided personal data, skip the application or provide a safe default from the form answers template if applicable.

## 5. Execution Speed
- Prioritize speed and volume over exhaustive troubleshooting. If an application form is broken, looping, or excessively complex (e.g., requires custom cover letters not present in data, or portfolio assessments), skip it and move on.
