# Web Search Discovery Strategy

## Objective
Find suitable job postings outside the major platform search flows, then continue the discovered job's actual application form.

## Search Strategy
1. Build searches from the target titles, accepted locations, and work modes in `personal_data/profile.md`.
2. Target direct ATS pages, for example:
   `site:boards.greenhouse.io "<target job title from profile.md>" "<location from profile.md>"`
   `site:jobs.lever.co "<target job title from profile.md>" "<location from profile.md>"`
3. Search relevant niche job boards or hiring posts when they lead to a direct application.
4. Do not require saved company career URLs for discovery.

## Execution Flow
1. Execute the discovery search and open a promising job result.
2. Read the job posting and run the fit, scoped duplicate, daily-limit, site-stop, and pacing checks.
3. Continue the discovered job's form from the current result. Do not restart another platform's search strategy.
4. If the discovered form is Workday, classify the application as `workday`, apply the Workday limit, and follow `instructions/platforms/workday_strategy.md`.
5. If the discovered form is another supported ATS, follow the matching form rules while keeping this job under `discovery` for the combined direct/discovery daily limit.
6. Compare prefilled facts with saved user data before submission.
7. Answer only from saved or matching context-specific answers. Otherwise stop and log `needs_user`.
8. If the resume upload is unsupported, ask the user to upload `personal_data/resume.pdf` in the current tab, wait for `done`, and verify it.
9. Before the first submit of the session, show the filled answers and wait for `ok`.
10. Submit, verify confirmation, and append the outcome immediately to today's `applied/YYYY-MM-DD/applications.md`.
11. Wait at least 2 minutes between submits in the combined `company_direct` + `discovery` workflow.

## Exclusions
- Avoid aggregators that only loop back to LinkedIn or Indeed.
- Do not restart a new search after opening a discovered job just because its form is hosted by another ATS.
- Do not claim a discovered job is applied until the actual form confirms it.
