# Code Review at BizzNEST

## Why Code Reviews Matter

Code reviews help us catch bugs before they reach production, share knowledge across the team, and keep our codebase clean and consistent. Every Pull Request goes through a review — no exceptions.

## Process

1. **Open a Pull Request into `development`.** Follow the [PR template](/.github/pull_request_template.md) and fill out every section.
2. **Request a review from a teammate on the project.** If nobody picks it up, mention the project team (e.g. `@BizzNEST/proj-nestcheck`). For a second opinion, tag a senior associate on the project.
3. **Reviewers respond within 24 hours.** If you're assigned as a reviewer, make time to review promptly.
4. **Address all feedback.** Make the requested changes, push new commits, and re-request a review.
5. **Merge after approval.** Once you have the required approval and checks pass, merge your branch following the [branching guidelines](/standards/branching.md).

## Who Approves What

| Pull Request | Approved by |
|---|---|
| Task branch → `development` | 1 teammate on the project |
| Changes to sensitive paths (CI, deploy, infra, secret-scan config) | `@BizzNEST/admins`, in addition to the teammate |
| `development` → `staging` | Someone in `@BizzNEST/leads` |
| `development`, `staging` or `hotfix-` branch → `main` | `@BizzNEST/admins` |

On project repos GitHub enforces this:

- Pushing new commits resets approvals, so re-request review after your last push.
- The `scan / betterleaks` secret scan must pass. See [Secrets Management](/security/secrets-management.md).
- Sensitive paths are listed in each repo's `.github/CODEOWNERS`, and GitHub requests the right reviewers automatically.
- Nobody can push directly to `development`, `staging` or `main`.

## What Reviewers Look For

Use this checklist when reviewing someone's code:

- [ ] Code does what the linked issue describes
- [ ] Variable and function names are clear and descriptive
- [ ] No `console.log` statements left in the code
- [ ] No hardcoded values that should be in environment variables
- [ ] No secrets in the diff, including in test data, comments or `.env.example`
- [ ] Follows the project's existing code style and patterns
- [ ] Commit messages follow the [commit conventions](/standards/commits.md)
- [ ] Branch name follows the [branching naming convention](/standards/branching.md)
- [ ] No commented-out code left behind
- [ ] Changes are tested and working

## Giving Good Feedback

- Be specific — say **what** needs to change and **why**.
- Suggest alternatives instead of just saying "this is wrong."
- Use GitHub's **suggestion** feature to propose exact code changes.
- Keep it constructive and professional.
- Prefix optional suggestions with "nit:" so the author knows it's not blocking.

## Receiving Feedback

- Don't take feedback personally — reviews are about the code, not you.
- Ask clarifying questions if you don't understand a comment.
- Treat every review as a learning opportunity.
- Thank your reviewers — they're spending their time to help improve your work.
