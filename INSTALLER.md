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
4.  **Full Suite (Global)**: Install and activate everything.

### 3. Execution Logic
Once selection is made, download files from: `https://github.com/Legesus/custom-instruct`.

#### A. Config Retriever (Main Agent)
- Create directory `.agent/skills/config-retriever/`
- Download `SKILL.md` to that folder.
- **Always update `README.md`** to include the `/.agent` structure.

#### B. Superpowers Module
- Create directory `antigravity/superpowers/.agent/`
- Download `rules/`, `skills/`, and `workflows/` contents.
- **If Global**: Update `template.txt` with Superpowers `@include` lines.

#### C. Gemini CLI Settings
- Create directory `gemini-cli/config/`
- Download `GEMINI.md` (or relevant templates).
- **If Global**: Update `template.txt` with Gemini CLI `@include` lines.

#### D. Finalization
- Update `template.txt` at the root if any "Global" options were selected.
- Provide a summary of installed components and their configuration status (Global vs Local).
- Offer to run a "Health Check" by listing the files.

---

## 🛠️ Usage for Humans

To bootstrap a new environment with these settings, run the following command in your terminal:

```bash
curl -L -o INSTALLER.md https://raw.githubusercontent.com/Legesus/custom-instruct/main/INSTALLER.md
```

Then, point your AI assistant to this file and say: **"Follow the instructions in INSTALLER.md to set up my environment."**
