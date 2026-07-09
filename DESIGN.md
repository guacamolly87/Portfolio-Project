# Portfolio — Design System

A precise implementation guide for generating interface screens consistently. **Always consume semantic tokens, never raw hex.**

**Reference implementation:** `test-2.html` — canonical homepage/demo page demonstrating tokens, components, layout patterns, theme showcases, motion utilities, and WCAG patterns below. **`stockandstem/index.html`** — canonical project case-study page (theme galleries, feature lists, deployment CTA).

**Global defaults** (unless a component explicitly overrides): dark surfaces only · `radius.none` on structural UI (buttons use `radius.md`) · flat elevation (no drop shadows except modals) · a single violet accent governed by the Accent Budget · content-based `em` padding inside controls · px `space.*` for layout gaps.

<style>
  /* Pop-in entrance utilities — fade + slide-up (motion.duration.slow + motion.easing.entrance) */
  @keyframes pop-in {
    from {
      opacity: 0;
      transform: translateY(16px);
    }
    to {
      opacity: 1;
      transform: translateY(0);
    }
  }

  .animate-pop-in {
    animation: pop-in 400ms cubic-bezier(0, 0, 0, 1) both;
  }

  .animate-pop-in--card  { animation-delay: 0ms; }
  .animate-pop-in--image { animation-delay: 120ms; }
  .animate-pop-in--text  { animation-delay: 240ms; }

  @media (prefers-reduced-motion: reduce) {
    .animate-pop-in,
    .animate-pop-in--card,
    .animate-pop-in--image,
    .animate-pop-in--text {
      animation: none;
      opacity: 1;
      transform: none;
    }
  }
</style>

---

## Brand Personality

Confident, modern, and moody — technical but stylish. Premium dark-mode UI with an editorial sensibility: selective uppercase on short H1/H2, sentence-case subheadings, dense media, and generous text padding. Balanced by a restrained single-accent palette, soft-rounded buttons, and flat rectilinear framing on cards and inputs. Personality of a design-forward creative professional. Positioning: **clarity at the intersection of information science and UX**. Keywords: research, strategy, modern UX.

### Brand mark (wordmark)
The nav wordmark is the **mgriffin designs** logo image — not a text heading.

| Property | Value |
|----------|-------|
| Asset | `assets/mgriffin-designs.png` |
| Version | **Final** — enlarged “designs” subtext for readability on dark surfaces |
| Variant | **Dark-background** — “griffin” + “designs” in `violet.100`; white “m” on `violet.500` circle; required on `bg.base` / dark nav |
| Composition | Purple circle + white **m** · **griffin** (bold lowercase) · **designs** (smaller lowercase, right-aligned under “iffin”) |
| Native size | 144 × 48 px |
| Display height | 36 px; width auto (preserves aspect ratio) |
| Markup | Home link → `<img>` with `alt="mgriffin designs"`; link `aria-label="mgriffin designs — home"` |
| Focus | `border.focus` ring on the link, 4px offset |

Do **not** use earlier logo iterations with smaller “designs” text or the light-background variant (dark gray wordmark) on dark surfaces — contrast fails against `bg.base`.

---

## Design Principles

1. **Default every surface to dark; earn brightness.** Base is `bg.base`, raised surfaces are `bg.surface`. Never use white or light-gray panels.
2. **Spend the violet accent by budget, not by feel.** `#6A53FE` has four allowed jobs only (see Accent Budget). Everything else is neutral.
3. **Use exactly two button variants** — solid violet primary, outlined secondary. No third fill variant, no gradients, no pills.
4. **Split typography into two locked roles.** Barlow Condensed for all headings; Manrope for all functional text. Never swap roles. Case follows heading case rules (caps only on H1/H2 ≤ 3 words).
5. **Keep structural UI rectilinear; soften buttons only.** Cards, inputs, badges, and frames use `radius.none`. Buttons use `radius.md` (12px). Curves on imagery and avatars come from content, not chrome.
6. **Express depth with value, not shadows.** Separate layers via surface color or a hairline. No drop shadows (modal overlay excepted).
7. **Pack media edge-to-edge; give text room.** Media grids use 0–4px gutters; reading content uses generous padding. On **homepage and demo pages**, body copy is capped at ≈ 65ch (`.measure`). On **project case-study pages**, body copy spans the full container width — padding comes from the container and theme-card interiors, not a character measure.
8. **Constrain imagery to two treatments** — saturated violet/lilac or high-contrast black-and-white, both dark and dramatically lit.

### Accent Budget (governs all violet `#6A53FE` usage)
Violet may appear on a screen **only** as:
1. **One** primary button (the single main action per view).
2. **One** current-location indicator (active nav item or active tab).
3. Focus rings and keyboard-focus emphasis.
4. Selected/active/error borders on controls (checkbox, selected card, invalid input).

Violet is **never** used for hover states, body text, decorative fills, dividers, or more than one primary button per view. Links use underline on `text.primary`, not violet fill.

---

## Color Tokens

### Primitives
| Token | Value | Notes |
|-------|-------|-------|
| `color.violet.500` | `#6A53FE` | Brand accent |
| `color.violet.100` | `#CAC8F3` | Primary text on dark |
| `color.ink.900` | `#0B0A10` | Page background |
| `color.ink.800` | `#1A191F` | Raised surfaces; lavender theme text |
| `color.neutral.200` | `#D1D2E0` | Night-theme header/body base |

### Semantic — surfaces & fills
| Token | Value | Usage |
|-------|-------|-------|
| `color.bg.base` | `ink.900` | App/page background |
| `color.bg.surface` | `ink.800` | Cards, nav, modals, demo panels, raised surfaces |
| `color.bg.primary` | `violet.500` | Primary button / selected fill |
| `color.bg.primary.hover` | `violet.500` @ 90% | Primary button hover (slightly darker) |
| `color.bg.primary.active` | `violet.500` @ 80% | Primary button pressed |
| `color.bg.secondary` | `transparent` | Secondary (outline) button fill; renders as its parent surface |
| `color.bg.hover` | `violet.100` @ 6% | Neutral hover wash on secondary buttons, nav items, rows, cards |
| `color.bg.disabled` | `ink.800` | Disabled control surface |

### Semantic — text (emphasis ladder)
| Token | Value | Usage |
|-------|-------|-------|
| `color.text.primary` | `violet.100` @ 100% | Default text on dark (12.3:1 on base — AAA) |
| `color.text.muted` | `violet.100` @ 70% | Secondary text, inactive nav/tab labels, contact values (6.3:1 on base — AA) |
| `color.text.disabled` | `violet.100` @ 40% | Disabled text, placeholders (2.8:1 — exempt from contrast requirements) |
| `color.text.onPrimary` | `ink.900` | **Mandatory** label on violet fill (4.0:1). Primary buttons and accent badges. |
| `color.text.accent` | `violet.500` | Emphasis on **large text only** (≥24px or ≥18.67px bold; 4.0:1 on base) |

### Semantic — borders
| Token | Value | Usage |
|-------|-------|-------|
| `color.border.subtle` | `violet.100` @ 18% | Dividers, card edges, input rest state, `elevation.2` hairline |
| `color.border.strong` | `violet.100` @ 100% | Secondary button outline, high-emphasis edges |
| `color.border.accent` | `violet.500` | Selected/active/error borders (Accent Budget #4) |
| `color.border.focus` | `violet.100` @ 100% | 2px keyboard focus ring |

### Secondary color usage (no second accent hue)
"Secondary" in this system means **neutral supporting tokens**, not a second brand color:
- **Surfaces:** `bg.surface` (`ink.800`) layered on `bg.base`
- **Text:** `text.muted` and `text.disabled` on the emphasis ladder
- **Borders:** `border.subtle` (low) vs `border.strong` (high)
- **Controls:** secondary button variant (transparent + `border.strong`)

> **Accessibility-First policy:** All text on `bg.primary` uses `text.onPrimary` (`ink.900`). Never use `violet.100` (#CAC8F3) on violet fills.
> **No semantic palette:** no red/green/amber. Status is conveyed by icon + text label + accent border for errors — never by hue.

### Color theme showcases

Two alternate section treatments for hero blocks, feature panels, or case-study intros. Each color theme ships in grid and split layouts.

| Theme | Token | Background | Text / header | Layout |
|-------|-------|------------|---------------|--------|
| **Option 1 — Light lavender** | `theme.lavender` | `#CAC8F3` (`violet.100`) | `#1A191F` (`ink.800`) | Body + one or two 16:9 images (stacked) |
| **Option 1b — Light lavender (split)** | `theme.lavender.split` | `#CAC8F3` (`violet.100`) | `#1A191F` (`ink.800`) | Header + body left; one tall placeholder far right — **demo/showcase only** |
| **Option 2 — Dark night** | `theme.night` | `#0B0A10` (`ink.900`) | `#D1D2E0` | Body + one or two 16:9 images (stacked) |
| **Option 2b — Dark night (split)** | `theme.night.split` | `#0B0A10` (`ink.900`) | `#D1D2E0` | One tall placeholder far left; header + body right — **demo/showcase only** |

**Layout (grid — default on project pages):** wrap the card in a `demo-panel` (see **Project pages** below for case-study wrapper rules). Theme cards use padding `space.5` (< `bp.md`) / `30px` (≥ `bp.md`) on **all sides** · border-radius `8px` (theme-card exception to `radius.none`) · body↔images gap `space.6` · image gap `16px` · figures `16:9`. Body copy is **full width within card padding** — no `65ch` cap.

**Layout (split — `test-2.html` showcase only):** card padding `0`; content column padding `30px`; tall placeholder `min-height` ≈ `300px` · width ≈ `38%` (max `240px`); lavender = text left / image right · night = image left / text right. **Do not use split layouts on project case-study pages** — side-by-side columns compress body copy on laptop viewports.

**Dark night** cards add `border.subtle` because fill (`ink.900`) matches `bg.base`.

**Theme typography & placeholder contrast:**

| Role | Lavender (`theme.lavender`) | Night (`theme.night`) |
|------|----------------------------|------------------------|
| Header | `#1A191F` (`ink.800`) | `#D1D2E0` (`neutral.200`) |
| Body | `ink.800` @ 75% | `neutral.200` @ 75% |
| Placeholder label | `ink.800` @ **70%** (5.1:1 AA) | `neutral.200` @ **55%** (4.5:1 AA) |

<div style="background: #1A191F; border: 1px solid rgba(202, 200, 243, 0.18); padding: 24px; font-family: Manrope, sans-serif;">

#### Option 1 — Light lavender

<div style="background: #CAC8F3; color: #1A191F; padding: 30px; border-radius: 8px; margin-bottom: 24px; font-family: Manrope, sans-serif;">
  <h3 style="color: #1A191F; font-family: 'Barlow Condensed', sans-serif; font-size: 20px; font-weight: 700; margin: 0 0 12px 0; line-height: 1.3;">Research at the intersection of clarity</h3>
  <p style="color: rgba(26, 25, 31, 0.75); font-size: 16px; line-height: 1.5; margin: 0 0 32px 0; max-width: 65ch;">A light lavender panel for editorial intros and feature callouts. High contrast ink text on a soft lilac field keeps the mood bright without breaking the brand palette.</p>
  <div style="display: flex; gap: 16px; flex-wrap: wrap; margin-bottom: 16px;">
    <div style="flex: 1 1 200px; aspect-ratio: 16 / 9; background: rgba(26, 25, 31, 0.08); border: 1px dashed rgba(26, 25, 31, 0.25); display: flex; align-items: center; justify-content: center; font-size: 14px; color: rgba(26, 25, 31, 0.70);">Image placeholder</div>
    <div style="flex: 1 1 200px; aspect-ratio: 16 / 9; background: rgba(26, 25, 31, 0.08); border: 1px dashed rgba(26, 25, 31, 0.25); display: flex; align-items: center; justify-content: center; font-size: 14px; color: rgba(26, 25, 31, 0.70);">Image placeholder</div>
  </div>
</div>

#### Option 1b — Light lavender (split)

<div style="background: #CAC8F3; color: #1A191F; padding: 0; border-radius: 8px; margin-bottom: 24px; font-family: Manrope, sans-serif; overflow: hidden;">
  <div style="display: flex; flex-direction: row; align-items: stretch; min-height: 300px;">
    <div style="flex: 1; display: flex; flex-direction: column; justify-content: center; padding: 30px;">
      <h3 style="color: #1A191F; font-family: 'Barlow Condensed', sans-serif; font-size: 20px; font-weight: 700; margin: 0 0 12px 0; line-height: 1.3;">Designing for human context</h3>
      <p style="color: rgba(26, 25, 31, 0.75); font-size: 16px; line-height: 1.5; margin: 0;">Split layout — header and body on the left; one tall placeholder on the far right spanning the full card height.</p>
    </div>
    <div style="flex: 0 0 38%; max-width: 240px; min-height: 300px; background: rgba(26, 25, 31, 0.08); border-left: 1px dashed rgba(26, 25, 31, 0.25); display: flex; align-items: center; justify-content: center; font-size: 14px; color: rgba(26, 25, 31, 0.70);">Image placeholder</div>
  </div>
</div>

#### Option 2b — Dark night (split)

<div style="background: #0B0A10; color: #D1D2E0; padding: 0; border-radius: 8px; border: 1px solid rgba(202, 200, 243, 0.18); margin-bottom: 24px; font-family: Manrope, sans-serif; overflow: hidden;">
  <div style="display: flex; flex-direction: row; align-items: stretch; min-height: 300px;">
    <div style="flex: 0 0 38%; max-width: 240px; min-height: 300px; background: rgba(209, 210, 224, 0.06); border-right: 1px dashed rgba(209, 210, 224, 0.25); display: flex; align-items: center; justify-content: center; font-size: 14px; color: rgba(209, 210, 224, 0.55);">Image placeholder</div>
    <div style="flex: 1; display: flex; flex-direction: column; justify-content: center; padding: 30px;">
      <h3 style="color: #D1D2E0; font-family: 'Barlow Condensed', sans-serif; font-size: 20px; font-weight: 700; margin: 0 0 12px 0; line-height: 1.3;">Strategy rooted in evidence</h3>
      <p style="color: rgba(209, 210, 224, 0.75); font-size: 16px; line-height: 1.5; margin: 0;">Split layout — one tall image placeholder on the far left, header and body on the right. Cool neutral text on ink-black ground.</p>
    </div>
  </div>
</div>

#### Option 2 — Dark night

<div style="background: #0B0A10; color: #D1D2E0; padding: 30px; border-radius: 8px; border: 1px solid rgba(202, 200, 243, 0.18); font-family: Manrope, sans-serif;">
  <h3 style="color: #D1D2E0; font-family: 'Barlow Condensed', sans-serif; font-size: 20px; font-weight: 700; margin: 0 0 12px 0; line-height: 1.3;">Strategy rooted in evidence</h3>
  <p style="color: rgba(209, 210, 224, 0.75); font-size: 16px; line-height: 1.5; margin: 0 0 32px 0; max-width: 65ch;">A deep night panel for immersive storytelling and project deep-dives. Cool neutral text on ink-black ground extends the default dark UI into full-bleed section moments.</p>
  <div style="display: flex; gap: 16px; flex-wrap: wrap; margin-bottom: 16px;">
    <div style="flex: 1 1 200px; aspect-ratio: 16 / 9; background: rgba(209, 210, 224, 0.06); border: 1px dashed rgba(209, 210, 224, 0.25); display: flex; align-items: center; justify-content: center; font-size: 14px; color: rgba(209, 210, 224, 0.55);">Image placeholder</div>
    <div style="flex: 1 1 200px; aspect-ratio: 16 / 9; background: rgba(209, 210, 224, 0.06); border: 1px dashed rgba(209, 210, 224, 0.25); display: flex; align-items: center; justify-content: center; font-size: 14px; color: rgba(209, 210, 224, 0.55);">Image placeholder</div>
  </div>
</div>

</div>

---

## Typography

**Families:** `font.family.display` = "Barlow Condensed"; `font.family.body` = "Manrope".
**Weights:** regular 400 · medium 500 · semibold 600 · bold 700.
**Sizes:** fluid `rem` scale anchored to a responsive root (see **Responsive root** below). Reference targets at 16px browser default: xs 12 · sm 14 · md 16 (base) · lg 20 · xl 28 · 2xl 40 · 3xl 56.
**Leading:** tight 1.1 · snug 1.3 · normal 1.5 · relaxed 1.625. **Tracking:** tight −0.01em · normal 0 · wide 0.04em.

### Responsive root
Set on `html` in every page — do **not** hard-code `px` on `body` or type presets:

```css
html {
  font-size: clamp(1rem, 0.9375rem + 0.35vw, 1.25rem);
}
```

This keeps body copy at 16px on narrow viewports and scales up to 20px on laptop/desktop widths, improving readability without oversized text on large monitors.

### Prose measure
Long-form reading blocks use a comfortable line length — **not** full card/container width:

```css
:root {
  --leading-relaxed: 1.625;
  --prose-max-width: 70ch;
}

.prose-measure,
.theme-card__body > p,
.theme-card__body > ul,
.theme-card__body > h3,
.theme-card__body > .theme-gallery__figure-title,
.theme-card__body .feature-list > li:not(:has(.theme-card__figure)),
.section__body,
.project-hero__summary {
  max-width: var(--prose-max-width);
}
```

Figures, galleries, and feature-list items with screenshots stay full card width. Body copy uses `line-height: var(--leading-relaxed)` for a calm, airy rhythm.

### Type tokens (`:root`)
Define once per page; all `.type-*` classes reference these variables:

| Token | CSS variable | Scale |
|-------|--------------|-------|
| `type.display.lg` | `--type-display-lg: clamp(2.5rem, 2rem + 2vw, 3.5rem)` | 40px → 56px |
| `type.display.md` | `--type-display-md: clamp(2rem, 1.625rem + 1.5vw, 2.5rem)` | 32px → 40px |
| `type.heading` | `--type-heading: clamp(1.5rem, 1.3rem + 0.75vw, 1.75rem)` | 24px → 28px |
| `type.subheading` | `--type-subheading: clamp(1.125rem, 1.05rem + 0.35vw, 1.375rem)` | 18px → 22px |
| `type.body` | `--type-body: 1rem` | follows root |
| `type.body.sm` | `--type-body-sm: 0.875rem` | 14px @ 16px root |
| `type.label` | `--type-label: 0.875rem` | 14px @ 16px root |
| `type.caption` | `--type-caption: 0.75rem` | 12px @ 16px root |

**Rules:** use `var(--type-*)` on all typography classes, buttons, nav links, theme-card body copy, and gallery captions. Do **not** add breakpoint-only jumps (e.g. `56px` at `768px`) — `clamp()` handles fluid scaling. Nested components inherit the responsive root via `rem`.

### Role presets
| Token | Family | Size | Weight | Case | Leading / Tracking |
|-------|--------|------|--------|------|--------------------|
| `type.display.lg` | display | `var(--type-display-lg)` | bold | see case rules | tight / wide† |
| `type.display.md` | display | `var(--type-display-md)` | bold | see case rules | tight / wide† |
| `type.heading` | display | `var(--type-heading)` | bold | sentence | snug / normal |
| `type.subheading` | display | `var(--type-subheading)` | semibold | sentence | snug / normal |
| `type.body` | body | `var(--type-body)` | regular | sentence | relaxed |
| `type.body.sm` | body | `var(--type-body-sm)` | regular | sentence | relaxed |
| `type.label` | body | `var(--type-label)` | medium | sentence | snug |
| `type.button` | body | `var(--type-body)` | semibold | sentence | snug |
| `type.caption` | body | `var(--type-caption)` | regular | sentence | normal |

†When `case.caps` applies, use wide tracking (0.04em). When `case.sentence` applies on H1/H2, use normal tracking.

### Case tokens
| Token | CSS | Usage |
|-------|-----|-------|
| `case.caps` | `text-transform: uppercase; letter-spacing: 0.04em` | Short H1/H2 only (≤ 3 words) |
| `case.sentence` | `text-transform: none; letter-spacing: normal` | H3/H4, long H1/H2, all body/UI text |

### Heading case rules
Count words in the heading string (split on whitespace).

| Level | Word count | Case token | Example |
|-------|------------|------------|---------|
| H1 | ≤ 3 words | `case.caps` | "Designing for clarity" → DESIGNING FOR CLARITY |
| H1 | > 3 words | `case.sentence` | "Building accessible design systems at scale" |
| H2 | ≤ 3 words | `case.caps` | "Selected work" → SELECTED WORK |
| H2 | > 3 words | `case.sentence` | "Recent projects and case studies" |
| H3 | any | `case.sentence` | "Color contrast validator" |
| H4 | any | `case.sentence` | "Project overview" |

Keep source HTML in sentence case; apply `case.caps` via CSS `text-transform` for screen-reader fidelity.

### Hierarchy rules
- **Heading mapping:** H1 → `type.display.lg` · H2 → `type.display.md` · H3 → `type.heading` · H4 → `type.subheading`. Do not skip levels.
- All headings use Barlow Condensed with `case.caps` or `case.sentence` per table. All non-heading text uses Manrope.
- **`type.label` vs `type.body.sm`:** `label` (medium) = form labels, column headers, metadata keys, contact anchors (weight 600 when anchoring). `body.sm` (regular) = helper text, card descriptions, secondary paragraphs.
- **Measure:** body text max ≈ 70ch (`.prose-measure` / `--prose-max-width`) on homepage intro copy and project case-study prose blocks; theme-card figures and galleries may span full card width. Homepage `.measure` maps to the same `70ch` token.
- **Links:** `text.primary` + 1px underline at rest; underline thickens / shifts to `border.accent` on hover. Not violet-filled text.

---

## Spacing

4px base scale for **layout** padding, margin, and gap.

| Token | Value | | Token | Value |
|-------|-------|-|-------|-------|
| `space.0` | 0 | | `space.5` | 24 |
| `space.1` | 4 | | `space.6` | 32 |
| `space.2` | 8 | | `space.7` | 48 |
| `space.3` | 12 | | `space.8` | 64 |
| `space.4` | 16 | | | |

### Usage bands
- **Control internal padding:** `button.padding.*` tokens (`em`) or `space.3` for inputs — not arbitrary px.
- **Element gaps within a group:** `space.2`–`space.4` (label↔field, icon↔text, button rows).
- **Card / content-block padding:** `space.5`.
- **Section rhythm:** `space.7`–`space.8` vertical gaps between major sections.

### Density aliases
- `space.gutter.media` = `space.0` — edge-to-edge media.
- `space.gutter.tile` = `space.1` — minimal gap mosaics.
- `space.gutter.grid` = `space.5` — standard content/card grids (24px).
- `space.pad.page` = `space.4` (< md) / `space.6` (≥ md) — container horizontal padding.

**Mosaic vs grid:** mosaic gutters only for pure-media galleries; standard grid for anything with text, controls, or data.

### Content-based sizing
Prefer **`em`** for padding inside components (scales with control font-size). Use **`space.*` (px)** for gaps between components.

| Context | Unit | Example |
|---------|------|---------|
| Button internal padding | `em` | `button.padding.default` |
| Input internal padding | `px` (`space.3`) | 12px — fixed for form alignment |
| Gaps between siblings | `space.*` | `space.3` between buttons |
| Page/section layout | `space.*` | `space.pad.section` |

**Rules:** set `font-size` first, then derive button padding from `em`; primary and secondary buttons share the same padding token per size variant; never hard-code px on buttons when a `button.padding.*` token applies.

### Button padding tokens
Relative to the button's `font-size`. Shared by primary and secondary variants.

| Token | Value | @ 16px | @ 14px |
|-------|-------|--------|--------|
| `button.padding.default` | `0.75em 1.5em` | 12px 24px | 10.5px 21px |
| `button.padding.compact` | `0.5em 1.25em` | 8px 20px | 7px 17.5px |

---

## Layout

### Breakpoints
| Token | Min width |
|-------|-----------|
| `bp.sm` | 640px |
| `bp.md` | 768px |
| `bp.lg` | 1024px |
| `bp.xl` | 1280px |

### Grid & containers
- **Container max-width:** 1200px, centered, `space.pad.page` horizontal padding.
- **Content grid:** 12 columns, `space.gutter.grid` (24px). 1 col < `bp.sm` · 2 cols `bp.sm`–`bp.md` · 12 cols `bp.lg`+.
- **Media mosaic:** irregular masonry, `gutter.tile` or `gutter.media`; may bleed to viewport edge.
- **Card media aspect ratio:** `16 / 9` to match cover artwork; `object-fit: cover`; `object-position: left center` to preserve left-aligned titles in cover images.

### Z-index scale
| Token | Value | Usage |
|-------|-------|-------|
| `z.base` | 0 | Default flow |
| `z.dropdown` | 1000 | Menus, popovers, mobile nav |
| `z.sticky` | 1100 | Sticky nav / headers |
| `z.overlay` | 1200 | Modal scrim |
| `z.modal` | 1300 | Modal panel |
| `z.toast` | 1400 | Toasts / notifications |

### Icons
Lucide line icons only. Sizes 12 / 16 / 20 / 24px, aligned to adjacent text. Stroke inherits `currentColor`. Decorative icons: `text.muted`. Brand icons (e.g. LinkedIn) are unavailable in Lucide — use `external-link` for social/external URLs.

---

## Radius

| Token | Value | Usage |
|-------|-------|-------|
| `radius.none` | 0px | Cards, inputs, badges, image frames, demo panels |
| `radius.md` | 12px | **Buttons only** — soft rounded rectangle, not pill |
| `radius.sm` | 2px | Optional hairline softening |
| `radius.full` | 9999px | Avatars only |

---

## Shadows & Elevation

| Token | Definition |
|-------|-----------|
| `elevation.0` | `bg.base` — flush |
| `elevation.1` | `bg.surface` — raised via lighter charcoal |
| `elevation.2` | `bg.surface` + `border.subtle` — raised + defined edge |
| `shadow.none` | none — default on all in-flow UI |
| `shadow.overlay` | `0 8px 24px rgba(0,0,0,0.6)` — **modal panels only** |

---

## Components

All components inherit global defaults unless noted. Every interactive component defines default / hover / focus / active / disabled. Hover states are **neutral** (never violet).

### Button
- **Variants:** Primary — `bg.primary`, `text.onPrimary`, no border, `radius.md`. Secondary — `bg.secondary` (transparent), `border.strong` (1px), `text.primary`, `radius.md`.
- **Sizes:**
  - `button.default` — `type.button` (16px/semibold), `button.padding.default`, `radius.md`. Content-driven height. Hero CTAs, forms, standalone actions. **Primary and secondary variants share this size** — primary differs by fill color only.
  - `button.compact` — `type.label` (14px/medium), `button.padding.compact`, `radius.md`. Dense UI: cards, tables, toolbars. Not the sole primary CTA on a view.
- **States:** Primary hover → `bg.primary.hover` · active → `bg.primary.active` · Secondary hover → `bg.hover` wash · Focus → `border.focus` 2px ring, 2px offset · Disabled → `bg.disabled`, `text.disabled`, `cursor: not-allowed`.
- **Layout:** icon↔label `space.2`; adjacent buttons `space.3`.
- **Rules:** one primary per view; sentence-case labels; shared padding per size; no pills or gradients.

### Link
- **Style:** `type.body`, `text.primary`, 1px underline, `text-underline-offset: 3px`.
- **Hover:** underline thickens to 2px; color shifts underline toward `border.accent`.
- **Rules:** use for inline URLs and contact content values; not for nav items (use Navigation).

### Input (text, textarea, select)
- **Style:** `bg.surface`, `text.primary`, `text.disabled` placeholder, `border.subtle`, `radius.none`. Label above in `type.label`.
- **States:** hover border `violet.100` @ 40% · focus `border.accent` + `border.focus` · error 2px `border.accent` + icon + `type.caption` message · disabled `bg.disabled`, `text.disabled`.
- **Spacing:** field padding `space.3`; label↔field `space.2`; stacked fields `space.5`.
- **Rules:** persistent visible label; full-width; status via icon + text.

### Card
- **Anatomy:** media (full-bleed, `gutter.media`, 16:9) → header (`type.subheading`, `case.sentence`) → body (`type.body.sm`, `text.muted`) → optional footer.
- **Style:** `elevation.2` on `bg.base`; `elevation.1` only when parent is already `bg.surface`.
- **States (interactive):** hover `bg.hover` · focus `border.focus` · selected `border.accent` (2px).
- **Spacing:** text padding `space.5`; grid gap `space.gutter.grid`.
- **Rules:** media edge-to-edge, text padded; square corners; no shadow.

### Theme Card
Alternate editorial panels for hero blocks, feature callouts, and case-study intros. See **Color theme showcases** for tokens. Not interchangeable with project Cards.

- **Variants:** `theme.lavender` (grid) · `theme.lavender.split` (showcase only) · `theme.night` (grid) · `theme.night.split` (showcase only)
- **Classes:** `.theme-card` · `.theme-card--lavender` / `.theme-card--night` · `.theme-card--split` (showcase only) · `.theme-card__split` · `.theme-card__split--image-left` · `.theme-card__content` · `.theme-card__body` · `.theme-card__figure` · `.theme-card__figure--full-width` · `.theme-card__figure--contain` · `.theme-card__images` · `.theme-card__placeholder` · `.theme-card__placeholder--tall`
- **Style:** `border-radius: 8px` (explicit exception to `radius.none` for theme panels only)
- **Padding:** `space.5` (24px) all sides below `bp.md`; `30px` all sides at `bp.md`+. Text must never touch the colored card edge.
- **Grid anatomy (project pages):** body (`type.body` @ 75% opacity theme color) → optional `type.subheading` → figures, galleries, or lists. Stack vertically — no side-by-side text/image columns.
- **Figure modifiers (project pages):**
  - `.theme-card__figure` — default 16:9, `object-fit: cover`, `object-position: left center`
  - `.theme-card__figure--full-width` — bleeds toward card edge, leaving `space.3` (12px) lavender/night frame visible; use for hero mockups and feature screenshots inside cards
  - `.theme-card__figure--contain` — no fixed aspect ratio; image centered at 68.4% width; use for mood boards and tall assets
- **Split anatomy (showcase only):** lavender = content left + tall image right · night = tall image left + content right; placeholder spans ≈ `300px` height. Reserved for `test-2.html` theme demos — not for generated case-study pages.
- **Spacing (grid):** paragraph stack inside body `space.4` · image gap in `.theme-card__images` `16px` · images↔card bottom `16px` · `.theme-card__body` uses `margin: 0` — card padding alone controls inset on all sides; do not add extra `margin-bottom` on the body wrapper
- **Image ↔ text spacing (project pages — required CSS):** theme-card body copy must never sit flush against figures or galleries. Copy these rules into every `{slug}/index.html`:
  - **Figure label → figure:** `.theme-gallery__figure-title` uses `margin: space.4 0 space.5` (16px above label, 24px below label before image)
  - **Figure → following text:** `.theme-card__body > .theme-card__figure` and `.theme-card__body .feature-list .theme-card__figure` use `margin-bottom: space.6` (32px)
  - **Text → gallery:** `.theme-card__body .theme-gallery` uses `margin-top: space.4` (16px)
  - **Gallery → following text:** `.theme-card__body .theme-gallery + p` uses `margin-top: space.5` (24px) — matches the gap a `type.subheading` already gets via its own `margin-top: space.5` when a gallery is followed by a new subsection
  - **Feature bullet → inline figure:** `.feature-list li .theme-card__figure` uses `margin-top: space.4` (16px); when preceded by a figure label inside the same `<li>`, reset with `.feature-list li .theme-gallery__figure-title + .theme-card__figure { margin-top: 0 }`
- **Wrapper:** on homepage/demo pages, inside `demo-panel` (`bg.surface` + `border.subtle`, `space.5` padding). On **project pages**, `demo-panel` is a pass-through wrapper (transparent, no border, no padding) — see **Project pages**.

### Theme Gallery
Horizontal image carousel inside theme cards (Process / Solution sections). Copy CSS and JS from `stockandstem/index.html`.

- **Classes:** `.theme-gallery` · `.theme-gallery--compact` · `.theme-gallery__hint` · `.theme-gallery__figure-title` · `.theme-gallery__figure-label` · `.theme-gallery__frame` · `.theme-gallery__viewport` · `.theme-gallery__track` · `.theme-gallery__slide` · `.theme-gallery__btn` · `.theme-gallery__caption` · `.theme-gallery__dots`
- **Markup:** root `[data-gallery]` · viewport `tabindex="0"` `role="region"` `aria-roledescription="carousel"` · prev/next chevron buttons · optional `aria-live` caption
- **Figure labels:** `<p class="theme-gallery__figure-title"><span class="theme-gallery__figure-label">Figure N.</span> Title</p>` before each gallery
- **Compact variant:** `.theme-gallery--compact` — frame `max-width: 84%`, centered; slides `aspect-ratio: 16/9`, images `object-fit: contain`. Use for user flows, prompt screenshots, and dense process artifacts.
- **Full-width variant:** default `.theme-gallery` — slides span viewport width; images `object-fit: contain`
- **Captions:** optional `data-caption` on `.theme-gallery__slide`; rendered in `.theme-gallery__caption` when present (user-flow galleries)
- **Hint:** `.theme-gallery__hint` with Lucide `move-horizontal`; visible ≥ `bp.md`
- **Spacing (project pages):** inherit **Image ↔ text spacing** rules from Theme Card. Inside the carousel: `.theme-gallery__dots` uses `margin-top: space.3` (12px below slide frame); slide captions (`.theme-gallery__slide-caption`) use `padding: space.3 space.4 space.4`. A gallery block is one unit — apply `margin-top` / `margin-bottom` to the `.theme-gallery` root and sibling selectors, not to inner viewport/slide elements.
- **JS:** `document.querySelectorAll('[data-gallery]')` init — layout slides to viewport width, scroll-snap, drag on desktop, dot nav when `.theme-gallery__dots` exists

### Feature List
Bulleted feature callouts inside lavender Solution theme cards.

- **Classes:** `.feature-list` on `<ul>`; items are plain `<li>` with `<strong>Feature name —</strong>` lead-in
- **Inline figures:** nest `.theme-card__figure.theme-card__figure--full-width` inside a `<li>` after copy; `margin-top: space.4` on figure
- **Spacing:** list `margin-top: space.5`; `li + li` gap `space.4`
- **Rules:** no list markers; full-width figures per feature when a screenshot supports the bullet; optional hero prototype figure above the list

### Navigation
- **Style:** `bg.base`, `border.subtle` bottom divider, sticky `z.sticky`. Items `type.label`; wordmark = Brand mark logo image (see Brand mark).
- **Wordmark:** link to home; logo at 36px height, `flex-shrink: 0`; no typography classes on the link.
- **States:** default `text.muted` · hover `text.primary` + `bg.hover` · active `text.primary` + 2px `border.accent` underline · focus `border.focus`.
- **Responsive:** below `bp.md`, hamburger → dropdown panel at `z.dropdown`.
- **Spacing:** item padding `space.3`/`space.4`; bar height ≥ 56px.
- **Rules:** one active item; violet indicator = location only; logo variant must match surface (dark-background on dark nav).
- **Skip link:** first focusable element in document; visually hidden until `:focus`; targets `#main`.

### Tabs
- **Style:** `bg.base`, full-width `border.subtle` baseline. Labels `type.label`.
- **States:** inactive `text.muted` · active `text.primary` + 2px `border.accent` underline segment · hover `text.primary`.
- **Overflow:** horizontal scroll; no pill tabs.
- **Rules:** peer content only, not page navigation.

### Badge
- **Style:** `bg.surface`, `text.primary`, `border.subtle`, `type.caption`, `radius.none`. Optional Lucide icon in `text.muted`.
- **Status:** neutral style + icon + label; error may add `border.accent`. No hue-coded fills.
- **Accent variant:** `bg.primary` + `text.onPrimary` — single featured tag; counts against Accent Budget.
- **Spacing:** padding `space.1`/`space.2`; group gap `space.2`.

### Modal
- **Style:** scrim `ink.900` @ 70%, `z.overlay` · panel `bg.surface` + `border.subtle` + `shadow.overlay`, `z.modal`.
- **Title:** `type.heading`, `case.sentence` · **Body:** `type.body`.
- **Sizes:** sm 400 · md 520 · lg 720px. Full-screen below `bp.sm`.
- **Rules:** ≤1 primary button in footer; dismiss via close + scrim + Esc.

### Contact List
- **Purpose:** Group of Contact Items for a contact/About section.
- **Style:** vertical list on `bg.base`; intro paragraph `type.body` + `text.muted`, max 65ch.
- **Spacing:** list top offset `space.5`; optional secondary CTA below list `space.6`; feedback line `space.3` below CTA (`.contact-feedback`, `aria-live="polite"`).
- **Mailto handling:** email link and CTA share `data-contact-link`; JS sets `mailto:` with encoded subject, triggers iframe + `location.href` fallback, copies address to clipboard, writes status to `#contact-feedback`. Required on homepage `index.html`.
- **Rules:** every row is a complete Contact Item; CTA below list uses `button.default` secondary variant.

### Contact Item
- **Purpose:** Single contact method row. **All three parts required:**
  1. **Icon** — Lucide 20px, `text.muted`, `aria-hidden="true"`, fixed 20px column width. Semantic icons (`mail`, `map-pin`); social/external URLs → `external-link` (Lucide has no brand icons).
  2. **Label** — `type.label`, `text.primary`, font-weight 600. Visual anchor ("Email", "Location", "LinkedIn").
  3. **Content** — `type.body` below label. Links → Link component. Plain text → `text.muted`.
- **Spacing:** row gap `space.4`; icon↔column `space.3`; label↔content `space.1`.
- **Rules:** never omit icon; fixed icon width keeps columns aligned across rows.

### Empty State
- **Style:** centered on `bg.base`; optional Lucide icon `text.disabled` · headline `type.heading` · support `type.body.sm` `text.muted` · one action button.
- **Spacing:** icon↔headline↔body `space.3`; body↔button `space.6`; block padding `space.8`.

---

## Page Patterns

Reference structure from `test-2.html`:

| Section | H-level | Case | Key components |
|---------|---------|------|----------------|
| Nav | — | — | Navigation, sticky; Brand mark logo |
| Hero | H1 | caps (≤3 words) | `type.display.lg`, one primary button |
| Project grid | H2 | caps | Cards 16:9 media, 2-col grid, `type.subheading` titles |
| Components demo | H2 | caps | `demo-panel` on `bg.surface`, swatches, badges, inputs, button sizes |
| Color themes | H2 | caps | `demo-panel`; four theme cards (lavender/night × grid/split) |
| Motion | H2 | caps | `pop-in-demo` on `#CAC8F3`; `animate-pop-in--card/image/text` |
| Contact | H2 | caps | Contact List + secondary button |
| Footer | — | — | `type.caption`, `text.muted`, placeholder copy |

**Accent budget per page:** one primary button (hero) + one nav location indicator. All other actions are secondary.

### Project pages (case studies)

**Reference implementation:** `stockandstem/index.html`

Nested project pages (`{slug}/index.html`) extend the homepage design system with case-study-specific layout rules.

| Section | H-level | Surface | Key components |
|---------|---------|---------|----------------|
| Nav | — | `bg.base` | Navigation; Work link active; wordmark links to `../index.html` |
| Project hero | H1 | `bg.base` | `type.display.lg` + `case.caps`, tagline (`type.subheading`), summary (`type.body text-muted`), 16:9 `.project-hero__media`, meta row (`dl.project-meta`), optional `btn--default btn--primary` when `externalUrl` set |
| Challenge | H2 | `theme.lavender` | Single-column theme card: body paragraphs + optional `section__list` |
| Process | H2 | `theme.night` | Single-column theme card: `type.subheading` blocks, `.theme-gallery` carousels, mood board (`.theme-card__figure--contain`) |
| Solution | H2 | `theme.lavender` | Single-column theme card: `feature-list` with optional per-item `.theme-card__figure--full-width`; prototype figure above list |
| Deployment | H2 | `bg.base` | `section__body` paragraphs; optional repeat of external CTA (`project-hero__actions` + `btn--default btn--primary`) |
| Reflection | H2 | `bg.base` | `section__body` paragraphs — full container width |
| Back link | — | `bg.base` | `btn btn--default btn--secondary` → `../index.html#work` |
| Footer | — | `bg.base` | `type.caption text-muted` |

**Section naming:** authors may use **Deployment** instead of Outcome when the section covers launch and live app links. Map `## Deployment` or `## Outcome` in `content.md` to the dark `#outcome` section pattern.

**Project hero order:** title → tagline (optional) → summary → hero media (16:9, before meta) → meta row → external CTA (optional).

**Body copy width:** Apply `--prose-max-width` (70ch) to long-form prose — `.section__body`, `.project-hero__summary`, and direct text children inside `.theme-card__body` (see **Prose measure**). Do **not** cap figures, galleries, or feature-list items that include full-width screenshots. Do not apply `.measure` or `max-width: 65ch` to entire `.theme-card__body` wrappers.

**`demo-panel` on project pages:** pass-through wrapper only — `background: transparent`, no border, `padding: 0`. The theme card inside spans the full container width. (Contrast: homepage/demo `demo-panel` uses `bg.surface` + `border.subtle` + `space.5` padding.)

**Theme cards on project pages:**
- Use **grid (single-column) layout only** — body stacked above media. Never use `.theme-card--split` or side-by-side text/image columns.
- Apply `type-body` to paragraphs, lists, and list items inside `.theme-card__body`.
- `.theme-card__body`: `max-width: none`, `width: 100%`, `margin: 0`.
- Card padding: `space.5` (< `bp.md`) / `30px` (≥ `bp.md`) on all sides — prevents text from touching the lavender or night card edge.
- Subheadings within cards: `type.subheading` (sentence case), `margin-top: space.5`.
- **Image ↔ text spacing:** include all Theme Card **Image ↔ text spacing** selectors in project-page CSS — do not rely on `p + p` alone; figures and galleries are not paragraphs and need explicit sibling margins.
- Process galleries: copy full `.theme-gallery` CSS + init script from `stockandstem/index.html`.
- Solution features: `.feature-list` with `<strong>Title —</strong>` lead-ins; nest `.theme-card__figure--full-width` inside `<li>` when a screenshot supports the bullet.

**Dark sections** (Deployment, Reflection): body copy as `<p class="section__body type-body text-muted">` directly in `.container` — no theme card, no `.measure`.

**Buttons on project pages:** always pair size with variant — `btn btn--default btn--primary` or `btn btn--default btn--secondary`. Primary and secondary share `button.default` sizing (16px/semibold); primary differs by violet fill only. External app links use `target="_blank"` `rel="noopener noreferrer"`.

**Paths (local `file://` browsing):** wordmark/home `../index.html` · work `../index.html#work` · contact `../index.html#contact` · project assets `assets/...` relative to project folder.

**Accent budget:** Work nav item is the location indicator. External published-app CTAs may use `btn--primary` in project hero and again in Deployment; back link stays `btn--secondary`. Do not add unrelated primary actions.

---

## Motion

| Token | Value |
|-------|-------|
| `motion.duration.instant` | 80ms |
| `motion.duration.fast` | 150ms — hover, focus |
| `motion.duration.base` | 250ms — dropdowns, toggles |
| `motion.duration.slow` | 400ms — overlays, modals |
| `motion.easing.standard` | `cubic-bezier(0.2, 0, 0, 1)` |
| `motion.easing.entrance` | `cubic-bezier(0, 0, 0, 1)` |
| `motion.easing.exit` | `cubic-bezier(0.4, 0, 1, 1)` |
| `motion.transition.default` | `all 150ms cubic-bezier(0.2,0,0,1)` |

Animate color, opacity, border, and transform only. Honor `prefers-reduced-motion`.

### Pop-in entrance utilities

Smooth fade-in + slide-up for staged content reveals. Defined in the `<style>` block at the top of this file.

| Class | Delay | Use on |
|-------|-------|--------|
| `animate-pop-in` | — | Required base class on every animated element |
| `animate-pop-in--card` | 0ms | Container / card shell |
| `animate-pop-in--image` | 120ms | Images, media placeholders |
| `animate-pop-in--text` | 240ms | Headlines, paragraphs, copy blocks |

**Timing:** `motion.duration.slow` (400ms) · `motion.easing.entrance` · 16px upward travel · `animation-fill-mode: both`.

#### Example — card, image, and text on light lavender

<div style="background: #CAC8F3; color: #1A191F; padding: 30px; border-radius: 8px; font-family: Manrope, sans-serif;">

<div class="animate-pop-in animate-pop-in--card" style="background: rgba(26, 25, 31, 0.06); border: 1px solid rgba(26, 25, 31, 0.12); border-radius: 8px; padding: 24px; margin-bottom: 16px;">
  <p style="font-family: 'Barlow Condensed', sans-serif; font-size: 14px; font-weight: 600; margin: 0 0 16px 0; color: #1A191F;">Featured project</p>

  <div class="animate-pop-in animate-pop-in--image" style="aspect-ratio: 16 / 9; background: rgba(26, 25, 31, 0.08); border: 1px dashed rgba(26, 25, 31, 0.25); display: flex; align-items: center; justify-content: center; font-size: 14px; color: rgba(26, 25, 31, 0.70); margin-bottom: 16px;">Image placeholder</div>

  <div class="animate-pop-in animate-pop-in--text">
    <h3 style="font-family: 'Barlow Condensed', sans-serif; font-size: 20px; font-weight: 700; margin: 0 0 8px 0; color: #1A191F;">Research at the intersection of clarity</h3>
    <p style="font-size: 16px; line-height: 1.5; margin: 0; color: rgba(26, 25, 31, 0.75);">Card, image, and text each pop in with a staggered delay — card first, then media, then copy.</p>
  </div>
</div>

</div>

```html
<!-- Pop-in example: light lavender surface -->
<div class="theme-card theme-card--lavender">
  <div class="animate-pop-in animate-pop-in--card pop-in-demo__shell">
    <div class="animate-pop-in animate-pop-in--image pop-in-demo__image" role="img" aria-label="Project cover">Image placeholder</div>
    <div class="animate-pop-in animate-pop-in--text pop-in-demo__text">
      <h3>Research at the intersection of clarity</h3>
      <p>Card, image, and text each pop in with a staggered delay.</p>
    </div>
  </div>
</div>
```

---

## Accessibility

### WCAG 2.2 AA conformance audit

Verified contrast ratios (calculated per WCAG relative luminance). Status key: **Pass** meets AA · **Pass (large)** meets AA large-text (≥18.67px bold or ≥24px) · **Exempt** intentionally out of scope · **Pass AAA** exceeds AAA.

| Pair | Ratio | WCAG AA | Notes |
|------|-------|---------|-------|
| `text.primary` on `bg.base` | 12.3:1 | Pass AAA | Body copy, links, headings |
| `text.primary` on `bg.surface` | 10.9:1 | Pass AAA | Cards, panels, inputs |
| `text.muted` on `bg.base` | 6.3:1 | Pass AA | Secondary copy, nav labels |
| `text.muted` on `bg.surface` | 6.0:1 | Pass AA | Helper text, captions |
| `text.onPrimary` on `bg.primary` | 4.0:1 | Known constraint | Primary buttons — short labels only; see Accessibility |
| `text.accent` on `bg.base` | 4.0:1 | Pass (large) | Large emphasis only |
| `ink.800` on `theme.lavender` | 10.9:1 | Pass AAA | Light lavender headers |
| Lavender body (75% ink) on lavender | 5.8:1 | Pass AA | Theme card body copy |
| Lavender placeholder (70% ink) on lavender | 5.1:1 | Pass AA | Decorative placeholder labels |
| `#D1D2E0` on `theme.night` | 13.2:1 | Pass AAA | Dark night headers |
| Night body (75%) on night | 7.6:1 | Pass AAA | Theme card body copy |
| Night placeholder (55%) on night | 4.5:1 | Pass AA | Decorative placeholder labels |
| `text.disabled` on `bg.base` / `bg.surface` | 2.8:1 | Exempt | Inactive controls — not required reading |

**Non-color requirements (`test-2.html`):**

| Criterion | Status | Implementation |
|-----------|--------|----------------|
| 1.3.1 Info & relationships | Pass | Semantic landmarks (`header`, `main`, `footer`); form labels; heading hierarchy H1→H2→H3 |
| 1.4.3 Contrast (minimum) | Pass | All required reading pairs meet AA after fixes above |
| 1.4.11 Non-text contrast | Pass | Focus rings, input borders, active nav underline supplement color |
| 2.1.1 Keyboard | Pass | All interactive elements focusable; hamburger menu keyboard-operable |
| 2.4.1 Bypass blocks | Pass | Skip link to `#main` |
| 2.4.7 Focus visible | Pass | 2px `border.focus` ring, 2px offset on `:focus-visible` |
| 2.5.5 Target size | Pass | Nav items and default buttons ≥ 44px height |
| 3.3.2 Labels | Pass | Persistent input labels; `aria-label` on icon-only controls |
| 4.1.2 Name, role, value | Pass | `aria-expanded` on menu toggle; `aria-describedby` on error field |
| 2.3.3 Animation | Pass | `prefers-reduced-motion` disables pop-in and transitions |

**Known constraints:**
- `text.disabled` and placeholder text in inactive fields are exempt — do not use for essential instructions.
- `text.onPrimary` on `violet.500` (4.0:1) does **not** meet 4.5:1 normal text AA. Primary buttons use `button.default` sizing (16px/semibold) for visual parity with secondary actions; keep labels short (≤3 words).
- Theme placeholder labels use minimum AA opacities: lavender `ink.800` @ 70% · night `#D1D2E0` @ 55%.

### Policy summary

- **Contrast:** `text.primary` on base/surface ≈12:1 (AAA). `text.muted` ≈6:1 (AA). `text.onPrimary` on `bg.primary` ≈4.0:1 — short primary-button labels only. `text.accent` violet on base ≈4.0:1 — large text only.
- **Focus:** visible 2px `border.focus`, 2px offset on all interactives.
- **Never rely on violet alone** for state — pair with indicator (underline, icon, text).
- **No hue-coded status** — icon + text always.
- **Targets:** `button.default` and nav items ≥ 44px effective height. `button.compact` permitted in dense UI where space is constrained; do not use compact for the page's primary CTA.
- **Labels:** persistent input labels; `aria-label` on icon-only buttons and logo home link; decorative contact icons `aria-hidden="true"`.
- **Skip link:** first focusable element links to `#main`.
- **Logo:** `alt` on the wordmark image; dark-background variant on `bg.base` for readable contrast.
- **Motion:** honor `prefers-reduced-motion`.
- **Heading case:** keep HTML sentence case; transform visually via `case.caps` for screen readers.

---

## CSS Implementation Map

Map tokens to CSS custom properties in implementation files:

```css
:root {
  /* Primitives */
  --color-violet-500: #6A53FE;
  --color-violet-100: #CAC8F3;
  --color-ink-900: #0B0A10;
  --color-ink-800: #1A191F;
  --color-neutral-200: #D1D2E0;

  /* Semantic */
  --color-bg-base: var(--color-ink-900);
  --color-bg-surface: var(--color-ink-800);
  --color-bg-primary: var(--color-violet-500);
  --color-text-primary: var(--color-violet-100);
  --color-text-muted: rgba(202, 200, 243, 0.7);
  --color-text-disabled: rgba(202, 200, 243, 0.4);
  --color-text-on-primary: var(--color-ink-900);
  --color-border-subtle: rgba(202, 200, 243, 0.18);
  --color-border-strong: var(--color-violet-100);
  --color-border-accent: var(--color-violet-500);
  --color-border-focus: var(--color-violet-100);
  --color-bg-hover: rgba(202, 200, 243, 0.06);

  /* Theme panels */
  --theme-lavender-bg: var(--color-violet-100);
  --theme-lavender-text: var(--color-ink-800);
  --theme-lavender-body: rgba(26, 25, 31, 0.75);
  --theme-lavender-placeholder: rgba(26, 25, 31, 0.70);
  --theme-night-bg: var(--color-ink-900);
  --theme-night-text: var(--color-neutral-200);
  --theme-night-body: rgba(209, 210, 224, 0.75);
  --theme-night-placeholder: rgba(209, 210, 224, 0.55);
  --theme-card-radius: 8px;

  /* Radius & button padding */
  --radius-none: 0;
  --radius-md: 12px;
  --button-padding-default: 0.75em 1.5em;
  --button-padding-compact: 0.5em 1.25em;
}

/* Primary button — fill variant; shares button.default sizing */
.btn--primary {
  background: var(--color-bg-primary);
  color: var(--color-text-on-primary);
}

/* Skip link — first focusable element */
.skip-link {
  position: absolute;
  top: -100%;
  left: var(--space-4);
  z-index: 9999;
}
.skip-link:focus { top: var(--space-4); }

/* Pop-in entrance — see Motion section */
@keyframes pop-in {
  from { opacity: 0; transform: translateY(16px); }
  to   { opacity: 1; transform: translateY(0); }
}
.animate-pop-in {
  animation: pop-in 400ms cubic-bezier(0, 0, 0, 1) both;
}
.animate-pop-in--card  { animation-delay: 0ms; }
.animate-pop-in--image { animation-delay: 120ms; }
.animate-pop-in--text  { animation-delay: 240ms; }
@media (prefers-reduced-motion: reduce) {
  .animate-pop-in, .animate-pop-in--card,
  .animate-pop-in--image, .animate-pop-in--text {
    animation: none; opacity: 1; transform: none;
  }
}
```

---

## Do / Don't Rules

**Do**
- Build on `bg.base`; raise with `bg.surface` and `border.subtle`.
- Keep violet within the Accent Budget (≤1 primary button + ≤1 location indicator + focus + selection per view).
- Use `radius.none` on cards, inputs, badges; `radius.md` on buttons; `radius.full` on avatars only; **`8px` only on theme cards**.
- Apply `case.caps` only to H1/H2 with ≤3 words; `case.sentence` on all H3/H4 and long H1/H2.
- Use `button.padding.default` for standard buttons; `button.compact` in dense UI only.
- Use `text.onPrimary` (`ink.900`) on all primary buttons and accent badges.
- Render every Contact Item with icon + label + content.
- Match card media to 16:9 with `object-position: left center`.
- Use the dark-background logo (`assets/mgriffin-designs.png`) in nav on `bg.base`.
- Wrap theme showcases in `demo-panel` (`bg.surface` + `border.subtle`); use all four theme variants (grid + split) on demo pages where appropriate.
- On project case-study pages, use single-column theme cards only; let body copy span full container width; keep `space.5` / `30px` padding inside theme cards; copy theme-gallery CSS/JS from `stockandstem/index.html` when carousels are needed.
- Use `btn--default` with every button (`btn--default btn--primary` or `btn--default btn--secondary`); primary and secondary share the same size.
- Include a skip link to `#main` as the first focusable element.
- Apply `animate-pop-in` utilities with `prefers-reduced-motion` fallback for staged reveals.
- Meet theme placeholder contrast minimums (lavender 70% · night 55%).

**Don't**
- Don't introduce white/light panels, a second accent hue, or semantic (red/green/amber) colors.
- Don't apply drop shadows except `shadow.overlay` on modals.
- Don't use violet for hover, dividers, body text, or decorative fills.
- Don't add button fill variants beyond primary/secondary, or pill shapes on buttons.
- Don't hard-code px padding on buttons when `button.padding.*` applies.
- Don't omit contact row icons or use Lucide brand icons (use `external-link`).
- Don't set body copy in Barlow Condensed or headings in Manrope.
- Don't rely on color alone for status, errors, or active state.
- Don't place two primary actions or two violet location indicators on one view.
- Don't set the nav wordmark as a text heading or use the light-background logo on dark surfaces.
- Don't use `16px` normal-weight text on `bg.primary` — contrast fails AA (4.0:1 requires large text).
- Don't use placeholder label opacities below theme minimums on readable text.
- Don't use split theme-card layouts (`.theme-card--split`) on project case-study pages — compresses body copy on laptop viewports.
- Don't apply `.measure` or `65ch` max-width to project page body copy.
- Don't remove horizontal padding from theme cards — text must not touch the colored card edge.
- Don't use `btn--primary` or `btn--secondary` without `btn--default` — size tokens live on the default modifier.
- Don't apply `8px` border-radius outside theme cards and pop-in demo shells.
