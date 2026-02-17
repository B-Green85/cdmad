# CDMAD  
Constraint-Driven Model-Assisted Development  

## Overview

CDMAD is a development discipline for working with probabilistic models inside deterministic systems.

Modern language models generate plausible outputs.  
Production systems require verifiable outcomes.

CDMAD introduces a structured control loop at the boundary between generation and system truth.

It is not a framework or a dependency.  
It is a disciplined approach to managing uncertainty in model-assisted workflows.

---

## The Core Tension

Model outputs are probabilistic.  
Software systems are accountable.

Fluency does not imply validity.  
Generation does not imply correctness.

When model output influences code, architecture, or system behavior, it must pass through explicit, reproducible constraints.

---

## The Principle

Constraint precedes generation.

Rather than:

Prompt → Generate → Assume correctness  

CDMAD favors:

Declare constraints  
Generate within scope  
Verify deterministically  
Accept or reject  
Refine constraints deliberately  

The model proposes.  
The system evaluates.  
The constraints evolve intentionally.

---

## The Control Loop

A CDMAD-oriented workflow separates generation from validation:

1. **Constraint Definition**  
   Explicit invariants, schemas, boundaries, and contracts.

2. **Model Assistance**  
   Generation constrained by declared scope.

3. **Deterministic Verification**  
   Static analysis, contract checks, schema validation, reproducible tests.

4. **Decision Boundary**  
   Output is accepted only if constraints are satisfied.

5. **Constraint Refinement**  
   When useful outputs repeatedly fail validation, constraints are examined and adjusted explicitly.  
   Refinement is intentional and versioned, not silent drift.

This creates a closed loop between generation and verification while preserving deterministic system boundaries.

---

## What CDMAD Emphasizes

- Explicit contracts over implicit assumptions  
- Falsifiable output  
- Separation of generation flow and verification flow  
- Deterministic enforcement in CI environments  
- Deliberate evolution of constraint sets  

The objective is not to limit model capability, but to make its contributions structurally accountable.

---

## What CDMAD Is Not

CDMAD does not:

- Replace human judgment  
- Eliminate experimentation  
- Treat models as inherently unreliable  
- Attempt to control model choice  

It introduces structure at the boundary where probabilistic output meets deterministic systems.

---

## Why It Matters

As model-assisted development becomes more common, unstructured generation increases architectural entropy.

Without explicit constraint systems, drift accumulates silently.

CDMAD offers a disciplined loop that allows models to accelerate development while preserving system integrity.

---

## Closing

In CDMAD, generation is optional.  
Verification is not.  
Refinement is deliberate and human-directed.
