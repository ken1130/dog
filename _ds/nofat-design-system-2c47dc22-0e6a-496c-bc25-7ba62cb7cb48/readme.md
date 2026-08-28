# nofat Design System

**nofat** is a mobile (iOS, portrait) app: a *proactive* AI fat-loss coach. The product persona is **诺教练 (Coach Nuo)** — a private trainer who, every day, tells you exactly **what to eat and what to train**, then sends a warm, human review at night. The core feeling is *"being led by a coach, never going hungry, able to keep going"* — a warm companion, **not** a cold data tool.

This project is the design system that backs that app: tokens, reusable React components, brand assets, and a full interactive UI kit of the seven core screens.

> **Source:** There was no existing codebase, Figma, or brand kit. This system was designed from the product brief (Chinese). All visual decisions below are original to nofat and open to iteration.

---

## Product principles (hard constraints)

1. **No weight numbers in daily screens.** Weight anxiety is addressed *only* in the Weekly Report, and only as a **trend** — never a daily number. The Today screen shows planned calories, never weight.
2. **"不挨饿 / 管饱" (never hungry, filling).** Meals must look generous and healthy — appetizing imagery, "管饱" tags, portions described as filling.
3. **A coach with warmth.** Copy reads like a real personal trainer texting you, not a system notification.

---

## Content fundamentals (voice & tone)

nofat speaks **as Coach Nuo, to you (你)**, like a trainer you trust.

- **Person:** First-person coach ("我给你配了…") addressing **你**. Never corporate "we", never clinical third person.
- **Warm, concrete, low-pressure.** Praises effort and *habits*, never shames. Skipping a meal gets "没事，下一顿继续就好" — never a red error.
- **Plain spoken, a little casual.** Short sentences. Real-talk phrasing: "盯着习惯，别盯着秤" / "吃得饱，又不囤".
- **Action-first.** Tells you the exact next move: order this, cook that, do this rep count.
- **Casing/punctuation:** Chinese primary; numbers and units in Latin (560 kcal, 3 组 × 12 次). Sentence-style, not Title Case.
- **Emoji:** Sparingly, only in coach messages, as warmth (☀️ 💪 🌙 👍). Never in labels, buttons, or data.

Examples:
- Greeting: *"早呀 ☀️ 今天给你配了顿吃得饱的三餐，蛋白质拉满。先把早餐解决，咱们慢慢来。"*
- Review: *"今天三餐照做了 2 顿，训练也练完了。这种节奏，挺稳的。"*
- Encouragement: *"别盯着秤，盯着习惯。你已经连续 12 天跟下来了。"*

---

## Visual foundations

**Mood:** warm, friendly, encouraging — energetic but never harsh. Light theme throughout.

- **Color.** Primary is a **fresh green** (`--color-primary` #16B97A) = health, vitality, the "照做了 / done" state. Accent is a **warm coral** (`--color-accent` #FF6A3D) = appetite, energy, calories — used sparingly. Neutrals are **warm-green-tinted greys** (`--ink-*`) so even greys feel friendly. Two backgrounds only: `--bg-canvas` (cool off-white) and `--bg-canvas-warm` (used for the evening review / coach chat).
- **Type.** Display & numerals in **Outfit** (geometric, sporty, great tabular figures for calories/reps); body & UI in **Plus Jakarta Sans** (warm, humanist, very legible). Chinese renders in **PingFang SC** (native iOS) with **Noto Sans SC** web fallback. Big numbers are always tabular.
- **Spacing.** 4px base scale. Screen padding 20px; cards padded 18px; cards stacked with 16px gaps.
- **Radii.** Generous and soft: cards **20px**, inputs 14px, chips/buttons are **full pills**. Nothing sharp.
- **Shadows.** Soft, low, slightly warm-green tinted (`--shadow-card` = `0 6px 20px rgba(20,50,35,.07)`). Primary CTAs get a colored green glow (`--shadow-primary`). No hard or dark drop shadows.
- **Cards.** White, 20px radius, soft shadow, no border. Tinted variants (green `tint`, coral `warm`) for emphasis blocks (coach greeting, disclaimer).
- **Backgrounds.** Mostly flat warm-off-white. Subtle decorative rings/blobs in tint colors on the login hero only. No heavy gradients, no textures, no full-bleed photography behind text.
- **Imagery.** Food = appetizing photos; exercises = clear demo photos/diagrams. Until real assets exist, `MediaPlaceholder` shows an on-brand tinted block (coral for food, green for exercise) with an icon — intentional, not broken-looking.
- **Motion.** Gentle. `--ease-out` for most, `--ease-spring` for toggles/checks (a small satisfying pop). Durations 140–360ms. Progress rings animate on mount. No infinite/looping decoration.
- **Hover (web/preview):** subtle background darken/lighten. **Press:** scale 0.97 (buttons), 0.92 (icon buttons), 0.985 (cards) — a tactile shrink, never a color flash.
- **Borders:** hairline `--border-subtle` for dividers; inputs use a 1.5px inset ring that turns green + glow on focus.
- **Transparency/blur:** only the floating chips over meal banners (frosted white `backdrop-filter`).

---

## Iconography

- **Lucide** (lucide.dev, ISC license) — clean 2px round-stroke icons. A curated subset is embedded inline in the **`Icon`** component (`components/core/Icon.jsx`) so the bundle is self-contained (no CDN dependency). Add glyphs to its `PATHS` map as needed; see `ICON_NAMES` for what's available (dumbbell, utensils, chef-hat, flame, leaf, droplet, trophy, target, timer, …).
  > **Substitution note:** Lucide is a stand-in icon system chosen for the warm/sporty stroke style; swap for a licensed/custom set later if desired.
- **Active tab icons** fill with `currentColor`; inactive are stroked.
- **Emoji** are content (coach voice) only — never used as UI icons.
- **Brand mark:** `assets/app-icon.svg` + the `Logo` component — a daily-plan **progress ring** with a coral energy core; wordmark sets "fat" in green so the name reads *no · fat*.

> **Font note:** Outfit / Plus Jakarta Sans / Noto Sans SC load from Google Fonts via `@import` in `tokens/fonts.css` (so no `@font-face` binaries ship in-repo). If you need fully offline/licensed fonts, drop the binaries in and add `@font-face` rules there.

---

## Index / manifest

**Foundations**
- `styles.css` — entry point (`@import` list only).
- `tokens/` — `fonts.css`, `colors.css`, `typography.css`, `spacing.css`, `effects.css`, `base.css`.
- `guidelines/` — foundation specimen cards (Colors, Type, Spacing) shown in the Design System tab.

**Components** (`window.NofatDesignSystem_2c47dc.<Name>`)
- `components/core/` — **Icon, Button, IconButton, Card, Avatar** (+ `styleInject.js` helper)
- `components/forms/` — **Input, Checkbox, Radio, Switch, SegmentedControl, Stepper**
- `components/feedback/` — **Badge, Tag, ProgressBar, MetricRing**
- `components/app/` — **MealCard, CoachBubble, ExerciseRow, ListRow, MediaPlaceholder**
- `components/navigation/` — **AppBar, BottomNav**
- `components/brand/` — **Logo**

**UI kit**
- `ui_kits/nofat/` — interactive 7-screen app (`index.html`): Login, Onboarding (with health-disclaimer gate), **Today's Prescription**, Training execution, Exercise detail, Evening review, Weekly report.

**Assets**
- `assets/app-icon.svg`

**Meta**
- `SKILL.md` — Agent-Skill front matter for reuse in Claude Code.
- Generated automatically (do not edit): `_ds_bundle.js`, `_ds_manifest.json`, `_adherence.oxlintrc.json`.
