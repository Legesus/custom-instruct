---
name: Library Checker
description: Validates library/dependency syntax usage and version compatibility. Use when writing or reviewing code that uses external libraries.
version: 1.0.0
tags:
  - validation
  - dependencies
  - syntax
  - version-check
---

# Library Checker Skill

## Overview
This skill ensures that all library and dependency usage in your code follows correct syntax patterns and uses current, non-deprecated versions. It leverages **Context7 MCP** for real-time documentation lookups.

## When to Use This Skill
- **Before writing code** that uses a library you're unfamiliar with
- **During code review** to validate library usage patterns
- **When upgrading dependencies** to check for breaking changes
- **When encountering runtime errors** that might be caused by incorrect API usage
- **Periodically** to audit codebase for deprecated library features

## Workflow

### Step 1: Identify Libraries in Use
Scan the relevant files to identify:
- Import statements
- Package dependencies (package.json, requirements.txt, go.mod, etc.)
- Inline library calls

### Step 2: Resolve Library ID via Context7
For each library, use `mcp_context7_resolve-library-id`:
```
libraryName: [library name, e.g., "react", "flask", "express"]
query: [specific feature or API being used]
```

### Step 3: Query Documentation
Use `mcp_context7_query-docs` with the resolved library ID:
```
libraryId: [resolved ID from step 2]
query: [specific API or syntax question]
```

### Step 4: Validate Usage
Compare actual code usage against documentation:

| Check | Action |
|-------|--------|
| ✅ Correct syntax | Confirm and proceed |
| ⚠️ Deprecated API | Flag and suggest modern alternative |
| ❌ Incorrect usage | Flag and provide correct syntax |
| 📅 Outdated version | Recommend upgrade path |

> [!IMPORTANT]
> **Version Priority Rule:**
> 1. **Always recommend the latest version** of a library
> 2. **Only fall back to stable version** if the latest has critical bugs or instability issues

### Step 5: Report Findings
Generate a summary with:
- **Valid**: APIs used correctly
- **Warnings**: Deprecated or soon-to-be-deprecated features
- **Errors**: Incorrect syntax or missing required parameters
- **Recommendations**: Version upgrades or better alternatives

## Validation Checklist

### Syntax Validation
- [ ] All import paths are correct
- [ ] Function signatures match documentation
- [ ] Required parameters are provided
- [ ] Return types are handled correctly
- [ ] Async/await patterns are correct (if applicable)

### Version Validation
- [ ] Library version is the **latest available** (first priority)
- [ ] If latest is unstable, use **most stable version** (second priority)
- [ ] Library version is not deprecated
- [ ] No known security vulnerabilities
- [ ] Breaking changes from recent updates are addressed
- [ ] Lock file versions match package manifest

### Best Practices
- [ ] Using recommended patterns from official docs
- [ ] Not using anti-patterns flagged in documentation
- [ ] Error handling follows library conventions

## Output Format

```markdown
## Library Check Report

### Summary
- Libraries checked: X
- Valid: X
- Warnings: X
- Errors: X

### Details

#### ✅ [Library Name] v[version]
- Status: Valid
- Usage: Correct syntax and patterns

#### ⚠️ [Library Name] v[version]
- Status: Warning
- Issue: [description]
- Recommendation: [action to take]

#### ❌ [Library Name] v[version]
- Status: Error  
- Issue: [description]
- Correct Usage:
  ```[language]
  [correct code example]
  ```
```

## Examples

### Example 1: React Hook Validation
```
User: "Check if my useEffect usage is correct"
Agent: 
1. Resolves React library ID
2. Queries docs for useEffect
3. Validates cleanup function, dependency array
4. Reports missing dependencies or stale closures
```

### Example 2: Python Package Version Check
```
User: "Validate my Flask code and check for updates"
Agent:
1. Reads requirements.txt for Flask version
2. Queries Context7 for Flask docs
3. Compares usage against current version
4. Flags deprecated decorators or methods
```

### Example 3: Node.js Dependency Audit
```
User: "Check my Express middleware usage"
Agent:
1. Scans package.json for Express version
2. Reviews middleware registration
3. Validates error handling patterns
4. Recommends security middleware if missing
```

## Integration Notes

> [!IMPORTANT]
> This skill relies on **Context7 MCP** for documentation lookups. Ensure the MCP server is available before using this skill.

> [!TIP]
> Combine with `superpowers-review` skill for comprehensive code quality checks.

## Related Skills
- [superpowers-review](../../superpowers/.agent/skills/superpowers-review/SKILL.md) - General code review
- [superpowers-tdd](../../superpowers/.agent/skills/superpowers-tdd/SKILL.md) - Test-driven development
