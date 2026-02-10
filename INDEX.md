# Design Framework Agents — Automated Design Processes

## What This Is

A system of 4 autonomous agents that **automate design processes**. Each agent takes an input (a page, component, flow, or HTML file), runs a multi-step compound action, evaluates its own output against a calibration document, and **iterates until the eval passes**. They produce concrete deliverables — CSS tokens, layout specs, responsive screenshots, flow maps, copy systems — not opinions.

Designed for **overnight, unattended execution**. Each agent is a compound action that self-extends, self-corrects, and burns tokens autonomously through Plan-Act-Verify loops.

```
design-framework-agents/
├── INDEX.md                              ← You are here
├── orchestrator/
│   ├── agent.md                          ← Fan-out coordinator + synthesis
│   ├── memory.md
│   └── prompts/
├── agent-1-how-it-works/                 ← Automates: flow mapping, process audits
│   ├── agent.md
│   ├── prompt.md
│   ├── memory.md
│   └── assets/
├── agent-2-how-we-communicate/           ← Automates: layout, responsive, IA
│   ├── agent.md
│   ├── prompt.md
│   ├── memory.md
│   └── assets/
├── agent-3-how-it-looks/                 ← Automates: color, typography, visual tokens
│   ├── agent.md
│   ├── prompt.md
│   ├── memory.md
│   └── assets/
└── agent-4-how-it-feels/                 ← Automates: emotion maps, copy, personality
    ├── agent.md
    ├── prompt.md
    ├── memory.md
    └── assets/
```

---

## Agent Quick Reference

| Agent | Automates | Compound Pattern | Eval Loop | Token Budget |
|-------|-----------|-----------------|-----------|--------------|
| **Agent 1** | Flow mapping, process audits, goal-directed redesign | Plan-Act-Verify | All steps justified + error recovery complete | 0.5M–5M |
| **Agent 2** | Layout specs, responsive CSS, Playwright verification | Spec-Driven Refactor + Playwright | Responsive Taste Test ≥ 27/30 at 7 viewports | 0.5M–5M |
| **Agent 3** | Color systems, type scales, spacing tokens, CSS output | TDD Sandbox (Taste Test = tests) | Design Taste Test ≥ 27/30 + WCAG AA pass | 0.5M–5M |
| **Agent 4** | Emotional journey maps, copy systems, personality guides | Evidence-Gap Probe | All gaps mapped + interventions specific | 0.5M–5M |

---

## The Compound Action Loop

Every agent runs this autonomously:

```
INPUT (page, component, HTML file, flow)
  │
  ▼
PLAN — Read input + calibration doc → generate execution plan
  │
  ▼
ACT — Execute step by step → produce files (CSS, md, screenshots)
  │
  ▼
EVAL — Score output against calibration doc
  │
  ├── PASS → Save output, update memory, report done
  │
  └── FAIL → Diagnose → adjust approach → retry ACT (max 3x)
```

This is the **Plan-Act-Verify Loop** from the strategy doc. The eval is what makes agents run longer — they don't stop when they "finish," they stop when the **target is met**.

---

## Overnight Execution Model

These agents are designed as overnight compound actions:

| Tactic | How It Applies |
|--------|---------------|
| **Compound Actions** | One prompt expands into 7-10 autonomous steps |
| **Eval Loops** | Agent keeps iterating until target score is met |
| **Concrete Outputs** | Files saved to disk (CSS, MD, screenshots), not conversation |
| **Self-Correction** | Failed eval → diagnose → retry (up to 3x) |
| **Token Budgets** | 0.5M–5M per task type, prevents runaway |
| **Fan-Out** | Orchestrator assigns all 4 in parallel, synthesis after |
| **Memory Logging** | Every session writes decisions, patterns, outcomes to memory.md |

### Overnight Setup

```
Evening:
  1. Load orchestrator → write prompts to all 4 agents
  2. Start each agent in a separate tab/session
  3. Each agent runs its compound action autonomously

Morning:
  4. Read memory.md files for outcomes
  5. Check assets/ folders for deliverables
  6. Orchestrator synthesizes cross-pillar results
```

---

## What Each Agent Produces

| Agent | Concrete Outputs |
|-------|-----------------|
| **Agent 1** | `flow-map-[feature].md`, `process-audit.md`, `goal-analysis.md`, `error-recovery-matrix.md` |
| **Agent 2** | `responsive-tokens.css`, `layout-spec-[page].md`, `hierarchy-map.md`, Playwright screenshots |
| **Agent 3** | `color-system.css`, `typography-scale.css`, `spacing-tokens.css`, `taste-test-score.md`, `visual-audit.md` |
| **Agent 4** | `emotion-map-[flow].md`, `personality-guide.md`, `copy-system.md`, `intervention-specs.md` |

---

## Cross-Agent Dependencies

```
                    ┌─────────────────────┐
                    │   ORCHESTRATOR       │
                    │   Fan-out + Synthesis│
                    └─────────┬───────────┘
                              │
         ┌────────────────────┼────────────────────┐
         │                    │                     │
    ┌────▼─────┐    ┌────────▼────────┐    ┌───────▼──────┐
    │ Agent 1  │    │ Agent 2         │    │ Agent 3      │
    │ Flows    │───►│ Layout + CSS    │───►│ Visual       │
    │          │    │ + Playwright    │    │ Tokens + CSS │
    └────┬─────┘    └────────┬────────┘    └───────┬──────┘
         │                   │                     │
         │          ┌────────▼────────┐            │
         └─────────►│ Agent 4         │◄───────────┘
                    │ Emotion + Copy  │
                    └─────────────────┘
```

**Agents 1, 2, 3 run in parallel.** Agent 4 integrates after.

---

## Calibration Documents

Each agent has a calibration doc that serves as its **eval target** — like test cases in TDD:

| Agent | Calibration Doc | What It Provides |
|-------|----------------|------------------|
| Agent 2 | `RESPONSIVE-DESIGN-MODEL.md` | 30-question responsive taste test, 20 patterns, 15 anti-patterns |
| Agent 3 | `DESIGN-TASTE-MODEL.md` | 30-question visual taste test, 20 patterns, 15 anti-patterns |

Agents 1 and 4 use their eval criteria checklists as calibration.

---

## Starting an Agent

```
You are [path]/agent.md
```

Then: **"read prompt.md"** — the agent executes its compound action autonomously until the eval passes.
