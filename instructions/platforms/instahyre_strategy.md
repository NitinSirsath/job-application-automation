# Instahyre Application Strategy

## Objective
Apply to relevant roles on Instahyre while keeping the workflow deliberately conservative.

## Search Strategy
1. Open Instahyre and inspect the actual current job/search UI at runtime.
2. Use target titles, locations, and work modes from \`personal_data/profile.md\`.
3. Do not assume a particular button name, form sequence, or quick-apply behavior unless the current page shows it.
4. Run fit, duplicate, and daily-limit checks before applying.

## Execution Flow
1. Instahyre has a hard maximum of 10 applications per local day, regardless of a larger user request.
2. Read today's daily file and available legacy history for scoped duplicates and today's count.
3. Read the complete current job post.
4. Compare any prefilled factual values with \`profile.md\`.
5. Answer questions only from the saved data and matching contextual answers.
6. Before the session's first submit-capable action, show the exact filled details and wait for \`ok\`.
7. Complete the actual current-page application flow.
8. Record \`applied\` only after the site shows confirmation. Otherwise record \`skipped\` or \`needs_user\` with the exact reason.
9. Append the outcome immediately to today's daily Markdown file.
10. Wait at least 2 minutes before another Instahyre submit.

## Exclusions
- Do not invent guaranteed Instahyre UI behavior.
- Stop Instahyre for the day on a restriction, CAPTCHA, unusual-activity, authentication, or daily-limit message and record the dated site stop.
