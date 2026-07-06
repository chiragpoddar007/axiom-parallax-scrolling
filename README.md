# AXIOM — Geometry in Motion

An interactive parallax scrolling experience built for **Techfest, IIT Bombay** (Web Development domain — *Interactive Parallax Scrolling Page*).

🔗 **Live demo:** https://chiragpoddar007.github.io/axiom-parallax-scrolling/

![Axiom](https://github.com/chiragpoddar007/axiom-parallax-scrolling/blob/main/image/main_page.png) ![01 — Lines](https://github.com/chiragpoddar007/axiom-parallax-scrolling/blob/main/image/01%20%E2%80%94%20Lines.png) ![02 — Planes](https://github.com/chiragpoddar007/axiom-parallax-scrolling/blob/main/image/02%20%E2%80%94%20Planes.png) ![03 — Volume](https://github.com/chiragpoddar007/axiom-parallax-scrolling/blob/main/image/03%20%E2%80%94%20Volume.png) ![Conclusion](https://github.com/chiragpoddar007/axiom-parallax-scrolling/blob/main/image/Conclusion%20%C2%B7%20The%20Axiom%20(2).png) 


---

## Concept

A scroll journey through the mathematical building blocks of geometry — **Points → Lines → Planes → Volume**. The progression mirrors Euclid's *Elements*, so the parallax isn't just decorative; it encodes the subject matter itself.

As you scroll, four independent depth layers move at different speeds, creating a convincing illusion of three-dimensional space on a flat screen. The further a layer is from the viewer, the less it moves — the same principle that makes distant mountains appear still while nearby trees blur past.

## How the parallax works

Four speed layers are positioned in a single `position: absolute` scene that spans the full document height:

| Layer | Speed | What it contains | Visual effect |
|-------|-------|-----------------|---------------|
| A | `0.06` | Giant section numbers (00–03), large rotating rings | Near-fixed — appears infinitely far back |
| B | `0.22` | Medium circles, squares, rectangles | Slow drift — mid-background |
| C | `0.47` | Accent diamonds, lines, outlined circles | Moderate drift — mid-foreground |
| D | `0.74` | Small bright glowing dots | Fast drift — closest layer |

**The formula:**
```js
offset = scrollY * (1 - speed);
element.style.transform = `translateY(${offset}px)`;
```
A higher speed value means more counteraction against the scroll → element appears to move *with* the viewer → feels closer. Lower speed → barely moves → feels far away.

## Features

- **4 genuine parallax depth layers** — not a CSS trick, actual JS-driven per-speed translation
- **Scroll progress bar** — `scaleX` animation tied to scroll position, gradient orange → violet
- **Section reveal animations** — `IntersectionObserver` fades content in as each section enters view
- **Active nav link highlighting** — tracks which section is currently in the viewport
- **Smooth anchor scrolling** with nav offset compensation
- **Idle shape animations** — float, rotate CW/CCW, diamond spin — layered on child elements (not the parallax wrapper) so transforms don't conflict
- **`prefers-reduced-motion` respected** — all parallax and animation disabled for users who request it
- **Fully responsive** — tested from 390px (iPhone) to 1440px+
- **Zero JS dependencies** — vanilla JS only, no libraries or build step

## Tech Stack

- HTML5 + CSS3 (custom properties, CSS Grid, `clamp()` for fluid type)
- Vanilla JavaScript — `requestAnimationFrame`, `IntersectionObserver`, passive scroll listener
- Fonts: Bebas Neue, DM Sans, JetBrains Mono (Google Fonts)
- No frameworks, no bundler, no dependencies

## Running locally

Single file — just open it.

```bash
git clone https://github.com/chiragpoddar007/axiom-parallax-scrolling.git
cd axiom-parallax-scrolling
open index.html   # or double-click the file
```

No internet connection needed after first load (fonts cache after the first visit).

## Sections

1. **Hero** — "PURE FORM. PURE MOTION." with Euclid quote and animated scroll indicator
2. **01 — Lines** — The first dimension, violet accent, right-aligned layout
3. **02 — Planes** — The second dimension, orange accent, left-aligned layout
4. **03 — Volume** — The third dimension, emerald accent, right-aligned layout
5. **End** — "FORM IS MOTION." — synthesis of all three, with CTA

## Design notes

Deliberately distinct from the other two Techfest submissions in this series ([Nerve-Cyborg-Landing-Page](https://github.com/chiragpoddar007/Nerve-Cyborg-Landing-Page) and [Build-in-3d](https://github.com/chiragpoddar007/Build-in-3d):

- Coral orange `#ff6542` as primary (vs. teal in the other builds)
- Bebas Neue display type (vs. Orbitron / Space Grotesk)
- Deep navy-black `#06070e` base with subtle film-grain texture overlay

The aesthetic risk: using near-invisible giant typography (opacity 0.03–0.04) as the furthest parallax layer — these section numbers drift so slowly they feel printed on the back wall of infinite space.

## Credits

Built by **Chirag** for Techfest, IIT Bombay — Web Development domain.
