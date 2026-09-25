All paths in this project are relative to this folder, not the computer's root.

# AI-Native Job Application Framework

This repository is a markdown-only job application framework. The AI agent uses these files as its instructions and the local personal-data files as the source of truth while applying through its browser/search tools.

## 1. Non-negotiable operating rules

- `AGENTS.md` is the primary instruction file. `CLAUDE.md` imports it.
- Do not run or invent executable setup, databases, dependencies, dashboards, or other automation infrastructure. This project is intentionally local Markdown + personal files + daily records.
- Never run `SETUP` against an unfinished profile and never apply while setup is unfinished.
- Never guess an answer. `None` means the user has no available value; it is not an answer that may be submitted into a required field.
- Save new user answers immediately. Do not repeatedly ask a question whose answer is already saved.
- Do not put passwords in application reports. Keep company-portal account records separate in `tracking/created_accounts.csv`.
- Before submission, compare any prefilled or parsed factual information with the saved user data. Correct mismatches before submitting.
- If a resume upload control is unsupported, ask the user to upload `personal_data/resume.pdf` in the current tab, wait for `done`, then verify that the resume is attached before continuing.
- Record application outcomes immediately after the outcome is known. Never invent a confirmation or mark a job `applied` without site confirmation.

## 2. `start` flow and resumable SETUP

Every time the user types `start`, do this first:

1. Read `setup_checklist.md` if it exists; otherwise create it from `setup_checklist_template.md`.
2. Inspect the actual required local files and saved answers, not only the checklist boxes:
   - `personal_data/resume.pdf` must exist.
   - `personal_data/profile.md` must exist and contain all required setup sections with each field either answered or set to `None`; no unresolved bracketed placeholders are allowed.
   - `personal_data/form_answers.md` must exist and contain all required screening sections with each field either answered or set to `None`; no unresolved bracketed placeholders are allowed.
   - `personal_data/credentials.md` must exist when the selected plan requires company-portal credentials.
   - Account/sign-in readiness must be checked for selected platforms when needed.
3. Compare the checklist with the actual files/answers. Checked boxes alone never prove readiness.
4. If any required setup item is incomplete, enter SETUP mode, resume the first unfinished topic, and do not start applications.
5. If setup is complete, continue to application-plan selection/resumption in START mode.

### SETUP mode

Work with the user one topic at a time and save each topic immediately before moving to the next:

1. **Resume**
   - Ask for the resume file or its local path.
   - Copy it to `personal_data/resume.pdf`.
   - If a verified resume already exists, keep it unless the user explicitly replaces it.
   - Verify that the file exists before marking this topic complete.

2. **Basic/contact information**
   - First name, last name, email, phone country code, phone number, location, and address.
   - Optional values may be `None`.
   - Save to `personal_data/profile.md`.

3. **Employment and education**
   - Current role, total experience, core skills, employment history, highest education/degree and year, and other education details needed by forms.
   - Save to `personal_data/profile.md`.

4. **Compensation and notice**
   - Current salary/CTC when available.
   - Expected salary/CTC when available.
   - For each salary value, save amount, currency, and period (for example, monthly or annual).
   - Notice period in days.
   - Save to `personal_data/profile.md`.

5. **Job preferences**
   - Target job titles, accepted locations, accepted work modes, companies to skip, and any lower daily limits.
   - `Work Modes Accepted` in `profile.md` is the authoritative source for work mode.
   - Save to `personal_data/profile.md`.

6. **Work authorization and sponsorship**
   - Country or countries relevant to applications.
   - Work authorization in each relevant country.
   - Whether sponsorship is required now or in the future in each relevant country.
   - `Work Authorization` in `profile.md` is the authoritative source for these facts.
   - Save to `personal_data/profile.md`.
   - If a site asks a contextual variant of the question, store that exact question and answer under `## Learned Answers` in `personal_data/form_answers.md` with employer/country/role/portal context.

7. **Common screening answers**
   - Skill-by-skill experience, English level, relocation/commute preferences, referral/history questions, EEO answers, standard source-of-job answer, number-field rules, and other common screening answers.
   - Save to `personal_data/form_answers.md`.
   - Never submit `None` into a required field.

8. **Credentials and account readiness**
   - When Workday, company-direct, or another custom company portal is selected, verify `personal_data/credentials.md` has the needed standard application email/password and that the separate account record can be used.
   - Never repeat passwords in chat summaries or application reports.
   - Selected-platform sign-in readiness is checked before applications begin.

Resume and saved answers are never overwritten just because a setup session resumes. Update only the incomplete or newly corrected information.

When setup becomes complete, update `setup_checklist.md`, re-check the actual files, and then give the model guidance described below. Do not begin an application in the same step that discovers unfinished setup.

## 3. Application plan after setup

After setup is complete, ask where to apply and how many applications to attempt on each selected platform.

Supported choices:
- `linkedin`
- `indeed`
- `naukri`
- `wellfound`
- `instahyre`
- `workday`
- `company_direct`
- `discovery`

For LinkedIn, Indeed, Naukri, and Wellfound, offer 10 or 15 as convenient starting counts where the platform's hard maximum permits. The user may choose a lower number or another count that stays within the hard maximum. Workday, company-direct, Instahyre, and discovery are subject to their smaller maximums below.

When `company_direct` is selected, ask for the company career URLs and save them in `personal_data/profile.md`. `discovery` does not require saved career URLs.

When `instahyre` is selected, use `instructions/platforms/instahyre_strategy.md`, inspect the real site at runtime, and never assume UI behavior that has not been observed. Its hard maximum is 10 applications per day.

Create or update today's application file at:

```text
applied/
  YYYY-MM-DD/
    applications.md
```

Store today's selected platforms, requested counts, effective hard/user limits, and progress in that one file so another chat can resume the plan on the same local date.

Do not force a new chat just because a lighter/heavier model would be useful. If a handoff is genuinely needed, save all setup/plan/progress first and tell the user exactly how to resume.

## 4. One daily application file

There must be exactly one application file per local date:

```text
applied/
  YYYY-MM-DD/
    applications.md
```

Use platform sections inside this one file. Do not create separate application files per platform, session, or job.

Recommended structure:

```markdown
# Applications — YYYY-MM-DD

## Today's Plan
- Platforms:
- Requested count per platform:
- User lower limits:
- Effective limits:
- Progress:
- Last updated:

## linkedin
### Company — Job Title
- Local date/time:
- Platform:
- Company:
- Job title:
- Location/work mode:
- Job URL:
- Job ID:
- Relevant submitted answers:
- Resume filename:
- Status:
- Confirmation shown:
- Skip reason / unanswered question / next action:

## indeed
<!-- same record format -->

## naukri
## wellfound
## instahyre
## workday
## company_direct
## discovery

## Site Stops
- Local date/time:
- Platform:
- Message:
- Next eligible date:
```

The exact heading names may be extended with numbered entries, but each job record must include all fields above. Use `None` or `Not applicable` where a field genuinely has no value.

Append the record immediately after each job outcome. Never batch-write outcomes at the end of a session.

For an `applied` job:
- Record the local date/time and platform.
- Record company, title, location/work mode, job URL, and job ID scoped to that company/portal.
- Record relevant answers that were submitted and the resume filename.
- Record the exact confirmation shown by the site when available.
- Write `Status: applied` only after confirmation is visible.
- Never invent a confirmation.

For a `skipped` or `needs_user` job:
- Record the same identifying fields.
- Record the relevant resume state.
- Use the skip reason, unanswered question, or next action field to make the next retry deterministic.

Site-stop records belong in the same daily file. A site with a site-stop record for today must not be used again that day.

### Legacy CSV history

`tracking/applied_jobs.csv` may exist from an older version. Treat it as read-only historical input:
- Do not delete, rewrite, migrate in place, or append new applications to it.
- Read it for duplicate detection and historical context when present.
- Never count the same application twice when it exists in both the legacy CSV and a new daily Markdown file.
- New application records are written only to `applied/YYYY-MM-DD/applications.md`.

Keep the separate company account record at `tracking/created_accounts.csv`. Do not put passwords in daily application records.

## 5. Hard daily limits and recount rules

Hard maximum applications per local day:
- LinkedIn: 20
- Indeed: 20
- Naukri: 25
- Wellfound: 10
- Instahyre: 10
- Workday: 5
- `company_direct` + `discovery` combined: 10
- All platforms: 50

The user's requested session count and any lower user-defined limit must both be respected. A user limit can lower a hard maximum, never raise it.

Before EVERY application:
1. Determine the current local date and local time.
2. Open that date's `applied/YYYY-MM-DD/applications.md`. If local date changed, create the new date file and recalculate from zero for the new day.
3. Recount `Status: applied` records for the relevant platform from the current daily file.
4. Recount today's total `Status: applied` records across all platform sections.
5. Recount the combined `company_direct` + `discovery` applied total.
6. Check today's site-stop records.
7. Re-check the job's scoped duplicate status.
8. Re-check pacing against the last successful submit on the same platform/workflow.

If a limit is reached, stop that platform for the day and record a site-stop entry. Recount after midnight before applying again.

Limits are application limits, not search-result limits. Skipped and `needs_user` records do not consume an application slot unless the site has explicitly stopped the platform.

## 6. Fit, duplicates, and authoritative answers

### Fit check

Apply only when:
- the job title matches the target titles in `personal_data/profile.md`;
- the location matches accepted locations;
- the work mode matches the authoritative `Work Modes Accepted` field in `profile.md`;
- required experience is compatible with the saved experience;
- the company is not on the skip list.

If the fit check fails, skip and record the reason.

### Duplicate check

A job is a duplicate when:
- the same scoped `job_id` is already logged as `applied` or `skipped`; or
- the same company and job title are already logged as `applied`.

A `needs_user` record may be retried after its unanswered question has a saved answer.

When a job ID is not globally unique, scope it to the company/portal shown in the daily record. Do not treat unrelated portals with the same visible ID as the same job.

### Authoritative user data

Keep one authoritative source for each fact:
- `profile.md`: identity, contact, employment, education, compensation, notice, job preferences, work mode, work authorization, sponsorship.
- `form_answers.md`: common screening answers and contextual/learned question-answer pairs.
- `resume.pdf`: resume content.
- `credentials.md`: standard application credential values.
- `tracking/created_accounts.csv`: separate company account records.

If a question is employer-, country-, role-, or portal-specific, store the context with the answer. Reuse a contextual answer only when the saved context matches the current employer/country/role/portal closely enough to be the same question context. Otherwise ask the user.

Never guess. If a required question is not answered by an authoritative source or a matching contextual answer:
1. Do not submit the job.
2. Log the job as `needs_user`.
3. Save the exact unanswered question under `## Learned Answers` immediately, including employer, country, role, portal/ATS, and date if known.
4. Ask the user for the answer.
5. Save the user's answer immediately and use it only for matching future contexts.

Never submit text that still contains square-bracket placeholders or placeholder text such as `X years`.

## 7. Submission approval and confirmation

Before the first submit/click that can immediately submit an application in each session:
- Show the user the filled answers, the resume filename/attachment state, and any relevant non-default selections.
- Wait for the user to reply `ok`.
- This review is required before Naukri's potentially instant Apply click as well.

If the host app requires another approval, keep that approval.

After approval:
- submit one application at a time;
- confirm the site's result before recording `applied`;
- append the daily record immediately;
- never mark success from intent alone.

Two-minute pacing:
- Wait at least 2 minutes between successful submits on the same platform.
- For `company_direct` and `discovery`, also use a 2-minute gap across that combined workflow.
- Re-evaluate pacing after every local-midnight change and every resumed session.

If a form is broken or keeps failing after 2 tries, skip the job, log the reason, and move on.

## 8. Site stops, CAPTCHAs, authentication, and retries

If a job site shows a daily-limit, unusual-activity, CAPTCHA, security check, or restriction message, stop that site for today, record the message in the daily file, and do not retry that site that day.

A CAPTCHA on one employer's own form skips that job only; it does not stop the whole platform.

Never attempt to bypass a CAPTCHA or 2FA challenge.

An email verification link for a new account is not itself a site stop. Use the fallback:

> Please sign in / create the account / click the email verification link in this tab, then reply done

Pause until the user replies `done`, then continue.

For unsupported resume uploads, use the separate current-tab upload fallback described in section 1.

## 9. Model guidance

Do not hard-code model names or versions.

- Before SETUP, recommend the strongest/higher tier available from the current model vendor.
- Before LinkedIn, Indeed, Naukri, Wellfound, or Instahyre quick applications, recommend a light tier.
- Before Workday, company-direct, or discovery, recommend a medium tier.
- Ask the user to select the appropriate tier when needed. Never pretend to switch models yourself.
- If the same form step fails on 3 jobs in a row, stop that workflow and suggest the medium tier from the same vendor.
- Do not force a new chat solely for model switching. If a handoff is needed for another reason, save all progress first and provide a resumable `start` instruction.

## 10. Logins and company accounts

The AI may use `personal_data/credentials.md` for company portals when its host app supports it.

`tracking/created_accounts.csv` is the separate reusable company-account record. Before creating a Workday or other company account:
1. Check whether the company already has an account record.
2. If it exists, use Sign In rather than creating another account.
3. If a new account is created, log it immediately.
4. Never copy the password into `applied/YYYY-MM-DD/applications.md`.

For selected job sites, sign-in readiness is checked during setup. If the app blocks the sign-in/create-account action, use the `done` fallback.

## 11. Strategy routing

Follow the relevant platform or advanced-strategy file for search and form flow. Strategy files never override the rules in this file.

- LinkedIn → `instructions/platforms/linkedin_strategy.md`
- Indeed → `instructions/platforms/indeed_strategy.md`
- Naukri → `instructions/platforms/naukri_strategy.md`
- Wellfound → `instructions/platforms/wellfound_strategy.md`
- Instahyre → `instructions/platforms/instahyre_strategy.md`
- Workday → `instructions/platforms/workday_strategy.md`
- company_direct → `instructions/advanced_strategies/company_direct_apply.md`
- discovery → `instructions/advanced_strategies/web_search_discovery.md`

### Workday classification

Any application form hosted by Workday counts as `workday`, regardless of how the job was discovered. Apply the Workday hard limit and Workday strategy even when the source was `discovery`, LinkedIn, or a company page.

### Discovery continuity

Discovery must continue the discovered job's form. Do not restart another platform's search strategy, and do not require saved career URLs. Once a suitable discovered job is open, finish that job through its actual form or stop it for a documented reason.

## 12. File references

Active committed instruction/template files:
- `AGENTS.md`
- `CLAUDE.md`
- `README.md`
- `setup_checklist_template.md`
- `instructions/platforms/linkedin_strategy.md`
- `instructions/platforms/indeed_strategy.md`
- `instructions/platforms/naukri_strategy.md`
- `instructions/platforms/wellfound_strategy.md`
- `instructions/platforms/instahyre_strategy.md`
- `instructions/platforms/workday_strategy.md`
- `instructions/advanced_strategies/company_direct_apply.md`
- `instructions/advanced_strategies/web_search_discovery.md`
