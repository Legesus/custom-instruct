---
name: Tool Calling Implementer
description: Identifies opportunities to use tool calls in your codebase and defines the necessary schemas.
tags:
  - agent-design
  - tool-use
  - architecture
---

# Tool Calling Implementer Skill

## Overview
This skill helps you identify parts of your codebase that would benefit from being converted into tool calls for an AI agent. By moving logic to tools, you increase determinism, capability, and safety.

## When to Use tools
Use this skill when:
- You are designing an agent's capability set.
- You have a large codebase and want to expose parts of it to an agent.
- You see complex logic that an L LM struggles to execute reliably in pure text generation.

## Heuristics for Tool Identification

Look for these patterns in your code:

1.  **API Clients / SDK Wrappers**: 
    - *Pattern*: Classes that wrap REST APIs or external services.
    - *Tool Strategy*: Map each major endpoint method to a distinct tool (e.g., `search_users`, `post_message`).

2.  **File System Operations**:
    - *Pattern*: Code that reads, writes, or searches files.
    - *Tool Strategy*: Define strictly scoped tools like `read_config_file` or `append_log` rather than generic `exec_python`.

3.  **Complex Data Parsing/Regex**:
    - *Pattern*: Fragile regex or specific parsing logic (e.g., log parsing, PDF scraping).
    - *Tool Strategy*: Create a tool that takes the raw input and returns structured JSON. Don't ask the LLM to parse it; give it a tool to *do* the parsing.

4.  **Database Interactions**:
    - *Pattern*: SQL queries or ORM calls.
    - *Tool Strategy*: Create high-level tools like `get_customer_history(id)` instead of a generic `run_sql_query` tool (unless for a specific DB-admin agent).

5.  **Deterministic Calculations**:
    - *Pattern*: Math, date manipulation, or cryptographic functions.
    - *Tool Strategy*: Always offload math and specific logic to code tools.

## Implementation Workflow

To implement a tool call:

1.  **Analyze**: Pick a function or capability.
2.  **Define Schema**: precise JSON schema for arguments.
    ```json
    {
      "name": "search_database",
      "description": "Searches the customer database by name.",
      "parameters": {
        "type": "object",
        "properties": {
          "query": { "type": "string", "description": "The name to search for" }
        },
        "required": ["query"]
      }
    }
    ```
3.  **Implement Handler**: Write the actual Python/Go/TS function receives the arguments and returns a string or JSON result.
4.  **Register**: Add the tool definition to your agent's context.

## Example Scenario

**Before (Prompt Engineering)**:
"Read the file 'data.txt', calculate the average of the numbers in column 3, and tell me the result."

**After (Tool Calling)**:
1.  Agent calls `read_file(path='data.txt')`.
2.  Agent sees content.
3.  Agent calls `calculate_stats(data=[...])`.
4.  Tool returns `{ "average": 42.5 }`.
5.  Agent responds: "The average is 42.5."
