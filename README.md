# Connect Care Plan Maker

The tool the CAs use to build a patient's care plan and investment options,
served by GitHub Pages at https://careplan.connectchiropractic.com

- `index.html` is the whole app. Practice rules (prices, the 5% pay-in-full
  reduction, card fee, payment dates, visit frequencies) sit at the top of its
  `<script>` under "practice settings".
- `assets/` holds the home-screen icons.
- Nothing typed into the app is saved or sent anywhere. Patient names stay in
  the browser and are gone when the page is closed.
- `robots.txt` and a `noindex` tag keep it out of search results. It is not
  password protected.

Printing: open in Chrome, click **Print / Save PDF**. Margins: Default.
Headers and footers: off. Each plan is exactly two letter pages.

GoCardless logo: add the official file as `gocardless-logo.png` in this folder
and it appears on the bank instalment option automatically.

## Publishing a change

Same as the meal plan app: commit, then **Push origin** in GitHub Desktop.
GitHub Pages publishes within a minute or two.

## Staff PIN

The maker opens behind a staff PIN screen. Each computer stays unlocked for
30 days. Only a SHA-256 fingerprint of the PIN is in `index.html` (`PIN_HASH`),
never the PIN itself. To change the PIN, replace `PIN_HASH` with the SHA-256 of
`connect-careplans:` followed by the new PIN, for example:

    printf 'connect-careplans:NEWPIN' | shasum -a 256

This keeps casual visitors out. It is not strong security, and the maker holds
no patient information.
