---
name: frontend-design
description: Create distinctive, production-grade frontend interfaces with exceptional design quality. Use when building web components, pages, UI mockups, or applications. Generates polished, memorable code with bold aesthetic choices that avoid generic AI patterns.
version: 1.0.0
tags:
  - frontend
  - design
  - ui
  - web-development
---

# Frontend Design

Create distinctive, production-grade frontend interfaces that stand out with bold aesthetic choices and exceptional attention to design details. This skill guides the creation of memorable, polished web interfaces that avoid generic "AI slop" aesthetics.

## When to Use This Skill

- Building new web components, pages, or applications
- Creating UI mockups or design prototypes
- Redesigning existing interfaces for better aesthetics
- When the user asks for anything to look "premium", "modern", or "unique"
- Any frontend work where visual impact matters

## Prerequisites

- HTML, CSS, JavaScript (vanilla or frameworks like React/Vue)
- Optional: CSS frameworks, animation libraries (Motion/Framer)
- `generate_image` tool for custom graphics/assets
- `browser_subagent` tool for visual verification

## Design Thinking Process

Before writing any code, commit to a **BOLD aesthetic direction**:

### 1. Understand Context
- **Purpose**: What problem does this interface solve? Who uses it?
- **Constraints**: Technical requirements (framework, performance, accessibility)
- **Differentiation**: What makes this UNFORGETTABLE? What's the one thing users will remember?

### 2. Choose an Extreme Design Tone

Pick one and commit fully:

| Tone | Characteristics |
|------|-----------------|
| **Brutally Minimal** | Monochrome, lots of whitespace, bold typography |
| **Maximalist Chaos** | Layered elements, bold colors, controlled visual density |
| **Retro-Futuristic** | Neon accents, gradients, cyber/synthwave vibes |
| **Organic/Natural** | Earth tones, flowing shapes, subtle textures |
| **Luxury/Refined** | Gold accents, serif fonts, elegant animations |
| **Playful/Toy-like** | Rounded corners, bright pastels, bouncy interactions |
| **Editorial/Magazine** | Strong typography hierarchy, grid-breaking layouts |
| **Brutalist/Raw** | Exposed structure, unconventional layouts, bold contrast |
| **Art Deco/Geometric** | Symmetric patterns, gold metallic, sharp angles |
| **Soft/Pastel** | Gentle gradients, rounded elements, calming palette |
| **Industrial/Utilitarian** | Muted colors, functional design, minimal decoration |

> [!IMPORTANT]
> Bold maximalism and refined minimalism both work—the key is **intentionality**, not intensity. Choose a direction and execute with precision.

## Frontend Aesthetics Guidelines

### Typography

**DO:**
- Choose fonts that are beautiful, unique, and characterful
- Pair a distinctive display font with a refined body font
- Use Google Fonts with personality: Outfit, Space Grotesk, DM Sans, Syne, Clash Display

**DON'T:**
- Use generic fonts like Arial, Inter, Roboto, or system fonts
- Default to boring, overused choices

### Color & Theme

**DO:**
- Commit to a cohesive aesthetic
- Use CSS variables for consistency
- Use dominant colors with sharp accents
- Create custom color palettes using HSL for flexibility

**DON'T:**
- Use timid, evenly-distributed palettes
- Default to cliché schemes (purple gradients on white)
- Use plain red, blue, green without intention

### Motion & Animation

**DO:**
- Use animations for high-impact moments
- Prioritize CSS-only solutions for simple effects
- Create staggered reveals with `animation-delay`
- Add scroll-triggered and hover effects that surprise
- Use Motion library for React when complex animation needed

**DON'T:**
- Scatter random micro-interactions everywhere
- Use animations that distract from content
- Ignore performance implications

### Spatial Composition

**DO:**
- Use unexpected layouts: asymmetry, overlap, diagonal flow
- Break the grid intentionally
- Balance generous negative space OR controlled density

**DON'T:**
- Default to centered, symmetric layouts
- Use predictable component patterns

### Backgrounds & Visual Details

**DO:**
- Create atmosphere with depth and texture
- Use gradient meshes, noise textures, geometric patterns
- Add layered transparencies, dramatic shadows
- Consider custom cursors, decorative borders, grain overlays

**DON'T:**
- Default to solid color backgrounds
- Ignore opportunities for visual interest

## What to NEVER Do

> [!CAUTION]
> Avoid these generic AI-generated aesthetics:
> - Overused fonts: Inter, Roboto, Arial, system fonts
> - Cliché colors: purple gradients, generic blue CTAs
> - Predictable layouts: centered hero, three-column features
> - Cookie-cutter design lacking context-specific character
> - Converging on common choices (e.g., Space Grotesk everywhere)

## Implementation Workflow

### Step 1: Establish Design System

Create `styles.css` or update `index.css` with:

```css
:root {
  /* Color Tokens */
  --color-primary: hsl(var(--hue-primary), 70%, 50%);
  --color-accent: hsl(var(--hue-accent), 80%, 60%);
  --color-background: hsl(var(--hue-bg), 10%, 8%);
  --color-surface: hsl(var(--hue-bg), 12%, 12%);
  --color-text: hsl(0, 0%, 95%);
  
  /* Typography */
  --font-display: 'Clash Display', sans-serif;
  --font-body: 'DM Sans', sans-serif;
  
  /* Spacing Scale */
  --space-xs: 0.25rem;
  --space-sm: 0.5rem;
  --space-md: 1rem;
  --space-lg: 2rem;
  --space-xl: 4rem;
  
  /* Animation */
  --ease-out-expo: cubic-bezier(0.16, 1, 0.3, 1);
  --duration-fast: 150ms;
  --duration-normal: 300ms;
  --duration-slow: 500ms;
}
```

### Step 2: Build Components

- Use predefined CSS variables consistently
- Keep components focused and reusable
- Add meaningful hover/focus states
- Include transition effects on interactive elements

### Step 3: Assemble Pages

- Implement responsive layouts
- Add scroll-triggered animations
- Ensure proper navigation flow

### Step 4: Polish

- Review overall user experience
- Add micro-interactions where impactful
- Verify accessibility (contrast, focus states)
- Optimize performance

## Examples

### Example 1: Hero Section with Glassmorphism

```html
<section class="hero">
  <div class="hero-content">
    <h1 class="hero-title">
      Design that
      <span class="gradient-text">speaks volumes</span>
    </h1>
    <p class="hero-subtitle">Craft interfaces that users remember</p>
    <button class="cta-button">Get Started</button>
  </div>
  <div class="hero-visual">
    <div class="glass-card"></div>
  </div>
</section>
```

```css
.hero {
  min-height: 100vh;
  display: grid;
  grid-template-columns: 1fr 1fr;
  align-items: center;
  gap: var(--space-xl);
  padding: var(--space-xl);
  background: var(--color-background);
}

.hero-title {
  font-family: var(--font-display);
  font-size: clamp(3rem, 8vw, 6rem);
  line-height: 1.1;
  color: var(--color-text);
}

.gradient-text {
  background: linear-gradient(135deg, var(--color-primary), var(--color-accent));
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}

.glass-card {
  width: 100%;
  aspect-ratio: 4/3;
  background: rgba(255, 255, 255, 0.05);
  backdrop-filter: blur(20px);
  border: 1px solid rgba(255, 255, 255, 0.1);
  border-radius: 24px;
  box-shadow: 0 25px 50px -12px rgba(0, 0, 0, 0.5);
}

.cta-button {
  padding: var(--space-md) var(--space-lg);
  font-family: var(--font-body);
  font-weight: 600;
  background: var(--color-primary);
  border: none;
  border-radius: 12px;
  color: white;
  cursor: pointer;
  transition: transform var(--duration-fast) var(--ease-out-expo),
              box-shadow var(--duration-fast) var(--ease-out-expo);
}

.cta-button:hover {
  transform: translateY(-2px);
  box-shadow: 0 10px 30px -10px var(--color-primary);
}
```

### Example 2: Animated Card Grid

```css
.card-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: var(--space-lg);
}

.card {
  background: var(--color-surface);
  border-radius: 16px;
  padding: var(--space-lg);
  opacity: 0;
  transform: translateY(20px);
  animation: slideUp 0.6s var(--ease-out-expo) forwards;
}

.card:nth-child(1) { animation-delay: 0ms; }
.card:nth-child(2) { animation-delay: 100ms; }
.card:nth-child(3) { animation-delay: 200ms; }

@keyframes slideUp {
  to {
    opacity: 1;
    transform: translateY(0);
  }
}
```

## Verification

After implementing, verify your design:

1. **Visual Check**: Use `browser_subagent` to capture screenshots
2. **Responsiveness**: Test at multiple viewport sizes
3. **Interactivity**: Verify hover states and animations work
4. **Performance**: Check for jank in animations
5. **Accessibility**: Ensure sufficient contrast ratios

## Notes

- Match implementation complexity to aesthetic vision—maximalist needs elaborate code, minimalist needs restraint
- Use `generate_image` tool for custom graphics, backgrounds, or hero images
- Vary between light/dark themes across different projects
- **Never converge on common choices**—each design should feel unique
- Remember: Antigravity is capable of extraordinary creative work. Don't hold back!

## Related Skills

- [code-simplifier](../code-simplifier/SKILL.md) - Clean up and optimize code after building
- [superpowers-review](../../superpowers/.agent/skills/superpowers-review/SKILL.md) - Review changes for quality
