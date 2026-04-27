# Portfolio UI Reference

Design system shared across the portfolio site and Postle app. Use this as context when building or modifying any UI in this project.

---

## Color Palette

### CSS Variables

```css
:root {
  /* Backgrounds */
  --bg:    #0D0806;   /* page background */
  --bg2:   #120B07;   /* slightly lighter bg */
  --panel: #1C120E;   /* card/surface background */
  --panel2:#241810;   /* secondary surface */

  /* Borders */
  --border:#3D2218;   /* default border */

  /* Text */
  --text:  #F5E6DC;   /* primary text */
  --muted: #A67860;   /* secondary/muted text */

  /* Accent */
  --accent:          #FF6B35;   /* primary orange */
  --accent2:         #FFB347;   /* amber */
  --accent-red:      #E8340A;   /* deep red-orange */
  --accent-gradient: linear-gradient(135deg, #FF4500, #FF8C00);

  /* Glow */
  --glow:        rgba(255,107,53,0.25);
  --glow-strong: rgba(255,107,53,0.45);

  /* Transitions */
  --tr: 0.3s cubic-bezier(0.4,0,0.2,1);
  --max: 1000px;  /* content max-width */
}
```

### Light theme overrides

```css
[data-theme="light"] {
  --bg:    #FFF5ED;
  --bg2:   #FFF0E5;
  --panel: #FFE8D6;
  --panel2:#FFDEC8;
  --border:#FFB899;
  --text:  #2D1200;
  --muted: #7A4030;
  --accent:         #C93A00;
  --accent2:        #D06000;
  --accent-red:     #B02200;
  --accent-gradient:linear-gradient(135deg,#C93A00,#D06000);
  --glow:           rgba(201,58,0,0.15);
  --glow-strong:    rgba(201,58,0,0.3);
}
```

### Status colors (unchanged in both themes)

| Name    | Hex       | Use            |
|---------|-----------|----------------|
| green   | `#34d399` | success/live   |
| red     | `#fb7185` | error/danger   |

---

## Typography

```
Font: Inter (Google Fonts)
Weights: 300, 400, 500, 600, 700
Monospace: DM Mono (used only in app for code/keys)
```

### Scale

| Element       | Size                        | Weight |
|---------------|-----------------------------|--------|
| `h1` (hero)   | `clamp(2.4rem, 7vw, 5rem)` | 700    |
| `h1` (detail) | `clamp(2rem, 6vw, 3.5rem)` | 700    |
| `h2`          | `clamp(1.8rem, 4vw, 2.6rem)`| 700    |
| Body          | `1rem / 1.65`               | 400    |
| Section label | `0.72rem` uppercase +0.18em | 700    |
| Tags          | `0.76rem`                   | 500    |

---

## Components

### Buttons

```css
/* Base */
.btn {
  display: inline-flex; align-items: center; gap: 0.4rem;
  padding: 0.75rem 1.4rem;
  border-radius: 999px;
  font-size: 0.92rem; font-weight: 600;
  transition: all 0.22s;
}

/* Primary — orange gradient, white text */
.btn-primary {
  background: linear-gradient(135deg, #FF4500, #FF8C00);
  color: #fff;
  box-shadow: 0 4px 22px rgba(255,107,53,0.25);
}
.btn-primary:hover {
  transform: translateY(-3px);
  box-shadow: 0 8px 32px rgba(255,107,53,0.45);
}

/* Secondary — transparent, bordered */
.btn-secondary {
  background: transparent; color: var(--text);
  border: 1px solid var(--border);
}
.btn-secondary:hover {
  border-color: var(--accent); color: var(--accent);
  box-shadow: 0 0 16px rgba(255,107,53,0.25);
}
```

### Cards

```css
.card {
  background: var(--panel);
  border: 1px solid var(--border);
  border-radius: 20px;
  padding: 1.5rem;
  transition: transform 0.25s, border-color 0.25s, box-shadow 0.25s;
}
.card:hover {
  transform: translateY(-6px);
  border-color: var(--accent);
  box-shadow: 0 14px 48px rgba(255,107,53,0.25);
}
/* Hover gradient overlay via ::after */
.card::after {
  content: '';
  position: absolute; inset: 0;
  background: linear-gradient(135deg, rgba(255,107,53,0.06), transparent 60%);
  opacity: 0; transition: opacity 0.3s;
}
.card:hover::after { opacity: 1; }
```

### Card icon

```css
.card-icon {
  width: 46px; height: 46px;
  border-radius: 13px;
  background: linear-gradient(135deg, rgba(255,107,53,0.18), rgba(232,52,10,0.12));
  border: 1px solid rgba(255,107,53,0.3);
  display: flex; align-items: center; justify-content: center;
  font-size: 1.25rem;
}
```

### Tags / Chips

```css
.tag {
  font-size: 0.76rem; font-weight: 500;
  color: var(--accent2);
  border: 1px solid rgba(255,179,71,0.3);
  border-radius: 999px;
  padding: 0.22rem 0.6rem;
  background: rgba(255,179,71,0.07);
}
```

### Panels

```css
.panel {
  background: var(--panel);
  border: 1px solid var(--border);
  border-radius: 20px;
  padding: 1.6rem;
  transition: border-color 0.25s, box-shadow 0.25s;
}
.panel:hover {
  border-color: rgba(255,107,53,0.45);
  box-shadow: 0 6px 28px rgba(255,107,53,0.25);
}
```

### Accent sidebar rule

```css
/* Left-border accent — used for callout panels */
border-left: 3px solid var(--accent);
```

---

## Layout

```css
/* Wrapper */
.wrap {
  width: min(100% - 2.5rem, var(--max));
  margin: 0 auto;
}

/* Common grids */
.grid-2 { display: grid; grid-template-columns: 1fr 1fr; gap: 1.1rem; }
.grid-3 { display: grid; grid-template-columns: repeat(auto-fit, minmax(270px,1fr)); gap: 1.1rem; }
```

### Section spacing

```
section { padding: 5.5rem 0; }
section (detail pages): padding: 4.5rem 0;
```

---

## Animations

```css
/* Fade-up entry (hero elements, staggered with animation-delay) */
@keyframes fadeUp {
  from { opacity: 0; transform: translateY(22px); }
  to   { opacity: 1; transform: translateY(0); }
}

/* Scroll reveal */
.reveal { opacity: 0; transform: translateY(28px); transition: opacity 0.65s, transform 0.65s; }
.reveal.visible { opacity: 1; transform: translateY(0); }

/* Stagger helpers */
.d1 { transition-delay: 0.1s; }
.d2 { transition-delay: 0.2s; }
.d3 { transition-delay: 0.3s; }
.d4 { transition-delay: 0.4s; }
.d5 { transition-delay: 0.5s; }
```

---

## Header / Nav

```
- Sticky, `z-index: 100`
- Background: rgba(13,8,6,0.88) with `backdrop-filter: blur(16px)`
- Brand: gradient text (--accent-gradient)
- Nav links: --muted color, hover → --accent
- Theme toggle: 38px circle button, hover glow
```

---

## Scrollbar

```css
::-webkit-scrollbar { width: 5px; }
::-webkit-scrollbar-track { background: transparent; }
::-webkit-scrollbar-thumb { background: var(--border); border-radius: 99px; }
::-webkit-scrollbar-thumb:hover { background: var(--accent); }
```

---

## Hero backgrounds

Two patterns used:
1. **Index hero** — animated radial gradients (JS `heroPulse` keyframes) + canvas particles
2. **Detail page hero** — static radial gradient overlay:
   ```css
   background:
     radial-gradient(ellipse 70% 60% at 85% 15%, rgba(255,107,53,0.15), transparent),
     radial-gradient(ellipse 50% 50% at 15% 85%, rgba(232,52,10,0.10), transparent);
   ```

---

## Files

| File | Role |
|------|------|
| `index.html` | Portfolio home — hero, projects grid, about, contact |
| `postle.html` | Postle project detail page |
| `homelab.html` | Homelab detail page |
| `tsnake.html` | TSnake detail page |
| `Media/` | Screenshot images |
| `Resume.pdf` | Linked from contact section |
| `/tmp/Postle/app/frontend/index.html` | Postle app — landing page + dashboard SPA |
