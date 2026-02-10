# Process Flow Model for Agent 1

Purpose: This document is the quality model for Agent 1 (How it Works). Use it to design, audit, and improve flows so users can complete goals quickly, safely, and confidently.

---

## Part 1: Flow Quality Stack

### Level 1: Goal Clarity (must pass first)
- User goal is explicit and testable.
- Business goal is explicit and testable.
- Entry condition and success condition are defined.

Failure signal: Team debates UI details before agreeing on the goal.

### Level 2: Path Efficiency
- Minimum number of steps to complete goal.
- No system-serving steps that do not help the user.
- Primary path is obvious for first-time users.

Failure signal: Users need help text to complete a "simple" action.

### Level 3: Recovery and Resilience
- Errors are anticipated and recoverable.
- Partial progress is preserved where possible.
- Every blocking state has a next best action.

Failure signal: One validation issue forces full restart.

### Level 4: Feedback and Confidence
- Clear progress, status, and completion signals.
- Waiting states include realistic expectation setting.
- Completion confirms outcome and next action.

Failure signal: Users repeat actions because they are unsure what happened.

---

## Part 2: Standard Flow Template

Use this structure for every feature flow:

1. Persona
2. User goal
3. Business goal
4. Trigger and entry point
5. Primary path (happy path)
6. Branches and edge cases
7. Error states and recovery paths
8. Exit states and follow-up actions

---

## Part 3: Decision Framework

For each step in a flow, answer:

1. Why does this step exist?
2. What user question does it answer?
3. What happens if this step is removed?
4. Can this step be merged with adjacent steps?
5. What can go wrong here and how does the user recover?

If a step fails questions 1 and 2, remove or redesign it.

---

## Part 4: Core Patterns

### 1) Single Intent per Screen
Each step has one primary decision. Secondary actions are de-emphasized.

### 2) Progressive Commitment
Ask for low-risk inputs first; delay high-friction asks until intent is clear.

### 3) Save and Resume
Long flows preserve progress and support re-entry.

### 4) Inline Recovery
Show fixes where the error occurs, not only in global banners.

### 5) Explicit Completion
End state confirms success and proposes one clear next action.

---

## Part 5: Anti-Patterns

- Hidden prerequisites discovered late in the flow
- Duplicate data entry across steps
- Dead-end states with no escape path
- Silent failures (no actionable feedback)
- Forced linear paths when safe shortcuts exist

---

## Part 6: Flow Scorecard (0-20)

Score each item 0 (fail), 1 (partial), 2 (pass):

1. Goals are explicit (user + business)
2. Entry and exit conditions are clear
3. Primary path is minimal
4. Edge cases are mapped
5. Error recovery is complete
6. Feedback states are clear
7. Progress is preserved
8. First-time user can complete unassisted
9. Flow supports mobile constraints
10. No unnecessary steps remain

Target: 16+ for release, 18+ for benchmark quality.
