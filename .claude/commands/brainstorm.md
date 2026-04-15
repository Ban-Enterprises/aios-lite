# Brainstorm

> Think through any topic — strategically, specifically, from the perspective of your situation.

## Variables

topic: $ARGUMENTS

---

## Instructions

You're running a brainstorm. Don't generate generic advice — think in the context of the user.

**Output:** Save to `outputs/brainstorm-YYYY-MM-DD-{topic}.md`

---

## Stage 1: CONTEXT

1. Read .context/ROOT.md
2. Read relevant files from .context/domains/ if the topic requires it
3. Restate the question in your own words and ask: "Is this what you mean?"

**STOP — wait for confirmation.**

---

## Stage 2: ANALYSIS

Think through the topic from multiple angles:
- **Current state** — what we know from context
- **Opportunities** — what can be done, what's underexplored
- **Risks** — what could go wrong
- **Constraints** — time, money, skills
- **Examples** — how others have solved this

Be specific. Generic observations are useless.

**STOP — present findings, discuss.**

---

## Stage 3: OPTIONS

Propose 3-5 options. For each:
- What exactly it means
- Pros and cons
- How much effort it requires
- How it fits current priorities

Give a recommendation with reasoning.

**STOP — discuss, iterate.**

---

## Stage 4: SAVE

Save to `outputs/brainstorm-YYYY-MM-DD-{topic}.md`:

```markdown
# Brainstorm: {Topic}

**Date:** YYYY-MM-DD
**Question:** {the strategic question}

## Summary
{3-5 sentences: what we explored, what emerged, what conclusion}

## Context
{Facts from context files}

## Key insights
{3-5 numbered — fact + what it means}

## Options

### Option A: {Name}
- **What:** description
- **For:** arguments
- **Against:** risks
- **Effort:** estimate

### Option B: {Name}
[...]

## Recommendation
{What I recommend and why}

## Next steps
{Specific actions}
```
