# Company Direct Apply Strategy

## Objective
Apply directly on company career pages or supported direct ATS pages such as Greenhouse, Lever, and Ashby.

## Entry points
This strategy supports two entry points:
- **company_direct plan** — use the company career URLs saved in `personal_data/profile.md`.
- **discovery handoff** — use the exact ATS/application URL discovered from the current job. Do not require a saved career URL and do not restart a search.

## Execution Flow
1. Start from the current company/job page supplied by the plan or discovery flow.
2. Locate the Apply/View Roles control shown by the current page.
3. Identify the current ATS from the actual URL/page.
4. Run fit, duplicate, and daily-limit checks before account creation or submission.
5. For Greenhouse / Lever / Ashby:
   - attach `personal_data/resume.pdf`;
   - fill Basic Info from `profile.md`;
   - fill links from `profile.md`;
   - answer common or contextual questions from `form_answers.md`;
   - compare prefilled factual values with `profile.md`;
   - if upload is unsupported, use the documented user-upload `done` fallback;
   - before the session's first submit-capable action, show the filled answers and wait for `ok`;
   - submit and wait for actual confirmation.
6. For custom/proprietary ATS:
   - inspect the actual page instead of assuming a fixed sequence;
   - use reusable credentials only when an account is required;
   - check `tracking/created_accounts.csv` before creating a new account;
   - log a new account immediately when created;
   - answer only from saved data and matching contextual answers.
7. Append the application outcome immediately to today's `applied/YYYY-MM-DD/applications.md`.
8. Wait at least 2 minutes before another submit in the company-direct/discovery workflow.

## Exclusions
- Skip essay-style behavioral questions that are required but not covered by saved user information.
- Never invent a Greenhouse/Lever/Ashby UI control or confirmation.
