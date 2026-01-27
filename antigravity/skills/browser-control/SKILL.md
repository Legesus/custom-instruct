---
name: browser-control
description: Enforce browser_subagent for all browser automation. Use when launching dev servers, verifying web UIs, capturing screenshots, or any task involving browser interaction. Prevents uncontrolled browser launches from Streamlit, Flask, or other frameworks.
version: 1.0.0
tags:
  - browser
  - automation
  - policy
  - verification
---

# Browser Control

Enforce `browser_subagent` for all browser automation tasks. This skill provides detailed patterns for common frameworks and verification workflows.

> [!CAUTION]
> **Strict Policy**: NEVER launch browsers via `webbrowser.open()`, `subprocess`, or framework auto-open. ALWAYS use `browser_subagent`.

## When to Use This Skill

- Starting local dev servers (Streamlit, Flask, Next.js, Vite)
- Verifying web UI implementations
- Capturing screenshots for documentation
- Recording user flows for walkthroughs
- Any task requiring browser interaction

## Anti-Patterns to Avoid

### ❌ NEVER Do This

```python
# BAD: Opens uncontrolled browser
import webbrowser
webbrowser.open("http://localhost:8501")

# BAD: Subprocess browser launch
import subprocess
subprocess.run(["start", "http://localhost:5000"], shell=True)

# BAD: Streamlit with auto-open (default behavior)
# streamlit run app.py  # <-- auto-opens browser
```

### ❌ Why These Are Prohibited

| Anti-Pattern | Problem |
|-------------|---------|
| `webbrowser.open()` | Opens system browser, no agent control |
| `subprocess` browser | Untracked process, no screenshots |
| Framework auto-open | Browser outside agent visibility |
| Direct Selenium/Playwright | Conflicts with `browser_subagent` |

---

## Framework-Specific Patterns

### Streamlit

**Start headless:**
```bash
streamlit run app.py --server.headless=true --server.runOnSave=true --server.port=8501
```

**Verify with browser_subagent:**
```
browser_subagent(
  TaskName="Verify Streamlit Dashboard",
  Task="Navigate to http://localhost:8501. Verify the page loads. Check for the main title and sidebar. Capture a screenshot.",
  RecordingName="streamlit_verify"
)
```

---

### Flask

**Start without auto-reload browser:**
```python
if __name__ == "__main__":
    app.run(host="127.0.0.1", port=5000, debug=True, use_reloader=False)
```

**Or via CLI:**
```bash
flask run --host=127.0.0.1 --port=5000
```

**Verify with browser_subagent:**
```
browser_subagent(
  TaskName="Verify Flask API Documentation",
  Task="Navigate to http://localhost:5000. Check the homepage renders. Navigate to /docs if available. Capture screenshots.",
  RecordingName="flask_verify"
)
```

---

### Next.js / Vite / React

**Start dev server (no auto-open by default):**
```bash
npm run dev
# or
npx vite --port 3000
```

**Verify with browser_subagent:**
```
browser_subagent(
  TaskName="Verify React App",
  Task="Navigate to http://localhost:3000. Verify the app loads without console errors. Test navigation between routes. Capture screenshot of homepage.",
  RecordingName="react_verify"
)
```

---

## Verification Workflow

### Standard Pattern

1. **Start server** in headless/non-auto-open mode
2. **Confirm server ready** (watch for port binding message)
3. **Launch browser_subagent** with:
   - Navigation to correct URL
   - Specific verification checks
   - Screenshot capture task
   - Optional: recording for walkthrough

### Example: Full Verification Flow

```markdown
## Verification Steps

1. Start Streamlit:
   ```bash
   streamlit run app.py --server.headless=true --server.port=8501
   ```

2. Verify with browser_subagent:
   - Navigate to http://localhost:8501
   - Confirm dashboard title is "My Dashboard"
   - Verify sidebar contains 3 navigation items
   - Capture screenshot as proof

3. Stop server when done
```

---

## Screenshot and Recording Patterns

### Capture Screenshot

```
browser_subagent(
  TaskName="Capture Homepage Screenshot",
  Task="Navigate to http://localhost:8501. Wait for full page load. Capture a full-page screenshot.",
  RecordingName="homepage_screenshot"
)
```

### Record User Flow

```
browser_subagent(
  TaskName="Record Login Flow",
  Task="Navigate to http://localhost:3000/login. Enter 'testuser' in username field. Enter 'password123' in password field. Click login button. Verify redirect to dashboard.",
  RecordingName="login_flow_demo"
)
```

---

## Troubleshooting

### Server Not Responding

1. Verify server is running (`curl http://localhost:<port>`)
2. Check for port conflicts
3. Ensure firewall allows localhost connections

### browser_subagent Fails to Connect

1. Wait longer for server startup (add delay)
2. Verify correct URL and port
3. Check server logs for errors

### Screenshot Not Captured

1. Ensure page fully loaded before screenshot
2. Add explicit wait in task description
3. Check browser_subagent logs for errors

---

## Related Resources

- [browser-control.md](../../rules/browser-control.md) - Always-on enforcement rules
- [frontend-design](../frontend-design/SKILL.md) - UI implementation with browser verification
