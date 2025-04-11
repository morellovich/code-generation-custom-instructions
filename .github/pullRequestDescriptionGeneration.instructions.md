## Pull Request Description Instructions

Always generate structured, comprehensive pull request descriptions that follow this format:

### Title Format

- Use the format: `[Type] Short description of changes`
- Types include: `Feature`, `Fix`, `Refactor`, `Docs`, `Test`, `Perf`, `Security`
- Keep titles concise (under 72 characters) and descriptive
- Example: `[Feature] Add user authentication with OAuth providers`

### Description Sections

#### 1. Overview

- Provide a clear, concise summary of what this PR accomplishes
- Explain the business value or problem being solved
- Reference related issues with `Closes #123` or `Relates to #123`

#### 2. Changes Made

- List major changes as bullet points
- Group related changes together
- Include both code and non-code changes (documentation, configuration)
- Highlight any architecture decisions or pattern changes

#### 3. Technical Details

- Explain any complex implementations or algorithms
- Describe database schema changes if applicable
- Detail any API changes with examples
- Note any performance considerations

#### 4. Testing Completed

- List all tests added or modified
- Describe manual testing performed
- Include screenshots for UI changes
- Report performance test results if applicable
- Mention browser/device testing coverage

#### 5. Security Considerations

- Describe security implications of changes
- Confirm proper input validation and sanitization
- Verify authentication and authorization checks
- Ensure sensitive data handling follows best practices
- Confirm API rate limiting where applicable

#### 6. Deployment Notes

- List environment variables added or changed
- Note any migration steps required
- Describe potential downtime or backward compatibility issues
- Include rollback instructions if complex

#### 7. Additional Notes

- Document known limitations or technical debt
- Mention future work that builds on these changes
- Include any resources that helped solve complex problems

### Style Guidelines

- Use clear, professional language
- Avoid jargon unless necessary for technical accuracy
- Include code snippets when helpful, formatted with proper markdown
- Use screenshots for visual changes
- Keep the entire description focused and scannable

### Example Template
