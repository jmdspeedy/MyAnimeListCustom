# Aqours Seaside Memory Voyage

A showcase-first custom CSS theme for the **Modern MyAnimeList anime-list
template**, designed for
[`jmdspeedy`](https://myanimelist.net/animelist/jmdspeedy).

The theme turns the list into an Aqours seaside travel journal: nine-member
official artwork, tactile photo cards, four rotating scrapbook treatments,
coastal stationery controls, and responsive 4/3/2/1-column layouts.

## Install

1. Open [MyAnimeList's Modern theme editor](https://myanimelist.net/ownlist/style/theme/1).
2. Enable at least **Image**, **Title**, **Score**, **Type**, and
   **Episodes/Progress**. Tags, Rated, dates, studios, notes, and other optional
   Modern columns are supported.
3. Replace the existing custom CSS with the complete contents of
   [`aqours-journal.css`](aqours-journal.css), then save.
4. Check both the public list and the signed-in owner view.

Do not append this stylesheet to the previous theme. It is a complete
replacement.

## Project map

- `aqours-journal.css` — paste-ready production stylesheet.
- `design.md` — source-of-truth visual, responsive, interaction, accessibility,
  asset, and performance specification.
- `assets/images/` — optimized official Aqours artwork derivatives.
- `assets/fonts/` — self-hosted webfont subsets and license files.
- `assets/ATTRIBUTION.md` — artwork provenance and usage notes.
- `index.html` — GitHub Pages project and asset-host landing page.

## Implementation notes

- Four equal-weight card treatments repeat through the list: polaroid,
  postcard, memory ticket, and taped photo mount. There is no arbitrary
  featured anime.
- The layout targets four columns at wide desktop sizes, three on typical
  desktops/laptops, two on compact screens, and one on narrow screens.
- Cover, title, score, and progress remain visible. Secondary metadata is
  revealed by hover and keyboard focus on capable layouts.
- The native MAL title link covers each card's safe click area while owner,
  score, progress, streaming, and detail controls remain independently usable.
- All custom imagery has a CSS-generated coastal fallback. The list stays
  functional if GitHub Pages or optional artwork is unavailable.
- Functional typography uses M PLUS Rounded 1c; Klee One is reserved for
  journal-style headings and captions.

## Rights

The original CSS and documentation are MIT licensed. Aqours artwork remains
the property of its respective rights holders and is not relicensed by this
repository. See [`assets/ATTRIBUTION.md`](assets/ATTRIBUTION.md) before reusing
the artwork files. Bundled fonts retain their own SIL Open Font License texts.
