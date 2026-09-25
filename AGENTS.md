All paths in this project are relative to this folder, not the computer's root.

# AI-Native Job Application Framework

This repository is a markdown-only job application framework. The AI agent uses the files in this folder as its instructions and personal-data source while applying through the browser tool.

## 1. Operating model

Use three modes:

- **SETUP** — create and complete the reusable personal files. Never apply for jobs in this mode.
- **PLAN** — after setup is complete, collect today's platforms and requested counts, create or resume today's application record, and verify any conditional prerequisites.
- **START** — runs when the user types `start` and setup plus today's plan are ready. Apply one job at a time and append the outcome immediately.

Never run SETUP, collect personal information, or submit applications merely because this repository is being edited. These instructions are the product itself.

## 2. State files and authority

### Personal data
- `personal_data/resume.pdf` — the user's current resume.
- `personal_data/profile.md` — the **authoritative source** for identity, contact details, employment, education, salary facts, notice period, job preferences, work modes, locations, relocation, and work authorization/sponsorship.
- `personal_data/form_answers.md` — reusable common screening answers plus contextual answers that are only reusable when their recorded context matches.
- `personal_data/credentials.md` — reusable company-portal credential information. Never copy passwords into application reports.

If two sources disagree about the same factual field, do not choose one silently. Mark the job `needs_user`, ask the user to resolve the conflict, and save the resolved answer immediately to the authoritative source.

### Runtime records
- `setup_checklist.md` — local, ignored setup progress. It is a convenience aid, not proof that setup is complete.
- `applied/YYYY-MM-DD/applications.md` — the single live application record for that local date.
- `tracking/created_accounts.csv` — the existing separate account record for reusable company-portal accounts. Keep it separate from application reports and never repeat passwords in daily records.
- `tracking/applied_jobs.csv` — legacy application history only. If present, treat it as read-only input. Never append new applications to it, delete it, or migrate it destructively.

The live application source of truth for NEW records is always the daily Markdown file.

## 3. SETUP mode — resumable, one topic at a time

Run SETUP when the required personal files are missing or still contain bracketed placeholder text. Do not treat the `Where to Apply` planning choice as a SETUP completeness requirement because PLAN collects the live daily plan afterward.

Before setup begins, recommend the strongest/current-vendor tier. Do not hard-code a model name or version and do not claim the agent can switch itself.

### Create missing files first
1. Create `personal_data/profile.md` from `personal_data/profile_template.md` if missing.
2. Create `personal_data/form_answers.md` from `personal_data/form_answers_template.md` if missing.
3. Create `personal_data/credentials.md` from `personal_data/credentials_template.md` if missing.
4. Create `setup_checklist.md` from the checklist below if missing.
5. Never replace a completed file with a fresh copy. Preserve existing answers and learned answers.

### Collect setup topics in this order
Ask one topic at a time and save the answer immediately before moving on:

1. **Resume** — ask for the resume file or a local path. Copy it to exactly `personal_data/resume.pdf`. Do not invent a resume path. If the environment cannot access the path, ask the user to provide/upload the file through the current app.
2. **Basic/contact information** — names, email, phone, location, and address when needed.
3. **Employment and education** — current role, total experience, employment history, education, core stack, notice period, and salary with amount, currency, and period.
4. **Work authorization** — country/countries, work authorization, and sponsorship now/future.
5. **Job preferences** — target titles, locations, work modes, relocation preference, skip companies, and company career URLs.
6. **Common screening answers** — populate reusable answers in `form_answers.md`.
7. **Credential readiness** — prepare the standard application credential only when needed for later company-portal use. Reusable account records remain in `tracking/created_accounts.csv`.

For every topic, inspect the existing files first. Never ask a question whose answer is already present.

### Optional answers
An optional answer may be stored as `None`. `None` means “unavailable / not provided”; it is never a value to submit into a required application field.

When the user skips a value:
- save `None` immediately;
- mark the corresponding optional checklist item as skipped;
- do not ask the same question again;
- never turn `None` into a guessed answer later.

### Setup checklist
Create `setup_checklist.md` with this exact checklist when it does not exist:

- [ ] Resume file copied to `personal_data/resume.pdf`
- [ ] Basic/contact information complete
- [ ] Employment history and current role complete
- [ ] Education complete
- [ ] Salary facts complete or explicitly `None` where optional
- [ ] Notice period complete
- [ ] Work authorization and sponsorship complete in `profile.md`
- [ ] Job titles, locations, work modes, relocation, and skip-company preferences complete
- [ ] `personal_data/form_answers.md` created and common screening answers reviewed
- [ ] Optional unanswered items explicitly stored as `None`
- [ ] Conditional credential readiness recorded when a selected plan later requires it

The checkboxes never prove readiness by themselves.

### Actual setup verification on every `start`
Before allowing PLAN or START, verify all of the following from the actual files:

- `personal_data/resume.pdf` exists and is non-empty.
- `personal_data/profile.md` exists and contains no unresolved `[bracketed placeholders]` in required fields.
- `personal_data/form_answers.md` exists and contains no unresolved bracketed placeholders in required fields, **except that empty `## Contextual Answers` and `## Learned Answers` sections are valid and expected until real contextual/learned questions arise**.
- Required factual values are present in their authoritative source, or an optional field is explicitly `None`.
- `setup_checklist.md` may contain stale checkboxes; the actual files above are authoritative.
- If a later application plan needs company-portal credentials, verify `personal_data/credentials.md` is ready before the first such application.
- If an existing `tracking/created_accounts.csv` exists, verify it can be read before creating a new company account.

If any required setup item is incomplete, resume SETUP at the first unfinished topic. Do not begin applications.

When SETUP is complete, do not force a new chat. Recommend the strongest/current-vendor tier for setup if appropriate. Continue in the current chat unless a real handoff is necessary.

## 4. PLAN mode — choose today's application plan

After setup is complete, ask which platforms to use and how many applications to attempt on each platform.

Supported choices:
- LinkedIn
- Indeed
- Naukri
- Wellfound
- Instahyre
- Workday
- company career pages (`company_direct`)
- web discovery (`discovery`)
- The Reliable Jobs
- TEKsystems
- Teksands
- D4hire
- Supersourcing
- We Work Remotely

The six job-source choices are source selectors, not new independent application-limit buckets. Route each selected source to the actual application destination at runtime and apply the existing destination limits. For quick-apply platforms, offer 10 or 15 as convenient starting counts when the limits permit. For `company_direct`, require company career URLs from `personal_data/profile.md` when applicable. `discovery` and the listed job sources do not require saved career URLs.

For each selected platform:
- ask for the requested application count;
- respect any lower user limit already stored in `profile.md`;
- never exceed the hard limits in this file;
- save today's platform plan and current progress in `applied/YYYY-MM-DD/applications.md`.

Use the user's local date, not UTC.

If today's file already exists, resume it instead of creating a second file or asking for the plan again unless the user wants to change the plan.

### Daily file layout

Use exactly one file:

```
applied/
  YYYY-MM-DD/
    applications.md
```

Inside that file, use platform sections. Do not create separate application files by platform or session.

Start the file with:

```md
# Applications — YYYY-MM-DD

## Application Plan

| Platform | Requested | Applied | Skipped | Needs User |
| --- | ---: | ---: | ---: | ---: |
| linkedin |  | 0 | 0 | 0 |
| indeed |  | 0 | 0 | 0 |
| naukri |  | 0 | 0 | 0 |
| wellfound |  | 0 | 0 | 0 |
| instahyre |  | 0 | 0 | 0 |
| workday |  | 0 | 0 | 0 |
| company_direct |  | 0 | 0 | 0 |
| discovery |  | 0 | 0 | 0 |
| the_reliable_jobs |  | 0 | 0 | 0 |
| teksystems |  | 0 | 0 | 0 |
| teksands |  | 0 | 0 | 0 |
| d4hire |  | 0 | 0 | 0 |
| supersourcing |  | 0 | 0 | 0 |
| we_work_remotely |  | 0 | 0 | 0 |

## Site Stops

- None

## linkedin

## indeed

## naukri

## wellfound

## instahyre

## workday

## company_direct

## discovery
```

Update the plan counts as outcomes are appended. Do not reset earlier entries.

For each job, append immediately after the outcome:

```md
### HH:MM:SS — Company — Job Title
- Local date/time:
- Platform:
- Company:
- Job title:
- Location:
- Work mode:
- Job URL:
- Job ID (company/portal scoped):
- Discovery source:
- Actual application destination:
- Resume filename:
- Submitted answers:
  - Question: Answer
- Status: applied | skipped | needs_user
- Confirmation shown:
- Skip reason / unanswered question / next action:
```

For `applied`, populate the actual confirmation shown by the site. Never invent a confirmation.

For `skipped` and `needs_user`, populate the reason or unanswered question/next action. If a site stop occurs, also add a dated entry under **Site Stops** such as `- 16:10 — linkedin — site stopped: CAPTCHA`.

The daily file is the single destination for all NEW application records.

## 5. Daily limits, counting, duplicates, retries, and midnight

Hard maximum applications per local day:
- LinkedIn: 20
- Indeed: 20
- Naukri: 25
- Wellfound: 10
- Workday: 5
- Instahyre: 10
- company direct + discovery combined: 10
- all platforms combined: 50

Requested session counts and lower user-defined limits must also be respected.

Before EVERY application:
1. Re-read today's daily Markdown file.
2. If `tracking/applied_jobs.csv` exists, re-read today's CSV rows from that legacy history.
3. Recount today's `applied` outcomes for the platform across both sources.
4. Recount today's all-platform `applied` outcomes across both sources.
5. Recount company_direct + discovery together across both sources.
6. Re-check the user's requested count for that platform.
7. Re-check the current local date/time. If the date crossed midnight, stop using the old day's limits and create/resume the new date's file.
8. Check today's Site Stops in Markdown and today's legacy CSV notes. A legacy row with status `skipped` and notes beginning exactly `site stopped:` stops that platform for the current local date. A stop from an earlier local date does not block today.

Do not count the same application twice. The preferred application key is:
`local date + platform + company + portal + job_id`.
If a reliable job ID is unavailable, use `local date + platform + company + job title + job URL`.

For duplicate/count decisions across Markdown and the legacy CSV:
- Match equivalent applications by the preferred key; when a key is unavailable, use the fallback key above and normalize obvious URL trailing-slash differences before comparing.
- An application present in both today's Markdown and today's legacy CSV counts once.
- Today's legacy `applied` rows count toward today's platform and global limits.
- Today's legacy `skipped` row with notes beginning `site stopped:` is a platform stop for today's local date.
- Yesterday's or any earlier legacy stop does not block today's work.
- `applied` or `skipped` means do not apply again for that job.
- `needs_user` is retryable after the unanswered question has been resolved.

Preserve existing CSV history as read-only input. Never delete it, append to it, or modify it in any other way. Write all NEW application records only to the current daily Markdown file.

## 6. Fit checks, duplicates, and factual answers

### Fit check
Apply only when:
- job title matches target titles;
- location matches accepted locations;
- work mode matches the authoritative `profile.md` value;
- required years of experience are compatible;
- company is not on the skip list.

If fit fails, log `skipped` immediately with the reason.

### Duplicate check
Skip when the same job is already `applied` or `skipped` in historical daily records or legacy history. A `needs_user` record may be retried after its blocker is answered.

### Never guess
Use factual information only from:
- `personal_data/profile.md`
- `personal_data/form_answers.md`
- the user's resume.

Before submission, compare any prefilled, parsed, or portal-supplied factual information against the saved authoritative data. If it differs materially, correct it from the authoritative source or mark `needs_user`; do not silently accept or overwrite user facts.

For contextual questions:
- save employer-, country-, role-, or portal-specific answers with explicit context;
- reuse a contextual answer only when the context recorded for it matches the current application;
- do not turn one employer's or country's answer into a global answer automatically;
- if the question is required and no matching answer exists, do not guess. Log `needs_user`.

Store new unanswered questions under `## Learned Answers` in `form_answers.md` immediately after the user answers them. Include the relevant context and the exact question. Add a **Contextual Answer** record only when a real contextual question arises; do not pre-populate placeholder contextual records.

Never submit square-bracket placeholders, sample values, or guessed years.

## 7. Submission safeguards

- Apply one job at a time.
- Read the job post before applying.
- Perform fit and scoped duplicate checks before opening account-creation flows.
- Before the first action in the session that can submit an application, show the user the exact job plus the filled answers/pitch that will be submitted and wait for the user to reply exactly `ok`.
- This approval gate applies before Naukri's potentially instant **Apply** click.
- Continue honoring any additional approval required by the host application.
- After the first approval, still review each application's final values before submission.
- Submit one application at a time.
- Leave at least two minutes between submits on the same platform/workflow.
- Record `applied` only after the site shows confirmation.
- If a site asks the user to upload a file manually because automated upload is unsupported, ask the user to upload `personal_data/resume.pdf` in the current tab, wait for `done`, then verify the upload before continuing.
- If a form is broken or keeps failing after two tries, log it as `skipped` with the reason and continue.
- Never bypass CAPTCHA, anti-bot, 2FA, or security checks.

### Site-stop and retry rules
If a site shows a daily-limit, unusual-activity, CAPTCHA, security check, or restriction message:
- stop that site for the day;
- log the dated stop under **Site Stops** and add a `skipped` record with notes `site stopped: <message>`;
- do not retry that site later the same day.

A normal signed-out or login-required prompt is **not** a site stop. When the site merely requires ordinary login:
- ask the user to sign in in the current tab and reply `done`;
- after `done`, verify that the site is signed in;
- continue the current application workflow.

Authentication language means a stop only when it is accompanied by an actual security restriction, CAPTCHA, unusual-activity warning, daily-limit message, or equivalent access restriction. Do not treat ordinary login as a security stop.

A CAPTCHA on an employer's own form skips that job only unless the employer portal itself blocks further use.

Email verification required to continue is not a permanent stop. Use:
"Please sign in / create the account / click the email verification link in this tab, then reply done"

Continue only after the user replies `done`.

## 8. Model guidance

Never hard-code model names or versions.

Tiers:
- **Strongest/current-vendor tier:** SETUP.
- **Light/current-vendor tier:** LinkedIn, Indeed, Naukri, Wellfound, and Instahyre quick applications.
- **Medium/current-vendor tier:** Workday, company direct, and discovery.

When a tier matters:
- recommend the appropriate tier from the same vendor the user is already using;
- ask the user to select/switch to that tier when needed;
- never pretend that the agent changed its own model.

Do not force a new chat merely because a different tier is preferred. If a handoff is genuinely needed, save all progress to the local files first and explain exactly how to resume.

If the same form step fails on three jobs in a row, stop that workflow and recommend the medium tier from the same vendor.

## 9. Logins and account creation

Keep the existing separate account record for reusable company-portal accounts:

`tracking/created_accounts.csv`

Header:

`"date","company","portal_url","login_email","password","email_verified"`

Before creating a Workday or other company account, check this file first. If a record for that company exists, use **Sign In** instead of creating another account.

`credentials.md` is for reusable standard company-portal credentials. Daily application reports must never contain passwords.

When a platform or ATS simply shows a signed-out/login-required state, ask the user to sign in in the current tab and reply `done`, then verify sign-in and resume the current flow. Do not stop the platform for the day unless the page also shows a security restriction, CAPTCHA, unusual-activity warning, daily-limit message, or equivalent restriction.

If the browser/app blocks automated sign-in or account creation, use:
"Please sign in / create the account / click the email verification link in this tab, then reply done"

Pause until `done`.

## 10. Platform and strategy routing

For each selected platform, read its strategy file before browsing.

- LinkedIn → `instructions/platforms/linkedin_strategy.md`
- Indeed → `instructions/platforms/indeed_strategy.md`
- Naukri → `instructions/platforms/naukri_strategy.md`
- Wellfound → `instructions/platforms/wellfound_strategy.md`
- Instahyre → `instructions/platforms/instahyre_strategy.md`
- Workday → `instructions/platforms/workday_strategy.md`
- company_direct → `instructions/advanced_strategies/company_direct_apply.md`
- discovery → `instructions/advanced_strategies/web_search_discovery.md`

Strategy files never override the rules in this file.

### Workday classification
Any application that uses a Workday application form counts as **workday**, regardless of whether the job was found through Workday search, discovery, a company URL, or another source.

### Job-source routing
The following selectable sources reuse existing flows and do not create new automation systems:
- **The Reliable Jobs** → use discovery. The current public route may lead to an external application form; inspect the actual job and continue only through a supported destination.
- **TEKsystems** → use company_direct from the careers page. If the actual job opens a Workday form, hand off to Workday and count it as workday.
- **Teksands** → use company_direct for the current Teksands/Hire4X candidate route. Inspect the actual form and use the custom/proprietary ATS rules; do not assume fields beyond what the page shows.
- **D4hire** → currently source-only unless a specific candidate job/application route is discoverable. The public site is a recruitment-agency site; if no job/application route exists, report the source as unavailable and do not invent an application flow.
- **Supersourcing** → use company_direct for the current developer/job route and inspect the actual candidate form; treat any profile/talent registration as incomplete until a specific job application is confirmed.
- **We Work Remotely** → use discovery. Inspect the job's **Apply for this position** destination. If it opens an ATS/company form, use the corresponding existing flow. If it provides only an email application, report that route as unavailable; do not send recruiter/application emails automatically.

For every selected source:
1. Record the selected source in the daily record.
2. Inspect the actual job/application destination before applying.
3. Record the actual destination URL/host in the daily record.
4. Route to the existing flow based on the actual destination, not the source name.
5. Count only a confirmed application to a specific job. A talent registration, profile creation, account creation, or Apply-button click without confirmed submission is not `applied`.
6. Preserve all existing duplicate, daily-limit, approval, login/upload fallback, security-stop, pacing, and confirmation rules.

Do not enable or use a source site's independent auto-apply service, and do not send recruiter emails automatically.

### Discovery handoff
Discovery must continue the currently discovered job's application flow:
- do not restart another platform's search;
- do not require a saved career URL just because the job was discovered on the web;
- if the discovered application is Workday, continue the Workday form at the current job and count it as workday;
- if the discovered application is Greenhouse, Lever, Ashby, or another supported direct ATS, continue the company-direct form flow at the current job;
- otherwise inspect the actual current page and use the closest supported form flow without inventing UI behavior.

## 11. End-of-session behavior

At the end of a session:
- summarize today's outcomes from the daily file;
- include applied, skipped, and needs_user jobs;
- include any site stops;
- ask the user unresolved questions;
- when the user answers a new question, save it immediately under `## Learned Answers`.

Never create a second daily application file for another session on the same local date.

## 12. Walkthrough checklist for verification

The instructions must support these scenarios without contradictions:

1. **Fresh setup** — missing files are created, resume is copied, topics are collected one at a time, empty contextual/learned sections are accepted, and no applications start before verification.
2. **Interrupted setup** — existing answers and checklist state are preserved, including already learned answers, and SETUP resumes at the first unfinished topic.
3. **Skipped optional fields** — `None` is stored once and does not cause a setup loop.
4. **Normal sign-in request** — an ordinary signed-out/login-required prompt asks the user to sign in in the current tab, wait for `done`, verify sign-in, and resume rather than stopping the platform.
5. **Real security restriction** — CAPTCHA, unusual activity, security restriction, or daily-limit messaging still stops the platform for that local date.
6. **First instant-submit application** — preview + `ok` happens before a submit-capable click, including Naukri Apply.
7. **Unsupported upload** — user uploads in the current tab, replies `done`, and the file is verified.
8. **Discovery into Lever** — the discovered Lever form is continued directly using the company-direct form rules; no saved career URL is required.
9. **Discovery into Workday** — continue the current Workday form and count it as workday.
10. **Context-specific unanswered question and later retry** — the unanswered question becomes `needs_user`, gets stored with context after the user answers, and the same job may then be retried.
11. **Two sessions on one date** — both sessions write to the same daily file.
12. **New local date/midnight** — a new date file is used for limits while historical duplicate checks remain active.
13. **Partly used limits + site stop** — today's counts and dated stop records persist in today's file and today's legacy CSV rows are included.
14. **Legacy site stop by date** — a today's legacy skipped row whose notes begin `site stopped:` blocks that platform today; an earlier-date stop does not.
15. **Overlapping legacy + Markdown application** — the same application recorded in both sources is counted once.
16. **New-chat/model handoff** — all progress is saved first; the user can resume without repeating completed setup or today's plan.
17. **Selectable job sources** — each new source can be selected in PLAN; the source is recorded, the actual destination is inspected, and routing follows the existing discovery/company-direct/Workday flow.
18. **Unconfirmed source action** — profile/talent registration or an Apply-button click without a site confirmation is not counted as `applied`.
19. **Source-route unavailable** — an unsupported destination or email-only route is reported as unavailable without inventing a flow or sending an automatic email.

Do not claim live application testing. These walkthroughs are static instruction/workflow checks unless an actual browser session is separately performed.
