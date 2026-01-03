# GitHub Auth

Ensure the GitHub CLI is properly authenticated with all required scopes.

## Workflow

### 1. Check Current Auth Status
```bash
gh auth status
```

### 2. Required Scopes
The following scopes are needed for full functionality:
- `repo` - Full repository access
- `read:org` - Read organization membership
- `project` - Full project access (for project boards)
- `read:project` - Read project access

### 3. Check Missing Scopes
Parse the current scopes and identify any missing ones.

### 4. Refresh Auth (if needed)
If scopes are missing:
```bash
gh auth refresh -s repo -s read:org -s project -s read:project
```

This will open a browser for re-authentication.

### 5. Verify SSH (Optional)
Check if SSH is configured for Git operations:
```bash
gh auth status
```

If using HTTPS, suggest switching to SSH:
```bash
gh auth setup-git
```

### 6. Test Access
Verify access works:
```bash
gh repo view --json name
gh project list --owner <owner>
```

### 7. Summary
Report:
- Authentication status
- Available scopes
- Git protocol (SSH/HTTPS)
- Any issues that need manual resolution

## Troubleshooting
If authentication fails:
1. Try `gh auth login` for fresh authentication
2. Ensure you have access to the organization
3. Check if SSO is required for the organization
