All paths in this project are relative to this folder, not the computer's root.

# AI-Native Job Application Framework

This repository is a markdown-only job application framework. The AI agent uses the files in this folder as its instructions and personal-data source while applying through the browser tool.

## 1. Modes

### SETUP mode

Run SETUP mode when any of these is missing or still contains bracketed placeholder text (ignore the `## Learned Answers` section):
- `personal_data/resume.pdf`
- `personal_data/profile.md`
- `personal_data/form_answers.md`

Work with the user one topic at a time, in this order:
1. Resume
2. Basic information
3. Job search preferences
4. Where to apply
5. Common screening answers
6. Application password

Save each answer to its file immediately before moving to the next topic:
- Resume: make sure `personal_data/resume.pdf` exists.
- Basic information: update `personal_data/profile.md`.
- Job search preferences: update `personal_data/profile.md`.
- Where to apply: update the **Where to apply** field in `personal_data/profile.md`.
- Common screening answers: update `personal_data/form_answers.md`.
- Application password: update `personal_data/credentials.md`.

Basic information covers Basic Information, Links, Professional Details and Pitch / Summary in profile.md. Common screening answers covers every section of form_answers.md except Learned Answers. If the user skips or has no value for a field, write None. Setup is complete only when no [brackets] remain in profile.md and form_answers.md.

Ask the user to sign in to each selected job site in the browser the agent uses.

Create these tracking files if they are missing, using the exact headers and rules in the **Tracking files** section below.

When setup is complete, give the model suggestion described in **Model suggestions** and then say exactly:

"Setup done. Open a new chat on the suggested model and type start."

Do not begin job applications during SETUP mode.

### START mode

START mode runs only when the user types `start` and setup is complete (ignore the `## Learned Answers` section).

For each site listed under **Where to apply** in `personal_data/profile.md`, use that site's strategy file:
- LinkedIn → `instructions/platforms/linkedin_strategy.md`
- Indeed → `instructions/platforms/indeed_strategy.md`
- Naukri → `instructions/platforms/naukri_strategy.md`
- Wellfound → `instructions/platforms/wellfound_strategy.md`
- Workday → `instructions/platforms/workday_strategy.md`
- company_direct → `instructions/advanced_strategies/company_direct_apply.md`
- discovery → `instructions/advanced_strategies/web_search_discovery.md`

Before browsing for applications, read:
- `personal_data/profile.md`
- `personal_data/form_answers.md`
- `personal_data/credentials.md`
- `tracking/applied_jobs.csv`
- `tracking/created_accounts.csv`

Apply only when the fit check passes, no duplicate exists, and the relevant daily limits allow the application.

Before the first submit of each START session, show the user the filled answers that will be submitted and wait for the user to reply `ok`. After that approval, continue on its own.

At the end of the session, report what was applied and what was skipped. For every skipped or `needs_user` job, include the reason or unanswered question. Ask the user any questions that could not be answered from the saved files. Save each answer the user gives under `## Learned Answers` in `personal_data/form_answers.md` right away.

## 2. Daily limits

Hard maximum applications per day:
- LinkedIn: 20
- Indeed: 20
- Naukri: 25
- Wellfound: 10
- Workday: 5
- company direct + discovery combined: 10
- all sites combined: 50

The user may set LOWER limits in `personal_data/profile.md`, never higher. If the profile asks for a higher limit, use the hard maximum and tell the user.

Before EVERY application:
1. Count today's rows with status `applied` in `tracking/applied_jobs.csv` for that platform.
2. Count today's rows with status `applied` across all platforms.
3. For company direct and discovery, enforce their combined total.
4. If the relevant limit is reached, stop that platform for today and tell the user.

Never skip these checks, even if the user asks.

Apply like a person:
- Work on one job at a time.
- Read the job post before applying.
- Never submit in rapid bursts.
- Leave at least 2 minutes between submits on the same site.

If a job site shows a daily-limit, unusual-activity, CAPTCHA, security check (such as 'verify you are human'), or restriction message, stop that site for today and tell the user.

A CAPTCHA on one employer's own form skips that job only; it does not stop the whole site.

Never attempt to bypass a CAPTCHA or 2FA challenge.

An email verification link for a new account is not a stop; use the fallback in section 5.

When you stop a site, log a `skipped` row with notes `site stopped: <message>`. At START, do not use a site that has such a row dated today.

## 3. Fit, duplicates, and answers

### Fit check

Apply only when:
- the job title matches the target job titles in `personal_data/profile.md`;
- the location matches the locations accepted in `personal_data/profile.md`;
- the work mode is one of the accepted work modes in `personal_data/profile.md`;
- the required years of experience are compatible with the user's experience in `personal_data/profile.md`;
- the company is not on the companies-to-skip list.

If the fit check fails, skip the job and log it as `skipped` with the reason.

### Duplicate check

Skip a job when:
- its `job_id` is already logged as `applied` or `skipped` (a `needs_user` job may be retried once its question has an answer); or
- the same company and job title are already marked `applied`.

### Never guess

Answer only from:
- `personal_data/profile.md`
- `personal_data/form_answers.md`
- the user's resume

If a required question is not covered:
1. Do not guess.
2. Skip the job.
3. Log it with status `needs_user`.
4. If it is not already there, add the question under `## Learned Answers` as `- **<question>:**` with nothing after the colon (no brackets).

Never submit text that still contains square-bracket placeholders or placeholder text such as `X years`.

## 4. Model suggestions

Do not hard-code specific model names or versions anywhere. Model names and versions change.

The AI works out which app and model it is running on and suggests models from that same vendor's CURRENT lineup, using its own knowledge or the app's model picker.

Tiers:
- Fast/light tier: LinkedIn, Indeed, Naukri, and Wellfound quick apply.
- Mid tier: Workday, company direct apply, and discovery mode.
- Default/strongest tier: SETUP.

At START:
- If the current model is heavier than the task needs, suggest a lighter model from the same vendor.
- If the current model is too light for Workday or direct apply, suggest the mid tier from the same vendor.

If the same form step fails on 3 jobs in a row, stop that workflow and suggest switching to the mid tier from the same vendor.

After setup, suggest starting a NEW chat on the suggested model instead of switching models mid-chat. All answers are saved in files, so nothing is lost.

## 5. Logins and account creation

The AI signs in and creates accounts itself using `personal_data/credentials.md` when its app allows it.

credentials.md is only for company portals (Workday, custom ATS). If LinkedIn, Indeed, Naukri or Wellfound is signed out, use the fallback message below.

Fallback only when the app blocks it, for example when the app will not type passwords or create accounts:

"Please sign in / create the account / click the email verification link in this tab, then reply done"

Pause until the user replies `done`, then continue.

For selected job sites, the user signs in during SETUP in the agent's browser.

## 6. Tracking files

SETUP creates `tracking/` and both files if they are missing.

### `tracking/applied_jobs.csv`

Header:

`"date","time","platform","company","job_title","job_id","job_url","status","notes"`

date is the local date as YYYY-MM-DD. time is local 24-hour HH:MM:SS. platform is exactly one of: linkedin, indeed, naukri, wellfound, workday, company_direct, discovery. Any Workday form counts as workday, however it was found.

Allowed status values:
- `applied`
- `skipped`
- `needs_user`

Every field must be enclosed in double quotes.

Write `"applied"` only after the site shows its confirmation.

The `notes` field contains the skip reason or unanswered question.

### `tracking/created_accounts.csv`

Header:

`"date","company","portal_url","login_email","password","email_verified"`

Log newly created company accounts immediately.

Before creating a Workday or other company account, check this file first. If an account for that company already exists, use **Sign In** instead of creating another account.

## 7. Submission behavior

Before the first submit of each session, show the filled answers and wait for `ok`.

After approval:
- submit one application at a time;
- write the tracking row only after confirmation;
- respect all daily limits and the 2-minute same-site gap;
- stop a site immediately when its restriction or daily-limit message appears.

If a form is broken or keeps failing after 2 tries, skip the job, log it as skipped with the reason, and move on.

Do not submit on jobs that fail the fit check, duplicate check, or answer requirements.

## 8. Strategy files

Follow the relevant platform or advanced-strategy file for search and form flow. The strategy files never override the rules in this file.

## 9. File references

The active instruction files are:
- `AGENTS.md`
- `CLAUDE.md`
- `instructions/platforms/linkedin_strategy.md`
- `instructions/platforms/indeed_strategy.md`
- `instructions/platforms/naukri_strategy.md`
- `instructions/platforms/wellfound_strategy.md`
- `instructions/platforms/workday_strategy.md`
- `instructions/advanced_strategies/company_direct_apply.md`
- `instructions/advanced_strategies/web_search_discovery.md`
- `personal_data/profile_template.md`
- `personal_data/form_answers_template.md`
- `personal_data/credentials_template.md`
