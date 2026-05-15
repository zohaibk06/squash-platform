# ARProformance — Brand & Design System

> Reference doc. This is the design-system manifest from David's **ARProformance
> design-system project** (built in Claude), shared 2026-05-15 as the brand
> reference for this platform. Only this manifest was shared — the files it
> references (`colors_and_type.css`, `assets/arlogo.png`, `preview/`,
> `ui_kits/website/`, `SKILL.md`) are **not** in this repo yet. Treat the rules
> below as the source of truth for visual direction; request the CSS variable
> file and logo SVG from David before building the branded prototype.

---

# ARProformance Design System

> **ARProformance** — *Architecting your squash journey.*
> Programs, video review and 1:1 coaching for ambitious squash players, from club regulars to tournament athletes.

This project is the brand & UI system for ARProformance. It contains the visual foundations (color, type, spacing), brand assets, voice & tone notes, and a working website UI kit.

## Sources

- `uploads/arlogo.png` — provided wordmark + monogram (white "AR" with red horizontal bar over "PROFORMANCE"). Designed for dark backgrounds.
- Color palette and typography were specified directly by the user (see CSS variables in `colors_and_type.css`).
- No codebase or Figma was provided. UI kit screens are interpretive, built from the brand rules + tagline; flag for replacement once the live site is shared.

## Index

| Path | What's there |
|------|--------------|
| `colors_and_type.css` | Single source of truth — CSS variables for color, type scale, spacing, radii, shadows, motion |
| `assets/arlogo.png` | Brand wordmark (use on dark) |
| `preview/` | Design-system specimen cards (registered to Design System tab) |
| `ui_kits/website/` | Marketing site recreation (React + Babel, click-thru booking flow) |
| `SKILL.md` | Skill manifest for using this system in other projects / Claude Code |

---

## Content fundamentals

ARProformance copy is **direct, athletic, and uncompromising**. It addresses ambitious players — not beginners — and treats squash as a serious craft.

**Tone:** confident, precise, unsentimental. Coaches talking to athletes, not marketers talking to leads.
**Voice:** "we" (the team) → "you" (the player). First-person plural is fine; second-person is the default frame.
**Casing:** SHOUTING UPPERCASE for all display headings (Barlow Condensed 900). Sentence case for body. Proper nouns and product names cased normally inline.
**Punctuation:** dashes used as kicker prefixes (`— Programs`, `— Performance Squash`). Periods after short imperative slogans (`Architect your squash journey.`).
**Italics inside headings:** decorative — one accent word per heading in italic + lighter color. Pattern: `MOVE *better*`, `HIT *cleaner*`, `PEAK *performance*`.
**Numbers:** large, red, display-cased (`+220`, `98%`, `14wk`). Stats lead with the number, follow with an uppercase microlabel.
**Emoji:** none. Brand is too serious.
**Vibe:** sports kit, performance-lab, tournament poster. Think Nike Pro × FT magazine layout.

**Do say:** *Architect. Engineered. Periodised. Built around how you actually train. Stop training generic.*
**Don't say:** *Game-changing. Ultimate. Unleash. Take it to the next level.* Avoid hype clichés.

---

## Visual foundations

**Backdrop.** Black-first (`--black #0a0a0a`) page; navy (`--navy #111827`) for elevated cards/sections. Light surfaces (`--off-white`) reserved for inverse moments — quotes, sponsor strips, occasional CTA bands. Color appears in pairs: dark + a single shock of red.

**Typography.** Two faces, no exceptions: **Barlow Condensed** for everything display (900 weight, uppercase, line-height 0.88–0.95, slight negative letter-spacing); **DM Sans** for everything else (300–600). Headings use a single italic accent word in 700 italic + `--light-grey` to break the wall of caps. `clamp()` everywhere for responsive scale.

**Spacing.** 4px base. Generous vertical rhythm — sections breathe at 96–130px top/bottom on desktop. Card interiors at 24–32px. The red bar (in logo, on cards) is the only non-rectangular bit of vocabulary — keep it.

**Backgrounds.** Flat solids. **No gradients** beyond the occasional protection scrim on imagery. **No texture, no grain, no patterns.** When imagery is used (placeholders for now), expect: cool/desaturated, grain-free, sports-photography crops, often duotone-able to red/black.

**Cards.** Dark navy fill, 4px solid red left-rule, 1px hairline border (`--border`), no rounding (sharp corners — this is sports kit, not SaaS). Hover: lift `-4px` and outline in red. Avoid drop shadows on dark cards — use the red stroke as the elevation cue.

**Borders & dividers.** 1px hairline `rgba(255,255,255,0.10)` between sections. 1.5px borders on ghost buttons and underline-style links. The 4px red bar is reserved for brand moments (logo, card accents, active nav indicator).

**Buttons.** Pill-shaped (`--radius-pill 999px`) — the *only* place rounding shows up. Uppercase, 0.2em tracking. Three forms: solid red primary, ghost (transparent + white border), underlined inline link with red rule.

**Hover / press.**
- Buttons: solid red → brighter red `#ff2a32` + soft red glow shadow.
- Ghost: white border ramps to full white + 5% white fill.
- Cards: 4px lift + red border stroke.
- Links: color-only change, light-grey → white. Press: subtle scale `0.98` if interactive.
**Animation:** `cubic-bezier(.2,.7,.2,1)` ease, 120/220/420ms tiers. Linear ticker scrolls. **No bounces, no decorative parallax, no scroll-jacking.**

**Transparency / blur.** Used sparingly: sticky nav uses `rgba(10,10,10,0.85)` + `backdrop-filter: blur(12px)`. Modals scrim the page at `rgba(0,0,0,0.7)` + 6px blur. Otherwise interfaces are opaque.

**Corner radii.** `0` for cards, sections, image frames. `4–8px` for inputs, dropdowns, swatches. `999px` only for buttons, badges, avatars.

**Shadow system.** Reserved for light-on-dark moments and the active-CTA red glow. Standard tiers: `sm` (resting), `md` (hover/overlay), `lg` (modal), `glow-red` (active primary CTA).

**Layout rules.** 1280px max content width with 48px gutters. Sticky nav. Section heads use a left-aligned eyebrow + display heading; right side stays empty intentionally — negative space is a brand element. Stat blocks span the full width as a four-up.

**Iconography vibe.** Minimal. Currently text-and-rule only. When icons are needed, use **Lucide** (CDN) — 1.75–2px stroke matches the system; never mix with filled icon sets or emoji.

---

## Iconography

The provided assets contain no icon set. The brand reads cleanly with **type + the red bar motif** as its primary "iconography." When functional icons are required:

- **Default substitute (flagged):** [Lucide](https://lucide.dev) via CDN — 24px, 1.75–2px stroke, `currentColor`. Use sparingly: nav toggles, form affordances, social links in footer. Do not decorate body copy with icons.
- **No emoji** anywhere in product surfaces.
- **No unicode pictographs** as decoration. The em-dash kicker (`— Programs`) is the only allowed glyph affordance.
- **Logo (`assets/arlogo.png`):** white wordmark on dark surfaces. On light surfaces, invert; preferably commission a true black variant. **Flagged:** a vector (SVG) version of the logo is recommended for crisp scaling — please supply.

**Flagged substitutions to confirm:**
1. **Fonts**: Barlow Condensed + DM Sans loaded from Google Fonts. If you have licensed display files, drop them into `fonts/` and update `colors_and_type.css`.
2. **Icon set**: Lucide is a placeholder. Confirm or replace with brand-specific marks.
3. **Logo SVG**: only PNG provided. SVG strongly recommended.

---

## Iterating

Open the **Design System tab** to review every specimen card. Click any card to see its registered version, request changes, or approve.

---

## Notes for this platform

- **Brand name is `ARProformance`** (deliberate spelling — not "Performance", not
  "AR Performance"). This resolves the PRD §10 brand-name open question; "SquashIQ"
  stays rejected. The coaching framework Ahad uses (Vision → Outcome → Process
  goals; physical/mental/technical/tactical assessment) is the *ARProformance
  coaching lens*.
- The current `prototype.html` already sits on a `#0a0a0a` black ground — that
  much is on-brand. To make a true branded exploration it still needs: Barlow
  Condensed + DM Sans, the navy card system with the 4px red left-rule, sharp
  corners (radius 0) everywhere except pill buttons, and the red `#ff2a32`
  accent used as a single shock per surface.
- Per the user (2026-05-14): the next prototype carries **2–3 visual directions**,
  and **one** of them applies this ARProformance system (Barlow Condensed,
  black/navy + red accent).
- Still needed from David: `colors_and_type.css` (exact CSS variables), the
  logo (SVG preferred), and the `ui_kits/website/` marketing-site reference.
