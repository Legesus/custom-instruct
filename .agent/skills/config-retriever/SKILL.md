---
name: Config Retriever
description: Helps users discover, browse, and select configurations from the settings repository.
version: 1.0.0
tags:
  - utility
  - configuration
  - retrieval
---

# Config Retriever Skill

## Overview
This skill helps you navigate and manage configurations in your central settings repository. Use it to:
- **List** all available configurations across platforms (Antigravity, Gemini CLI, General)
- **Search** for specific topics or keywords
- **Preview** the contents of a configuration file
- **Add** configurations to your active manifest (template.txt)

## Repository Structure
```
/settings-repo
├── .agent/                   # Main Agent Folder (Orchestration)
│   └── skills/
│       └── config-retriever/
├── template.txt              # The "Brain" - central manifest
├── general/                  # Platform-agnostic settings
│   ├── workflows/
│   └── uncategorized/
├── antigravity/              # Antigravity-specific
│   ├── rules/
│   ├── skills/
│   ├── workflows/
│   └── superpowers/          # Superpowers module
└── gemini-cli/               # Gemini CLI specific
    └── config/
```

## Usage Instructions

### 1. List All Configurations
Ask the agent:
> "List all available configurations in this repo"

The agent will scan all folders and return a categorized list.

### 2. Search for Specific Configs
Ask the agent:
> "Find configs related to [topic]"

Example: "Find configs related to Python" or "Find configs for workflows"

### 3. Preview a Configuration
Ask the agent:
> "Show me the contents of [path]"

Example: "Show me the contents of antigravity/rules/RULES_TEMPLATE.md"

### 4. Add to Active Configurations
Ask the agent:
> "Add [path] to my active configurations"

This will update template.txt to include the specified configuration.

### 5. Remove from Active Configurations
Ask the agent:
> "Remove [path] from my active configurations"

This will comment out the line in template.txt.

## Examples

### Example 1: Browse by Platform
```
User: "What Antigravity configurations are available?"
Agent: Lists all files under antigravity/
```

### Example 2: Quick Setup
```
User: "Set me up with the standard Antigravity rules and workflows"
Agent: Adds @include lines for rules and workflows to template.txt
```

### Example 3: Find and Add
```
User: "Find anything about coding standards and add it"
Agent: Searches for matching files, presents options, adds selected ones
```

## Notes
- The Brain (template.txt) uses `@include` syntax for compatibility with Gemini CLI.
- Configurations are loaded hierarchically - more specific overrides general.
- Use `/memory refresh` in Gemini CLI after updating template.txt.

## Related Skills
- [SKILL_TEMPLATE.md](./SKILL_TEMPLATE.md) - Template for creating new skills
