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

## Execution Model

### Pipeline Run

```
1. Give orchestrator a design target + raw content
2. Agent 1 → bare functional HTML         (step-1-works/)
3. Agent 2 → structured wireframe          (step-2-communicates/)
4. Agent 3 → production-styled page        (step-3-looks/)
5. Agent 4 → emotionally intelligent page  (step-4-feels/)
6. Validation loop: all 4 agents score the final page in parallel
7. Fix failures, re-validate until all pass (validation/)
```

| Tactic | How It Applies |
|--------|---------------|
| **Sequential Pipeline** | Each agent builds on the previous agent's HTML output |
| **Compound Actions** | One prompt expands into 7-10 autonomous steps |
| **Eval Loops** | Agent keeps iterating until target score is met |
| **Concrete Outputs** | Files saved to disk (HTML, CSS, MD), not conversation |
| **Self-Correction** | Failed eval → diagnose → retry (up to 3x) |
| **Validation Loop** | All 4 agents review final output in parallel |
| **Memory Logging** | Every session writes decisions, patterns, outcomes to memory.md |

---

## What Each Agent Produces

| Agent | Concrete Outputs |
|-------|-----------------|
| **Agent 1** | `flow-map-[feature].md`, `process-audit.md`, `goal-analysis.md`, `error-recovery-matrix.md` |
| **Agent 2** | `responsive-tokens.css`, `layout-spec-[page].md`, `hierarchy-map.md`, Playwright screenshots |
| **Agent 3** | `color-system.css`, `typography-scale.css`, `spacing-tokens.css`, `taste-test-score.md`, `visual-audit.md` |
| **Agent 4** | `emotion-map-[flow].md`, `personality-guide.md`, `copy-system.md`, `intervention-specs.md` |

---

## Sequential Pipeline — Each Agent Builds on the Previous

The agents run as a **sequential pipeline**, not in parallel. Each agent receives the previous agent's HTML output as its input and layers on its specific concern. This is the core architectural principle.

```
INPUT (text content, feature spec, or raw data)
  │
  ▼
┌──────────────────────────────────────────────────────┐
│  Agent 1 — How it Works                             │
│  Takes raw content → produces bare functional HTML   │
│  No styling, just A→B. Every action reachable.       │
│  Output: ugly but complete page                      │
└──────────────────────┬───────────────────────────────┘
                       │ HTML file
                       ▼
┌──────────────────────────────────────────────────────┐
│  Agent 2 — How we Communicate                       │
│  Takes Agent 1's HTML → improves information         │
│  architecture, cognitive load, layout, hierarchy.    │
│  Output: well-structured wireframe                   │
└──────────────────────┬───────────────────────────────┘
                       │ HTML file
                       ▼
┌──────────────────────────────────────────────────────┐
│  Agent 3 — How it Looks                             │
│  Takes Agent 2's HTML → applies visual design        │
│  system (colors, typography, shadows, icons).        │
│  Must follow Style-guide.md exactly.                 │
│  Output: production-quality styled page              │
└──────────────────────┬───────────────────────────────┘
                       │ HTML file
                       ▼
┌──────────────────────────────────────────────────────┐
│  Agent 4 — How it Feels                             │
│  Takes Agent 3's HTML → adds emotional intelligence. │
│  Reframes copy, adds empathy, micro-interactions,    │
│  reassurance, celebration. No visual changes.        │
│  Output: final page with all 4 layers               │
└──────────────────────┴───────────────────────────────┘
```

**Why sequential, not parallel:** Each layer depends on the previous one. You can't style a layout that doesn't exist yet. You can't add emotional copy to unstyled wireframes. The pipeline ensures each agent has the right context to do its job well.

After the pipeline completes, a **validation loop** runs all 4 agents in parallel — each reviewing the final output through their specific lens.

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
