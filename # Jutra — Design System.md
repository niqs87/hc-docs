# Jutra — Design System

> **Project:** Jutra ("Jutro" / Tomorrow)
> **Type:** Psychological AI app for teens to talk with their future selves
> **Visual Direction:** Aesthetic Pixel Art × Lo-fi Hip-hop × Retro-Future Sunset
> **Audience:** Polish-speaking teenagers (13–19)
> **Voice:** Empathetic, calm, hopeful, never clinical

---

## 1. Design Philosophy

Jutra lives at the intersection of **nostalgia and possibility**. The pixel art aesthetic evokes the warmth of cozy indie games (Coffee Talk, Stardew Valley, Sea of Stars) — a familiar, safe visual language for the generation that grew up with them. The retro-future sunset palette frames the future as something warm, not intimidating.

### Core Principles

1. **Cozy, never childish** — pixel art that feels modern and crafted, not 8-bit retro novelty.
2. **Calm motion** — every animation breathes slowly. Nothing rushes the user.
3. **Soft technology** — AI is mint-green and gentle, not blue-clinical.
4. **Liminal beauty** — sunsets, dusk, twilight: in-between moments mirror the in-between age of teens.
5. **Empathetic copy** — Polish, second person, present tense, no jargon.

---

## 2. Color Palette — "Retro-Future Sunset"

### Primary Tokens

| Token | Hex | Role | Usage |
|---|---|---|---|
| `--color-midnight` | `#2D1B4E` | Primary | Deep midnight purple — the unknown future, primary surface base |
| `--color-coral` | `#FF8E72` | Secondary | Soft sunset coral — hope, warmth, primary CTAs, user voice |
| `--color-mint` | `#72FFA9` | Accent | Mint neon — AI presence, growth, success, AI voice |

### Supporting Tokens

| Token | Hex | Role |
|---|---|---|
| `--color-deep-blue` | `#0D0A1F` | Background base (deepest) |
| `--color-purple` | `#4A2D7A` | Mid surface, building shadows |
| `--color-soft-purple` | `#3D2060` | Card backgrounds (pre-blur) |
| `--color-light-mint` | `#A8FFD0` | Mint hover/highlight |
| `--color-dark-coral` | `#CC6A50` | Coral button shadow (pixel depth) |

### Gradient — Background

```css
background: linear-gradient(180deg,
  #0D0A1F 0%,
  #1A0D2E 30%,
  #2D1B4E 60%,
  #1A0D2E 100%
);
```

A vertical gradient that sinks from near-black at the top to midnight purple in the middle and back. Suggests deep evening sky.

### Sky Gradient — Dynamic

The hero sky cycles through a full day/night loop. The gradient is computed in real time:

- **Day (timeOfDay 0.0–0.4):** soft blue → warm amber
- **Sunset (0.4–0.6):** orange → coral → magenta
- **Night (0.6–1.0):** deep violet → indigo → near-black with stars

### Color Usage Rules

- **Midnight purple** — never below 60% of the surface. It's the room you sit in.
- **Coral** — reserved for warmth: CTAs, user-spoken text, sunsets, the "human" elements.
- **Mint** — reserved for AI presence: AI text, portal glow, terminal cursors, growth indicators.
- **Never mix coral + mint at equal weight** — one always leads. Coral leads in human contexts, mint leads in AI contexts.
- **No pure white backgrounds. Ever.** White is reserved for sparkles and stars.

---

## 3. Typography

### Font Stack

| Use | Font | Source |
|---|---|---|
| Body / UI | `'Inter', sans-serif` | Google Fonts |
| Headers / AI / Pixel | `'VT323', monospace` | Google Fonts |

### Type Scale

| Level | Font | Size | Letter Spacing | Use |
|---|---|---|---|---|
| Display | VT323 | 72px / 1.0 | normal | Hero headline |
| H1 | VT323 | 48px | 4px | Section titles |
| H2 | VT323 | 36px | 3px | Card titles |
| H3 | VT323 | 24px | 2px | Feature titles |
| Logo / Brand | VT323 | 28px | 3px | Navbar wordmark |
| Body Large | Inter | 16px / 1.6 | normal | Paragraphs |
| Body | Inter | 14px / 1.6 | normal | Card body |
| Caption (pixel) | VT323 | 14–18px | 1–4px | Metadata, labels, tickers |
| Terminal / AI | VT323 | 18px | normal | Chat messages |

### Typography Rules

- VT323 is always uppercase for short labels (`> INICJALIZACJA PORTALU`, `[JUTRO]`).
- VT323 may be mixed case for AI dialogue.
- Inter is always sentence case for body copy.
- Headers can use a coral-to-white gradient via `background-clip: text` for hero impact.
- Letter-spacing **increases** with importance — display text breathes wider.
- Never combine VT323 with all-caps Inter — clash of two voices.

---

## 4. Layout & Spacing

### Grid

- **Max content width:** 900px (text), 1280px (full layouts)
- **Section padding (vertical):** 40–60px
- **Section padding (horizontal):** 48px
- **Card internal padding:** 24px

### Spacing Scale

`4px → 8px → 12px → 16px → 20px → 24px → 32px → 40px → 60px`

All spacing must come from this scale. Pixel art demands rhythm.

### Pixel Grid

All decorative SVG elements snap to a **4px sub-grid**. Stars, particles, hourglass cells, sky elements — never sub-pixel.

---

## 5. Component System

### 5.1 Glass Card

The canonical container.

```
background:        rgba(45, 27, 78, 0.45)    // midnight @ 45% opacity
backdrop-filter:   blur(12px)
border:            2px solid rgba(114, 255, 169, 0.3)  // mint @ 30%
padding:           24px
clip-path:         12-vertex pixel-staircase corners (8px notch)
overlay:           subtle mint top-left light wash
```

**Variants:**
- `default` — as above
- `glow` — adds `animation: glowPulse 4s` (pulsing mint shadow)
- `coral-bordered` — swap mint border for coral when card is human-themed

### 5.2 Pixel Button

```
font:             VT323 / 22px / letter-spacing 1px
padding:          10px 28px
border:           2px solid (coral if primary, mint if secondary)
shadow:           4px 4px 0 (offset block, no blur)
clip-path:        pixel-staircase (4px notch)
on press:         translate(3px, 3px), shadow → none
transition:       0.05s (snappy, not soft)
```

**Variants:**
- `primary` — coral fill, midnight text, dark-coral shadow
- `secondary` — transparent fill, mint text & border, mint-tint shadow

The press effect is **the most important interaction** in the system. It must feel tactile.

### 5.3 Pixel Divider

A row of 4×4px dots cycling coral / mint / transparent. Used to separate sections inside cards. Adds rhythm without weight.

### 5.4 Terminal Chat Bubble

```
[JUTRO]   AI text in mint or near-white
[TY]      User text in coral
font:     VT323 / 18px
prefix:   80px fixed-width column for speaker tag
```

No avatar circles. No message backgrounds. Terminal aesthetic — speaker label + message, like a console log.

### 5.5 Time Portal

The signature animated element.

- 200×220px SVG
- 8 large + 8 small pixel "ring nodes" rotating in a 20s loop
- Inner dark window with the **hourglass→human logo** at center
- 4 ambient particles floating upward on stagger
- Color shifts with `timeOfDay` (mint by day, coral by sunset)

### 5.6 Future Self Avatar

- 120×160px SVG silhouette
- Pixelated translucent figure (mint, layered opacities 0.15→0.8)
- Question mark on the face — "you, but unknown"
- Animations: `avatarFloat 3s` (gentle bob) + `avatarGlow 2s` (mint drop-shadow pulse)

### 5.7 Pixel Logo

The hourglass-merging-into-human silhouette is built from `<rect>` cells:

- Hourglass top → narrow waist → bottom
- A glowing dot falls through the waist (animated)
- Below the waist, the bottom half **morphs into a head + shoulders** in coral
- Symbolizes time crystallizing into a person — the user's future self

---

## 6. Motion & Animation

All animations are **slow and ambient**. No bounces, no springs, no fast easing.

### Animation Library

| Name | Duration | Easing | Use |
|---|---|---|---|
| `pixelTwinkle` | 2s alt | ease-in-out | Star opacity |
| `scrollText` | 20s loop | linear | Marquee ticker |
| `portalSpin` | 20s loop | linear | Portal ring |
| `portalPulse` | 1–2.6s | ease-in-out | Portal node glow |
| `particleFloat` | 2–3s | ease-out | Ambient particles rising |
| `avatarFloat` | 3s alt | ease-in-out | Avatar bob |
| `avatarGlow` | 2s alt | ease-in-out | Avatar mint glow |
| `glowPulse` | 4s | ease-in-out | Card breathing |
| `fadeInUp` | 0.8s | ease-out | Section entrance |
| `dayNightCycle` | live | linear | `timeOfDay` 0→1 over ~100s |

### Motion Rules

- **Nothing snaps except button press.** Buttons are tactile; everything else is breath.
- **No parallax scroll.** The portal and sky are the only motion focal points.
- **Background motion never demands attention** — sky/stars/particles loop slowly enough to feel ambient, not animated.

---

## 7. Iconography

### Style

Icons are **monochrome pixel glyphs**, drawn from these primitives:

- `◈` (diamond outline) — process, transformation
- `◉` (filled circle) — safety, presence, focus
- `★` (star) — moment, milestone, decoration
- `◆` (filled diamond) — active state, power
- `♀ ♂` (gender symbols) — testimonial avatars (placeholder until illustrated portraits exist)

### Rules

- Single color per icon (mint or coral by context)
- Sized in 4px increments (16, 24, 32, 36)
- Never use multi-color emoji or vector icons (Lucide, Heroicons, etc.) — breaks the pixel aesthetic.

---

## 8. Pixel Art Conventions

### Sub-grid

Every decorative pixel element snaps to a **2px or 4px sub-grid**. Stars are 2×2 or 3×3. Hourglass cells are 4×4. Building windows are 6×6 or 8×8. Consistency is the entire aesthetic.

### Staircase Corners

All borders use 12-point clip-paths to create 4–8px corner notches. This converts straight rectangles into pixel-art frames without bitmap sprites:

```css
clip-path: polygon(
  0 8px, 8px 8px, 8px 0,
  calc(100% - 8px) 0, calc(100% - 8px) 8px, 100% 8px,
  100% calc(100% - 8px), calc(100% - 8px) calc(100% - 8px), calc(100% - 8px) 100%,
  8px 100%, 8px calc(100% - 8px), 0 calc(100% - 8px)
);
```

### Scanline Overlay

A fixed full-screen overlay applies subtle horizontal scanlines (2px transparent / 2px 3% black) over the entire UI, evoking CRT screens without obscuring content.

---

## 9. Voice & Copy (Polish)

### Tonality

- **Second person, informal** ("Ty", "Twoje", not "Państwo")
- **Present and future tense** — never past
- **Empathetic, never directive** — "Porozmawiaj z…" not "Musisz porozmawiać"
- **No tech jargon** — "Portal czasu" not "Algorytm AI"
- **Lowercase emotional register, uppercase functional register**

### Sample Copy Bank

| Context | Copy |
|---|---|
| Hero headline | `POROZMAWIAJ Z PRZYSZŁYM SOBĄ` |
| Hero subhead | "Jutra to bezpieczna przestrzeń, gdzie możesz porozmawiać z AI, które wciela się w Ciebie za 10 lat." |
| Primary CTA | `ZACZNIJ TERAZ` / `OTWÓRZ PORTAL` |
| Secondary CTA | `DOWIEDZ SIĘ WIĘCEJ` |
| Status (pixel) | `> INICJALIZACJA PORTALU CZASU…` |
| AI greeting | "WITAJ. Jestem Tobą — Tobą za 10 lat. Czego chcesz się dowiedzieć?" |
| Speaker tag (AI) | `[JUTRO]` |
| Speaker tag (user) | `[TY]` |
| Ticker phrases | "TWOJE JUTRO CZEKA", "POROZMAWIAJ Z PRZYSZŁOŚCIĄ", "ODKRYJ KIM BĘDZIESZ" |
| Footer brand | `JUTRA © 2034` |

### What to Avoid

- Marketing speak ("rewolucyjna platforma")
- Mental-health clinical language ("terapia", "diagnoza")
- Patronizing teen voice ("hej młody!", "wbijaj")
- Emojis in copy — pixel glyphs only
- Exclamation points in hero copy — calm wins

---

## 10. Sky & Day/Night Cycle

The hero sky is a living element — the design system's emotional anchor.

### Cycle Phases

| Phase | timeOfDay | Mood |
|---|---|---|
| Dawn | 0.0–0.2 | Soft blue, sun rising right |
| Day | 0.2–0.4 | Warm amber-blue, sun high |
| Sunset | 0.4–0.6 | Coral wash, sun on horizon |
| Dusk | 0.6–0.8 | Magenta-purple, moon rising |
| Night | 0.8–1.0 | Deep indigo, full stars, moon high |

The cycle progresses ~0.0005 per 50ms (~100s full loop).

### Symbolic Meaning

The cycle reinforces the app's core message: **time always moves, and tomorrow always comes**. The user sits in a window watching the sky change while talking to their future — visually grounding the metaphor.

---

## 11. Accessibility & Responsibility

### Contrast

- All body text on backgrounds passes WCAG AA at minimum.
- Pixel-font headers (VT323) require larger sizes (≥18px) to maintain legibility.
- Mint and coral are calibrated to remain readable on midnight backgrounds.

### Reduced Motion

When users opt into `prefers-reduced-motion`:
- Sky cycle pauses at neutral dusk
- Portal stops spinning (nodes still glow gently)
- Particles disappear
- Avatar stops floating

### Audience Care

This is a product for teenagers exploring identity and emotional life. Design carries responsibility:

- Never use streaks, gamification, or social pressure mechanics.
- Never style emotional disclosures with confetti or celebrations.
- Always provide a visible exit — "Zamknij portal" should always be one click away.
- The AI never claims to be human, never claims to predict real futures — it is explicitly framed as "wyobrażenie Ciebie" (an imagining of you).

---

## 12. File Reference

| File | Role |
|---|---|
| `artifacts/mockup-sandbox/src/components/mockups/jutra-landing/LandingPage.tsx` | Reference implementation of every component in this system |
| `artifacts/mockup-sandbox/index.html` | Loads VT323 + Inter from Google Fonts |
| `jutra-design-system.md` | This document |

---

## 13. Quick Reference Cheat Sheet

```
COLORS    midnight #2D1B4E · coral #FF8E72 · mint #72FFA9
FONTS     Inter (body) · VT323 (headers, AI, pixel)
RADIUS    none — use pixel staircase clip-path instead
BORDERS   2px solid, mint @ 30% opacity by default
SHADOWS   block offset (4px 4px 0), never blurred
ANIMATION slow & ambient (≥2s), button press snaps (50ms)
GRID      4px sub-grid for all pixel elements
LANGUAGE  Polish, second person, calm, present tense
```

---

*Jutro nie jest miejscem, do którego idziesz. Jutro to ktoś, z kim rozmawiasz.*
