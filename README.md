# Song Sorter Template

A [copier](https://copier.readthedocs.io/) template for the TRiDENT-style band song sorter. See https://tridentsort.github.io.

Generates a fresh sorter site (HTML/CSS/JS, no build step, deploys to GitHub Pages) with
band name, URLs, and accent color swapped in.

## Generating a New Sorter

This template requires Python to be installed. Download it from https://www.python.org/downloads/.

To generate a new sorter, run the following steps in a terminal window. Replace `mybandsort` with the name of your band, e.g. `tridentsort`

```sh
pip install copier
copier copy gh:<your_github_username>/sorter-template ./mybandsort.github.io
# …or from a local checkout:
copier copy ~/src/sorter-template ./mybandsort.github.io
```

# Customizing This Sorter

Copier will prompt for `band_name`, `band_slug`, `sorter_url`, `official_url`, and `accent_hex`. Defaults are derived from the slug where possible.

After generation:

1. `cd ./mybandsort.github.io && npm install`
2. Drop band art into `img/` (`bandphoto.jpg`, `bandlogo.png`, `favicon.png`,
   `apple-touch-icon.png`) and album covers into `img/albums/`. See `img/README.md`.
   * The img/favicon.png and img/apple-touch-icon.png are optional but can be found on the band's website. This is usually located at https://<bandwebsite>/favicon.ico. If it's not there you'll need to find it in the web page's source.
3. Replace the placeholder album in `js/songlist.js` with the real catalog.
4. `npm start` to preview locally.

## Changing the Accent Color

If you want to change the accent colors at any time, run the following with any `#rrggbb` value. Replace `<hexvalue>` with the hex value including the `#`.

```sh
node scripts/set-accent.mjs "<hexvalue>"
```

It updates `--accent` in `css/style.css` and the `theme-color` meta tag in `index.html`.
The full palette derives from `--accent` via CSS `color-mix()`, so one substitution
re-themes the whole site. You can run it as many times as you want while iterating.

## Updating an Existing Sorter

`copier update` in the generated repo re-runs the template against the latest
sorter-template, preserving your answers from `.copier-answers.yml`. Useful for pulling
in upstream improvements (new sort engine features, CSS tweaks, etc.) without losing
the band-specific customizations.
