# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

A mobile-first, Linktree-style links page for the band Apothecary, built with Jekyll and published by GitHub Pages at https://galaterro.github.io/apothecary/. There is no JavaScript build, test suite or linter, and the only JS is the small inline share-button script in `index.html`.

Everything in the repo is in Spanish (site copy, comments, identifiers, CSS classes, commit messages, README). Keep it that way.

## Commands

Local preview, only needed for design changes (requires Ruby; the repo has no Gemfile):

```sh
gem install jekyll
jekyll serve
```

Then open http://localhost:4000. Use `jekyll build` to check that the site compiles.

Deployment is GitHub Pages building `main` from `/ (root)`: pushing to `main` publishes within 1-2 minutes. A build failure shows as a red ❌ in the Actions tab, and the live site stays on the previous version.

## How the page is assembled

`index.html` (the only page, with `layout: null`) loops over `_data/enlaces.yml` and calls `_includes/enlace.html` for each link. That include normalizes the URL, picks an icon from `_data/iconos.yml` and renders the button. Links without a `url` are skipped, and an empty `lema` is hidden.

## Things to preserve

- **`_data/enlaces.yml` is edited by non-programmers** in the GitHub web editor, and its header comment is their manual. If you add or change a link field or a forceable icon, update that header and the README too. Keep the commented-out examples at the bottom of the file.
- **Icon matching order matters.** A URL is compared with each entry's `dominios` in `_data/iconos.yml`, as `//domain` or `.domain`, and the last match in the file wins. So `youtubemusic` must stay after `youtube`. Entries with no `dominios` are never matched by URL: they are set through `icono:`, are built-in defaults (`enlace` as the fallback, `correo` for `mailto:`) or are used directly by the templates (`flecha`, `compartir`).
- **Icon SVGs** are the inner markup of a `0 0 24 24` viewBox and use `currentColor`, so CSS can recolor them. They are single-quoted YAML strings.
- **Liquid include variables persist between calls.** `_includes/enlace.html` reassigns all of its variables at the top for this reason, so any new variable needs the same treatment.
- **Asset paths in `index.html` are relative on purpose** (`assets/...`), so they work under the `/apothecary/` base path and on a future custom domain. Only canonical and Open Graph URLs use `absolute_url`. The images and stylesheet get a `?v={{ version }}` cache-buster from the build time.
- **Changing the palette touches more than the CSS.** The colors live in `:root` in `assets/css/estilo.css`, but `theme-color` in `index.html` is hardcoded to match `--fondo`, and the logo, favicons and `og.jpg` in `assets/img/` are raster images in the same colors, so they need regenerating too.
- **Anything new at the repo root gets published** unless it is listed under `exclude` in `_config.yml`.
- **Fonts are self-hosted** in `assets/fonts/` (IM Fell, SIL OFL). Icon and font attributions are in the README and in the `iconos.yml` header.
