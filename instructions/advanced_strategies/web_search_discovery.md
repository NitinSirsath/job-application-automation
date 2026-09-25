# Web Search Discovery Strategy

## Objective
Find relevant direct job postings outside the major platforms and continue the discovered job's actual application flow.

## Search Strategy
1. Build searches from target job titles, accepted locations, and work modes in \`personal_data/profile.md\`.
2. Prefer direct ATS/application pages such as Greenhouse, Lever, Ashby, and Workday.
3. Avoid aggregators that merely redirect back to LinkedIn or Indeed.
4. Do not require saved company career URLs for discovery.

## Execution Flow
1. Execute discovery searches.
2. Open a discovered job and inspect the actual job page.
3. Run fit, duplicate, and daily-limit checks.
4. **Continue this exact discovered job** rather than restarting a different strategy's search.
5. If the application is a Workday form, continue with \`instructions/platforms/workday_strategy.md\` starting at the current job. Count it as workday.
6. If the application is Greenhouse, Lever, Ashby, or another supported direct ATS, continue with \`instructions/advanced_strategies/company_direct_apply.md\` starting at the current job.
7. If the site is another supported application flow, inspect the current page and use the closest existing strategy without inventing UI behavior.
8. Compare prefilled factual values with \`personal_data/profile.md\`.
9. Answer questions only from saved answers whose context matches.
10. If required information is missing, record \`needs_user\` and save the exact question under \`## Learned Answers\` when the user answers it.
11. Before the session's first submit-capable action, show the exact filled answers/pitch and wait for \`ok\`.
12. Confirm success from the actual site.
13. Append the outcome immediately to today's daily Markdown file.
14. Wait at least 2 minutes between submits in the combined company-direct/discovery workflow.

## Exclusions
- Do not restart the search after a discovered job has been opened.
- Do not require a saved career URL for a discovered direct application.
- Avoid aggregators that do not lead to a direct application path.
