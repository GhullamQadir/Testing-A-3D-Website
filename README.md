<!-- ────────────────────────────────────────────────────────────────────── -->
<!--                         TOONHUB  ·  README                          -->
<!-- ────────────────────────────────────────────────────────────────────── -->

<p align="center">
  <img src=".github/assets/banner.png" alt="TOONHUB — Character Figurine Carousel" width="100%" />
</p>

<p align="center">
  <a href="#-quick-start"><img src="https://img.shields.io/badge/-Get_Started-F4845F?style=for-the-badge&logoColor=white" alt="Get Started" /></a>
  &nbsp;
  <a href="#-live-demo"><img src="https://img.shields.io/badge/-Live_Demo-6BBF7A?style=for-the-badge&logoColor=white" alt="Live Demo" /></a>
  &nbsp;
  <a href="#-contributing"><img src="https://img.shields.io/badge/-Contribute-6EB5FF?style=for-the-badge&logoColor=white" alt="Contribute" /></a>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/React-19.2-61DAFB?style=flat-square&logo=react&logoColor=white" />
  <img src="https://img.shields.io/badge/TypeScript-6.0-3178C6?style=flat-square&logo=typescript&logoColor=white" />
  <img src="https://img.shields.io/badge/Vite-8.0-646CFF?style=flat-square&logo=vite&logoColor=white" />
  <img src="https://img.shields.io/badge/Tailwind_CSS-3.4-06B6D4?style=flat-square&logo=tailwindcss&logoColor=white" />
  <img src="https://img.shields.io/badge/Lucide-1.16-F56565?style=flat-square&logo=feather&logoColor=white" />
  <img src="https://img.shields.io/badge/License-MIT-22C55E?style=flat-square" />
</p>

<br />

<h1 align="center">TOONHUB</h1>

<p align="center">
  <strong>A cinematic, full-viewport character-figurine carousel<br />built with React 19, TypeScript, and zero animation libraries.</strong>
</p>

<p align="center">
  <sub>Role-based carousel engine &nbsp;·&nbsp; GPU-accelerated CSS transitions &nbsp;·&nbsp; SVG film-grain overlay &nbsp;·&nbsp; Responsive-first architecture</sub>
</p>

<br />

<p align="center">
  <img src=".github/assets/preview.png" alt="TOONHUB UI Preview" width="90%" style="border-radius: 12px;" />
</p>

<br />

---

<br />

## Why TOONHUB?

Most carousels ship bloated runtimes — Framer Motion, GSAP, Swiper — just to slide an image sideways. **TOONHUB proves you don't need any of them.** Every transition — scale, blur, depth, color — is driven by a single `activeIndex` state variable and pure CSS `transition` properties. The result:

- **Zero animation-library overhead.** Fewer kilobytes, fewer abstractions, fewer bugs.
- **GPU-composited motion at 60 fps.** CSS transitions on `transform`, `filter`, and `opacity` are handled by the compositor thread — no main-thread jank.
- **A design that stops the scroll.** Giant typographic ghost layers, depth-of-field blur, dynamic background color crossfades, and SVG grain all work together to create a premium editorial feel.

<br />

---

<br />

## ✨ Feature Highlights

<table>
  <tr>
    <td width="50%">
      <h4>🎠 Role-Based Carousel Engine</h4>
      <p>Four deterministic roles — <code>center</code>, <code>left</code>, <code>right</code>, <code>back</code> — computed via modular arithmetic on every render. No animation timeline, no imperative DOM manipulation.</p>
    </td>
    <td width="50%">
      <h4>🎬 Cinematic Transitions</h4>
      <p>7 properties animate simultaneously over 650ms with <code>cubic-bezier(0.4, 0, 0.2, 1)</code> — transform, filter, opacity, left, bottom, height, and background-color.</p>
    </td>
  </tr>
  <tr>
    <td>
      <h4>🎞️ SVG Film Grain</h4>
      <p>An inline <code>&lt;feTurbulence&gt;</code> fractal-noise texture at <code>baseFrequency=0.9</code> adds analog character without a single raster asset.</p>
    </td>
    <td>
      <h4>📐 Fluid Typography</h4>
      <p>Ghost text scales with <code>clamp(90px, 28vw, 380px)</code> — pixel-perfect from 375px phones to 4K displays, no media queries needed.</p>
    </td>
  </tr>
  <tr>
    <td>
      <h4>⚡ Preloaded Assets</h4>
      <p>All figurine images are preloaded on mount via <code>new Image()</code>. Transitions start instantly — zero pop-in, zero layout shift.</p>
    </td>
    <td>
      <h4>⌨️ Keyboard + Accessibility</h4>
      <p>Full arrow-key navigation, <code>aria-label</code> on buttons, <code>aria-hidden</code> on decorative layers, descriptive <code>alt</code> text on all images.</p>
    </td>
  </tr>
</table>

<br />

---

<br />

## 🛠 Tech Stack

| Layer | Technology | Role |
|:---|:---|:---|
| **UI Framework** | [React 19](https://react.dev) | Declarative component rendering, hooks-based state |
| **Type System** | [TypeScript 6](https://typescriptlang.org) | Compile-time safety, discriminated union roles |
| **Build Tool** | [Vite 8](https://vite.dev) | ESM-native HMR, sub-second cold starts |
| **Utility CSS** | [Tailwind CSS 3.4](https://tailwindcss.com) | Responsive breakpoints, layout utilities |
| **Iconography** | [Lucide React](https://lucide.dev) | Tree-shakeable SVG icons (`ArrowLeft`, `ArrowRight`) |
| **Typography** | [Google Fonts](https://fonts.google.com) | **Anton** (display) + **Inter** (body) |

<br />

---

<br />

## 🚀 Quick Start

> **Prerequisites:** Node.js ≥ 18 &nbsp;·&nbsp; npm ≥ 9 (or pnpm / yarn)

```bash
# Clone
git clone https://github.com/your-username/toonhub.git && cd toonhub

# Install
npm install

# Develop
npm run dev          # → http://localhost:5173
```

That's it. No `.env` files, no API keys, no backend. Open the URL and you're running.

<br />

### Production Build

```bash
npm run build        # TypeScript check → Vite production bundle
npm run preview      # Serve the dist/ folder locally
```

<br />

---

<br />

## 🏛 Architecture

```
┌──────────────────────────────────────────────────────────────────┐
│                       ToonHubHero                                │
│                                                                  │
│   State                    Role Engine          Style Factory     │
│  ┌──────────────┐        ┌──────────────┐     ┌──────────────┐   │
│  │ activeIndex  │───────▶│  center  (0) │────▶│ scale 1.68   │   │
│  │ isAnimating  │        │  left   (+3) │     │ blur  0px    │   │
│  │ isMobile     │        │  right  (+1) │     │ opacity 1    │   │
│  └──────────────┘        │  back   (+2) │     │ zIndex 20    │   │
│                          └──────────────┘     └──────────────┘   │
│                                                                  │
│   Visual Layers (z-index stack)                                  │
│  ┌──────────────────────────────────────────────────────────┐    │
│  │  60  ░░ UI Controls — Brand · Nav Buttons · CTA Link    │    │
│  │  50  ░░ Grain Overlay — feTurbulence SVG texture         │    │
│  │  20  ░░ Center Figurine — hero image, no blur            │    │
│  │  10  ░░ Left / Right — peripheral, blur(2px)             │    │
│  │   5  ░░ Back — deepest layer, blur(4px)                  │    │
│  │   2  ░░ Ghost Text — "3D SHAPE", Anton 380px             │    │
│  │   0  ░░ Background — dynamic color from IMAGES[]         │    │
│  └──────────────────────────────────────────────────────────┘    │
└──────────────────────────────────────────────────────────────────┘
```

### How Navigation Works

```typescript
// One state variable drives everything
const [activeIndex, setActiveIndex] = useState(0);

// Roles are pure derivations — no imperative assignment
const center = activeIndex;
const left   = (activeIndex + 3) % 4;   // wraps: 0→3, 1→0, 2→1, 3→2
const right  = (activeIndex + 1) % 4;
const back   = (activeIndex + 2) % 4;

// Navigate simply bumps the index; CSS handles the rest
navigate('next') → setActiveIndex((i) => (i + 1) % 4);
navigate('prev') → setActiveIndex((i) => (i + 3) % 4);
```

An `isAnimating` lock prevents overlapping transitions. The lock releases after a `650ms` timeout — identical to the CSS transition duration — ensuring visual and logical state stay in sync.

<br />

---

<br />

## 📁 Project Structure

```
toonhub/
│
├── index.html                  ← Entry point · Google Fonts preconnect
├── package.json                ← Scripts & dependency manifest
├── tailwind.config.js          ← Content paths for class purging
├── postcss.config.js           ← Tailwind + Autoprefixer pipeline
├── vite.config.ts              ← Vite plugin configuration
├── tsconfig.json               ← TypeScript project references
│
├── .github/
│   └── assets/
│       ├── banner.png          ← Repository social banner
│       └── preview.png         ← UI screenshot for README
│
├── public/
│   └── vite.svg                ← Default favicon
│
└── src/
    ├── main.tsx                ← ReactDOM.createRoot entry
    ├── App.tsx                 ← Root component shell
    ├── index.css               ← @tailwind directives + reset
    └── components/
        └── ToonHubHero.tsx     ← ★ Core carousel (372 LOC)
```

> The entire UI lives in a **single component file** — intentionally. For a hero section this focused, splitting into micro-components would add indirection without meaningful reuse.

<br />

---

<br />

## 🎨 Design System

### Color Palette

Each carousel item carries a **background** and **panel** color pair. The viewport background crossfades between them.

| # | Figurine | Background | Panel | Preview |
|:-:|:---|:---|:---|:---|
| 1 | Orange | `#F4845F` | `#F79B7F` | ![#F4845F](https://via.placeholder.com/12/F4845F/F4845F.png) ![#F79B7F](https://via.placeholder.com/12/F79B7F/F79B7F.png) |
| 2 | Green | `#6BBF7A` | `#85CC92` | ![#6BBF7A](https://via.placeholder.com/12/6BBF7A/6BBF7A.png) ![#85CC92](https://via.placeholder.com/12/85CC92/85CC92.png) |
| 3 | Pink | `#E882B4` | `#ED9DC4` | ![#E882B4](https://via.placeholder.com/12/E882B4/E882B4.png) ![#ED9DC4](https://via.placeholder.com/12/ED9DC4/ED9DC4.png) |
| 4 | Blue | `#6EB5FF` | `#8DC4FF` | ![#6EB5FF](https://via.placeholder.com/12/6EB5FF/6EB5FF.png) ![#8DC4FF](https://via.placeholder.com/12/8DC4FF/8DC4FF.png) |

### Typography Scale

| Element | Font | Weight | Size |
|:---|:---|:---:|:---|
| Body copy | Inter | 400 | `text-xs` — `text-sm` |
| Section title | Inter | 700 | `text-base` — `22px` |
| Brand label | Inter | 600 | `text-xs`, tracking `0.18em` |
| Ghost text | Anton | 900 | `clamp(90px, 28vw, 380px)` |
| CTA link | Anton | 400 | `clamp(20px, 4vw, 56px)` |

### Motion

```
Easing:    cubic-bezier(0.4, 0, 0.2, 1)
Duration:  650ms
Properties: transform · filter · opacity · left · bottom · height · background-color
```

All transitions run on the **compositor thread** — `transform`, `opacity`, and `filter` are GPU-composited by default, and `will-change` hints are declared on each carousel item.

<br />

---

<br />

## 📱 Responsive Breakpoints

A single breakpoint at **640px** (`sm:`) governs all adaptive behavior:

| Property | Mobile (`< 640px`) | Desktop (`≥ 640px`) |
|:---|:---:|:---:|
| Center scale | `1.25×` | `1.68×` |
| Center height | `60%` | `92%` |
| Side figurine height | `16%` | `28%` |
| Back figurine height | `13%` | `22%` |
| Side positions | `20%` / `80%` | `30%` / `70%` |
| Description copy | Hidden | Visible |
| Nav button diameter | `48px` | `64px` |

<br />

---

<br />

## ⚡ Performance

| Optimization | Impact |
|:---|:---|
| **Image preloading** | `new Image()` on mount — zero pop-in during transitions |
| **`will-change` declarations** | Carousel items promoted to composited layers |
| **CSS-only animation** | No `requestAnimationFrame` loops — browser compositor handles all motion |
| **Animation lock** | `isAnimating` guard prevents transition stacking and visual tearing |
| **`useCallback` memoization** | `navigate()` reference is stable across renders |
| **`useRef` timer cleanup** | Timeout cleared on unmount — no stale state updates or memory leaks |

<br />

---

<br />

## ⌨️ Keyboard & Accessibility

| Input | Action |
|:---|:---|
| `←` Arrow Left | Previous figurine |
| `→` Arrow Right | Next figurine |
| Click / Tap | Nav buttons in bottom-left |

**Accessibility considerations:**
- `aria-label` on both navigation buttons
- `aria-hidden="true"` on all decorative elements (grain, ghost text)
- Descriptive `alt` attributes on every figurine `<img>`
- Unique `id` attributes on interactive elements for automated testing

<br />

---

<br />

## 🔧 Customization

<details>
<summary><strong>Add more figurines</strong></summary>

<br />

1. Append entries to the `IMAGES` array:
```typescript
{ src: '/path/to/figurine.png', bg: '#HEX', panel: '#HEX' }
```

2. Replace every `% 4` with `% IMAGES.length` in:
   - `navigate()` — index wrapping
   - Role derivations — `center`, `left`, `right`, `back`

</details>

<details>
<summary><strong>Change transition timing</strong></summary>

<br />

Search for `650ms` and update in three places:
- `getRoleStyle()` — the CSS `transition` string
- `navigate()` — the `setTimeout` duration
- Outer `<div>` — `background-color` transition

For snappier feel, try `400ms`. For dramatic slow-motion, try `1000ms`.

</details>

<details>
<summary><strong>Swap the ghost text</strong></summary>

<br />

Find the ghost text `<span>` (line ~203) and replace `"3D SHAPE"` with any string. The `clamp()` sizing will adapt automatically.

</details>

<details>
<summary><strong>Adjust grain intensity</strong></summary>

<br />

Modify the `GRAIN_SVG` data URI:
- `baseFrequency`: `0.5` (coarse) → `1.5` (fine)
- `numOctaves`: `2` (simple) → `6` (detailed)
- Container `opacity`: `0.0` (off) → `1.0` (heavy)

</details>

<details>
<summary><strong>Change the color palette</strong></summary>

<br />

Each `IMAGES` entry has `bg` (viewport background) and `panel` (reserved for expanded layouts). Update both hex values per figurine. The crossfade animation works with any valid CSS color.

</details>

<br />

---

<br />

## 📜 Available Scripts

| Command | Description |
|:---|:---|
| `npm run dev` | Start Vite dev server with HMR at `localhost:5173` |
| `npm run build` | Type-check (`tsc -b`) + production bundle (`vite build`) |
| `npm run preview` | Serve the `dist/` output locally |
| `npm run lint` | Run ESLint with React + TypeScript rules |

<br />

---

<br />

## 🤝 Contributing

Contributions are welcome. Here's the workflow:

```bash
# 1. Fork & clone
git clone https://github.com/your-username/toonhub.git

# 2. Create a feature branch
git checkout -b feat/your-feature

# 3. Make changes, then verify
npm run lint
npm run build

# 4. Commit with conventional commits
git commit -m "feat: add swipe gesture support"

# 5. Push & open a Pull Request
git push origin feat/your-feature
```

**Before submitting:** ensure `npm run lint` and `npm run build` pass with zero errors.

<br />

---

<br />

## 📄 License

Released under the [MIT License](LICENSE). Use it, fork it, ship it.

<br />

---

<p align="center">
  <sub>
    Crafted with precision for the Hackathon &nbsp;·&nbsp; Powered by
    <a href="https://react.dev">React</a> +
    <a href="https://vite.dev">Vite</a> +
    <a href="https://tailwindcss.com">Tailwind CSS</a>
  </sub>
</p>

<p align="center">
  <sub>
    <strong>If this project helped you, consider giving it a ⭐</strong>
  </sub>
</p>
