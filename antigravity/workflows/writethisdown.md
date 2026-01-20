---
description: Capture and organize research notes, tech insights, and useful information into a structured notes.md file
---

# Write This Down - Research Notes Workflow

## Purpose
Create and maintain a centralized `notes.md` file to capture:
- Useful and unique information from conversations
- Technology insights with pros, cons, and edge cases
- Research findings and references

---

## Steps

### 1. Check for Existing Notes
// turbo
Check if `notes.md` exists in the project root folder. If not, create it with the following template:

```markdown
# Research Notes

> Last Updated: [DATE]

## Table of Contents
<!-- Auto-updated as sections are added -->

---

## Quick Reference
<!-- Key findings and frequently accessed info -->

---

## Technology Notes
<!-- Tech-specific research -->

---

## Insights & Ideas
<!-- General observations and brainstorming -->
```

### 2. Categorize New Information
Before adding content, determine which category it belongs to:
- **Technology Notes**: Libraries, frameworks, APIs, tools
- **Quick Reference**: Commands, snippets, configurations
- **Insights & Ideas**: Observations, potential improvements, brainstorming

### 3. Research Technology Mentions
When a technology is mentioned:
1. Note the technology name and version (if applicable)
2. Research and document:
   - **Pros**: Key benefits and strengths
   - **Cons**: Limitations and drawbacks
   - **Edge Cases**: Known issues, gotchas, and special considerations
   - **Alternatives**: Similar tools/libraries worth considering
3. Include relevant links to official documentation

### 4. Update the Notes File
Add the new information under the appropriate section using this structure:

```markdown
### [Topic Name]
> Added: [DATE]

**Summary**: Brief description

**Details**:
- Key point 1
- Key point 2

**Pros**:
- ✅ Benefit 1
- ✅ Benefit 2

**Cons**:
- ⚠️ Limitation 1
- ⚠️ Limitation 2

**Edge Cases**:
- 🔍 Case 1
- 🔍 Case 2

**Links**:
- [Official Docs](url)
```

### 5. Update Table of Contents
// turbo
After adding new sections, update the Table of Contents with links to the new headings.

---

## Best Practices
- Keep notes concise and scannable
- Use consistent formatting throughout
- Include dates for temporal context
- Link to external sources when referencing documentation
- Remove outdated information periodically
