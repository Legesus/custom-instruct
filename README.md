# Settings Repository

This repository centralizes configurations for AI agents, CLI tools, and general development rules.

## Structure

- `/.agent`: **Main Agent Folder**. Contains core skills like the `config-retriever` for repository orchestration.
- `/general`: Platform-agnostic rules, workflows, and uncategorized docs.
- `/antigravity`: Skills and workflows specifically for the Antigravity agent (including the `superpowers` module, `skill-writer`, and `code-simplifier` skills).
- `/gemini-cli`: Configurations and documentation for the Gemini CLI.

## How to Initialize
To quickly set up this repository in a new environment:
1.  **Download Installer**:
    - **Terminal (Bash/Zsh)**: `curl -L -o INSTALLER.md https://raw.githubusercontent.com/Legesus/custom-instruct/main/INSTALLER.md`
    - **PowerShell**: `Invoke-WebRequest -Uri "https://raw.githubusercontent.com/Legesus/custom-instruct/main/INSTALLER.md" -OutFile "INSTALLER.md"`
2.  **Bootstrap**: Tell your AI agent: *"Follow the instructions in INSTALLER.md to set up my environment."*

## How to use the template

Edit `template.txt` at the root to include the specific instructions you want to load for a given session.
