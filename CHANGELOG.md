# Changelog

## [Unreleased]

### Added

- `hebstr-slide` is a standalone Quarto revealjs theme extension, contributing the `hebstr-slide-revealjs` format from `_extensions/hebstr-slide/`.
- Self-hosted fonts under the extension: Luciole for prose and headings, Fira Code for code, with their licences.
  No CDN call.
- Slide variants (`.light-centered`, `.dark-centered`, `.black-centered`), a radial-dot card panel, speech bubbles, a 4x3 grid, colour utility classes, and a macOS traffic-light code window drawn in SCSS.
- `render.yml` and `pages.yml` workflows.
  No release workflow: the repo is a personal theme library, not a versioned distribution.

### Changed

- The theme moved out of `styles/slides.scss` into the extension as a single `theme.scss`.
  No light/dark split, unlike `hebstr-doc` and `hebstr-book`: the revealjs format has no light/dark theme pair, its `theme` option taking a single value or a list of files merged together.
- Canvas is 1280x800 (16:10) instead of Quarto's 1050x700, with `controls: true` pinned on rather than left to `controls: auto`, which resolves at runtime to a value that gives a directly opened deck no arrows.
- Output is a single self-contained file (`embed-resources: true`, `self-contained-math: true`), so a deck can be sent and presented offline.
- The colour palette is named once in `scss:defaults` and every Quarto variable is assigned to a name, rather than repeating the same hex in both SCSS regions.

### Fixed

- Links were distinguishable by colour alone, which WCAG 1.4.1 allows only past 3:1 against body text; neither the former teal nor the current purple reaches it (1.33:1 and 1.43:1), so content links now carry an underline.
  Dark slide variants invert the link colour to `#DFE4FF` (8.72:1 on navy), the purple falling to 1.67:1 there.
- A light container on a dark slide inherited the variant's text colour and rendered cream on white, which made the whole roadmap slide unreadable.
- The code window carried a horizontal scrollbar across its rounded corners, its `pre` padding adding to a width reveal had already fixed.
- The demo deck stated four things about itself that were not true: the fonts it ships, a resource directory that does not exist, the absence of JavaScript, and the link colour.
