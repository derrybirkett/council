# Build Simple Task Playbook

## Goal

Implement a simple BUILD-labeled issue into a PR.

## When To Use

- Run periodically (daily/weekly) on BUILD-labeled issues
- Or triggered manually for specific issues

## Steps

### 1. Fetch OPEN Issues With BUILD Label

```graphql
query {
  repository(owner: "derrybirkett", name: "anna") {
    issues(first: 10, states: OPEN, labels: ["build"]) {
      nodes {
        number
        title
        body
        labels(first: 10) {
          nodes {
            name
          }
        }
      }
    }
  }
}
```

### 2. For Each Issue, Assess Complexity

Check:
| Factor | Question |
|--------|----------|
| File count | Will changes touch 1-2 files or 3+? |
| Dependencies | Needs new packages? |
| Security | Affects auth/permissions? |
| Scope | Affects multiple features? |
| Requirements | Clear or ambiguous? |

**Decision:**
- **COMPLEX** → Add `complex` label, comment, skip
- **SIMPLE** → Proceed to implement

### 3. For Simple Tasks

a. Read the issue description fully
b. Read relevant code files
c. Understand the existing patterns
d. Implement the change
e. Test locally if possible
f. Commit changes
g. Create PR with proper description

### 4. Create Pull Request

```
## What
[One sentence description]

## Why
Closes #[issue-number]

## How
- [Implementation step 1]
- [Implementation step 2]

## Testing
[How to verify]
```

## Complexity Markers

Add `complex` label and comment if:
- Requires 3+ file changes
- Needs new dependencies
- Affects security
- Needs DB changes
- Unclear requirements
- Could break things

## Output

**Simple implemented:**
- Branch created with changes
- PR created
- Issue linked in PR body

**Complex skipped:**
- `complex` label added
- Comment with complexity explanation
- No further action