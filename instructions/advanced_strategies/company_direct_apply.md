# Company Direct Apply Strategy

## Objective
Apply directly on company career pages using only the URLs saved under `Company Career Page URLs` in `personal_data/profile.md`.

## Execution Flow
1. Open one saved company career URL at a time. If `company_direct` was selected but no URLs are saved, pause and collect them; do not substitute a different discovery strategy.
2. Locate the current job posting and read the full job post.
3. Identify the actual ATS/form being used.
4. Run the fit, scoped duplicate, daily-limit, site-stop, and pacing checks in `AGENTS.md`.
5. If the form is Workday, classify and count it as `workday` and follow the Workday strategy. This classification applies even though the source URL was a company career page.
6. For standard ATS forms such as Greenhouse, Lever, or Ashby:
   - attach `personal_data/resume.pdf`;
   - if upload is unsupported, ask the user to upload it in the current tab, wait for `done`, and verify it;
   - fill basic information and links from authoritative saved data;
   - compare prefilled facts with saved values before submission;
   - answer EEO and screening questions only from matching saved data.
7. For custom/proprietary ATS:
   - use `personal_data/credentials.md` only when an account is required;
   - reuse an existing company account from `tracking/created_accounts.csv`;
   - log a new account immediately when created;
   - never put passwords in the daily application record.
8. If a required question is not answered by a matching saved context, stop and log `needs_user` rather than guessing.
9. Before the first submit of the session, show the filled answers and wait for `ok`.
10. Submit, verify confirmation, then append the outcome immediately to today's `applied/YYYY-MM-DD/applications.md`.
11. Wait at least 2 minutes before another `company_direct` or `discovery` submit because their hard daily limit is combined.

## Exclusions
- Do not turn `company_direct` into general web discovery.
- If a custom ATS requires essay-style behavioral answers not covered by saved data, skip it and record the unanswered question.
