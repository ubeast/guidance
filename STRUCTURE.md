# Project File Structure Guide

A standardized directory structure for Python and SQL projects.

## Minimal Project Structure

Start with this core structure:

```
project-root/
├── src/                  # Your Python package
├── sql/                  # SQL migrations and queries
├── tests/                # Tests
├── docs/                 # Documentation
└── README.md             # Information on your project
```

## Minimum for Building a Wheel

To create a distributable Python wheel, you need at minimum:

```
project-root/
├── src/package_name/     # Your Python package
│   └── __init__.py       # Required: makes it a package
├── pyproject.toml        # Required: build configuration
├── setup.py              # Required: package metadata
├── README.md
└── LICENSE
```

Then build with:
```bash
python -m build
```

This creates a `.whl` file in `dist/` that can be installed with `pip install`.

## Full Project Structure

As your project grows, expand to this complete structure:

```
project-root/
├── .git/                      # Git configuration and history
├── .gitignore                 # Files to ignore in version control
├── README.md                  # Project overview and setup
├── LICENSE                    # Project license
├── docs/                      # Project documentation
│   ├── SETUP.md               # Installation and setup instructions
│   ├── DATABASE.md            # Database schema and design (if applicable)
│   └── references/            # PDF reference materials (optional)
│       ├── api-specification.pdf
│       └── database-schema.pdf
├── src/                       # Python source code
│   └── package_name/          # Your Python package
│       ├── __init__.py
│       ├── main.py
│       ├── utilities (sample)/# Utility functions module
│       │   ├── __init__.py
│       │   └── helpers.py
│       ├── cleansing (sample)/# Data cleansing module
│       │   ├── __init__.py
│       │   └── data_cleaning.py
│       └── database (sampl3e)/# Database module
│           ├── __init__.py
│           └── queries.py
├── sql/                       # SQL scripts and migrations
│   ├── migrations/            # Database migrations
│   │   ├── 001_initial.sql
│   │   └── 002_add_table.sql
│   └── queries/               # Reusable SQL queries
│       └── example.sql
├── tests/                     # Unit and integration tests
│   ├── fixtures/              # Sample data for tests
│   │   ├── users.csv
│   │   └── sample_data.sql
│   └── test_main.py
├── data/                      # Sample datasets for development (optional)
│   ├── users.csv
│   ├── transactions.csv
│   └── README.md
├── .env.example               # Template for environment variables
├── pyproject.toml             # Python package configuration
├── setup.py                   # Package setup script
└── requirements.txt           # Project dependencies
```

## Directory Details

### `/src/package_name` - Python Package

Your application code goes here. The directory name must match your package name. Organize related code into modules:

```
src/package_name/
├── __init__.py                # Makes it a Python package
├── main.py                    # Main application logic
├── utilities/                 # Utility functions module
│   ├── __init__.py
│   ├── helpers.py
│   └── validators.py
├── cleansing/                 # Data cleansing module
│   ├── __init__.py
│   ├── text_cleaning.py
│   └── data_validation.py
└── database/                  # Database module
    ├── __init__.py
    ├── models.py
    └── queries.py
```

**Module structure example:**

Each module is a directory with an `__init__.py` file. This allows organized code:

```python
# src/package_name/utilities/__init__.py
from .helpers import format_date, parse_input
from .validators import validate_email, validate_phone

__all__ = ["format_date", "parse_input", "validate_email", "validate_phone"]
```

Then import from modules:
```python
from package_name.utilities import validate_email
from package_name.cleansing import clean_text
from package_name.database import get_user
```

### `/sql` - Database Scripts

All SQL code lives here, organized by purpose.

**Migrations** - Sequential database changes
```
migrations/
├── 001_initial_schema.sql
├── 002_add_users_table.sql
└── 003_add_indexes.sql
```

**Queries** - Reusable SQL queries
```
queries/
├── get_user.sql
├── list_users.sql
└── create_user.sql
```

### `/docs` - Documentation

- `SETUP.md` - How to install and run the project
- `DATABASE.md` - Database schema documentation (if applicable)
- `references/` - PDF reference materials (optional)
  - `api-specification.pdf`
  - `database-schema.pdf`
  - Any other reference PDFs

### `/data` - Sample Datasets (Optional)

Sample data for local development and testing.

```
data/
├── users.csv
├── transactions.csv
└── README.md
```

### `/tests` - Tests

Write tests for your Python code here. Use `/tests/fixtures/` for test data.

```
tests/
├── fixtures/
│   ├── users.csv
│   └── sample_data.sql
├── test_main.py
└── test_utils.py
```

## Required Root Files

| File | Purpose |
|------|---------|
| `pyproject.toml` | Python package configuration and build settings |
| `setup.py` | Package metadata and installation script |
| `requirements.txt` | Project dependencies |
| `.env.example` | Template for environment variables |
| `.gitignore` | Files to exclude from git |
| `README.md` | Project overview |


## What Goes Where

| Item | Location |
|---|---|
| Python code | `/src/package_name/` |
| Tests | `/tests/` |
| Test data/fixtures | `/tests/fixtures/` |
| Sample datasets | `/data/` (optional) |
| Database migrations | `/sql/migrations/` |
| SQL queries | `/sql/queries/` |
| Setup instructions | `/docs/SETUP.md` |
| Database docs | `/docs/DATABASE.md` |
| Reference PDFs | `/docs/references/` (optional) |
| Environment setup | `.env.example` |
| Package config | `pyproject.toml` and `setup.py` |


## File Naming

- **Python files:** `snake_case` (e.g., `my_module.py`)
- **SQL files:** `snake_case` (e.g., `get_user.sql`)
- **Migrations:** Start with number (e.g., `001_initial.sql`, `002_add_table.sql`)
- **Directories:** lowercase

## Quick Tips

- Keep business logic in `/src`, not in tests or scripts
- Write SQL in `/sql`, import and use it from Python
- Always add dependencies to `requirements.txt`
- Add environment variables to `.env.example` (without secrets)
- Run tests before committing: `make test`
- Never commit `.env` file (only `.env.example`)
- Never commit `build/`, `dist/`, `*.egg-info/`, `__pycache__`

## Getting Started

1. Read `docs/SETUP.md` for installation
2. Explore `/src/package_name/` to understand the code structure
4. Run `pytest` to verify everything works
