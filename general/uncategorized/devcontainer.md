## 🐳 GLOBAL: Dev Container Mandate (ALWAYS ENFORCED)
**Scope:** This rule applies to **ALL project creation and development tasks**, regardless of mode.
### Dev Container Requirements
1.  **Mandatory for New Projects:**
    *   When creating **any** new project (Python, Node.js, Go, Rust, etc.), you **MUST** initialize a `.devcontainer` configuration.
    *   This ensures reproducible, isolated development environments across all machines.
2.  **Dev Container Structure:**
    *   Create a `.devcontainer/` folder in the project root containing:
        *   `devcontainer.json` - The primary configuration file
        *   `Dockerfile` (optional) - For custom base images when needed
3.  **Minimum `devcontainer.json` Template:**
    ```json
    {
      "name": "<project-name>",
      "image": "mcr.microsoft.com/devcontainers/<language>:latest",
      "features": {},
      "customizations": {
        "vscode": {
          "extensions": [],
          "settings": {}
        }
      },
      "postCreateCommand": "",
      "remoteUser": "vscode"
    }
    ```
    *   Replace `<project-name>` with the actual project name.
    *   Replace `<language>` with the appropriate base image (e.g., `python`, `javascript-node`, `go`, `rust`).
4.  **Language-Specific Defaults:**
    | Language   | Base Image                                          | Key Features                          |
    |------------|-----------------------------------------------------|---------------------------------------|
    | Python     | `mcr.microsoft.com/devcontainers/python:3.12`       | `ghcr.io/devcontainers-contrib/features/poetry` |
    | Node.js    | `mcr.microsoft.com/devcontainers/javascript-node:20`| npm/yarn/pnpm                         |
    | Go         | `mcr.microsoft.com/devcontainers/go:1.22`           | gopls, delve                          |
    | Rust       | `mcr.microsoft.com/devcontainers/rust:latest`       | cargo, rust-analyzer                  |
    | Universal  | `mcr.microsoft.com/devcontainers/universal:2`       | Multi-language support                |
5.  **Existing Projects:**
    *   When working on an existing project **without** a `.devcontainer`, prompt the user:
        > "This project doesn't have a Dev Container configuration. Would you like me to create one for a consistent development environment?"
    *   If the user agrees, create the appropriate configuration.
6.  **AI Orchestration Safety:**
    *   When running AI agents (like Gemini CLI in `--yolo` mode), **always** recommend using Dev Containers.
    *   This provides isolation, protecting host files from accidental modification or deletion by sub-agents.