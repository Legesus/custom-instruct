# Browser Control Rules (Always-On)

These rules apply to ALL work involving browser automation or web UI verification.

> **Strict Enforcement**: These are not suggestions—they are mandatory requirements.

---

## 1) NEVER Launch Uncontrolled Browsers

You MUST NOT use any of the following to open browsers:

| ❌ Prohibited | Why |
|---------------|-----|
| `webbrowser.open()` | Opens system default browser, uncontrolled |
| `subprocess` to launch Chrome/Firefox/etc. | Uncontrolled process |
| `os.system("open ...")` or `start` commands | Uncontrolled process |
| Framework auto-open (Streamlit, Flask debug) | Opens outside agent control |
| `selenium`, `playwright`, `puppeteer` directly | Use `browser_subagent` instead |

---

## 2) ALWAYS Use browser_subagent

For ANY browser interaction, you MUST use the `browser_subagent` tool:

- **Viewing web pages**: `browser_subagent` with navigation task
- **Capturing screenshots**: `browser_subagent` with screenshot task
- **Verifying UI**: `browser_subagent` to inspect rendered output
- **Recording flows**: `browser_subagent` with recording enabled

### Example
```
browser_subagent(
  TaskName="Verify Streamlit App",
  Task="Navigate to http://localhost:8501, verify the dashboard loads, capture a screenshot",
  RecordingName="streamlit_verification"
)
```

---

## 3) Framework-Specific Patterns

### Streamlit
```bash
# Start headless (no auto-open)
streamlit run app.py --server.headless=true --server.runOnSave=true
```
Then use `browser_subagent` to navigate to `http://localhost:8501`.

### Flask (Development)
```python
# Disable auto-reload browser opening
app.run(debug=True, use_reloader=False)
```
Then use `browser_subagent` to navigate to `http://localhost:5000`.

### Next.js / Vite / React Dev Server
```bash
# These don't auto-open by default, just start normally
npm run dev
```
Then use `browser_subagent` to navigate to the dev server URL.

---

## 4) Verification Workflow

After starting any local server:

1. **Start server** in headless/non-auto-open mode
2. **Wait** for server ready message (port binding confirmation)
3. **Use browser_subagent** to:
   - Navigate to the URL
   - Verify page loads correctly
   - Capture screenshots if needed
   - Record user flows for documentation

---

## Why This Matters

- **Observability**: `browser_subagent` actions are logged and visible
- **Reproducibility**: Recordings can be reviewed and replayed
- **Control**: Agent can interact with the page, not just view it
- **Artifacts**: Screenshots and recordings are saved automatically
