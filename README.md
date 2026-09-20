# hebstr-slide

[![Render](https://github.com/hebstr/quarto-hebstr-slide/actions/workflows/render.yml/badge.svg)](https://github.com/hebstr/quarto-hebstr-slide/actions/workflows/render.yml)
[![Pages](https://github.com/hebstr/quarto-hebstr-slide/actions/workflows/pages.yml/badge.svg)](https://hebstr.github.io/quarto-hebstr-slide/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE.md)

A Quarto revealjs theme in the tradition of [Pingfan Hu](https://github.com/pingfan-hu)'s slides: cream ground, brown body text, purple headings, navy section dividers, amber accent, and a macOS traffic-light code window drawn in SCSS.

> **Status (0.1.0)**: a personal theme library, published to be at hand rather than distributed.
> No release is tagged, and none is planned before the API settles.
> Tested under Quarto 1.10.18; `quarto-required` is set at `>=1.6`, which is a plausible lower bound rather than a tested one.

## Install

```bash
quarto add hebstr/quarto-hebstr-slide
```

Then in a document's front matter:

```yaml
---
title: "My talk"
format: hebstr-slide-revealjs
---
```

The extension ships a format, not a project template, so `quarto add` leaves you with an empty document.
`example.qmd` in this repository is the starting point to copy from.

## Fonts

Luciole for prose and headings, Fira Code for code, both self-hosted under `_extensions/hebstr-slide/fonts/` with their licences.
Luciole is a typeface designed for low vision, and it is a deliberate departure from Pingfan's TsangerJinKai and Maple Mono, which load from CDNs.

## What's in the box

- `_extensions/hebstr-slide/_extension.yml`: the `hebstr-slide-revealjs` format.
  1280x800 canvas, `controls: true`, `slide-number`, `transition: none`, and a self-contained output (`embed-resources` with `self-contained-math`), so a deck can be emailed and presented offline.
- `_extensions/hebstr-slide/theme.scss`: the theme.
  One file, because the revealjs format has no light/dark theme pair to split along, unlike the HTML format that `hebstr-doc` and `hebstr-book` target.
- `resources/*.qmd`: the demo slide bodies, one partial per slide, pulled in with `{{< include >}}`.
- `example.qmd`: the demo deck, thirteen slides covering every class the theme provides.

## Slide classes

  | Class                          | Effect                                                             |
  | ------------------------------ | ------------------------------------------------------------------ |
  | `.light-centered`              | centred content on the cream ground                                |
  | `.dark-centered`               | full-bleed navy slide, light text, amber inline code               |
  | `.black-centered`              | the same on near-black                                             |
  | `.custom-title-slide`          | nudges an `h1` opener and its author name down by `5vh`            |
  | `.dot-panel` / `.accent-card`  | the radial-dot panel holding white cards with a purple left border |
  | `.bubble-left` / `.bubble-top` | speech bubbles with a tail                                         |
  | `.four-by-three-grid`          | a 4x3 grid of teal-bordered cells                                  |
  | `.eyebrow`                     | small uppercase amber label above a title                          |
  | `.pill-dark`                   | dark pill behind a colour that only clears AA on a dark ground     |

Colour utilities carry the palette names: `.purple`, `.teal`, `.amber`, `.navy`, `.coral`, `.rose`, `.sage`, `.slate`, `.gold`, `.blue`.

## Accessibility

Links carry an underline rather than relying on colour: neither the purple nor the teal it replaced reaches the 3:1 against body text that WCAG 1.4.1 requires of colour used as the sole marker.
On dark variants the link colour inverts to the light purple, the dark one falling to 1.67:1 there.
Amber clears AA only on a dark ground, which is what `.pill-dark` is for.

## Licence

MIT, see [LICENSE.md](LICENSE.md).
The bundled fonts keep their own licences, alongside them.
