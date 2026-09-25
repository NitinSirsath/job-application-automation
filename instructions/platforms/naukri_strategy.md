# Naukri Application Strategy

## Objective
Quickly apply to relevant technical roles on Naukri.com.

## Search Strategy
1. Navigate to Naukri.com search.
2. Input key skills from `personal_data/profile.md` (e.g., React, Next.js, JavaScript).
3. Set the experience filter appropriately based on the user's profile.
4. Filter for postings in the last 1 to 2 days.

## Execution Flow
1. Focus on listings that have the simple **Apply** button which does not redirect externally.
2. Read the post and run the fit, duplicate and daily-limit checks in `AGENTS.md`. Apply may submit at once, so before the first Apply click of the session show the job and the profile details Naukri will send, and wait for `ok`.
3. Click Apply. Often, Naukri auto-submits based on the existing user profile.
4. If additional questions are prompted, answer using `personal_data/form_answers.md`.
5. Log the application to `tracking/applied_jobs.csv`.
6. Wait at least 2 minutes before another Naukri apply.

## Exclusions
- Skip roles where the required location does not match the user's preferences in `personal_data/profile.md`.
