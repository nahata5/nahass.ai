# nahass.ai — Design System v1

**"Clinical Modern."** Near-white ground, one deep ink, one accent. Big quiet numbers,
hairline rules, real whitespace. No shadows, no gradients, no texture, no illustration.
The credibility comes from the data, not from decoration.

Everything lives in `assets/system.css`. Pages carry only the CSS unique to that page,
in a `<style>` block in the head.

---

## Tokens

### Color

| Token | Value | Use |
|---|---|---|
| `--ground` | `#FBFBF9` | Page background |
| `--surface` | `#FFFFFF` | Lifted band (metrics, prose) |
| `--surface-alt` | `#F4F4F1` | Secondary band |
| `--ink` | `#101417` | Headings, numbers, emphasis |
| `--ink-2` | `#3A4248` | Body copy |
| `--muted` | `#5B646B` | Supporting copy, labels |
| `--faint` | `#8D959B` | Dates, counters |
| `--accent` | `#0F5E54` | Links, micro-labels, buttons. **One accent only.** |
| `--accent-deep` | `#0A423B` | Accent hover |
| `--rule` | `rgba(16,20,23,.10)` | Hairline dividers |
| `--inverse-bg` | `#101417` | Contact band |

Contrast: `--muted` on `--ground` is 5.6:1, `--accent` on `--ground` is 7.4:1 — both pass
WCAG AA for body text. `--faint` is only used at metadata scale on large-ish type.

### Type

Three families, no more.

- **Display** — Inter Tight, 500/600. Headings, buttons, big numbers. Negative tracking
  (−2.2% to −4.5%, tighter as size grows).
- **Body** — Inter, 400/450/500/600. Everything readable.
- **Data** — IBM Plex Mono, 400/500. Micro-labels, dates, counters, section eyebrows.
  Always uppercase with 0.14em tracking.

Nine sizes. Do not introduce a tenth.

```
--t-micro 11px    labels, eyebrows
--t-tiny  12.5px  dates, footer
--t-small 14px    card copy, list items, metadata
--t-base  16.5px  body
--t-lead  17→20   lede paragraphs
--t-h3    19→22   card and subsection headings
--t-h2    27→42   section headings
--t-h1    36→68   page title
--t-num   38→60   metric figures
```

### Space

Strict 4px base: `--s-1` 4 → `--s-10` 128. Nothing off-scale.
`--band` (64→112px fluid) is the vertical rhythm between sections.
`--gutter` (20→56px fluid) is the page side padding — set once, never per-component.

### Structure

- `--wrap` 1180px — standard content width
- `--wrap-narrow` 760px — long-form prose
- `--measure` 66ch — hard cap on paragraph width
- `--radius` 3px — buttons and images only. Rules and cards stay square.

---

## Components

| Class | What it is |
|---|---|
| `.label` | The one decorative device: uppercase mono micro-label. `.label--accent` for teal. |
| `.sec-head` | Label → hairline → heading → optional lede. Opens every section. |
| `.metrics` / `.metric` | Four-up outcome figures. Vertical hairlines between; collapses 4 → 2 → 1. |
| `.rows` / `.row` | Year / title / venue definition rows. Used for work and publication lists. |
| `.card` | Top-ruled block: accent key, heading, body. Sits in `.grid-2/3/4`. |
| `.facts` / `.fact` | Two-column definition list for credentials and contact. |
| `.inverse` | Dark band. Used exactly once per page, for contact. |
| `.btn` / `.btn--ghost` | Solid accent, or outlined neutral. Two variants only. |

## Rules of the system

1. **One accent.** If something needs to stand out and teal is already used nearby,
   use weight or size, not a second color.
2. **Hairlines, not boxes.** Structure comes from 1px rules and whitespace. No cards
   with borders on four sides, no drop shadows.
3. **Numbers are the hero.** Metric figures get the largest type on the page after the H1.
4. **66ch, always.** No paragraph runs wider than `--measure`.
5. **Mono is for metadata.** Never body copy.
6. **Motion is optional.** Transitions are ≤ .18s on color only. No scroll animation,
   no reveals — the previous site's fade-ins are gone deliberately.

## Accessibility

- Skip link on every page (`.skip`).
- `:focus-visible` rings in accent, 2px, 3px offset.
- One `<h1>` per page; heading order never skips.
- `aria-current="page"` marks the active nav item.
- Body copy meets AA at every size in the scale.

## Pages

```
/            business-facing practice page
/about/      personal narrative, path, credentials
/cv/         full structured CV (print stylesheet included)
```
