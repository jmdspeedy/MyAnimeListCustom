# Aqours Seaside Memory Voyage — Design Specification

## 1. Purpose

This document is the source of truth for the CSS-only redesign of
`https://myanimelist.net/animelist/jmdspeedy` using MyAnimeList's Modern anime
list template.

The finished list is a showcase-dominant Aqours seaside scrapbook: an
illustrated travel route through the owner's anime history, built from layered
paper, postcards, stamps, official member artwork, and lively but bounded
motion. It remains a working list, but visual storytelling now takes priority
over maximum card density.

## 2. Locked direction

- **Concept:** Seaside Memory Voyage.
- **Priority:** showcase first, functionality preserved.
- **Entry hierarchy:** every anime has equal importance; there are no featured
  or enlarged entries.
- **Composition:** four cards on wide displays, three on normal desktops, two
  on compact screens, and one on narrow screens.
- **Aqours treatment:** all nine members receive equal visual weight.
- **Typography:** M PLUS Rounded 1c for the interface and Klee One for a small
  set of handwritten journal accents.
- **Assets:** project-hosted official downloads whose usage terms allow use,
  beginning with the nine 7th Anniversary member icons and wallpapers.
- **Hosting:** public GitHub repository and GitHub Pages with immutable,
  versioned asset filenames.

## 3. Scope

### Included

- Public and owner views of `jmdspeedy`'s Modern anime list.
- Header, status navigation, search, sorting, statistics, anime entries, owner
  controls, More panels, loading state, advanced filters, and footer.
- Watching, Completed, On Hold, Dropped, Plan to Watch, and All Anime views.
- Several hundred entries and current Chrome, Firefox, and Edge.
- MAL light and dark appearance settings normalized into the bright journal.

### Excluded

- Manga list, profile, detail pages, JavaScript, browser extensions, generated
  cover maps, analytics, video backgrounds, and animated GIFs.
- Any mechanism that invents a ranking or promotes an arbitrary anime because
  of its current sort position.
- Rehosting artwork whose redistribution or intended-use terms are unclear.

## 4. Experience principles

1. **One physical story.** Every surface belongs to the same sunlit seaside
   journal rather than mixing unrelated materials.
2. **Showcase through composition.** Creativity comes from page rhythm,
   framing, member art, and travel ephemera—not unequal card sizes.
3. **Equal Aqours presence.** The complete nine-member ensemble is visible in
   the main header, with equal portrait scale and no permanent lead.
4. **Native function survives.** MAL links, filters, editing, score, progress,
   streaming, More, and keyboard navigation remain operable.
5. **Fast enough to revisit.** Assets are optimized, cached, and measured;
   decorative resolution is reduced before interaction performance.
6. **Graceful failure.** The list remains coherent when every custom image and
   web font fails.

## 5. Visual system

### 5.1 Palette

| Token | Value | Purpose |
| --- | --- | --- |
| `--color-sky` | `#BDEAF4` | Coastal background |
| `--color-ocean` | `#168FC5` | Primary accent and focus |
| `--color-ocean-deep` | `#0B5275` | Strong surfaces and text |
| `--color-paper` | `#FFF9E8` | Journal and card paper |
| `--color-paper-deep` | `#F1E4BF` | Paper edges and insets |
| `--color-sun` | `#F6C84C` | Active marks and highlights |
| `--color-coral` | `#EF6A62` | Warm scrapbook accent |
| `--color-ink` | `#17384A` | Primary text |
| `--color-ink-muted` | `#5D707A` | Secondary text |
| `--color-white` | `#FFFFFF` | Sheen and contrast |

Member accents remain Chika `#F28C28`, Riko `#E9789D`, Kanan `#36B98A`,
Dia `#C83E4D`, You `#49AEE8`, Yoshiko `#7B86A2`, Hanamaru `#E9B928`,
Mari `#9A6CC1`, and Ruby `#E85E9C`. They are decorative only and never encode
anime status.

Status continues to use color plus symbol and written label: `▶ WATCHING`,
`✓ COMPLETED`, `Ⅱ ON HOLD`, `× DROPPED`, and `○ PLANNED`.

### 5.2 Typography

- **M PLUS Rounded 1c:** all navigation, inputs, buttons, anime titles,
  metadata, score, progress, status, statistics, and footer text.
- **Klee One:** journal title, short captions, route annotations, stamp copy,
  and no functional control labels.
- Self-host only required WOFF2 weights and subsets. Use `font-display: swap`.
- Fallback stack: `"Yu Gothic UI", Meiryo, "Segoe UI", sans-serif`.
- Functional body text is 13–15px; metadata is never below 11px; card titles
  are 15–17px; navigation is 13–14px; journal display text is 28–42px.
- Use tabular numerals for scores and progress, two-line title clamping, and no
  decorative letter spacing on normal copy.

### 5.3 Materials

- One cream paper family with subtle CSS grain.
- A single upper-left light source.
- Medium photo shadows, shallow stationery-control shadows.
- Four repeating card treatments: polaroid, postcard, ticket pocket, and taped
  photo. These change framing, mat, caption rule, tape, corner detail, and
  deterministic rotation—not data hierarchy or card footprint.
- CSS supplies paper grain, sun, waves, route lines, tape, pins, perforations,
  photo corners, ink rules, and stamp borders.

## 6. Page composition

### 6.1 Ensemble masthead

- Desktop height is 330–390px, intentionally larger than the previous compact
  header.
- Nine official portraits form a balanced layered ensemble. Each member uses
  equal display area and comparable crop.
- A coastal CSS scene remains underneath the artwork as a complete fallback.
- The journal title and short caption occupy a paper label rather than a plain
  rectangular panel.
- A nine-color route legend reinforces the full ensemble.
- MAL account and list-menu controls remain on a high-contrast plate.

### 6.2 Navigation and index

- Status filters resemble overlapping destination tabs mounted to the page.
- The active tab is pressed and marked by a sun-yellow rule.
- Search is a luggage-label input with a visible focus treatment.
- Sort links form a compact field-note index; statistics and Filters remain
  visible and wrap before they overlap.

### 6.3 Voyage route

- The list surface contains a low-contrast winding route line behind entries.
- Rows alternate a small horizontal inset and vertical breathing room.
- Decorative route stops repeat predictably through CSS rather than attaching
  meaning to specific anime.
- The route is reduced or removed at high zoom and below the desktop layout.

## 7. Equal-weight anime cards

### 7.1 Responsive grid

| Viewport | Columns | Gap |
| --- | ---: | ---: |
| `>= 1480px` | 4 | `26px` |
| `1040–1479px` | 3 | `22px` |
| `660–1039px` | 2 | `18px` |
| `< 660px` | 1 | `14px` |

The journal has a maximum width of 1440px. Every entry has the same grid track
size. Staggering never changes DOM order, keyboard order, or implied priority.

### 7.2 Always visible

- Native MAL cover with a mostly uncropped 2:3 presentation.
- Anime title clamped to two lines.
- Score with a clear dash for unscored entries.
- Episode progress, including MAL's unknown-total representation.
- Status stamp containing both symbol and words.

### 7.3 Revealed layer

Hover and keyboard focus pull a paper slip from the card containing available
type, rating, studio, dates, tags, and notes. Empty fields do not reserve rows.
The slip is bounded and scrolls internally when necessary.

Edit, More, streaming, score editing, episode editing, and increment controls
sit above the enlarged title-link hit area. On narrow/touch layouts, essential
owner controls remain visible and secondary metadata stays hidden unless MAL
provides a native expansion.

### 7.4 Repeating treatments

`nth-of-type` cycles only decorative treatments:

1. Polaroid with handwritten caption rule.
2. Air-mail postcard with coral/ocean edge marks.
3. Ticket pocket with perforated side and stamped metadata slip.
4. Taped photograph with offset cream mounting paper.

No treatment receives more space, more information, or stronger semantic
weight than another.

## 8. Motion

- Card lift: 160ms transform.
- Paper-slip reveal: 180–200ms transform and opacity.
- Tab response: 120ms transform.
- Header entrance: one 600–700ms opacity/translate sequence.
- A single subtle route or wave loop may run for 12–16 seconds.
- Do not animate layout properties, filters, large blurs, or every card on load.
- Under `prefers-reduced-motion: reduce`, remove loops, rotation changes,
  translated lifts, and staggered entrances while preserving focus and shadow.

## 9. Accessibility

- Normal text meets WCAG AA 4.5:1; large text and meaningful graphics meet 3:1.
- Focus uses a 3px ocean ring with 2px paper separation.
- Hover content also appears through `:focus-within` and a `:has(:focus)`
  fallback for table-row-group repaint behavior.
- Status does not rely on color.
- Decorative layers use `pointer-events: none`.
- At 200% zoom, route decoration and overlap simplify before content collides.
- The page remains understandable with fonts, portraits, and all optional
  artwork blocked.

## 10. Assets, rights, and performance

### 10.1 Approved source classes

- Official downloads explicitly offered for public use, starting with the
  Aqours 7th Anniversary SNS icons and smartphone wallpapers.
- Artwork carrying an explicit license or usage statement compatible with the
  intended public, non-commercial list theme.
- Open-font binaries under the SIL Open Font License.

Official promotional images without a compatible usage statement may be linked
in research notes but are not copied into the repository.

### 10.2 Hosting

- Public GitHub repository and GitHub Pages.
- Versioned names such as `chika-7th-icon-v1.webp`.
- No authentication, analytics, unstable hotlinks, or large base64 payloads.
- Source URLs, retrieval date, permission wording summary, copyright owner, and
  transformation history are recorded in `assets/ATTRIBUTION.md`.

### 10.3 Performance policy

- Target 1–1.5MB compressed custom first view; this is a target rather than a
  rigid ceiling.
- Larger transfers require a visible quality benefit and measured acceptable
  loading from GitHub Pages.
- Prefer AVIF plus WebP fallback where MAL accepts `image-set()`; otherwise use
  optimized WebP.
- Reserve header and card geometry to prevent image-driven layout shifts.
- Use long-lived caching through immutable filenames.
- Reuse loaded member portraits throughout the page; native MAL covers are not
  duplicated or remapped.

## 11. CSS architecture

1. Metadata, `@font-face`, public asset URLs, and tokens.
2. Modern anime-list scope and light/dark normalization.
3. Scoped box sizing and functional resets.
4. Coastal background and journal surface.
5. Nine-member showcase masthead.
6. Destination navigation, search, sort, statistics, and filters.
7. Four/three/two/one-column voyage composition.
8. Equal card foundation and four repeating treatments.
9. Card data, safe title link, metadata slips, and owner controls.
10. Status variants, loading, and missing-data states.
11. Footer, responsive simplification, focus, and reduced motion.

Selectors remain beneath `body.ownlist:not(.classic-ownlist).anime`. Global
link and image rules are prohibited. Absolute positioning is limited to bounded
art, decoration, metadata slips, and the title-link hit area. `!important` is
used only to override MAL inline/high-specificity rules and is documented.

## 12. Acceptance checklist

- [ ] The page reads as an Aqours seaside voyage before it reads as a database.
- [ ] All nine members appear at equal scale in the desktop masthead.
- [ ] No anime receives arbitrary featured placement.
- [ ] Four/three/two/one-column behavior matches the documented thresholds.
- [ ] Four card treatments create rhythm without changing data hierarchy.
- [ ] Cover, title, score, progress, and status remain visible.
- [ ] Metadata reveals on hover and keyboard focus.
- [ ] Safe card-body links and every native MAL control remain independent.
- [ ] Search, sorting, filters, statistics, More, and footer links work.
- [ ] M PLUS Rounded 1c is consistent across functional UI.
- [ ] Klee One is limited to decorative journal copy.
- [ ] Reduced motion, 200% zoom, long titles, unknown progress, missing covers,
      empty metadata, and failed custom assets remain usable.
- [ ] Owner, visitor, all six status filters, and several hundred entries pass.
- [ ] Current Chrome, Firefox, and Edge render the core interaction consistently.
- [ ] Asset sources, licenses/permissions, and optimization are documented.
- [ ] Published assets resolve over HTTPS without authentication or tracking.

## 13. Decision log

| Decision | Alternatives | Reason |
| --- | --- | --- |
| Switch to showcase-dominant | Balanced utility/showcase | The user wants a more distinctive, creative public list. |
| Use Seaside Memory Voyage | Travel trunk; idol magazine | Strongest Aqours scrapbook identity with manageable controls. |
| Keep entries equal-weight | Featured cards | CSS cannot choose meaningful featured anime across changing sorts and filters. |
| Use 4/3/2/1 columns | Previous 6/5/4/2/1 grid | Larger cards and wider spacing create showcase presence. |
| Cycle four card treatments | One uniform card | Adds editorial rhythm without semantic hierarchy. |
| Use M PLUS Rounded 1c | System UI stack; Nunito Sans | Cohesive rounded Latin/Japanese-capable interface voice. |
| Use Klee One sparingly | Generic serif; script-heavy interface | Supplies handwritten journal character without harming functional consistency. |
| Use official 7th Anniversary downloads | Unattributed fan art; arbitrary key visuals | Matching nine-member art is officially distributed for use. |
| Allow measured assets above 1MB | Hard 750KB ceiling | Showcase quality may justify additional bytes when optimized and tested. |
| Use public GitHub Pages | Third-party hotlinks | Provides versioning, ownership, HTTPS, and predictable URLs. |
| Retain native MAL covers | Cover scraper | Reliable, current, and low-maintenance. |

## 14. Implementation handoff

Implementation must update this document before changing any locked content
hierarchy, responsive threshold, font family, artwork-rights rule, interaction
layering, or equal-weight principle. Visual tuning inside those constraints may
proceed through rendered browser comparison.
