---
name: skill-writer
description: Guide users through creating Agent Skills for Antigravity. Use when creating, writing, or designing new skills, or when helping with SKILL.md files, frontmatter, or skill structure.
version: 1.0.0
tags:
  - meta
  - authoring
  - utility
---

# Skill Writer

This skill helps you create well-structured Agent Skills for Antigravity that follow best practices and validation requirements.

## When to Use This Skill

Use this skill when:
- Creating a new Agent Skill
- Writing or updating `SKILL.md` files
- Designing skill structure and frontmatter
- Troubleshooting skill discovery issues
- Converting existing prompts or workflows into skills

## Instructions

### Step 1: Determine Skill Scope

First, understand what the skill should do:

1. **Ask clarifying questions**:
   - What specific capability should this skill provide?
   - When should the agent use this skill?
   - What tools or resources does it need?
   - Is this for project-specific use or repository-wide sharing?

2. **Keep it focused**: One skill = one capability
   - ✅ Good: "PDF form filling", "Excel data analysis"
   - ❌ Too broad: "Document processing", "Data tools"

### Step 2: Choose Skill Location

Determine where to create the skill:

**Project Skills** (`.agent/skills/`):
- Team workflows and conventions
- Project-specific expertise
- Shared utilities (committed to git)

**Repository Skills** (`antigravity/skills/`):
- Skills for this custom-instruct repository
- Reusable across multiple projects

### Step 3: Create Skill Structure

Create the directory and files:

```bash
# Project skill
mkdir -p .agent/skills/skill-name

# Repository skill (for this repo)
mkdir -p antigravity/skills/skill-name
```

For multi-file skills:
```
skill-name/
├── SKILL.md (required)
├── reference.md (optional)
├── examples.md (optional)
├── scripts/
│   └── helper.py (optional)
└── templates/
    └── template.txt (optional)
```

### Step 4: Write SKILL.md Frontmatter

Create YAML frontmatter with required fields:

```yaml
---
name: skill-name
description: Brief description of what this does and when to use it
version: 1.0.0
tags:
  - category1
  - category2
---
```

**Field requirements**:

- **name**:
  - Lowercase letters, numbers, hyphens only
  - Max 64 characters
  - Must match directory name
  - ✅ Good: `pdf-processor`, `git-commit-helper`
  - ❌ Bad: `PDF_Processor`, `Git Commits!`

- **description**:
  - Max 1024 characters
  - Include BOTH what it does AND when to use it
  - Use specific trigger words users would say
  - Mention file types, operations, and context

- **version**: Semantic version (e.g., `1.0.0`)

- **tags**: Categorization for discovery

### Step 5: Write Effective Descriptions

The description is critical for the agent to discover your skill.

**Formula**: `[What it does] + [When to use it] + [Key triggers]`

**Examples**:

✅ **Good**:
```yaml
description: Extract text and tables from PDF files, fill forms, merge documents. Use when working with PDF files or when the user mentions PDFs, forms, or document extraction.
```

✅ **Good**:
```yaml
description: Analyze Excel spreadsheets, create pivot tables, and generate charts. Use when working with Excel files, spreadsheets, or analyzing tabular data in .xlsx format.
```

❌ **Too vague**:
```yaml
description: Helps with documents
description: For data analysis
```

**Tips**:
- Include specific file extensions (.pdf, .xlsx, .json)
- Mention common user phrases ("analyze", "extract", "generate")
- List concrete operations (not generic verbs)
- Add context clues ("Use when...", "For...")

### Step 6: Structure the Skill Content

Reference `antigravity/skills/SKILL_TEMPLATE.md` for the standard structure:

```markdown
# Skill Name

Brief overview of what this skill does.

## Overview
Briefly describe the skill's purpose and when the agent should invoke it.

## Prerequisites
- List any required tools, APIs, or dependencies.

## Usage Instructions
1. Step one of how to use the skill.
2. Step two (be specific about inputs and expected outputs).
3. Step three.

## Examples

### Example 1: Basic Usage
```bash
# Example command or code snippet
example_command --flag value
```

### Example 2: Advanced Usage
```bash
# More complex example
example_command --advanced --options
```

## Notes
- Any caveats, limitations, or best practices.
- Consider edge cases.

## Related Skills
- [Another Skill](../another-skill/SKILL.md)
```

### Step 7: Add Supporting Files (Optional)

Create additional files for progressive disclosure:

- **reference.md**: Detailed API docs, advanced options
- **examples.md**: Extended examples and use cases
- **scripts/**: Helper scripts and utilities
- **templates/**: File templates or boilerplate

Reference them from SKILL.md:
```markdown
For advanced usage, see [reference.md](reference.md).
```

### Step 8: Validate the Skill

Check these requirements:

✅ **File structure**:
- [ ] `SKILL.md` exists in correct location
- [ ] Directory name matches frontmatter `name`

✅ **YAML frontmatter**:
- [ ] Opening `---` on line 1
- [ ] Closing `---` before content
- [ ] Valid YAML (no tabs, correct indentation)
- [ ] `name` follows naming rules
- [ ] `description` is specific and < 1024 chars
- [ ] `version` is present
- [ ] `tags` array is present

✅ **Content quality**:
- [ ] Follows `SKILL_TEMPLATE.md` structure
- [ ] Clear instructions for the agent
- [ ] Concrete examples provided
- [ ] Edge cases handled
- [ ] Dependencies listed (if any)

### Step 9: Test the Skill

1. **Verify skill appears** in available skills list

2. **Ask relevant questions** that match the description:
   ```
   Can you help me extract text from this PDF?
   ```

3. **Verify activation**: The agent should use the skill automatically

4. **Check behavior**: Confirm the agent follows the instructions correctly

### Step 10: Debug If Needed

If the agent doesn't use the skill:

1. **Make description more specific**:
   - Add trigger words
   - Include file types
   - Mention common user phrases

2. **Check file location**:
   ```bash
   # Project skill
   ls .agent/skills/skill-name/SKILL.md
   
   # Repository skill
   ls antigravity/skills/skill-name/SKILL.md
   ```

3. **Validate YAML**:
   ```bash
   cat SKILL.md | head -n 10
   ```

## Common Patterns

### Read-Only Skill
```yaml
---
name: code-reader
description: Read and analyze code without making changes. Use for code review, understanding codebases, or documentation.
version: 1.0.0
tags:
  - analysis
  - review
---
```

### Script-Based Skill
```yaml
---
name: data-processor
description: Process CSV and JSON data files with Python scripts. Use when analyzing data files or transforming datasets.
version: 1.0.0
tags:
  - data
  - automation
---

# Data Processor

## Instructions

1. Use the processing script:
```bash
python scripts/process.py input.csv --output results.json
```

2. Validate output with:
```bash
python scripts/validate.py results.json
```
```

### Multi-File Skill
```yaml
---
name: api-designer
description: Design REST APIs following best practices. Use when creating API endpoints, designing routes, or planning API architecture.
version: 1.0.0
tags:
  - api
  - design
---

# API Designer

Quick start: See [examples.md](examples.md)

Detailed reference: See [reference.md](reference.md)

## Instructions

1. Gather requirements
2. Design endpoints (see examples.md)
3. Document with OpenAPI spec
4. Review against best practices (see reference.md)
```

## Best Practices

1. **One skill, one purpose**: Don't create mega-skills
2. **Specific descriptions**: Include trigger words users will say
3. **Clear instructions**: Write for the agent, not just humans
4. **Concrete examples**: Show real code, not pseudocode
5. **List dependencies**: Mention required packages in description
6. **Use `SKILL_TEMPLATE.md`**: Follow the standard structure
7. **Version your skills**: Update `version` when making changes
8. **Use progressive disclosure**: Put advanced details in separate files

## Validation Checklist

Before finalizing a skill, verify:

- [ ] Name is lowercase, hyphens only, max 64 chars
- [ ] Description is specific and < 1024 chars
- [ ] Description includes "what" and "when"
- [ ] Version follows semantic versioning
- [ ] Tags array is populated
- [ ] YAML frontmatter is valid
- [ ] Instructions are step-by-step
- [ ] Examples are concrete and realistic
- [ ] Dependencies are documented
- [ ] Follows `SKILL_TEMPLATE.md` structure
- [ ] Skill activates on relevant queries
- [ ] Agent follows instructions correctly

## Troubleshooting

**Skill doesn't activate**:
- Make description more specific with trigger words
- Include file types and operations in description
- Add "Use when..." clause with user phrases

**Multiple skills conflict**:
- Make descriptions more distinct
- Use different trigger words
- Narrow the scope of each skill

**Skill has errors**:
- Check YAML syntax (no tabs, proper indentation)
- Verify file paths (use forward slashes)
- Ensure scripts have execute permissions
- List all dependencies

## Output Format

When creating a skill, I will:

1. Ask clarifying questions about scope and requirements
2. Suggest a skill name and location
3. Create the `SKILL.md` file with proper frontmatter
4. Follow `SKILL_TEMPLATE.md` structure
5. Include clear instructions and examples
6. Add supporting files if needed
7. Provide testing instructions
8. Validate against all requirements

The result will be a complete, working skill that follows Antigravity best practices and validation rules.

## Related Skills

- [SKILL_TEMPLATE.md](../SKILL_TEMPLATE.md) - Template for creating new skills
- [config-retriever](../../../.agent/skills/config-retriever/SKILL.md) - Browse and manage configurations
