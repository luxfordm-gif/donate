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

## One-time GitHub Pages setup

1. In this repository go to **Settings → Pages**.
2. Under **Build and deployment**, set **Source** to *Deploy from a branch*.
3. Choose the `main` branch and the `/ (root)` folder, then **Save**.
4. The site will be published at `https://<your-username>.github.io/donate/`.
   Use that address when generating the QR code.
