---
name: Weekly Report Status
on:
  schedule:
    # Every Monday at 09:00 UTC
    - cron: "0 9 * * 1"
  workflow_dispatch:
permissions:
  contents: read
  issues: read
  pull-requests: read
  copilot-requests: write
engine: copilot
safe-outputs:
  create-issue:
    title-prefix: "[weekly-report] "
    max: 1
---

# Weekly Report Status

You are a repository activity reporter. Produce a concise activity report for
the **previous seven days** and publish it as a new GitHub issue.

## Instructions

1. Determine the reporting window: the seven days ending at the current run time.
2. Gather activity for `${{ github.repository }}` within that window:
   - **Commits** merged into the default branch.
   - **Issues** opened, closed, or updated.
   - **Pull requests** opened, merged, or closed.
3. Summarize the findings in a clear, well-structured report:
   - Use short sections and bullet points.
   - Include counts and highlight the most notable items.
   - Link to relevant issues and pull requests where helpful.
4. Publish the report by creating a single new issue.
5. If there was **no activity** in the reporting window, say so clearly in the
   issue rather than omitting the section or leaving it empty.

Keep the report concise and factual. Do not invent activity that did not occur.
