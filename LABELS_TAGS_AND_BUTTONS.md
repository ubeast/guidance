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

---

## Standard GitHub Label Colors

| Label | Color | Hex Code | Use For |
|-------|-------|----------|---------|
| bug | <span style="display:inline-block;width:20px;height:20px;background-color:#d73a4a;border:1px solid #000;"></span> | `#d73a4a` | Something is broken |
| documentation | <span style="display:inline-block;width:20px;height:20px;background-color:#0075ca;border:1px solid #000;"></span> | `#0075ca` | Docs need updating |
| duplicate | <span style="display:inline-block;width:20px;height:20px;background-color:#cfd3d7;border:1px solid #999;"></span> | `#cfd3d7` | Already reported |
| enhancement | <span style="display:inline-block;width:20px;height:20px;background-color:#a2eeef;border:1px solid #000;"></span> | `#a2eeef` | New feature/improvement |
| feature | <span style="display:inline-block;width:20px;height:20px;background-color:#7057ff;border:1px solid #000;"></span> | `#7057ff` | New feature |
| good-first-issue | <span style="display:inline-block;width:20px;height:20px;background-color:#7bc96f;border:1px solid #000;"></span> | `#7bc96f` | Good for beginners |
| help wanted | <span style="display:inline-block;width:20px;height:20px;background-color:#008672;border:1px solid #000;"></span> | `#008672` | Need community help |
| in progress | <span style="display:inline-block;width:20px;height:20px;background-color:#cccccc;border:1px solid #999;"></span> | `#cccccc` | Currently being worked on |
| invalid | <span style="display:inline-block;width:20px;height:20px;background-color:#e4e669;border:1px solid #999;"></span> | `#e4e669` | Not valid/won't fix |
| question | <span style="display:inline-block;width:20px;height:20px;background-color:#d876e3;border:1px solid #000;"></span> | `#d876e3` | Question/needs clarification |
| wontfix | <span style="display:inline-block;width:20px;height:20px;background-color:#ffffff;border:1px solid #999;"></span> | `#ffffff` | Won't be fixed |

## Priority Labels (Custom)

| Label | Color | Use For |
|-------|-------|---------|
| priority-critical | <span style="display:inline-block;width:20px;height:20px;background-color:#d73a4a;border:1px solid #000;"></span> `#d73a4a` | Must fix immediately |
| priority-high | <span style="display:inline-block;width:20px;height:20px;background-color:#ff6b35;border:1px solid #000;"></span> `#ff6b35` | Important, do soon |
| priority-medium | <span style="display:inline-block;width:20px;height:20px;background-color:#ffa500;border:1px solid #000;"></span> `#ffa500` | Normal priority |
| priority-low | <span style="display:inline-block;width:20px;height:20px;background-color:#d3d3d3;border:1px solid #999;"></span> `#d3d3d3` | Can wait |

## Status Labels (Custom)

| Label | Color | Use For |
|-------|-------|---------|
| status-needs-review | <span style="display:inline-block;width:20px;height:20px;background-color:#0075ca;border:1px solid #000;"></span> `#0075ca` | Waiting for review |
| status-in-progress | <span style="display:inline-block;width:20px;height:20px;background-color:#ffb819;border:1px solid #000;"></span> `#ffb819` | Being worked on |
| status-blocked | <span style="display:inline-block;width:20px;height:20px;background-color:#d73a4a;border:1px solid #000;"></span> `#d73a4a` | Blocked by something |
| status-ready | <span style="display:inline-block;width:20px;height:20px;background-color:#28a745;border:1px solid #000;"></span> `#28a745` | Ready to merge/deploy |

## Type Labels (Custom)

| Label | Color | Use For |
|-------|-------|---------|
| type-bug | <span style="display:inline-block;width:20px;height:20px;background-color:#d73a4a;border:1px solid #000;"></span> `#d73a4a` | Bug fix |
| type-feature | <span style="display:inline-block;width:20px;height:20px;background-color:#7057ff;border:1px solid #000;"></span> `#7057ff` | New feature |
| type-refactor | <span style="display:inline-block;width:20px;height:20px;background-color:#d4c5f9;border:1px solid #000;"></span> `#d4c5f9` | Code cleanup |
| type-test | <span style="display:inline-block;width:20px;height:20px;background-color:#0184bc;border:1px solid #000;"></span> `#0184bc` | Testing related |
| type-docs | <span style="display:inline-block;width:20px;height:20px;background-color:#0075ca;border:1px solid #000;"></span> `#0075ca` | Documentation |

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

1. <span style="display:inline-block;width:20px;height:20px;background-color:#d73a4a;border:1px solid #000;"></span> **bug** - `#d73a4a`
2. <span style="display:inline-block;width:20px;height:20px;background-color:#7057ff;border:1px solid #000;"></span> **feature** - `#7057ff`
3. <span style="display:inline-block;width:20px;height:20px;background-color:#0075ca;border:1px solid #000;"></span> **documentation** - `#0075ca`
4. <span style="display:inline-block;width:20px;height:20px;background-color:#7bc96f;border:1px solid #000;"></span> **good-first-issue** - `#7bc96f`
5. <span style="display:inline-block;width:20px;height:20px;background-color:#0075ca;border:1px solid #000;"></span> **needs-review** - `#0075ca`

---

## Recommended Minimal Set

Start with just these 6 and add more as needed:

1. **bug** - <span style="display:inline-block;width:20px;height:20px;background-color:#d73a4a;border:1px solid #000;"></span> `#d73a4a`
2. **feature** - <span style="display:inline-block;width:20px;height:20px;background-color:#7057ff;border:1px solid #000;"></span> `#7057ff`
3. **documentation** - <span style="display:inline-block;width:20px;height:20px;background-color:#0075ca;border:1px solid #000;"></span> `#0075ca`
4. **good-first-issue** - <span style="display:inline-block;width:20px;height:20px;background-color:#7bc96f;border:1px solid #000;"></span> `#7bc96f`
5. **needs-review** - <span style="display:inline-block;width:20px;height:20px;background-color:#ffa500;border:1px solid #000;"></span> `#ffa500`
6. **wontfix** - <span style="display:inline-block;width:20px;height:20px;background-color:#cccccc;border:1px solid #999;"></span> `#cccccc`

These colors are standardized across GitHub and developers will recognize them immediately.

---

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
Labels: bug, priority-critical, status-in-progress

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

---

## Mentions (@) and Issue References (#)

These are **special tags** that link people and issues together in GitHub:

### Mentions (@username)

**What:** Tags that notify a specific person

**Syntax:**
```markdown
@sarah - Hey Sarah, can you review this?
@dev-team - This needs input from the development team
Thanks @john for catching this bug!
```

**Where to use:**
- Comments on issues/PRs
- PR descriptions
- Commit messages
- Issue descriptions
- README files

**Benefits:**
- Notifies the person directly
- They get an email and notification
- Creates accountability
- Easy to direct questions to the right person

**Examples:**
```markdown
# PR Description
Fixes #342

@sarah - This is ready for your review
@dev-team - Please test on staging before we deploy
```

**When to use:** 
- Assign work to someone
- Ask for feedback
- Give credit/thanks
- Draw attention to something urgent

---

### Issue References (#number)

**What:** Tags that link to specific issues or PRs

**Syntax:**
```markdown
Closes #123          # Auto-closes issue when PR merges
Fixes #456          # Same as "Closes"
Relates to #789     # Links without closing
See #101 for context
Duplicate of #555
```

**Where to use:**
- PR descriptions (most important)
- Commit messages
- Comments on issues
- Discussion threads
- README files

**Benefits:**
- Automatic linking between issues and PRs
- Automatically closes issues when PR merges
- Shows related work
- Creates audit trail
- Prevents duplicate work

**Examples:**

```markdown
# PR Example 1
Title: Fix login bug

Closes #342

This PR fixes the authentication timeout issue reported in #342.
Changes:
- Extended session timeout from 30 to 60 minutes
- Added refresh token logic
- Updated tests

Tested on staging. Ready for @sarah review.
```

```markdown
# PR Example 2
Title: Add dark mode feature

Relates to #501
Closes #488

Implements the dark mode feature requested in #501.
Also fixes the contrast issue mentioned in #488.
```

```markdown
# Issue Comment Example
@dev-team - This is a duplicate of #223. 
See the discussion there for more context.
```

---

## When @ and # Work Together

**Common workflow:**

```
1. Issue #456 created: "Database performance is slow"

2. Developer works on fix, creates PR #789
   PR description: "Closes #456 - Optimize database queries"

3. In PR comments: "@sarah can you review the query optimization?"

4. Sarah comments: "Looks good! See my suggestions in #789 (line 45)"

5. Developer makes changes and comments: "@sarah addressed your feedback"

6. Sarah approves and merges PR

7. Issue #456 automatically closes because PR said "Closes #456"
```

---

## Quick Reference Table

| Syntax | Purpose | Example |
|--------|---------|---------|
| `@username` | Mention a person | `@john please review` |
| `@team-name` | Mention a team | `@backend-team needs this` |
| `#123` | Reference an issue | `Relates to #123` |
| `Closes #123` | Auto-close when merged | In PR description |
| `Fixes #123` | Same as Closes | In PR description |
| `Relates to #123` | Link without closing | For related issues |

---

## Best Practices

### For Mentions (@)
✅ **Do:**
- Use to notify relevant people
- @ the person whose input you need
- Give context in the same comment
- Use @ in PR description if major changes

❌ **Don't:**
- @ someone multiple times in one comment
- @ people who aren't involved
- Overuse @ (saves it for important stuff)

### For Issue References (#)
✅ **Do:**
- Always reference related issues in PR description
- Use `Closes #` in PR when it fixes an issue
- Link to duplicates
- Reference in commit messages when helpful

❌ **Don't:**
- Leave PRs without any issue reference
- Use # for things not actually related
- Create PRs without linking to issues

---

## Example for Your Projects

**In a PR for the `guidance` repo:**

```markdown
# PR: Improve contribution guidelines

Closes #234
Relates to #198

@sarah - This updates the CONTRIBUTING.md file per your feedback in #234.
Also addresses the template issue mentioned in #198.

Changes:
- Added checklist template
- Clarified code style requirements
- Added testing guidelines

Ready for review when you have time!
```

**In an issue comment:**

```
@dev-team - I found this is actually related to #567 as well.
See the discussion there for context.
This might be a duplicate of #567, let's check before fixing.
```

---

## Summary

**Three powerful linking tools:**

1. **Labels** - Organize and categorize work
2. **@ Mentions** - Notify specific people
3. **# References** - Link related issues and PRs

Use all three together to create organized, transparent workflows where everyone knows what's happening and who needs to do what.

---

## GitLab-Specific Features

If you're using GitLab instead of GitHub, there are some important differences and additional features to know about:

### Scoped Labels (GitLab Unique Feature)

GitLab has a powerful feature called **scoped labels** that use double-colon (::) syntax in the title, for example: `workflow::in-review`. An issue, merge request, or epic cannot have two scoped labels with the same key, so if you add a new label with the same key but different value, the previous one is automatically replaced.

**Examples:**
```
priority::critical
priority::high
workflow::in-progress
workflow::review
workflow::blocked
team::backend
team::frontend
platform::iOS
platform::Android
```

**Benefits:**
- Create mutually exclusive label groups (only one value per key)
- Automatically swap labels when status changes
- Filter by scope using `scope::*` (e.g., `priority::*` shows all priority labels)
- Perfect for workflow states and team assignments

### Merge Requests vs Pull Requests

GitLab calls them **Merge Requests (MR)** instead of Pull Requests (PR). The syntax uses `!` instead of nothing:

| Concept | GitHub | GitLab |
|---------|--------|--------|
| Issue reference | `#123` | `#123` |
| PR/MR reference | (no symbol) | `!456` |
| Mention | `@username` | `@username` |
| Cross-project issue | N/A | `group/project#123` |
| Cross-project MR | N/A | `group/project!456` |

### Issue Closing Keywords (Same as GitHub)

In your merge request description add "Closes #123" or "Fixes #123" - this works the same way in GitLab.

**Additional GitLab-specific keywords:**
```markdown
Closes #123
Fixes #123
Closes group/otherproject#456       # Cross-project
Fixes group/otherproject#789        # Cross-project
Related to #101
Relates to #101
```

### Quick Actions

GitLab has quick actions (slash commands) in comments and descriptions:

```markdown
/label ~bug ~documentation          # Add labels
/unlabel ~wontfix                   # Remove label
/relabel ~feature ~enhancement      # Replace all labels
/assign @username                   # Assign person
/unassign @username                 # Unassign person
/close                              # Close issue
/reopen                             # Reopen issue
```

### Project vs Group Labels

GitLab has two types of labels: Project labels can be assigned to issues and merge requests in that project only. Group labels can be assigned to epics, issues and merge requests in any project in the selected group or its subgroups.

**Use group labels for:**
- Shared standards across multiple projects
- Organization-wide conventions
- Team-wide workflows

**Use project labels for:**
- Project-specific categorization
- Internal organization
- Project-specific status tracking

### GitLab Reference Syntax Summary

| Syntax | Purpose | Example |
|--------|---------|---------|
| `#123` | Local issue | `Closes #123` |
| `!456` | Merge request | `!456 fixes the bug` |
| `group/project#123` | Cross-project issue | `Related to backend/api#456` |
| `group/project!789` | Cross-project MR | `Closes frontend/web!789` |
| `@username` | Mention person | `@sarah please review` |
| `/label` | Quick action | `/label ~bug ~critical` |
| `workflow::*` | Scoped label filter | Filter by `workflow::*` |

### Example: GitLab Workflow with Scoped Labels

```markdown
# Issue: Login timeout on mobile

Labels:
- type-bug
- priority::critical
- workflow::in-progress
- platform::iOS

---

## MR: Fix login timeout

Related to #342
Closes #342

@sarah - Ready for review
@platform-team - Please test on iOS devices
```

When the MR is reviewed and moved to testing, you would add:
```
/relabel ~workflow::in-review ~workflow::testing
```

This automatically removes `workflow::in-review` and adds `workflow::testing`.

### Key Differences from GitHub

| Feature | GitHub | GitLab |
|---------|--------|--------|
| Label scoping | No | Yes (`::` syntax) |
| Mutually exclusive labels | Manual | Automatic (same scope) |
| Merge request name | Pull Request | Merge Request |
| Merge request symbol | (none) | `!` |
| Cross-project references | Limited | Full support |
| Quick actions | No | Yes (`/label`, `/assign`, etc.) |
| Label filtering by scope | No | Yes (`scope::*`) |
| Epics | No | Yes (GitLab Premium+) |

### Recommendation for GitLab Projects

Use scoped labels for maximum organization:

```
priority::critical
priority::high
priority::medium
priority::low

workflow::backlog
workflow::in-progress
workflow::in-review
workflow::blocked
workflow::done

type::bug
type::feature
type::docs
type::refactor

team::backend
team::frontend
team::devops
```

Then add unscoped labels for additional organization:

```
good-first-issue
help-wanted
accessibility
security
performance
```
