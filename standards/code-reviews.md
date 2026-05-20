# Code Review at BizzNEST

## Why Code Reviews Matter

Code reviews help us catch bugs before they reach production, share knowledge across the team, and keep our codebase clean and consistent. Every Pull Request goes through a review — no exceptions.

## Process

1. **Open a Pull Request.** Follow the [PR template](/.github/pull_request_template.md) and fill out every section.
2. **Assign at least two reviewers.** One reviewer must be a team lead or admin.
3. **Reviewers respond within 24 hours.** If you're assigned as a reviewer, make time to review promptly.
4. **Address all feedback.** Make the requested changes, push new commits, and re-request a review.
5. **Merge after approval.** Once you have the required approvals, merge your branch following the [branching guidelines](/standards/branching.md).

## What Reviewers Look For

Use this checklist when reviewing someone's code:

- [ ] Code does what the linked issue describes
- [ ] Variable and function names are clear and descriptive
- [ ] No `console.log` statements left in the code
- [ ] No hardcoded values that should be in environment variables
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
