# /obsidian — Connect Obsidian to your AIOS

> Turns your AIOS folder into a full Obsidian vault with AI superpowers.

## Rules

- Explain what you're doing BEFORE doing it
- Wait for confirmation before each step
- If something breaks — explain simply and fix it
- Assume the user is NOT technical

---

## PRE-CHECK: Module availability

Before anything, check if the module has been published:

```bash
curl -sf "https://raw.githubusercontent.com/Ban-Enterprises/aios-modules/main/obsidian/manifest.json" -o /dev/null
```

**If curl fails (404 or connection error):**

Print:
```
═══════════════════════════════════════

  OBSIDIAN MODULE

  Status: Coming soon

  This module is being prepared.
  You'll be notified when it's ready.

  In the meantime, you can already
  open this folder in Obsidian manually:

  1. Download Obsidian from obsidian.md
  2. Open → "Open folder as vault"
  3. Point to this AIOS folder

  That's it — you'll see all your
  .context/ files in Obsidian.

═══════════════════════════════════════
```

**STOP — do not continue.**

---

**If curl succeeds (module is live):**

Download the manifest:
```bash
MANIFEST=$(curl -sf "https://raw.githubusercontent.com/Ban-Enterprises/aios-modules/main/obsidian/manifest.json")
```

Read the version and file list from manifest, then proceed:

---

## STEP 1: INSTALL OBSIDIAN

Print:
```
═══════════════════════════════════════
  OBSIDIAN MODULE — Step 1/4: Install
═══════════════════════════════════════
```

Check if Obsidian is installed:
- Mac: `ls /Applications/Obsidian.app`
- If not: `brew install --cask obsidian`
- If brew fails: "Download from obsidian.md"

**STOP — wait for confirmation.**

---

## STEP 2: CONFIGURE VAULT

Print:
```
═══════════════════════════════════════
  OBSIDIAN MODULE — Step 2/4: Vault
═══════════════════════════════════════
```

Say: "I'm going to configure this folder as an Obsidian vault. This means you'll be able to browse your AIOS files visually."

1. Create `.obsidian/` config directory (if not exists)

2. Write `.obsidian/app.json`:
```json
{
  "showHiddenFolders": true,
  "newFileLocation": "folder",
  "newFileFolderPath": "outputs",
  "attachmentFolderPath": ".obsidian/attachments"
}
```

3. Enable Daily Notes — write `.obsidian/daily-notes.json`:
```json
{
  "folder": "dziennik",
  "format": "YYYY-MM-DD",
  "template": ""
}
```

4. Create `dziennik/` folder

5. Add to `.gitignore` (if not already there):
```
.obsidian/
dziennik/
```

Say: "Vault configured. Hidden folders are visible, daily notes go to dziennik/."

**STOP — wait for confirmation.**

---

## STEP 3: INSTALL SKILLS

Print:
```
═══════════════════════════════════════
  OBSIDIAN MODULE — Step 3/4: Skills
═══════════════════════════════════════
```

Say: "Now I'm installing Obsidian skills — these teach me how to work with Obsidian's special formats like wikilinks, callouts, and canvas files."

Download skills from the module repo:

```bash
# Download each skill from the manifest file list
BASE_URL="https://raw.githubusercontent.com/Ban-Enterprises/aios-modules/main/obsidian"

# Core skills (always installed)
mkdir -p .claude/skills/obsidian-markdown/references
curl -sf "$BASE_URL/skills/obsidian-markdown/SKILL.md" -o .claude/skills/obsidian-markdown/SKILL.md
curl -sf "$BASE_URL/skills/obsidian-markdown/references/CALLOUTS.md" -o .claude/skills/obsidian-markdown/references/CALLOUTS.md
curl -sf "$BASE_URL/skills/obsidian-markdown/references/EMBEDS.md" -o .claude/skills/obsidian-markdown/references/EMBEDS.md
curl -sf "$BASE_URL/skills/obsidian-markdown/references/PROPERTIES.md" -o .claude/skills/obsidian-markdown/references/PROPERTIES.md

mkdir -p .claude/skills/obsidian-cli
curl -sf "$BASE_URL/skills/obsidian-cli/SKILL.md" -o .claude/skills/obsidian-cli/SKILL.md

mkdir -p .claude/skills/defuddle
curl -sf "$BASE_URL/skills/defuddle/SKILL.md" -o .claude/skills/defuddle/SKILL.md
```

Verify each file was downloaded (not empty, not 404 HTML).

Say: "3 skills installed: obsidian-markdown, obsidian-cli, defuddle."

**STOP — wait for confirmation.**

---

## STEP 4: LAUNCH AND TEST

Print:
```
═══════════════════════════════════════
  OBSIDIAN MODULE — Step 4/4: Test
═══════════════════════════════════════
```

1. Open Obsidian: `open -a Obsidian`
2. Wait 3 seconds
3. Check vault exists: `ls .obsidian/workspace.json`

If vault is working, create a test note to verify skills:

Write `outputs/obsidian-test.md`:
```markdown
# Obsidian + AIOS Test

This note was created by your AI assistant.

## Links work
- [[.context/ROOT.md|Your profile]]
- [[.context/SESSION-STATE.md|Last session]]

## Callouts work
> [!tip] Your AIOS is connected to Obsidian
> You can now browse all your context files visually.

## Tags work
#aios #obsidian #setup-complete
```

Print:
```
═══════════════════════════════════════

  Obsidian module installed!

  What changed:
  - Your AIOS folder is now an Obsidian vault
  - Hidden folders (.context, .claude, .agents) are visible
  - Daily notes go to dziennik/
  - 3 AI skills installed (markdown, CLI, web clipping)

  Try it:
  - Open Obsidian — browse your files
  - Cmd+P → "Open today's daily note"
  - Ask me to create a note with [[wikilinks]]

  New commands available:
  - "Create a daily note"
  - "Clip this webpage to Obsidian"
  - "Search my vault for..."

═══════════════════════════════════════
```
