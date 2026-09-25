# Workday Application Strategy

## Objective
Complete Workday-hosted application forms while preserving the global fit, duplicate, answer, pacing, confirmation, and daily-limit rules in `AGENTS.md`.

## Classification
Any application form hosted by Workday counts as `workday`, regardless of whether the job was found through Workday search, web discovery, LinkedIn, or a company career page.

## Search Strategy
1. Search for target jobs using the saved titles and locations.
2. Web search can use queries such as:
   `site:myworkdayjobs.com "<target job title from profile.md>" "<location from profile.md>"`.
3. Do not require the user to save career URLs just to discover Workday roles.

## Execution Flow
1. Open one job, read the post, and run fit, scoped duplicate, daily-limit, site-stop, and pacing checks before creating or signing into an account.
2. Check `tracking/created_accounts.csv`.
   - If the company already has an account record, use Sign In.
   - Otherwise continue with account creation using `personal_data/credentials.md`.
3. When an account is created, append it immediately to `tracking/created_accounts.csv`. Never place its password in the daily application record.
4. **Resume upload:** upload `personal_data/resume.pdf`.
   - If the control is unsupported, ask the user to upload the resume in the current tab, wait for `done`, and verify the attachment.
5. Review parsed/pre-filled information against the authoritative values in `personal_data/profile.md`. Correct mismatches before continuing.
6. Complete required experience and education fields from saved data.
7. For application questions, use `form_answers.md` and only matching context-specific learned answers. If a required question has no match, stop this job, log `needs_user`, and save the exact question/context immediately.
8. Complete voluntary disclosures only from saved answers.
9. Run the global final answer check from `AGENTS.md`.
10. Before the first submit of the session, show the filled answers and attachment state and wait for `ok`.
11. Submit the application and verify Workday's confirmation/status before recording `Status: applied`.
12. Append the outcome immediately to today's `applied/YYYY-MM-DD/applications.md`.
13. Wait at least 2 minutes before another Workday submit.

## Account verification
If Workday requires email verification and the agent cannot open the inbox, pause and say:

> Please sign in / create the account / click the email verification link in this tab, then reply done

Continue only after the user replies `done`.

## Exclusions
- Do not repeatedly correct harmless historical parsing differences after the required fields match the saved data.
- Do not guess country-, employer-, or role-specific answers.
