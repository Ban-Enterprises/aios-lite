# Commit — Save changes

> Save current changes to git. Local only — nothing goes public.

---

## Instructions

### 1. See what changed
```bash
git status
git diff HEAD
```

### 2. Stage files
Add specific files by name. NEVER use `git add -A`.

**Never stage:** `.env`, `credentials/`

### 3. Commit
```bash
git commit -m "$(cat <<'EOF'
<change description>

Co-Authored-By: Claude <noreply@anthropic.com>
EOF
)"
```

### 4. Confirm
```bash
git status
```

Print: what was committed, which branch.

### Rules
- Never push — local commit only
- Never commit files with passwords
- New commit every time (no amend)
