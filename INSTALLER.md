# 🚀 Repository Bootstrap & Module Installer

> [!IMPORTANT]
> **AI AGENT INSTRUCTIONS**: You have been loaded to facilitate the setup of this repository. Please follow the procedural steps below to assist the user.

## 📂 Understanding Deployment Structures

> [!NOTE]
> **Repo vs. Local Deployment**: The source repository structure differs from the target local deployment structure. Although modules like Superpowers are organized separately in the repo (`antigravity/superpowers/.agent/`), they are **unified** into a single `.agent/` folder during local deployment.

### Repository Structure (Source)
```
custom-instruct/
├── .agent/skills/config-retriever/          # Config Retriever
├── antigravity/
│   ├── rules/                               # Antigravity rules
│   ├── skills/                              # Antigravity skills
│   ├── workflows/                           # Antigravity workflows
│   └── superpowers/.agent/                  # Superpowers module (separate)
│       ├── rules/
│       ├── skills/
│       └── workflows/
└── gemini-cli/                              # Gemini CLI configs
```

### Local Deployment Structure (Target: `<workspace>`)
```
<workspace>/
└── .agent/
    ├── rules/
    │   ├── browser-control.md               # From antigravity/rules/
    │   └── superpowers.md                   # From antigravity/superpowers/.agent/rules/
    ├── skills/
    │   ├── config-retriever/                # Core orchestrator
    │   ├── browser-control/                 # From antigravity/skills/
    │   ├── frontend-design/                 # From antigravity/skills/
    │   ├── library-checker/                 # From antigravity/skills/
    │   ├── skill-writer/                    # From antigravity/skills/
    │   ├── superpowers-brainstorm/          # From antigravity/superpowers/.agent/skills/
    │   ├── superpowers-debug/               # From antigravity/superpowers/.agent/skills/
    │   ├── superpowers-finish/              # From antigravity/superpowers/.agent/skills/
    │   ├── superpowers-plan/                # From antigravity/superpowers/.agent/skills/
    │   ├── superpowers-python-automation/   # From antigravity/superpowers/.agent/skills/
    │   ├── superpowers-rest-automation/     # From antigravity/superpowers/.agent/skills/
    │   ├── superpowers-review/              # From antigravity/superpowers/.agent/skills/
    │   ├── superpowers-tdd/                 # From antigravity/superpowers/.agent/skills/
    │   └── superpowers-workflow/            # From antigravity/superpowers/.agent/skills/
    └── workflows/
        ├── superpowers-brainstorm.md        # From antigravity/superpowers/.agent/workflows/
        ├── superpowers-debug.md             # From antigravity/superpowers/.agent/workflows/
        ├── superpowers-execute-plan.md      # From antigravity/superpowers/.agent/workflows/
        ├── superpowers-execute-plan-parallel.md
        ├── superpowers-finish.md            # From antigravity/superpowers/.agent/workflows/
        ├── superpowers-reload.md            # From antigravity/superpowers/.agent/workflows/
        ├── superpowers-review.md            # From antigravity/superpowers/.agent/workflows/
        ├── superpowers-write-plan.md        # From antigravity/superpowers/.agent/workflows/
        └── writethisdown.md                 # From antigravity/workflows/
```

---

## 🤖 Setup Instructions

If you are an AI assistant and this file has just been downloaded or shared with you, perform the following actions:

### 1. Identify Target Environment
Verify if the current directory is a fresh repository or an existing one. Ensure you have write access. The workspace path is referred to as `<workspace>` throughout this document.

### 2. 🚨 IMMEDIATE ACTION: MANDATORY CONFIG RETRIEVER INSTALLATION
**STOP! BEFORE ASKING THE USER ANYTHING, YOU MUST INSTALL THE CONFIG RETRIEVER.**

This module is the core orchestrator and is **MANDATORY** for all setups.

**Perform these steps explicitly:**
1.  **Create Directory**: `<workspace>/.agent/skills/config-retriever/`
2.  **Download File**:
    - Source: `https://raw.githubusercontent.com/Legesus/custom-instruct/main/.agent/skills/config-retriever/SKILL.md`
    - Dest: `<workspace>/.agent/skills/config-retriever/SKILL.md`
3.  **Activate**:
    - Ensure `template.txt` exists at `<workspace>/template.txt` (create if missing).
    - Add `@include .agent/skills/config-retriever/SKILL.md` to `template.txt`.

---

### 3. Module Selection & Configuration Scope (Additional Modules)
**After** the Config Retriever is installed, ask the user:
**"Config Retriever has been successfully installed. Which additional modules would you like to set up?"**

For each module, clarify if they want a **Global Configuration** or a **Local Setup**.

#### Deployment Scopes:

| Scope | Target Path | Activation |
|-------|-------------|------------|
| **Global** | `~/.gemini/antigravity/global_skills/` | Add `@include` to global `template.txt` |
| **Local** | `<workspace>/.agent/` (unified) | Available to workspace only |

#### Available Modules:
1.  **Superpowers (Antigravity)**:
    - **Global**: Download to `~/.gemini/antigravity/global_skills/.agent/` + add `@include` to `template.txt`.
    - **Local**: Download to `<workspace>/.agent/` (merged into rules/, skills/, workflows/).
2.  **Gemini CLI Settings**:
    - **Global**: Download to `~/.gemini/antigravity/global_skills/` + add `@include` to `template.txt`.
    - **Local**: Download to `<workspace>/gemini-cli/` for reference only.
3.  **Antigravity Templates**: Custom rules, skills (including **Skill Writer**, **Code Simplifier**, **Library Checker**, **Frontend Design**, **Tool Calling Implementer**, and **Browser Control**), and workflows.
    - **Global**: Download to `~/.gemini/antigravity/global_skills/`.
    - **Local**: Download to `<workspace>/.agent/` (merged).
4.  **Full Suite (Local)**: Install everything to `<workspace>/.agent/` unified structure.
5.  **Full Suite (Global)**: Install everything to global paths and activate.

---

### 4. Structural Setup Guide (Verification)

After the user makes their selection, use the following logic to organize the project:

#### A. Local Deployment (Unified `.agent/` Structure)

> [!IMPORTANT]
> For **Local** deployments, ALL modules are merged into a single `<workspace>/.agent/` folder. Do NOT create nested structures like `antigravity/superpowers/.agent/`.

**Target Structure:**
```
<workspace>/
└── .agent/
    ├── rules/           # All rules from all modules
    ├── skills/          # All skills from all modules
    └── workflows/       # All workflows from all modules
```

**Merge Logic:**
- Superpowers rules → `<workspace>/.agent/rules/`
- Superpowers skills → `<workspace>/.agent/skills/`
- Superpowers workflows → `<workspace>/.agent/workflows/`
- Antigravity rules → `<workspace>/.agent/rules/`
- Antigravity skills → `<workspace>/.agent/skills/`
- Antigravity workflows → `<workspace>/.agent/workflows/`

#### B. Global Deployment
- **Dir**: Use `~/.gemini/antigravity/global_skills/` as the platform root.
- **Structure**: Can use nested paths or unified as preferred.

#### C. Manifest Configuration (template.txt)
- **Check**: If `template.txt` does not exist, create it at `<workspace>/template.txt`.
- **Local Setup**: Point to relative paths within `<workspace>/.agent/`.
- **Global Setup**: Point to absolute paths in `~/.gemini/antigravity/global_skills/`.
- **Organization**: Group `@include` lines by module (e.g., `## Superpowers`, `## Browser Control`).

---

### 5. Execution Logic (Source Mapping)

Download files from the following paths at: `https://raw.githubusercontent.com/Legesus/custom-instruct/main/`

> [!NOTE]
> **Source → Target Mapping**: The "Source" column shows the repo path. The "Local Target" shows where to place files in a unified `<workspace>/.agent/` deployment.

#### A. Config Retriever (Main Agent) - [Already Installed in Step 2]
| Source | Local Target |
|--------|--------------|
| `.agent/skills/config-retriever/SKILL.md` | `<workspace>/.agent/skills/config-retriever/SKILL.md` |

#### B. Superpowers Module
**Rules:**
| Source | Local Target |
|--------|--------------|
| `antigravity/superpowers/.agent/rules/superpowers.md` | `<workspace>/.agent/rules/superpowers.md` |

**Skills:**
| Source | Local Target |
|--------|--------------|
| `antigravity/superpowers/.agent/skills/superpowers-brainstorm/SKILL.md` | `<workspace>/.agent/skills/superpowers-brainstorm/SKILL.md` |
| `antigravity/superpowers/.agent/skills/superpowers-plan/SKILL.md` | `<workspace>/.agent/skills/superpowers-plan/SKILL.md` |
| `antigravity/superpowers/.agent/skills/superpowers-tdd/SKILL.md` | `<workspace>/.agent/skills/superpowers-tdd/SKILL.md` |
| `antigravity/superpowers/.agent/skills/superpowers-review/SKILL.md` | `<workspace>/.agent/skills/superpowers-review/SKILL.md` |
| `antigravity/superpowers/.agent/skills/superpowers-debug/SKILL.md` | `<workspace>/.agent/skills/superpowers-debug/SKILL.md` |
| `antigravity/superpowers/.agent/skills/superpowers-finish/SKILL.md` | `<workspace>/.agent/skills/superpowers-finish/SKILL.md` |
| `antigravity/superpowers/.agent/skills/superpowers-python-automation/SKILL.md` | `<workspace>/.agent/skills/superpowers-python-automation/SKILL.md` |
| `antigravity/superpowers/.agent/skills/superpowers-rest-automation/SKILL.md` | `<workspace>/.agent/skills/superpowers-rest-automation/SKILL.md` |
| `antigravity/superpowers/.agent/skills/superpowers-workflow/SKILL.md` | `<workspace>/.agent/skills/superpowers-workflow/SKILL.md` |

**Workflows:**
| Source | Local Target |
|--------|--------------|
| `antigravity/superpowers/.agent/workflows/superpowers-brainstorm.md` | `<workspace>/.agent/workflows/superpowers-brainstorm.md` |
| `antigravity/superpowers/.agent/workflows/superpowers-execute-plan.md` | `<workspace>/.agent/workflows/superpowers-execute-plan.md` |
| `antigravity/superpowers/.agent/workflows/superpowers-execute-plan-parallel.md` | `<workspace>/.agent/workflows/superpowers-execute-plan-parallel.md` |
| `antigravity/superpowers/.agent/workflows/superpowers-write-plan.md` | `<workspace>/.agent/workflows/superpowers-write-plan.md` |
| `antigravity/superpowers/.agent/workflows/superpowers-debug.md` | `<workspace>/.agent/workflows/superpowers-debug.md` |
| `antigravity/superpowers/.agent/workflows/superpowers-finish.md` | `<workspace>/.agent/workflows/superpowers-finish.md` |
| `antigravity/superpowers/.agent/workflows/superpowers-reload.md` | `<workspace>/.agent/workflows/superpowers-reload.md` |
| `antigravity/superpowers/.agent/workflows/superpowers-review.md` | `<workspace>/.agent/workflows/superpowers-review.md` |

#### C. Antigravity Core
**Rules:**
| Source | Local Target |
|--------|--------------|
| `antigravity/rules/browser-control.md` | `<workspace>/.agent/rules/browser-control.md` |
| `antigravity/rules/RULES_TEMPLATE.md` | `<workspace>/.agent/rules/RULES_TEMPLATE.md` (reference) |

**Skills:**
| Source | Local Target |
|--------|--------------|
| `antigravity/skills/skill-writer/SKILL.md` | `<workspace>/.agent/skills/skill-writer/SKILL.md` |
| `antigravity/skills/code-simplifier/SKILL.md` | `<workspace>/.agent/skills/code-simplifier/SKILL.md` |
| `antigravity/skills/pentester-research/SKILL.md` | `<workspace>/.agent/skills/pentester-research/SKILL.md` |
| `antigravity/skills/library-checker/SKILL.md` | `<workspace>/.agent/skills/library-checker/SKILL.md` |
| `antigravity/skills/frontend-design/SKILL.md` | `<workspace>/.agent/skills/frontend-design/SKILL.md` |
| `antigravity/skills/tool-calling-implementer/SKILL.md` | `<workspace>/.agent/skills/tool-calling-implementer/SKILL.md` |
| `antigravity/skills/browser-control/SKILL.md` | `<workspace>/.agent/skills/browser-control/SKILL.md` |

**Templates (Reference Only):**
| Source | Local Target |
|--------|--------------|
| `antigravity/skills/SKILL_TEMPLATE.md` | `<workspace>/.agent/skills/SKILL_TEMPLATE.md` |
| `antigravity/workflows/WORKFLOW_TEMPLATE.md` | `<workspace>/.agent/workflows/WORKFLOW_TEMPLATE.md` |

**Workflows:**
| Source | Local Target |
|--------|--------------|
| `antigravity/workflows/writethisdown.md` | `<workspace>/.agent/workflows/writethisdown.md` |

#### D. Gemini CLI & General
| Source | Local Target |
|--------|--------------|
| `gemini-cli/config/GEMINI_TEMPLATE.md` | `<workspace>/gemini-cli/GEMINI_TEMPLATE.md` (reference) |
| `general/uncategorized/devcontainer.md` | `<workspace>/devcontainer.md` |

---

### 6. Finalization
- Update `template.txt` at `<workspace>/template.txt` with `@include` lines for all active modules.
- Provide a summary of installed components and their configuration status (Global vs Local).
- Verify the unified structure matches the expected local deployment pattern.
- Offer to run a "Health Check" by listing the `.agent/` folder structure.

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
