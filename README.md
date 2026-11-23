# Magazine

Free magazines, published at **https://suryarao.in/magazine/**.

## Publishing a new issue

1. Copy the PDF into `data/`. The file name becomes the title:
   `2026-11-winter-edition.pdf` shows up as "2026 11 Winter Edition".
2. Commit and push to `gh-pages`:
   ```
   git add data
   git commit -m "Add winter edition"
   git push
   ```
3. The **Publish magazine site** workflow rebuilds `magazines.json` and
   deploys the site. The new issue is live in about a minute.

GitHub won't accept a single file over 100 MB, so compress very large PDFs
before adding them.

## What readers can do

| Where | Action |
|---|---|
| Home | Tap a cover or **Read** to open the issue full screen |
| Home / reader | **Download** saves the PDF to the phone's or computer's Downloads folder |
| Home / reader | **Share** opens the phone's share sheet (or copies a link on desktop) |
| Reader | Tap the **right side** for the next page, **left side** for the previous one |
| Reader | **Swipe right-to-left** to go back to the list of issues |
| Reader | Tap the **middle** to show or hide the toolbar (sound, download, share) |
| Desktop | ← / → arrow keys turn pages, Esc goes back to the list. Ctrl+L switches between fit-to-page and fit-to-width; in fit-to-width, scroll down past the end of a page to go to the next one (and up past the top for the previous one) |

Shared links open straight into the issue (`…/magazine/#read=data/<file>.pdf`).

## Local preview

```
node tools/build-manifest.mjs
python -m http.server 8000
```
Then open http://localhost:8000.

## Layout

```
index.html                 home page + reader
css/style.css
js/app.js                  catalog, PDF rendering, page-turn animation and sound, gestures
vendor/pdfjs/              PDF.js 4.10.38 (Mozilla, Apache-2.0)
tools/build-manifest.mjs   writes magazines.json from data/*.pdf
.github/workflows/pages.yml
data/                      the issues (PDFs)
```
