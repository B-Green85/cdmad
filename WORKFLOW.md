# CDMAD Workflow (Current Practice)

This document describes how I currently practice CDMAD in active projects.

It is not automated.
It is not tool-driven.
It is procedural and deliberate.

The discipline is simple:
Define constraints.
Generate carefully.
Verify deterministically.
Refine intentionally.

---

## Step 1 — Establish Constraint Consensus

Before generating anything, I define the boundaries clearly.

This usually includes:

- The exact goal (one sentence).
- What files are allowed to change.
- What files are off-limits.
- What must not change (public APIs, schemas, behavior).
- Any structural constraints (no new dependencies, no refactors, etc.).

This happens explicitly before generation.
Sometimes written.
Sometimes conversational.
But always clarified.

Constraint precedes generation.

---

## Step 2 — Structured Prompting

I prefer structured prompts (often JSON) over open-ended conversation.

Typical structure:

- goal
- scope
- non-goals
- constraints
- required output format (usually unified diff)
- verification instructions

Example (simplified):

{
  "goal": "Refactor function X without changing behavior.",
  "scope": {
    "files_allowed": ["module_x/file.py"],
    "forbidden": ["api/", "cli.py"]
  },
  "constraints": [
    "No new dependencies.",
    "Preserve public interfaces.",
    "No behavior changes."
  ],
  "output_format": "unified_diff"
}

The goal is clarity and diffability, not verbosity.

---

## Step 3 — Apply Changes in Isolation

I:

- Create a branch.
- Apply the diff.
- Avoid mixing unrelated changes.
- Keep the patch minimal.

The model’s output is treated as a proposal, not truth.

---

## Step 4 — Deterministic Verification

After applying the patch, I run whatever checks the repository supports:

- Unit tests (if present)
- Linting
- Type checks (if configured)
- Manual CLI verification (if relevant)
- Static checks (if available)

If tests fail, the change is rejected or revised.

Model fluency does not override failing checks.

Verification is the decision boundary.

Drift is expected in generative systems.

Scope expansion, unsolicited refactors, and adjacent “improvements” are common.

Part of the discipline is staying present enough to detect drift and reassert declared boundaries before accepting changes.

---

## Multi-Model Triangulation

When possible, I separate generation and critique across different models.

One model generates proposals (typically as diffs).  
A separate model critiques those proposals against scope, constraints, and likely failure modes.

Different models exhibit different blind spots. Triangulation increases the chance that drift, edge cases, or structural issues are surfaced before I run verification and freeze a commit.

---

## Step 5 — Manual Audit (Diff Review)

I review:

- The diff directly.
- Structural changes.
- Unexpected side effects.
- Scope violations.

Often, I request an audit pass from a separate model focused strictly on critique.

The auditing model does not generate new features.
It evaluates the proposed patch against declared constraints, scope, and potential drift.

Different models exhibit different blind spots.
Using a separate model reduces self-justifying bias and increases the likelihood of surfacing edge cases or structural concerns.

Final acceptance remains a human decision.

---

## What This Is Today

CDMAD, in practice, is:

- Structured prompting
- Explicit constraint agreement before generation
- Deterministic local verification
- Manual diff auditing
- Intentional constraint evolution

There is no automated enforcement engine.
There is no formal constraint registry.
There is no required team structure.

It is a disciplined workflow, not a toolchain.

---

## What Is Not Yet Automated

The current CDMAD workflow is procedural and human-directed.

The following elements are not automated at this time:

- Constraint storage in a formal registry or schema.
- Versioned prompt packets tied to CI pipelines.
- Automated enforcement of architectural boundaries.
- Programmatic diff auditing.
- Machine-verifiable constraint drift detection.

Constraint definition, audit, and refinement are currently manual steps.

This is intentional.

The discipline is being exercised at the behavioral level before introducing enforcement tooling.

Automation may evolve where it improves clarity and repeatability.
It is not introduced for its own sake.

---

## Why This Works

It keeps a visible boundary between:

- Suggestion (model output)
- System truth (verified code)

It reduces architectural drift.
It discourages scope creep.
It preserves deterministic confidence.

---

In CDMAD, generation is optional.
Verification is not.
Refinement is deliberate and human-directed.
