# Contributing Guide

Thank you for contributing! This guide will help you get started.

## Setup Development Environment

**1. Clone the repository**
```bash
git clone <repo-url>
cd project-name
```

**2. Create virtual environment**
```bash
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
```

**3. Install dependencies**
```bash
pip install -r requirements.txt
```

**4. Install package in development mode**
```bash
pip install -e .
```

**5. Verify setup**
```bash
pytest
```

All tests should pass. If not, ask for help.

## Code Standards

### Style

We follow **PEP 8** with Black formatting.

Format your code before committing:
```bash
make format
```

### Naming Conventions

- **Files:** `snake_case` (e.g., `user_service.py`)
- **Functions:** `snake_case` (e.g., `get_user_by_id()`)
- **Classes:** `PascalCase` (e.g., `UserService`)
- **Constants:** `UPPER_SNAKE_CASE` (e.g., `MAX_RETRIES = 3`)
- **Modules:** `snake_case` directories (e.g., `/utilities/`, `/cleansing/`)

### Docstrings and Comments

Write docstrings for all functions and classes:

```python
def validate_email(email: str) -> bool:
    """
    Validate email format.
    
    Args:
        email: Email address to validate
        
    Returns:
        True if valid, False otherwise
    """
    return "@" in email and "." in email
```

Use comments only for complex logic, not obvious code:

```python
# Good - explains why
# Retry 3 times in case of temporary network failure
for attempt in range(3):
    try:
        response = fetch_data(url)
        break
    except ConnectionError:
        if attempt < 2:
            time.sleep(1)

# Bad - obvious from code
# Loop through the list
for item in items:
    process(item)
```

### Type Hints

Use type hints for all function arguments and return values:

```python
def process_data(data: dict, count: int) -> list[str]:
    """Process data and return results."""
    results = []
    for i in range(count):
        results.append(str(data.get(f"item_{i}")))
    return results
```

## Git Workflow

### Branch Naming

Create branches with descriptive names:

- `feature/user-authentication` - New feature
- `bugfix/email-validation` - Bug fix
- `docs/update-readme` - Documentation
- `refactor/clean-up-utils` - Code cleanup

```bash
git checkout -b feature/your-feature-name
```

### Commit Messages

Write clear, descriptive commit messages:

```
Good:
git commit -m "Add email validation to user registration"
git commit -m "Fix: correct calculation in revenue report"
git commit -m "Docs: update database schema documentation"

Bad:
git commit -m "fix stuff"
git commit -m "updates"
git commit -m "wip"
```

Format: `<type>: <description>`

Types: `feature`, `fix`, `docs`, `refactor`, `test`, `chore`

### Pull Request Process

1. **Push your branch**
   ```bash
   git push origin feature/your-feature-name
   ```

2. **Create a pull request (PR)** with:
   - Clear title: `Add email validation to user registration`
   - Description of what changed and why
   - Link any related issues: `Fixes #123`
   - List of changes

3. **Example PR description:**
   ```
   ## What
   Added email validation to the user registration process.
   
   ## Why
   Users were registering with invalid emails, causing issues.
   
   ## How
   Created new `validate_email()` function in utilities module
   and integrated it into the registration flow.
   
   ## Testing
   Added 5 test cases covering valid and invalid emails.
   
   Fixes #45
   ```

4. **Wait for code review** - Address any feedback

5. **Merge** - Maintainers will merge after approval

## Before Submitting a Pull Request

**Run tests:**
```bash
make test
```

All tests must pass.

**Format code:**
```bash
make format
```

**Check for common issues:**
- ✅ No hardcoded credentials or API keys
- ✅ No secrets in `.env` (use `.env.example`)
- ✅ No unnecessary print statements
- ✅ No commented-out code blocks
- ✅ Updated documentation if needed
- ✅ Added tests for new features

## Testing Requirements

### Where to Add Tests

Add tests in `/tests/` matching the module structure:

```
src/package_name/cleansing/text_cleaning.py
tests/test_text_cleaning.py

src/package_name/utilities/validators.py
tests/test_validators.py
```

### How to Run Tests

```bash
# Run all tests
pytest

# Run with verbose output
pytest --verbose

# Run specific test file
pytest tests/test_validators.py

# Run specific test function
pytest tests/test_validators.py::test_validate_email

# Run with coverage
pytest --cov=src/package_name tests/
```

### Test Examples

```python
# tests/test_validators.py
import pytest
from package_name.utilities.validators import validate_email

def test_validate_email_valid():
    """Valid emails should return True."""
    assert validate_email("user@example.com") is True
    assert validate_email("test.user@company.co.uk") is True

def test_validate_email_invalid():
    """Invalid emails should return False."""
    assert validate_email("invalid") is False
    assert validate_email("@example.com") is False
    assert validate_email("user@") is False

def test_validate_email_edge_cases():
    """Test edge cases."""
    assert validate_email("") is False
    assert validate_email("user@.com") is False
```

### Minimum Coverage

Aim for **80%+ code coverage** for new code. Check with:

```bash
pytest --cov=src/package_name tests/
```

## Database Changes

### Creating Migrations

Create migrations for any schema changes:

```bash
# Create migration file
touch sql/migrations/004_add_user_status.sql
```

Name migrations sequentially: `001_`, `002_`, `003_`, etc.

### Migration Requirements

Migrations must be:
- **Idempotent** - Safe to run multiple times
- **Reversible** - Can be undone if needed
- **Tested** - Verify they work on test database

Example migration:

```sql
-- sql/migrations/004_add_user_status.sql
-- Add status column to users table

ALTER TABLE users 
ADD COLUMN status VARCHAR(20) DEFAULT 'active' NOT NULL;

CREATE INDEX idx_users_status ON users(status);
```

### Testing Migrations

Run migrations against a test database:

```bash
psql -U test_user -d test_db -f sql/migrations/004_add_user_status.sql
```

Verify data integrity after running.

## Documentation

### Update Documentation When

- Adding new modules or major features
- Changing how something works
- Adding environment variables
- Changing database schema

### Where to Document

- `/docs/SETUP.md` - Installation and setup
- `/docs/DATABASE.md` - Database schema and design
- `/README.md` - Project overview (keep current)
- Code comments - Explain complex logic
- Docstrings - Document all functions

### Documentation Example

Update `docs/DATABASE.md` if you add a new table:

## Users Table

Stores user account information.

| Column | Type | Description |
|--------|------|-------------|
| id | INT PRIMARY KEY | Unique identifier |
| email | VARCHAR(255) UNIQUE | User email |
| name | VARCHAR(255) | Full name |
| status | VARCHAR(20) | Account status (active, inactive, suspended) |
| created_at | TIMESTAMP | When account was created |

**Indexes:**
- `idx_users_email` on email
- `idx_users_status` on status

## Code Review Process

When your PR is reviewed:

1. **Feedback is about code, not you** - It's collaborative
2. **Respond to all comments** - Even if just to acknowledge
3. **Push fixes as new commits** - Don't force push
4. **Ask clarifying questions** - If feedback is unclear
5. **Thank reviewers** - When done

Example response:
```
Good point about error handling. I've added try/except blocks 
and updated the test cases to cover that scenario. 
Ready for another review.
```

## Common Issues

### "Tests are failing"

```bash
# Run tests locally first
make test

# See what changed
git diff

# Check test output
pytest --verbose
```

### "Merge conflicts"

```bash
# Update your branch with latest main
git fetch origin
git rebase origin/main

# Resolve conflicts in your editor
# Then continue
git rebase --continue
```

### "I have uncommitted changes on main"

```bash
# Save your work to a new branch
git stash
git checkout -b feature/my-feature
git stash pop

# Or start fresh
git checkout -b feature/my-feature
git add .
git commit -m "Work in progress"
```

## Getting Help

### Ask a Question

- Create a discussion in the repository
- Ask in Slack (if available)
- Comment on the issue you're working on

### Report a Bug

- Check if it's already reported
- Create an issue with:
  - What happened
  - What you expected
  - Steps to reproduce
  - Your environment (Python version, OS, etc.)

### Unsure About Something?

- Read the existing code
- Check documentation in `/docs/`
- Look at similar features already in code
- Ask before spending hours on the wrong approach!

## Summary

1. Fork and clone the repo
2. Create a feature branch
3. Make your changes
4. Write/update tests
5. Format code: `make format`
6. Run tests: `make test`
7. Commit with clear messages
8. Push and create a PR
9. Respond to code review feedback
10. Done! 🎉

Thank you for contributing!
