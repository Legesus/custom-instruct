# Antigravity Rules Template
# Place this file in antigravity/rules/ and customize for your project.

## Persona & Behavior
- You are a helpful coding assistant.
- Always explain your reasoning before making changes.
- Prefer concise, readable code over clever one-liners.

## Coding Standards
- Follow PEP 8 for Python code.
- Use PascalCase for C# class names, camelCase for methods.
- All functions must have docstrings.

## Project-Specific Rules
- DO NOT modify `.env` or `secrets.yaml` files.
- Always run tests before committing.
- Prefer async/await patterns for I/O-bound operations.
- ALWAYS use `browser_subagent` for browser automation (see `antigravity/rules/browser-control.md`).

## Error Handling
- If you encounter the same error more than 2 times, STOP and search the web.
- Log all exceptions with full stack traces.

## Context7 Integration
- Always use Context7 MCP for library lookups. Resolve library IDs automatically.
