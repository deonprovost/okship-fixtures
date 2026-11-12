# okship-fixtures

Public test fixtures for OKShip's staging smokes. They hold no data: no cookies, no forms that
post, no analytics, and no requests to any other site (each page's Content-Security-Policy
forbids them).

This folder is the record of what is hosted at https://deonprovost.github.io/okship-fixtures/
(owner ruling 20, 2026-11-12). Change a page here first, then upload it again.

## Pages

- `save.html` -- one button and a status line. The button's label comes from the query string,
  and clicking it shows "Saved.":
  - `save.html?label=Save` shows a "Save" button;
  - `save.html?label=Save%20changes` shows a "Save changes" button;
  - with no `label`, the button reads "Save".

  Used by `scripts/smoke-path-adaptation.ts` (the two-run case, test plan S5): run 1 passes on
  "Save", the app's start URL is switched to "Save changes", and run 2 must report the changed
  control. The same page with the label unchanged is the control that must report nothing.

## Upload steps (owner)

1. On GitHub, create a new PUBLIC repository named `okship-fixtures` under `deonprovost`
   (no template; a README is optional).
2. Upload `save.html` and this `README.md` to the root of the `main` branch
   (Add file -> Upload files -> Commit changes).
3. Settings -> Pages -> Build and deployment -> Source: Deploy from a branch -> Branch: `main`,
   folder `/ (root)` -> Save.
4. Wait for the Pages deployment to finish (the Actions tab shows it), then open
   https://deonprovost.github.io/okship-fixtures/save.html?label=Save%20changes and check that
   the button reads "Save changes" and that clicking it shows "Saved.".
