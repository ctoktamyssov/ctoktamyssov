# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

Chingis Toktamyssov's personal portfolio: a single hand-written page (`index.html` + `style.css`) with screenshots in `images/`. No build step, no package manager, no dependencies, no tests. Google Fonts is loaded from a CDN at runtime.

## Commands

There is nothing to build or install. To preview:

```bash
python -m http.server 8000   # then open http://localhost:8000
```

Opening `index.html` directly in a browser also works, since all paths are relative.

## Deployment

The repo is `ctoktamyssov/ctoktamyssov` — a GitHub Pages **user site**, so whatever is on `main` is published live at `ctoktamyssov.github.io`. Pushing to `main` is deploying. A `CNAME` existed earlier but was deleted (f248ef2), so there is no custom domain. Feature work happens on branches like `update/main-page` and merges to `main`.

## Structure and conventions

The page is one `.hero` column: an `.intro-band` (name, blurb, role, contact links), a `.projects-section` holding the `.project-grid`, and a `footer`. `.hero` supplies the page background, text color, `50px` padding, and the flex column.

Palette: an earthy/coffee scheme defined as custom properties in `:root` at the top of `style.css` — `--coffee` (page), `--espresso` (intro and footer bands), `--cream` (text), `--caramel` (accent), `--sage` (tags and hover), plus `--rule`/`--hairline` for borders. Recolor there, not in individual rules.

Type: Fraunces (serif) for the name and card titles, Karla for body text, both from Google Fonts.

`.intro-band`, `footer`, and `.projects-section` use negative margins of `-50px` to cancel `.hero`'s `50px` padding, so their backgrounds and top rules reach the page edges. Those values are coupled — change `.hero`'s padding and you must change all three.

The contact lines (intro and footer) share the `.intro-link` class: a `.label` in cream, an optional `.value` in caramel, and a `border-bottom` underline that turns sage on hover along with the label. The border is used instead of `text-decoration` so the underline color can differ from the text.

Each project is a `.project-card` (title, `.card-image` frame, description, `.card-tags`, `.card-links`) copy-pasted into `.project-grid`; there is no data file or templating. The grid is capped at `70vw` and drops to 2 columns under 950px, 1 under 640px.

Card screenshots live in `images/` and the filenames contain spaces, so `src` attributes are percent-encoded (`images/breadboard%20computer.jpg`).

## Known quirks

- `style.css` still carries the rules for a deleted `projects.html` — `.projects-page`, `.projects-title`, `.projects-container`, `.project-item`, `.project-links`, `.divider`, `.logo`, `.top-buttons`, `.tagline`. Nothing on the live page uses them.
- `current_resume.pdf` sits in the repo root untracked. The page links to the Google Drive copy instead, so committing the PDF would publish a second public copy at `ctoktamyssov.github.io/current_resume.pdf`.
