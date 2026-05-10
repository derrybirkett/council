# Architecture Review

## Goal

Assess whether a proposed architecture is fit for current business needs and unlikely to create avoidable delivery, reliability, or cost problems.

## Inputs

- business objective
- current architecture or system map
- proposed change
- expected scale and usage assumptions
- operational constraints

## Review Steps

1. Clarify the business outcome and decision deadline.
2. Identify whether the decision is reversible or expensive to unwind.
3. Evaluate fit against current scale, team capability, and maintenance burden.
4. Check reliability, observability, and operational support implications.
5. Check security-sensitive boundaries and involve `ciso` if required.
6. Compare at least one simpler alternative.
7. Record a recommendation and explicit tradeoffs.

## Output

- approved, revise, or reject recommendation
- rationale
- key tradeoffs
- implementation conditions
- risks to monitor after adoption