# Web Search Discovery Strategy

## Objective
Use web search tools to find niche job postings, direct company listings, or hiring posts outside the major platforms.

## Search Strategy
1. Build searches using the **target job titles from `personal_data/profile.md`** and the accepted locations/work modes from the same file.
2. Target common ATS pages with queries such as:
   `site:boards.greenhouse.io "<target job title from profile.md>" "<location from profile.md>"`
   `site:jobs.lever.co "<target job title from profile.md>" "<location from profile.md>"`
3. Search hiring posts on relevant platforms using the same target job titles from `profile.md`.
4. Target niche job boards that match the user's preferences.

## Execution Flow
1. Execute search queries.
2. Parse the search results to extract direct application links.
3. Navigate to the extracted links.
4. Read the job post and run the fit and duplicate checks in `AGENTS.md`.
5. If it's a standard ATS (Greenhouse, Lever) or Workday, follow the respective strategy guide in `instructions/`.
6. Answer from `personal_data/form_answers.md`; otherwise skip and log.
7. Before the first submit of the session, show the filled answers and wait for `ok`.
8. Apply and log to `tracking/applied_jobs.csv`.
9. Wait at least 2 minutes before another submit in the discovery/company-direct workflow.

## Exclusions
- Avoid aggregators that just loop you back to LinkedIn or Indeed. Focus on direct ATS links.
