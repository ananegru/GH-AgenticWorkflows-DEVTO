---
name: New Day
on:
  schedule:
    # Once per day at 06:00 UTC
    - cron: "0 6 * * *"
  workflow_dispatch:
permissions:
  contents: read
  copilot-requests: write
engine: copilot
tools:
  edit:
safe-outputs:
  create-pull-request:
    allowed-files:
      - index.html
    max: 1
---

# New Day

You maintain the "Daily Updates" section of `index.html`. Each day, add an entry
for the current UTC date confirming that the daily update ran.

## Instructions

1. Determine the current **UTC date** of this workflow run (for example,
   `2026-09-14`). Express it in the same human-readable wording already used in
   the file (for example, `14th of September`).
2. Open `index.html` and inspect the existing **Daily Updates** navigation and
   the corresponding dialogs.
3. **Check for duplicates first.** If the current UTC date already appears as a
   navigation control or dialog, make **no change** at all and stop.
4. If the date is not yet present, add:
   - A new navigation entry in the `.daily-updates-list` `<ul>`, following the
     exact structure of the existing `<li>` / `<button data-dialog-trigger>`
     entries, including the `aria-haspopup`, `aria-controls`, and arrow markup.
   - A matching accessible `<dialog>` element that confirms the daily update
     ran for that date, following the exact structure, `id` conventions
     (for example, `september-14-dialog`, `september-14-question`,
     `september-14-answer`), heading, and close-button markup of the existing
     dialogs.
5. Match the existing HTML structure, ID naming conventions, date wording, and
   styling exactly. **Do not modify `styles.css`.**
6. **Preserve every existing daily update** — never remove or alter previous
   navigation entries or dialogs.
7. Do not duplicate any date, navigation control, or dialog.

Only `index.html` may be changed. Open a single pull request with your update.
