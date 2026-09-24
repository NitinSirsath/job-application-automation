# Web Search Discovery Strategy

## Objective
Use web search tools to bypass crowded major job boards and find niche job postings, direct company listings, or hiring posts on social platforms.

## Search Strategy
1. **Utilize Dorks / Advanced Search Queries:**
   - Search for specific ATS URLs combined with the role:
     `site:boards.greenhouse.io "Frontend Engineer" "React" "Remote"`
     `site:jobs.lever.co "Software Engineer" "Next.js"`
   - Search for hiring posts on platforms like Twitter/X or Reddit:
     `"hiring" OR "looking for" "Frontend Engineer" "React" site:twitter.com/search`
     `site:reddit.com/r/reactjs "who is hiring"`

2. **Target Niche Job Boards:**
   - Search for specialized job boards (e.g., "remote react jobs board", "web3 frontend jobs", "climate tech jobs").
   - Navigate to these boards and parse their listings.

## Execution Flow
1. Execute search queries.
2. Parse the search results to extract direct application links.
3. Navigate to the extracted links.
4. If it's a standard ATS (Greenhouse, Lever) or Workday, follow the respective strategy guides in `/instructions/`.
5. Apply and log to `/tracking/applied_jobs.csv`.

## Exclusions
- Avoid aggregators that just loop you back to LinkedIn or Indeed. Focus on direct ATS links.
