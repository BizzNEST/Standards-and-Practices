# Issue Documentation Guidelines

This document provides comprehensive guidance on how to create and fill out GitHub issues effectively within the BizzNEST repositiories

## Issue Template Structure

All issues should follow this standardized template to ensure consistency and clarity:

```markdown
## Desired Feature
[Describe the feature, enhancement, or improvement you want to see implemented]

## Actual/Current Behavior
[Describe what currently happens or what the current state is]

## Steps to Implement
[Outline the specific steps needed to implement the desired feature]

## Additional Context
[Any additional information, screenshots, links, or context that might be helpful]
```

## Field Explanations

### Desired Feature
**Purpose**: Clearly articulate what you want to achieve or what functionality you're requesting.

**Guidelines**:
- Be specific and descriptive
- Focus on the end goal or outcome
- Avoid technical implementation details (save those for Steps to Implement)
- Use clear, concise language
- If applicable, mention the user story or business value

**Example**:
```
Add a search functionality to the documentation page that allows users to quickly find relevant content by keywords or phrases.
```

### Actual/Current Behavior
**Purpose**: Document the current state or behavior that needs to be changed or improved.

**Guidelines**:
- Describe what currently exists or happens
- Be objective and factual
- Include any relevant error messages or unexpected behaviors
- If this is a new feature request, describe the current workaround or lack of functionality

**Example**:
```
Currently, users must manually scroll through all documentation pages to find specific information. There is no search capability available.
```

### Steps to Implement
**Purpose**: Provide a clear roadmap for how the feature should be implemented.

**Guidelines**:
- Break down the implementation into logical, sequential steps
- Include technical considerations and requirements
- Reference any existing code or systems that need to be modified
- Consider dependencies and prerequisites
- Be specific enough to guide development but flexible enough to allow for technical decisions

**Example**:
```
1. Research and select an appropriate search library (e.g., Algolia, Elasticsearch, or client-side search)
2. Design the search UI component with input field and results display
3. Implement search functionality in the documentation system
4. Add search result highlighting and relevance scoring
5. Test search functionality across different content types
6. Update documentation to include search feature instructions
```

### Additional Context
**Purpose**: Provide supplementary information that helps clarify the issue or implementation approach.

**Guidelines**:
- Include screenshots, mockups, or wireframes if applicable
- Reference related issues, pull requests, or discussions
- Link to external resources, documentation, or examples
- Mention any constraints, limitations, or special considerations
- Include user feedback or requirements if available

**Example**:
```
Related Issues: #123, #456
Design Mockup: [Link to Figma/Design file]
User Feedback: "Users frequently ask about search functionality in support tickets"
Technical Constraints: Must work with existing static site generation setup
```

## Issue Types and Categories

### Feature Requests
- Use when requesting new functionality or enhancements
- Focus on user value and business impact
- Include user stories when possible

### Bug Reports
- Clearly describe the unexpected behavior
- Include steps to reproduce
- Specify environment details (browser, OS, etc.)
- Include error messages or logs

### Documentation Requests
- Specify what documentation is missing or unclear
- Include target audience and use case
- Reference existing documentation that needs updates

### Process Improvements
- Describe current process pain points
- Propose specific improvements
- Include impact on team workflow

## Best Practices

### Writing Clear Issues
1. **Use descriptive titles**: Make the issue title clear and specific
2. **Be concise but complete**: Provide enough detail without being verbose
3. **Use markdown formatting**: Structure content with headers, lists, and code blocks
4. **Include examples**: Provide concrete examples when possible
5. **Reference existing work**: Link to related issues, PRs, or documentation

### Issue Management
1. **Assign appropriate labels**: Use labels to categorize and prioritize issues
2. **Set milestones**: Group related issues into milestones for better project management
3. **Assign to team members**: Assign issues to the appropriate person or team
4. **Update status**: Keep issues updated as work progresses

### Collaboration
1. **Respond to comments**: Engage in discussions and provide clarifications
2. **Update with progress**: Comment on issues as work progresses
3. **Close when complete**: Close issues when the work is finished and tested
4. **Link to PRs**: Reference pull requests that address the issue

## Issue Labels

Use these standard labels to categorize issues:

- **bug**: Something isn't working as expected
- **enhancement**: New feature or request
- **documentation**: Improvements or additions to documentation
- **good first issue**: Good for newcomers
- **help wanted**: Extra attention is needed
- **priority: high/medium/low**: Issue priority level
- **status: in progress**: Work has started
- **status: blocked**: Waiting for something else
- **status: ready for review**: Ready for team review

## Example Issues

### Feature Request Example
```markdown
## Desired Feature
Add dark mode toggle to the documentation site to improve readability in low-light environments.

## Actual/Current Behavior
The documentation site only supports light mode, which can be difficult to read in dark environments or for users with light sensitivity.

## Steps to Implement
1. Design dark mode color scheme that maintains accessibility standards
2. Implement CSS variables for theme switching
3. Add theme toggle button in the site header
4. Implement theme persistence using localStorage
5. Test dark mode across all documentation pages
6. Update documentation to mention the new feature

## Additional Context
- Accessibility requirements: Must maintain WCAG 2.1 AA compliance
- Browser support: Must work in all modern browsers
- Related issue: #789 (accessibility improvements)
- Design inspiration: [Link to design system]
```

### Bug Report Example
```markdown
## Desired Feature
Fix the broken link in the contributing guidelines that leads to a 404 error.

## Actual/Current Behavior
The link to "BizzNEST's guideline" in the contributing.md file returns a 404 error when clicked.

## Steps to Implement
1. Identify the correct path for the branching guidelines
2. Update the link in contributing.md to point to the correct location
3. Test the link to ensure it works properly
4. Check for any other broken links in the documentation

## Additional Context
- File: standards/contributing.md, line 3
- Current broken link: `/standards/branching.md`
- Correct path appears to be: `standards/branching.md`
- Browser: Chrome 120.0.6099.109
- OS: macOS 14.0
```

## Conclusion

Following these guidelines ensures that issues are clear, actionable, and provide the necessary context for successful implementation. Well-written issues lead to better collaboration, faster resolution, and higher quality outcomes.

Remember: The goal is to make it as easy as possible for developers to understand what needs to be done and why it's important.
