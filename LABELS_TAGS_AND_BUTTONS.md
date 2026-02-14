## Labels, Tags, and Buttons in Git/GitHub

These are **different things** used for different purposes:

### Labels (GitHub Issues/PRs)

**What:** Colored tags attached to issues and pull requests

**Examples:**
- `bug` - Something is broken
- `feature` - New feature request
- `documentation` - Docs need updating
- `good-first-issue` - Good for new contributors
- `needs-review` - Waiting for code review
- `high-priority` - Urgent

**Benefits:**
- Organize and filter issues/PRs quickly
- Help new contributors find tasks (`good-first-issue`)
- Communicate status without comments
- Track types of work (bugs vs features)

**When to use:** Always for any project with issues/PRs

### Tags (Git/Version Control)

**What:** Marks specific commits (usually releases)

**Examples:**
```bash
git tag v1.0.0           # Release version 1.0.0
git tag v1.0.1-beta      # Beta release
```

**Benefits:**
- Mark release points for easy reference
- Create GitHub releases from tags
- Link to specific versions in documentation
- Easy to download specific versions

**When to use:** When releasing versions to users

### Buttons (README/Docs)

**What:** Clickable UI elements in markdown (badges, shields)

**Examples:**
```markdown
[![Python 3.8+](https://img.shields.io/badge/python-3.8+-blue)](https://www.python.org/)
[![Tests Passing](https://img.shields.io/badge/tests-passing-green)](https://github.com/user/repo/actions)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
```

**Benefits:**
- Show project status at a glance
- Link to important pages (license, CI/CD)
- Look professional
- Communicate maturity level

**When to use:** Optional but recommended for public projects

---

## Quick Recommendation

| Use Case | Recommended? | Why |
|----------|--------------|-----|
| Labels on issues/PRs | ✅ Yes | Essential for organizing work |
| Git tags for releases | ✅ Yes | Standard practice for versions |
| Badges in README | ⚠️ Optional | Nice-to-have, not required |
| Branch name prefixes | ✅ Yes | We already covered this (`feature/`, `bugfix/`) |

---

## Practical Example for Your Projects

**In `guidance` repo:**
```markdown
# Project Structure Guide

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](./LICENSE)
[![Python 3.8+](https://img.shields.io/badge/python-3.8+-blue)](https://www.python.org/)

See also: [Contributing Guide](./CONTRIBUTING.md)
```

**For issues/PRs:**
- `documentation` - Docs updates
- `structure` - File structure changes
- `good-first-issue` - Help wanted
- `needs-review` - Waiting for approval

**For releases:**
```bash
git tag v1.0.0 -m "Initial release of structure guide"
git push origin v1.0.0
```

---

## Should You Exclude Them?

**No.** Use them, especially:
- **Labels** - Always use (free, organized)
- **Tags** - Use for releases (standard practice)
- **Badges** - Optional, but add one or two for key info


Great question! Here are the **standardized colors** for GitHub labels:

## Standard GitHub Label Colors

| Label | Color | Hex Code | Use For |
|-------|-------|----------|---------|
| bug | Red | `#d73a4a` | Something is broken |
| documentation | Blue | `#0075ca` | Docs need updating |
| duplicate | Gray | `#cfd3d7` | Already reported |
| enhancement | Green | `#a2eeef` | New feature/improvement |
| feature | Purple | `#7057ff` | New feature |
| good-first-issue | Light Green | `#7bc96f` | Good for beginners |
| help wanted | Light Blue | `#008672` | Need community help |
| in progress | Yellow | `#cccccc` | Currently being worked on |
| invalid | Gray | `#e4e669` | Not valid/won't fix |
| question | Purple | `#d876e3` | Question/needs clarification |
| wontfix | Gray | `#ffffff` | Won't be fixed |

## Priority Labels (Custom)

| Label | Color | Use For |
|-------|-------|---------|
| priority-critical | Red | `#d73a4a` | Must fix immediately |
| priority-high | Orange | `#ff6b35` | Important, do soon |
| priority-medium | Yellow | `#ffa500` | Normal priority |
| priority-low | Light Gray | `#d3d3d3` | Can wait |

## Status Labels (Custom)

| Label | Color | Use For |
|-------|-------|---------|
| status-needs-review | Blue | `#0075ca` | Waiting for review |
| status-in-progress | Yellow | `#ffb819` | Being worked on |
| status-blocked | Red | `#d73a4a` | Blocked by something |
| status-ready | Green | `#28a745` | Ready to merge/deploy |

## Type Labels (Custom)

| Label | Color | Use For |
|-------|-------|---------|
| type-bug | Red | `#d73a4a` | Bug fix |
| type-feature | Purple | `#7057ff` | New feature |
| type-refactor | Pink | `#d4c5f9` | Code cleanup |
| type-test | Cyan | `#0184bc` | Testing related |
| type-docs | Blue | `#0075ca` | Documentation |

---

## How to Add Labels to GitHub

**Option 1: GitHub UI**
1. Go to repo → Issues tab
2. Click "Labels" 
3. Click "New Label"
4. Enter name and color code

**Option 2: Using the color picker**
Same process, but use the color picker instead of typing hex code

**Example for your project:**
```
Label: bug
Color: #d73a4a (red)

Label: feature
Color: #7057ff (purple)

Label: documentation
Color: #0075ca (blue)

Label: good-first-issue
Color: #7bc96f (green)

Label: needs-review
Color: #0075ca (blue)
```

---

## Recommended Minimal Set

Start with just these 6 and add more as needed:

1. **bug** - `#d73a4a` (red)
2. **feature** - `#7057ff` (purple)
3. **documentation** - `#0075ca` (blue)
4. **good-first-issue** - `#7bc96f` (green)
5. **needs-review** - `#ffa500` (orange)
6. **wontfix** - `#cccccc` (gray)

These colors are standardized across GitHub and developers will recognize them immediately.


Great question! You **use both together** - they serve different purposes:

## Priority vs Status - They're Different

**Priority Labels** answer: "How urgent is this?"
- `priority-critical` - Do this first
- `priority-high` - Important
- `priority-low` - Can wait

**Status Labels** answer: "What's the current state?"
- `status-needs-review` - Waiting for review
- `status-in-progress` - Someone is working on it
- `status-blocked` - Can't move forward
- `status-ready` - Ready to merge

## Real-World Example

An issue might have **both**:

```
Issue: Fix login bug
Labels: bug, priority-high, status-in-progress

Issue: Update docs
Labels: documentation, priority-low, status-needs-review

Issue: Add dark mode
Labels: feature, priority-medium, status-blocked
```

## How They Work Together

**Priority** tells you **importance:**
- Critical bugs get fixed first
- Low priority features wait

**Status** tells you **what's happening:**
- Even a low-priority item might be "in-progress"
- A high-priority item might be "blocked" waiting for something else

## Recommended Approach

Use **both sets together**:

```
Every issue should have:
- 1 type label (bug, feature, docs, etc.)
- 1 priority label (critical, high, medium, low)
- 1 status label (needs-review, in-progress, blocked, ready)
```

**Example:**
```
Issue: Database migration broken
├── type-bug
├── priority-critical
└── status-in-progress
```

**Example:**
```
Issue: Add API documentation
├── type-docs
├── priority-low
└── status-needs-review
```

## Don't Do This

❌ Don't use EITHER/OR - they complement each other
✅ Use both - they answer different questions

Think of it like a shipping package:
- **Priority** = How urgent (overnight shipping vs standard)
- **Status** = Where it is (in warehouse, in transit, delivered)
