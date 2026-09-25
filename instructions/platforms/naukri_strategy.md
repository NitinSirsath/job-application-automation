# Naukri Application Strategy

## Objective
Apply to relevant technical roles on Naukri.com.

## Search Strategy
1. Navigate to Naukri.com search.
2. Input key skills from `personal_data/profile.md`.
3. Set the experience filter appropriately based on the saved profile.
4. Filter for postings in the last 1 to 2 days.

## Execution Flow
1. Read the listing and run the fit, scoped duplicate, daily-limit, site-stop, and pacing checks in `AGENTS.md`.
2. Focus on listings with the simple **Apply** button that does not redirect externally.
3. Because Naukri may submit immediately on Apply, before the first Apply click of the session show the job and the profile/answers Naukri will send and wait for `ok`.
4. Compare any prefilled/parsed factual information with the saved profile before the potentially instant submit.
5. If additional questions appear, answer only from matching saved data. Otherwise stop and log `needs_user`.
6. Click Apply and verify the resulting confirmation/status before recording success.
7. Append the outcome immediately to today's `applied/YYYY-MM-DD/applications.md`.
8. Wait at least 2 minutes before another Naukri apply.

## Exclusions
- Skip roles where the required location does not match the user's preferences.
- Do not guess answers.
