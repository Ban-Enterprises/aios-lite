# /install-aios — Set up your AIOS

> Step by step. No rushing. Every step is a conversation.

## Rules

- Explain what you're doing BEFORE doing it
- Wait for confirmation before moving to the next step
- If something breaks — explain in plain English and fix it
- Assume the user is NOT technical

---

## STEP 1: ORIENTATION

Print:
```
═══════════════════════════════════════
  AIOS LITE — Step 1/4: Orientation
═══════════════════════════════════════
```

Explain in 3 sentences:
1. This folder is your workspace — Claude reads it and knows what's going on
2. Files in .context/ are your "memory" for AI — we'll fill them in now
3. After setup, every session starts with Claude already knowing who you are and what you're working on

Show the folder structure. Explain each folder in one sentence.

Say: "Ready? This will take about 15-20 minutes. Type 'go' when you're ready."

**STOP — wait for confirmation.**

---

## STEP 2: WHO ARE YOU

Print:
```
═══════════════════════════════════════
  AIOS LITE — Step 2/4: Who are you
═══════════════════════════════════════
```

Say: "Now I'm going to learn who you are and what you do. Answer however you like — short or detailed. There are no wrong answers."

Ask ONE at a time. Wait for each answer:

1. "What's your name and how old are you?"
2. "What do you do? What does your day-to-day look like — work, school, projects?"
3. "What projects or activities are you currently working on?"
4. "What tools do you use? (e.g. Canva, Notion, Instagram, Excel...)"
5. "What's your main priority right now — what do you want to get done soon?"
6. "What takes up most of your time or frustrates you the most?"

After collecting answers, fill in:
- `.context/ROOT.md` — personal info, priority, projects
- `.context/domains/projects.md` — project details
- `.context/domains/tools.md` — tool list

Read back what you wrote. Ask: "Does this accurately capture your situation? Anything to fix?"

Fix if needed.

**STOP — wait for confirmation.**

---

## STEP 3: INFRASTRUCTURE

Print:
```
═══════════════════════════════════════
  AIOS LITE — Step 3/4: Git
═══════════════════════════════════════
```

Say: "Now I'm setting up git — a system that tracks all changes to your files. This means you can always go back to an earlier version."

1. Check: `git --version`
   - If missing on Mac: "You need to install git. On Mac, type: `brew install git`"
   - If missing on Windows: "Download from git-scm.com"
2. `git init && git branch -M main`
3. Create `.gitignore` with:
   ```
   .env
   .env.*
   credentials/
   node_modules/
   .DS_Store
   ```
4. First commit:
   ```bash
   git add CLAUDE.md .context/ .claude/ .gitignore
   git commit -m "init: AIOS Lite workspace ready"
   ```

Say: "Git is ready. Your files are now version-controlled. Every change is tracked."

**STOP — wait for confirmation.**

---

## STEP 4: TEST

Print:
```
═══════════════════════════════════════
  AIOS LITE — Step 4/4: Test
═══════════════════════════════════════
```

Check:
- [ ] ROOT.md — exists and filled in
- [ ] SESSION-STATE.md — exists
- [ ] domains/projects.md — exists and filled in
- [ ] domains/tools.md — exists and filled in
- [ ] git works (`git status` is clean)

Run `/prime` — check if the summary is accurate.

Fix anything that doesn't work.

Print:
```
═══════════════════════════════════════

  Your AIOS Lite is ready!

  What now:

  /prime       — Start every session
  /brainstorm  — Think through any topic
  /plan        — Plan something before doing it
  /research    — Search for information
  /status      — Quick overview
  /end-session — Close session

  Every session:
  1. Launch Claude Code
  2. /prime
  3. Work
  4. /end-session

═══════════════════════════════════════
```
