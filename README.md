# Song Sorter Template

A [copier](https://copier.readthedocs.io/) template for the TRiDENT-style band song sorter. See https://tridentsort.github.io.

Generates a fresh sorter site (HTML/CSS/JS, no build step, deploys to GitHub Pages) with
band name, URLs, and accent color swapped in.

## Generating a New Sorter

This template assumes familiarity with using GitHub. If you do not understand GitHub, please look up some tutorials on how to create, pull, edit, and push repositories first.

This template requires Python and Node.js to be installed. Download them from https://www.python.org/downloads/ and https://nodejs.org/en/download.

To generate a new sorter, follow the steps below. 

:information: `mybandsort` is only an example below. Replace it with the name of your band's sorter, e.g. `tridentsort`

:warning: This sorter will not work unless you follow the exact steps below. The GitHub URL _must_ be in the format https://github.com/mybandsort/mybandsort.github.io

1. Go to https://github.com and create a new organization called `mybandsort`
   * This and the New Repository option can be found in the `+` menu at the top right of the page
2. In that organization, create a repository called `mybandsort.github.io`
3. Clone the repository to your local computer
4. Open a terminal and change directories to the local directory of your computer that you cloned your repo to
5. Run the following steps:
   ```sh
   pip install copier
   copier copy gh:mstie/band-sorter-template .
   ```
6. Customize the sorter as per the instructions below
7. Push the changes to your repository
8. The changes will automatically be build in GitHub actions and published to GitHub pages. Find your site at https://mybandsort.github.io

# Customizing This Sorter

Copier will prompt for `band_name`, `band_slug`, `sorter_url`, `official_url`, and `accent_hex`. Defaults are derived from the slug where possible.

After generation:

1. `cd ./mybandsort.github.io && npm install`
2. Drop band art into `img/` (`bandphoto.jpg`, `bandlogo.png`, `favicon.png`,
   `apple-touch-icon.png`) and album covers into `img/albums/`. See `img/README.md`.
   * The img/favicon.png and img/apple-touch-icon.png are optional but can be found on the band's website. This is usually located at https://<bandwebsite>/favicon.ico. If it's not there you'll need to find it in the web page's source.
3. Run `npm install && npm start` in a command line or terminal to start the server locally.
4. Open https://127.0.0.1:8000/editor.html to edit the catalog
5. Save your catalog per the instructions on the editor page then view the sorter at https://127.0.0.1:8000
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
band-sorter-template, preserving your answers from `.copier-answers.yml`. Useful for pulling
in upstream improvements (new sort engine features, CSS tweaks, etc.) without losing
the band-specific customizations.
