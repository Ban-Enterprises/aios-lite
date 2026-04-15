# /aios-update — Check for AIOS updates

> Checks the remote repo for new commands, skills, and framework updates. Never touches your data.

## Rules

- NEVER modify anything in .context/, outputs/, plans/, docs/, dziennik/, .obsidian/
- Only update framework files (commands, skills, CLAUDE.md, .agents/)
- Show what changed BEFORE applying
- Ask for confirmation before updating
- Keep a backup of any file being replaced

---

## STEP 1: CHECK VERSION

Print:
```
═══════════════════════════════════════
  AIOS UPDATE — Checking for updates
═══════════════════════════════════════
```

Check current local version:
```bash
LOCAL_VERSION="unknown"
if [ -f manifest.json ]; then
  LOCAL_VERSION=$(python3 -c "import json; print(json.load(open('manifest.json'))['version'])" 2>/dev/null || echo "unknown")
fi
echo "Local version: $LOCAL_VERSION"
```

Fetch remote manifest:
```bash
REMOTE_MANIFEST=$(curl -sf "https://raw.githubusercontent.com/Ban-Enterprises/aios-lite/main/manifest.json")
```

If curl fails:
- Print: "Could not reach update server. Check your internet connection."
- **STOP**

Parse remote version:
```bash
REMOTE_VERSION=$(echo "$REMOTE_MANIFEST" | python3 -c "import sys,json; print(json.load(sys.stdin)['version'])")
REMOTE_CHANGELOG=$(echo "$REMOTE_MANIFEST" | python3 -c "import sys,json; print(json.load(sys.stdin)['changelog'])")
```

Compare versions:
- If LOCAL_VERSION == REMOTE_VERSION: Print "You're up to date! (v$LOCAL_VERSION)" → **STOP**
- If different: Continue

---

## STEP 2: SHOW CHANGES

Print:
```
═══════════════════════════════════════
  Update available: v{LOCAL} → v{REMOTE}
═══════════════════════════════════════

  What's new: {REMOTE_CHANGELOG}
```

Download the remote file list from manifest and compare with local files.

For each file in `framework_files`:
1. Fetch remote file content
2. Compare with local file (if exists)
3. Classify as: NEW (doesn't exist locally), UPDATED (content differs), UNCHANGED

Print a summary table:

```
  Files to update:

  NEW      .claude/commands/obsidian.md
  UPDATED  CLAUDE.md
  UPDATED  .claude/commands/status.md
  —        .claude/commands/prime.md (unchanged)

  Your data is SAFE:
  .context/  outputs/  plans/  — NOT touched
```

Ask: "Apply update? (yes/no)"

**STOP — wait for confirmation.**

---

## STEP 3: APPLY UPDATE

Print:
```
═══════════════════════════════════════
  AIOS UPDATE — Applying v{REMOTE}
═══════════════════════════════════════
```

For each file marked NEW or UPDATED:

1. If file exists locally and is UPDATED:
   - Create backup: `cp file file.backup-{date}`
   - Download new version: `curl -sf URL -o file`

2. If file is NEW:
   - Create directories if needed: `mkdir -p $(dirname file)`
   - Download: `curl -sf URL -o file`

3. Update local manifest:
   - Download new manifest.json

After all files:
```bash
# Clean up backups older than 7 days
find . -name "*.backup-*" -mtime +7 -delete 2>/dev/null
```

---

## STEP 4: CONFIRM

Print:
```
═══════════════════════════════════════

  AIOS updated to v{REMOTE_VERSION}!

  What changed:
  {list of NEW and UPDATED files}

  Backups saved as .backup-{date}

  Your data was NOT touched:
  .context/  outputs/  plans/  docs/

═══════════════════════════════════════
```

If any commands were added, show them:
```
  New commands available:
  /obsidian  — Connect Obsidian to your AIOS
```
