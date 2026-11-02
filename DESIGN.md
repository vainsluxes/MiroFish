---
tokens:
  colors:
    background: "#0f172a"
    surface: "#1e293b"
    primary: "#38bdf8"
    accent: "#6366f1"
    text: "#f8fafc"
    muted: "#94a3b8"
    border: "#334155"
  typography:
    font_sans: "Inter, system-ui, -apple-system, sans-serif"
    font_mono: "JetBrains Mono, monospace"
  radii:
    sm: "4px"
    md: "8px"
    lg: "12px"
  spacing:
    xs: "4px"
    sm: "8px"
    md: "16px"
    lg: "24px"
    xl: "32px"
---

# DESIGN.md — MiroFish Visual Specification & Design System

## Brand Voice & Aesthetic Direction
- Functional, clean, and data-dense digital sandbox UI.
- High-contrast visual hierarchy optimized for tracking multi-agent graph clusters, timeline progressions, and event feeds.
- Anti-slop baseline: avoid unnecessary neon glow, blurry backdrop filters, or hollow decorative widgets.

## Component Guidelines
- **Network Graph Canvas**: D3 nodes representing agent entities must use distinct categorical colors by faction/sentiment, with clear edge weight representations.
- **Simulation Timeline**: Linear progression slider with clear round-by-round checkpoints and God-mode intervention markers.
- **Agent Inspector Drawer**: Clean tabular display of persona attributes, state, and recent actions.

## Do's and Don'ts
- **DO**: Maintain readable contrast ratios across dark slate backgrounds.
- **DO**: Display exact numerical metrics (rounds, agent counts, token usage, convergence scores).
- **DON'T**: Add decorative AI particles or non-functional visual animations that degrade rendering performance during heavy simulation runs.
