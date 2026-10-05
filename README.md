# Halloween Display – Donation Redirect

A tiny GitHub Pages site used as a **permanent QR-code destination** for the
annual Halloween charity display raising money for Cancer Research.

The printed QR code always points here. This page immediately forwards
visitors to the current year's JustGiving fundraising page, so the QR code
never needs reprinting.

## Updating the link each year

1. Open `index.html`.
2. Find this line near the top of the `<script>` block:

   ```js
   const JUSTGIVING_URL = "PASTE_CURRENT_JUSTGIVING_URL_HERE";
   ```

3. Replace the text between the quotes with the new JustGiving page URL, for example:

   ```js
   const JUSTGIVING_URL = "https://www.justgiving.com/page/your-new-page";
   ```

4. Commit the change. GitHub Pages republishes within a minute or two.

That is the only change needed each year.

## How it works

- `window.location.replace()` sends the visitor straight to JustGiving and
  keeps this page out of their browser history.
- While that happens (or if JavaScript is blocked), the page shows a short
  thank-you message and a **Continue to JustGiving** button as a fallback.
- If the URL placeholder has not been replaced yet, the page shows a
  "not set up yet" message instead of redirecting somewhere broken.

## JustGiving logo

The page shows a JustGiving logo above the message if a file named
`justgiving-logo.svg` (or swap the extension in `index.html` for `.png`)
sits next to `index.html`. Download the official logo from JustGiving's
brand resources, save it under that name, and commit it. If the file is
missing the page simply hides the logo, so nothing breaks.

## GitHub Pages hosting

Publishing is automatic. The workflow in `.github/workflows/pages.yml`
runs on every push to `main`, switches GitHub Pages on the first time, and
deploys the site to:

    https://luxfordm-gif.github.io/donate/

Use that address when generating the QR code. You can watch deployments
under the repository's **Actions** tab.

Note: GitHub only publishes Pages from a **public** repository on the free
plan. If the repository is private, make it public under
**Settings → General → Danger zone → Change visibility** first.
