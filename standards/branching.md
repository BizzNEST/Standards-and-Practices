### Branch Structure

```
Main
L- Staging
L- Development
   L- *Feature Branch*
   L- *Bug fix branch*
```

**Main** branch is for finalized, tested, and production-ready code. It is the default branch, and on many projects merging into it deploys to production.

**Staging** branch is for finalized, tested, and demo-ready code. It is optional: projects without client demos go straight from `development` to `main`.

Working branch will be **development**. Pushes to development require a Pull Request and review. GitHub pre-selects `main` when you open a PR, so change the base branch to `development`.

Sub-branches of development will be used to isolate tasks that are being worked on. These are for new features, fixes, or other tasks.

Create feature/fix/task branches to perform your work in.
Keep to the standard `<initials>-<issue#>-<small-description>`.
Where:

- `<initials>` are your initials. This helps everyone keep track of who owns branches easily.
- `<issue#>` is the GitHub issue number this branch relates to.
- `<small-description>` is a small description usually no more than 3 words.

For example, if I'm (Alex) working on an bug fix task, I'll create a branch such as `ar-111-fix-uploader`.

When work is completed and tested, make a Pull Request to the development branch. This PR requires approval from a teammate on the project before it is merged. See [Code Reviews](code-reviews.md).

When code is ready to be locked in for demo, a Pull Request from `development` to `staging` will be created and approved by someone in `@BizzNEST/leads`.

When code is ready to be deployed, a Pull Request from `development` (or `staging`) to `main` will be created and approved by Eli Manzo or Alex Rodriguez.

### Hotfixes

Urgent production fixes are the one exception to branching off `development`:

1. Branch off `main`: `hotfix-<initials>-<issue#>-<small-description>` (e.g. `hotfix-ar-140-login`).
2. Open a Pull Request into `main`, approved by Eli Manzo or Alex Rodriguez.
3. Open a second Pull Request bringing the same fix into `development`, so it isn't lost on the next release.

On project repos, GitHub only accepts PRs into `staging` from `development`, and into `main` from `development`, `staging` or a `hotfix-` branch.

### Doing Development

- Always have an issue created for any work you are doing. It should contain:
  - Description of work to be done
  - Labels to categorize what type of task it is
- Make sure to include your new task on the project board in the correct column

### Bug Fixing

- If fixing a bug or issue reference the issue in the branch ex: `git checkout -b ar-111-fix-uploader`
- Also, include the issue number in the commit message to link to the issue ex: `git commit -m "type(scope):body. resolves #1"`


### Finishing a task

- If testing is complete, all issues fixed, move the task to "Done" and close the issue

### Git Commands

- To clone a repository from GitHub onto your local machine
  - `git clone https://github.com/bizznest/standards-and-practices`
- Add all changes to be tracked:
  - `git add .`
- Commit tracked changes:
  - `git commit -m "type(scope):body"`
  - [Follow commit conventions found at this link](commits.md)
- Push changes up to GitHub
  - `git push`

Get the latest changes:

- Check out development  
   `git checkout development`
- Pull from development  
   `git pull`
- Change to my branch  
   `git checkout your-branch-name`
- Merge from development  
   `git merge development`
