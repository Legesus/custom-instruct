# Gemini CLI Rules (GEMINI.md)
# Place this file at the root of your project or in ~/.gemini/GEMINI.md for global rules.

## Project Overview
- **Name**: My Project
- **Tech Stack**: Python, FastAPI, PostgreSQL
- **Architecture**: Microservices with REST APIs

## Coding Standards
- All Python code must follow PEP 8 style.
- Use type hints for all function signatures.
- Prefer f-strings over .format() or % formatting.

## Forbidden Actions
- DO NOT modify or open `.env`, `secrets.yaml`, or `terraform.tfstate`.
- DO NOT commit directly to `main` branch.

## Build & Test Commands
```bash
# Build
python -m build

# Test
pytest -v

# Lint
ruff check .
```

## Include Additional Context
# Use @include to modularize your rules:
# @./docs/api-guidelines.md
# @./docs/database-conventions.md

## Memory Commands
# Use these in the CLI:
# /memory show    - View current context
# /memory refresh - Reload after changes to GEMINI.md
