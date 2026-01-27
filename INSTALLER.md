# 🚀 Repository Bootstrap & Module Installer

> [!IMPORTANT]
> **AI AGENT INSTRUCTIONS**: You have been loaded to facilitate the setup of this repository. Please follow the procedural steps below to assist the user.

## 🤖 Setup Instructions

If you are an AI assistant and this file has just been downloaded or shared with you, perform the following actions:

### 1. Identify Target Environment
Verify if the current directory is a fresh repository or an existing one. Ensure you have write access.

### 2. Module Selection & Configuration Scope
Ask the user: **"Which modules would you like to set up, and how should they be configured?"**

For each module, clarify if they want a **Global Configuration** (active in `template.txt`) or a **Local Setup** (files downloaded but inactive).

#### Options:
1.  **Config Retriever (Main Agent)**:
    - *Always Global*: This is the core orchestrator.
2.  **Superpowers (Antigravity)**:
    - **Global**: Download files + add `@include` to `template.txt`.
    - **Local**: Download files only.
3.  **Gemini CLI Settings**:
    - **Global**: Download files + add `@include` to `template.txt`.
    - **Local**: Download files only.
4.  **Antigravity Templates**: Custom rules, skills (including **Skill Writer**, **Code Simplifier**, **Library Checker**, **Frontend Design**, **Tool Calling Implementer**, and **Browser Control**), and workflows.
5.  **Full Suite (Global)**: Install and activate everything.

---

### 3. Structural Setup Guide (Final Implementation)

After the user makes their selection, use the following logic to organize the project:

#### A. Core Orchestration (.agent/)
- **Dir**: Create `.agent/skills/config-retriever/` at the ROOT.
- **Action**: Fetch `SKILL.md` and place it in that folder.
- **README**: Ensure the root `README.md` structure reflects the `/.agent` folder as the **Main Agent Folder**.

#### B. Antigravity Platform (antigravity/)
- **Dir**: Use `antigravity/` as the platform root.
- **Superpowers**: Nest the module at `antigravity/superpowers/.agent/`.
- **Templates**: Ensure `rules/`, `skills/`, and `workflows/` folders are present under `antigravity/`.

#### C. Manifest Configuration (template.txt)
- **Check**: If `template.txt` does not exist, create it at the ROOT.
- **Global Setup**: For every "Global" selection, add an `@include` line pointing to the absolute/relative path of the main configuration file (e.g., `superpowers.md` or `GEMINI.md`).
- **Organization**: Group `@include` lines by platform (e.g., `## Antigravity`, `## Gemini CLI`).

---

### 4. Execution Logic (Source Mapping)
Download files from the following paths at: `https://raw.githubusercontent.com/Legesus/custom-instruct/main/`

#### A. Config Retriever (Main Agent)
- Path: [SKILL.md](https://raw.githubusercontent.com/Legesus/custom-instruct/main/.agent/skills/config-retriever/SKILL.md)
- Target: `.agent/skills/config-retriever/SKILL.md`

#### B. Superpowers Module
- **Rules**: [superpowers.md](https://raw.githubusercontent.com/Legesus/custom-instruct/main/antigravity/superpowers/.agent/rules/superpowers.md)
- **Skills**:
    - [superpowers-brainstorm/SKILL.md](https://raw.githubusercontent.com/Legesus/custom-instruct/main/antigravity/superpowers/.agent/skills/superpowers-brainstorm/SKILL.md)
    - [superpowers-plan/SKILL.md](https://raw.githubusercontent.com/Legesus/custom-instruct/main/antigravity/superpowers/.agent/skills/superpowers-plan/SKILL.md)
    - [superpowers-tdd/SKILL.md](https://raw.githubusercontent.com/Legesus/custom-instruct/main/antigravity/superpowers/.agent/skills/superpowers-tdd/SKILL.md)
    - [superpowers-review/SKILL.md](https://raw.githubusercontent.com/Legesus/custom-instruct/main/antigravity/superpowers/.agent/skills/superpowers-review/SKILL.md)
    - [superpowers-debug/SKILL.md](https://raw.githubusercontent.com/Legesus/custom-instruct/main/antigravity/superpowers/.agent/skills/superpowers-debug/SKILL.md)
    - [superpowers-finish/SKILL.md](https://raw.githubusercontent.com/Legesus/custom-instruct/main/antigravity/superpowers/.agent/skills/superpowers-finish/SKILL.md)
    - [superpowers-python-automation/SKILL.md](https://raw.githubusercontent.com/Legesus/custom-instruct/main/antigravity/superpowers/.agent/skills/superpowers-python-automation/SKILL.md)
    - [superpowers-rest-automation/SKILL.md](https://raw.githubusercontent.com/Legesus/custom-instruct/main/antigravity/superpowers/.agent/skills/superpowers-rest-automation/SKILL.md)
    - [superpowers-workflow/SKILL.md](https://raw.githubusercontent.com/Legesus/custom-instruct/main/antigravity/superpowers/.agent/skills/superpowers-workflow/SKILL.md)
- **Workflows**:
    - [superpowers-brainstorm.md](https://raw.githubusercontent.com/Legesus/custom-instruct/main/antigravity/superpowers/.agent/workflows/superpowers-brainstorm.md)
    - [superpowers-execute-plan.md](https://raw.githubusercontent.com/Legesus/custom-instruct/main/antigravity/superpowers/.agent/workflows/superpowers-execute-plan.md)
    - [superpowers-execute-plan-parallel.md](https://raw.githubusercontent.com/Legesus/custom-instruct/main/antigravity/superpowers/.agent/workflows/superpowers-execute-plan-parallel.md)
    - [superpowers-write-plan.md](https://raw.githubusercontent.com/Legesus/custom-instruct/main/antigravity/superpowers/.agent/workflows/superpowers-write-plan.md)
    - [superpowers-debug.md](https://raw.githubusercontent.com/Legesus/custom-instruct/main/antigravity/superpowers/.agent/workflows/superpowers-debug.md)
    - [superpowers-finish.md](https://raw.githubusercontent.com/Legesus/custom-instruct/main/antigravity/superpowers/.agent/workflows/superpowers-finish.md)
    - [superpowers-reload.md](https://raw.githubusercontent.com/Legesus/custom-instruct/main/antigravity/superpowers/.agent/workflows/superpowers-reload.md)
    - [superpowers-review.md](https://raw.githubusercontent.com/Legesus/custom-instruct/main/antigravity/superpowers/.agent/workflows/superpowers-review.md)

#### C. Antigravity Core
- **Rules**:
    - [RULES_TEMPLATE.md](https://raw.githubusercontent.com/Legesus/custom-instruct/main/antigravity/rules/RULES_TEMPLATE.md)
    - [browser-control.md](https://raw.githubusercontent.com/Legesus/custom-instruct/main/antigravity/rules/browser-control.md)
- **Templates**:
    - [SKILL_TEMPLATE.md](https://raw.githubusercontent.com/Legesus/custom-instruct/main/antigravity/skills/SKILL_TEMPLATE.md)
    - [WORKFLOW_TEMPLATE.md](https://raw.githubusercontent.com/Legesus/custom-instruct/main/antigravity/workflows/WORKFLOW_TEMPLATE.md)
- **Skills**:
    - [skill-writer/SKILL.md](https://raw.githubusercontent.com/Legesus/custom-instruct/main/antigravity/skills/skill-writer/SKILL.md)
    - [code-simplifier/SKILL.md](https://raw.githubusercontent.com/Legesus/custom-instruct/main/antigravity/skills/code-simplifier/SKILL.md)
    - [pentester-research/SKILL.md](https://raw.githubusercontent.com/Legesus/custom-instruct/main/antigravity/skills/pentester-research/SKILL.md)
    - [library-checker/SKILL.md](https://raw.githubusercontent.com/Legesus/custom-instruct/main/antigravity/skills/library-checker/SKILL.md)
    - [frontend-design/SKILL.md](https://raw.githubusercontent.com/Legesus/custom-instruct/main/antigravity/skills/frontend-design/SKILL.md)
    - [tool-calling-implementer/SKILL.md](https://raw.githubusercontent.com/Legesus/custom-instruct/main/antigravity/skills/tool-calling-implementer/SKILL.md)
    - [browser-control/SKILL.md](https://raw.githubusercontent.com/Legesus/custom-instruct/main/antigravity/skills/browser-control/SKILL.md)
- **Workflows**:
    - [writethisdown.md](https://raw.githubusercontent.com/Legesus/custom-instruct/main/antigravity/workflows/writethisdown.md)

#### D. Gemini CLI & General
- [GEMINI_TEMPLATE.md](https://raw.githubusercontent.com/Legesus/custom-instruct/main/gemini-cli/config/GEMINI_TEMPLATE.md)
- [devcontainer.md](https://raw.githubusercontent.com/Legesus/custom-instruct/main/general/uncategorized/devcontainer.md)

---

### 5. Finalization
- Update `template.txt` at the root if any "Global" options were selected.
- Provide a summary of installed components and their configuration status (Global vs Local).
- Offer to run a "Health Check" by listing the files.

---

## 🛠️ Usage for Humans

To bootstrap a new environment with these settings, run one of the following commands in your terminal:

**Terminal (Bash/Zsh)**:
```bash
curl -L -o INSTALLER.md https://raw.githubusercontent.com/Legesus/custom-instruct/main/INSTALLER.md
```

**PowerShell**:
```powershell
Invoke-WebRequest -Uri "https://raw.githubusercontent.com/Legesus/custom-instruct/main/INSTALLER.md" -OutFile "INSTALLER.md"
```

Then, point your AI assistant to this file and say: **"Follow the instructions in INSTALLER.md to set up my environment."**
