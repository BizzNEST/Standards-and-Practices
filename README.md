# BizzNEST Standards and Practices

## Purpose of this Repository

- Establish and maintain high standards for BizzNEST projects.
- Provide a central repository for team members to share knowledge and best practices.
- Serve as a reference point for starting new projects or addressing common questions.

[Click Here](/standards/contributing.md) to contribute!

## Code of Conduct

1. Maintain professionalism in all communications.
2. Keep requests and issues relevant to the work at BizzNEST.
3. Treat everyone with respect—no exceptions.
4. Collaborate, have fun, and share your knowledge!


#### Git

- **Workflow**: Follow the [Gitflow](https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow) workflow:
  - Maintain `main` and `development` branches.
  - Branch off `development` for new features.
  - Request code reviews for your Pull Requests to `development`.
  - Merge reviewed code into `development`.
  - For milestone completion, create a `release` branch from `development`, QA it, then merge into `main` (tag it) and back into `development`.
  - For hotfixes, branch off `main`, fix the issue, then merge back into `main` (tag it) and `development`.
  - ![Gitflow diagram](https://nvie.com/img/git-model@2x.png) Credit: <https://nvie.com/posts/a-successful-git-branching-model/>
- [Branching](/standards/branching.md) at BizzNEST
- [Commit Messages](/standards/commits.md) at BizzNEST

#### Code Versioning

- [BizzNEST SemVer](/standards/code-versioning.md)

#### Project Setup

- [Using GitHub Projects](/standards/project-setup.md) to track progress.
- [Readme Guidelines](/standards/readme-guidelines.md) for project documentation.
- [EditorConfig](/best-practices/development-tools/editorconfig.md) for consistent code style.

#### Code Review

- [Code Review](/standards/code-reviews.md#process) process at BizzNEST:
  - [Code Review Slides](https://docs.google.com/presentation/d/16S4qMbwdBT2u9c3-djHhSRXoUUytf12HGxloWh4y4cE/edit#slide=id.g35f391192_00)
- [Acceptance Testing](/standards/acceptance-testing.md)
- [Bug Reporting](/standards/bug-reporting.md)

#### Machine Setup

##### Mac: Install

- [Homebrew](https://brew.sh/)
- [nvm](https://www.wdiaz.org/how-to-install-nvm-with-homebrew/)
- Either [Visual Studio Code](https://code.visualstudio.com/download) or your preferred code editor.
- Install the regular version of Visual Studio (Community Edition or higher) if required by your project.

#### Account Setup

You will need to schedule time with a team lead to gain access to the following:

- WPE (Wordpress Engine)
- AWS (Amazon Web Services - Coming Soon)
- GitHub Organization (should be here if your look at this ;))

##### BizzNEST Project and Team Meetings

- **Weekly Project Meetings**: Held every week to discuss project-specific progress, blockers, and next steps.
- **Monthly All-Team Meetings**: Once a month, all team members gather to share accomplishments, discuss workflows, and address any team-wide issues.

## Need Help?

Getting stuck happens to the best of us. If you're blocked for more than 45 minutes, here's where you can get help:

##### Problem Solving

- [Problem Solving Guide](standards/problem-solving.md)

##### Communication Channels

1. **Your team channel**: Post questions in your private team channel. Your lead may help you through blockers.

#### Problem Solving

Before reaching out, attempt to resolve issues on your own. Here's a resource to improve your problem-solving skills:

- [How to Think Like a Programmer](https://www.freecodecamp.org/news/how-to-think-like-a-programmer-lessons-in-problem-solving-d1d8bf1de7d2/)

## Contributing to BizzNEST

Contributions to our processes are expected. You can contribute in many ways, such as leading a BizzNEST Developer Connect meeting, writing a markdown sheet on a topic you're passionate about, leading a workshop, or posting in BizzNEST's technical discussions channel.

[Click Here](/standards/contributing.md) to start contributing.
