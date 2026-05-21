# Bug Reporting at BizzNEST

## When to File a Bug

File a bug report when you encounter:

- **Unexpected behavior** — something works differently than it should based on the requirements.
- **Visual glitches** — layout breaks, overlapping elements, or styling issues.
- **Crashes or errors** — the app crashes, shows error screens, or throws unhandled exceptions.
- **Regressions** — something that was working before is now broken after a recent change.

If you're unsure whether something is a bug, ask in your team channel first.

## How to File a Bug Report

1. Go to the project's GitHub repository.
2. Click the **Issues** tab and then **New issue**.
3. Select the **Bug Report** template.
4. Fill out **every section** of the template — don't skip fields.
5. Add the `bug` label to your issue.
6. Assign the issue to yourself if you plan to fix it, or leave it unassigned for your lead to triage.
7. Add the issue to the project board in the **Backlog** column.

Our bug report template is located at [`.github/ISSUE_TEMPLATE/bug_report.md`](/.github/ISSUE_TEMPLATE/bug_report.md).

## Writing Good Reproduction Steps

The most important part of a bug report is **how to reproduce it**. Follow these rules:

- **Number every step.** Use a numbered list, not a paragraph.
- **Be specific.** Say "Click the Submit button on the Contact form" not "Click submit."
- **Include the starting point.** Where does the user begin? (e.g., "Start on the home page, logged in as an admin.")
- **State expected vs. actual.** What should happen? What actually happens?
- **Attach screenshots or screen recordings.** A picture is worth a thousand words.
- **Include environment info.** Browser, OS, screen size — anything relevant.

## Bug Lifecycle

1. **Open** — Bug is reported and sitting in the Backlog.
2. **In Progress** — Someone is actively working on a fix. Create a branch following the naming convention: `<initials>-<issue#>-<description>` (e.g., `ar-15-fix-login-crash`).
3. **In Review** — A fix has been submitted as a Pull Request and is waiting for code review.
4. **Closed** — The fix has been reviewed, approved, merged, and verified.
