---
description: Analyze repo and suggest improvements, create GitHub issues
allowed-tools: Bash(git:*), Bash(gh:*), Bash(pnpm:*), Read, Grep, Glob, AskUserQuestion, Task
---

# Suggest

Analyze the repository and suggest improvements, features, and maintenance tasks.

## Workflow

You MUST use ultrathink for all analysis in this command.

### 1. Codebase Analysis
Thoroughly analyze the repository:
- Read key configuration files (package.json, tsconfig, etc.)
- Understand the project structure
- Review recent commits and changes
- Check for existing issues and PRs

### 2. Categories to Evaluate

#### Code Quality
- Missing or inadequate tests
- Code duplication that could be refactored
- Inconsistent patterns or styles
- Outdated dependencies
- Security vulnerabilities (npm audit)

#### Developer Experience
- Missing or outdated documentation
- CI/CD improvements
- Development workflow enhancements
- Better error messages or logging
- Type safety improvements

#### Performance
- Obvious performance issues
- Missing caching opportunities
- Database query optimization
- Bundle size improvements

#### Features
- TODO comments in code
- Incomplete implementations
- Natural feature extensions
- User-requested features (from issues)

### 3. Prioritize Suggestions
For each suggestion, assess:
- **Impact**: How much value does it add?
- **Effort**: How much work is required?
- **Risk**: What could go wrong?
- **Dependencies**: What needs to happen first?

Categorize as:
- 🔴 **P0 - Critical**: Should be done ASAP
- 🟠 **P1 - High**: Important for next sprint
- 🟡 **P2 - Medium**: Nice to have
- 🟢 **P3 - Low**: Future consideration

### 4. Present Findings
Display suggestions in a clear format:

```
## Suggestions for <repo-name>

### 🔴 Critical (P0)
1. **<Title>**: <Description>
   - Impact: High | Effort: Low | Risk: Low
   - Files affected: ...

### 🟠 High Priority (P1)
...
```

### 5. Create Issues
Use AskUserQuestion with multiSelect to let the user choose which suggestions to create as GitHub issues.

For each selected suggestion:
- Use tabs/questions to refine the implementation details
- Create a well-structured GitHub issue with:
  - Clear description
  - Acceptance criteria
  - Implementation hints
  - Estimated size (XS/S/M/L/XL)
- Add to the project board with appropriate priority

### 6. Summary
Report:
- Number of suggestions found
- Issues created
- Recommended next steps
