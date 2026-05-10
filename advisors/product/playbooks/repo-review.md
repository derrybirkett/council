# Repo Review Playbook

## Goal

Review a repository's product health, mission coherence, and recommend improvements.

## When To Use

- Weekly or on-demand product review
- After significant launches
- When roadmap feels unfocused
- During strategic planning

## Inputs

- README.md — product vision and stated mission
- package.json — tech stack and dependencies
- lib/*.ts — core logic and services
- app/**/* — routes and pages
- AGENTS.md — AI agent instructions
- Any roadmap or planning docs

## Review Steps

### 1. Mission Coherence

Read README.md and identify:
- What is the product?
- Who is it for?
- What problem does it solve?

Then examine the code:
- Does the implementation match the stated mission?
- Are there features that diverged from the original vision?
- Is there feature bloat that dilute the core value?

### 2. Product Health

Examine core files:
- Is the code well-organized?
- Are there clear separation of concerns?
- Is there technical debt slowing delivery?
- Are there missing fundamentals?

### 3. Gap Analysis

Identify:
- What's the README promise that isn't in code?
- What user needs have no solution?
- What's missing to fulfill the mission?

### 4. Recommendations

Prioritize:
- **Cut** — what to remove or defer
- **Fix** — what to improve
- **Build** — what to add
- **Invest** — what to pay down technically

## Output Format

```markdown
# Product Review: [Repo Name]

## Mission Coherence
[Assessment]

## Product Health
- Working: [what's good]
- Frail: [what needs attention]

## Gaps
- [Gap 1]
- [Gap 2]

## Recommendations
1. **[Priority]**: [Action]
2. **[Priority]**: [Action]

## Escalation
- [Any advisor needed for follow-up]
```

## Execution Notes

- Use all available inputs — don't guess
- Be ruthless about prioritization
- Flag scope creep
- Identify what to cut before what to add