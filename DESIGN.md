# Controlled Growth Design System

Dark terminal/cyber aesthetic with neon accents on near-black backgrounds. Monospace everything. Glow effects for emphasis, opacity for hierarchy.

## Color Palette

### Brand Accents
| Token | Hex | Usage |
|-------|-----|-------|
| `--cg-cyan` | `#00ffc8` | Primary accent, links, entity highlights |
| `--cg-green` | `#00ff41` | Support/positive, data flow, success |
| `--cg-lime` | `#39ff14` | Concepts, tertiary accent |
| `--cg-pink` | `#ff0066` | Opposition/negative, people, warnings |
| `--cg-orange` | `#ffa000` | Organizations, uncertainty, system UI |
| `--cg-purple` | `#bf5fff` | Unique identifiers, special states |
| `--cg-yellow` | `#FBBF24` | Simulation/warning state |

### Backgrounds (dark to light)
| Token | Hex | Usage |
|-------|-----|-------|
| `--cg-bg-deep` | `#060611` | Page background |
| `--cg-bg` | `#0a0a1a` | Panels, primary containers |
| `--cg-bg-alt` | `#0a0e1d` | Alternative containers |
| `--cg-bg-panel` | `#0d1117` | Elevated panels |
| `--cg-bg-card` | `#1a1a1a` | Cards, boxes |
| `--cg-bg-nested` | `#111111` | Nested containers |

### Text (bright to dim)
| Token | Hex | Usage |
|-------|-----|-------|
| `--cg-text` | `#cdd6f4` | Primary readable text |
| `--cg-text-bright` | `#e8e6e3` | Highlighted text |
| `--cg-text-mid` | `#aaaaaa` | Secondary text |
| `--cg-text-dim` | `#888888` | Tertiary text |
| `--cg-text-muted` | `#666666` | Subtle text |
| `--cg-text-faint` | `#555555` | De-emphasized text |
| `--cg-text-ghost` | `#444444` | Minimum contrast |

## Typography

- **Font**: `'Courier New', 'Fira Code', monospace` for everything
- **Title**: 16px bold, `letter-spacing: 3px`, uppercase, cyan with glow
- **Section labels**: 10px bold, `letter-spacing: 2px`, uppercase
- **Body**: 12px, `line-height: 1.8`
- **Small**: 10px for buttons/badges, 9px for metadata

## Borders & Outlines

Borders use accent colors at low opacity:
- Standard: `1px solid rgba(accent, 0.22)`
- Hover: `1px solid rgba(accent, 0.55)`
- Dividers: `#333` or `#222` solid
- Left accent borders: `3px solid` on cards

## Shadows & Glows

- **Text glow**: `text-shadow: 0 0 10px <accent-color>`
- **Panel glow**: `box-shadow: 0 0 20px #00ffc811, inset 0 0 30px #00ffc805`
- **Subtle glow**: `box-shadow: 0 0 15px #00ffc808`
- Glows at 25-50% opacity hex suffix

## Opacity System

Hierarchy through opacity, not color shifts:
| Level | Opacity | Usage |
|-------|---------|-------|
| Active/highlighted | `1.0` | Focused element |
| Strong | `0.9` | Primary content |
| Medium | `0.5-0.7` | Secondary, hover states |
| Low | `0.15-0.25` | Inactive, de-emphasized |
| Background | `0.02-0.08` | Grids, ambient effects |

## Component Patterns

### Buttons
- Transparent background, colored border at 0.33 opacity
- Hover: subtle fill at 0.08 opacity, border brightens to 0.55
- Sizes: small (2px 8px / 9px), default (4px 10px / 10px), large (14px 18px / 12px)
- All uppercase with letter-spacing

### Badges (vote/status)
- Pill-shaped (`border-radius: 8px`)
- Solid colored background with contrasting text
- Support: green bg / black text
- Oppose: pink bg / white text
- Unsure: orange bg / black text

### Tooltips
- Dark semi-transparent bg (`#0a0e1dee`)
- Cyan text, thin border, glow shadow
- Max-width 320px, `pointer-events: none`

### Panels
- Collapsible with `width/padding/opacity/border` transitions at 0.3s
- Typical widths: sidebar 24-38%, main flex-grows

### HUD Corner Brackets (decorative)
- Top-left: cyan
- Top-right: orange
- Bottom-left: pink
- Bottom-right: orange
- 2px borders at 0.25 opacity

## Canvas / Visualization Colors

For JS canvas rendering (graphs, data viz):

```javascript
const CG_CANVAS = {
  // Entity nodes
  component: '#00ffc8',
  person:    '#ff0066',
  concept:   '#39ff14',
  org:       '#ffa000',

  // Edges
  normal:    { color: '#00ff41', opacity: [0.18, 0.66] },
  tension:   { color: '#ff0066', dash: [8, 4], pulse: true },
  reference: { color: '#00ff41', opacity: 0.08, dash: [2, 4] },

  // Particles & effects
  dataFlow:  { color: '#00ff41', opacity: [0.33, 0.88] },
  grid:      { color: '#00ff41', opacity: [0.02, 0.15] },
  rain:      { color: '#00ff41' },

  // Glow
  nodeGlow:  { blur: [4, 20] }, // px range

  // Background gradient
  bgGradient: 'radial-gradient(ellipse at center, #0a0a2a 0%, #060611 70%)',
};
```

## Animations

- **Pulse**: opacity 0.3 → 1.0 → 0.3 over 1.5s (typing indicators)
- **Breathe**: box-shadow 5px → 20px over 3s (ambient glow)
- **Standard transition**: `all 0.3s ease`
- **Panel collapse**: `width/padding/opacity/border 0.3s ease`
- **Canvas tension lines**: `0.3 + sin(tick * 0.03) * 0.15`
- **Rotating arc**: `(tick * 0.02) % (PI * 2)`

## Quick Start

```html
<link rel="stylesheet" href="controlled-growth.css">
<body class="cg-theme">
  <h1 class="cg-title">Project Name</h1>
  <div class="cg-panel cg-panel-glow cg-hud-corners">
    <span class="cg-section-label">Status</span>
    <span class="cg-badge cg-badge--support">Active</span>
  </div>
  <button class="cg-btn">Action</button>
  <input class="cg-input" placeholder="Type here...">
</body>
```
