# Workday Application Strategy

## Objective
Complete Workday application forms safely. Any Workday application counts toward the Workday daily limit, regardless of where the job was discovered.

## Search / Entry Point
1. When Workday is selected directly, discover roles using the current search flow.
2. When a Workday job arrives from discovery or a company page, **continue the current discovered job**. Do not restart a Workday search.
3. Use target titles, locations, and work modes from \`personal_data/profile.md\`.

## Execution Flow
1. Read today's daily file and applicable history for scoped duplicates.
2. Read the complete job post and run fit and daily-limit checks before creating or signing in to an account.
3. Check \`tracking/created_accounts.csv\` before creating a company account.
4. If an account exists for that company, use **Sign In**. Do not create a duplicate account.
5. If no account exists, create one with \`personal_data/credentials.md\` as permitted, then log the new account immediately in \`tracking/created_accounts.csv\`.
6. Upload \`personal_data/resume.pdf\`.
7. Compare Workday-parsed information with \`profile.md\` before accepting it. Correct material discrepancies from the authoritative source.
8. If automated upload is unsupported, ask the user to upload \`personal_data/resume.pdf\` in the current tab, wait for \`done\`, and then verify the upload.
9. Complete the current Workday steps shown by the site. Do not invent a fixed sequence; labels can vary.
10. Answer application questions from \`form_answers.md\` only when the answer and context match. Do not guess.
11. Re-check final factual values before submission.
12. Before the first submit-capable action of the session, show the exact application data/questions and wait for \`ok\`.
13. Honor any additional Workday approval prompt.
14. Submit.
15. Wait for confirmation shown by Workday.
16. Append the outcome immediately to today's daily Markdown file.
17. Wait at least 2 minutes before another Workday submit.

## Account / verification fallback
If Workday requires email verification that the agent cannot complete, say:
"Please sign in / create the account / click the email verification link in this tab, then reply done"

Continue only after the user replies \`done\`.

## Exclusions / Rules
- Do not create another account when an existing company account record is available.
- Do not get stuck repeatedly correcting harmless old-experience parsing issues; correct required material values and proceed.
- A Workday CAPTCHA or security restriction stops that application or site according to \`AGENTS.md\`; never bypass it.
