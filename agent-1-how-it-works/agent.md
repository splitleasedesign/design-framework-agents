# Agent 1 — How it Works
**Automates:** Flow mapping, process audits, goal-directed redesign
**Compound Pattern:** Plan-Act-Verify Loop
**Eval Target:** All steps goal-justified + error recovery documented

---

## What This Agent Does

Takes a **feature, page, or user journey** as input and autonomously:
1. Maps the complete flow (every step, decision, branch)
2. Identifies waste (steps that serve the system, not the user)
3. Designs the minimum viable path to goal completion
4. Documents error recovery for every failure point
5. Validates against eval criteria
6. Iterates until all criteria pass

This is a **compound action** — one prompt expands into many dependent steps. The agent self-extends until the eval target is met.

---

## Compound Action: Plan-Act-Verify

```
PLAN
├── Read prompt.md → identify feature/page/journey
├── Read current flow (screenshots, code, docs)
├── Identify user goal + business goal
│
ACT
├── Step 1: Map current flow (every step, decision, branch)
├── Step 2: For each step → "Does this serve the user's goal?"
├── Step 3: Eliminate steps that serve only the system
├── Step 4: Design minimum viable flow
├── Step 5: Document error recovery for every failure point
├── Step 6: Document edge cases (first-time, power user, mobile, error)
│
EVAL
├── Run eval criteria checklist
├── PASS? → Save files, update memory, done
└── FAIL? → Identify which criteria failed → fix → re-run eval (max 3x)
```

---

## Eval Criteria (Self-Check)

The agent runs this checklist against its own output. **All must pass.**

- [ ] User goal is explicitly stated
- [ ] Business goal is explicitly stated
- [ ] Current flow is fully mapped (no missing steps)
- [ ] Every step in proposed flow is justified against the user goal
- [ ] Steps eliminated are documented with reasons
- [ ] Error states are documented for every failure point
- [ ] Edge cases covered: first-time user, power user, mobile, error recovery
- [ ] A first-time user can complete the flow in one session
- [ ] Entry and exit points are clear
- [ ] Output files are saved to assets/

**If any criterion fails:** diagnose which one, fix it, re-run the checklist. Max 3 retries.

---

## Token Budgets

| Task Type | Budget | Expected Runtime |
|-----------|--------|-----------------|
| Flow audit (single feature) | 0.5M | ~15 min |
| Journey map (full user type) | 1.5M | ~45 min |
| Process redesign (with alternatives) | 2M | ~1 hr |
| Multi-flow analysis | 3M | ~2 hr |
| Full platform flow review (all pages) | 5M | ~4 hr (overnight) |

---

## Concrete Outputs

Every run produces these files in `assets/[YYYY-MM-DD]-[project]/`:

```
reports/
├── flow-map-[feature].md          ← Every step, decision, branch
├── goal-analysis-[feature].md     ← User goal, business goal, persona, context
├── proposed-flow-[feature].md     ← Simplified goal-directed flow
├── steps-eliminated.md            ← What was cut and why
└── error-recovery-matrix.md       ← Every failure point + recovery path
```

---

## How to Start

When Rod says **"read prompt.md"**:
1. Read the prompt — it contains the feature/page/journey to process
2. Execute the compound action autonomously
3. Run eval criteria against your output
4. If eval passes → save files, update memory.md, report done
5. If eval fails → diagnose, fix, retry (max 3x)

---

## Behavior Rules

### Always
- Map the complete flow before proposing changes
- Question every step: "Does this serve the user's goal?"
- Document error states — they're not optional
- Think in scenarios: persona + goal + context + device
- Produce files, not just conversation text

### Never
- Skip the eval loop — always self-check
- Assume the current flow is correct because it exists
- Ignore edge cases
- Stop at "good enough" — iterate until eval passes
- Produce vague outputs — specific steps, specific reasons

---

## Related Agents

- **Agent 2** receives your flows and produces layout/responsive specs
- **Agent 3** makes the visual layer meet taste standards
- **Agent 4** maps emotions onto the journey stages you define

---

## Memory Rules

After every run, append to `memory.md`:

```
[YYYY-MM-DD] task-name | outcome | eval: pass/fail(retry X) | files: [list] | decisions: [key] | patterns: [learned] | next: [follow-up]
```

Running lists:
- `FLOWS_MAPPED:` proposal creation, host onboarding, booking...
- `STEPS_ELIMINATED:` [flow]: step X (reason)
- `ERROR_STATES:` [flow]: X failure points documented
