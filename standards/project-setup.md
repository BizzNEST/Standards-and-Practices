# Setting Up GitHub Projects at BizzNEST

## Overview

GitHub Projects is how we track tasks, bugs, and progress at BizzNEST. Every project should have a Project Board that your team lead and teammates can view to see what you're working on, what's blocked, and what's done.

## Creating a Project Board

1. Go to the [BizzNEST GitHub Organization](https://github.com/BizzNEST).
2. Click on the **Projects** tab.
3. Click **New project**.
4. Choose the **Board** view (Kanban-style).
5. Name it to match your project (e.g., `Project Name - Sprint Board`).

## Recommended Columns

Set up these columns on your board:

| Column | What Goes Here |
|---|---|
| **Backlog** | Tasks that are planned but not started yet |
| **In Progress** | Tasks you are actively working on |
| **In Review** | Tasks with an open Pull Request waiting for review |
| **Done** | Completed and merged tasks |

## Adding Issues to the Board

- Every task should start as a **GitHub Issue** before it goes on the board.
- When creating an issue, use the appropriate issue template (feature request, bug report, or epic).
- Add the issue to your project board from the issue sidebar under **Projects**.
- Assign the issue to yourself when you start working on it.

## Using the Board During Sprints

- **Update your cards daily.** Move them to the correct column as your work progresses.
- When you open a Pull Request, move the card to **In Review**.
- When your PR is merged, move the card to **Done** and close the issue.
- Your team lead will check the board during standups and weekly meetings — keep it accurate.

## Tips

- Don't let cards pile up in **In Progress** — focus on finishing tasks before starting new ones.
- Link your Pull Requests to issues using keywords like `Closes #12` in the PR description.
- If you're blocked, add a comment to the issue explaining why and mention your lead.
