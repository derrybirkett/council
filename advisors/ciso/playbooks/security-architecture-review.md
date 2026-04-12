# Security Architecture Review

## Goal

Assess whether a system design has appropriate controls for its exposure, data sensitivity, and operational context.

## Inputs

- system description
- data classification or sensitivity level
- user and service access model
- network or trust-boundary overview
- existing controls and known gaps

## Review Steps

1. Identify critical assets and sensitive data paths.
2. Map trust boundaries, entry points, and privileged paths.
3. Review auth, secrets, encryption, logging, and recovery posture.
4. Identify missing controls, weak ownership, or unreviewed assumptions.
5. Classify findings by materiality and urgency.
6. Require `cto` review if remediation changes architecture or delivery sequencing.

## Output

- overall risk posture
- key findings
- compensating controls if immediate remediation is not possible
- owner and target dates for critical actions