# Time Traveler website

Public site for the game **Time Traveler: Love & Choices** (Android package `com.mz.ttlc`), served
by GitHub Pages at <https://minggamecn.github.io/time_traveler_site/>. Plain HTML and CSS: no
build step, no JavaScript, no cookies, no external services.

The game itself lives in the `hera_client` repository; open `../time_traveler.code-workspace` to
work on both side by side.

| Route | Page |
| --- | --- |
| `/` | Homepage: the story, features, and links to every help page |
| `/support/` | FAQ (purchases, new phone, refunds, language) and contact |
| `/privacy/` | Privacy policy |
| `/terms/` | Terms of service |
| `/delete-account/` | Data deletion: on-device steps and email requests |

## URLs for Google Play Console

- Privacy policy: `https://minggamecn.github.io/time_traveler_site/privacy/`
- Delete account / data URL: `https://minggamecn.github.io/time_traveler_site/delete-account/`
- Website and support: `https://minggamecn.github.io/time_traveler_site/` and `.../support/`

## Files

```
index.html               Homepage
support/ privacy/ terms/ delete-account/   One index.html each
404.html                 Not-found page (absolute /time_traveler_site/ paths; GitHub serves it from any URL)
styles.css               Shared stylesheet
assets/hero.jpg          Feature graphic, 1600 px wide (from hera_client/store/feature-graphic.png)
assets/share.jpg         Social preview image, 1200 px wide
assets/icon-256.png      Header icon (from hera_client/store/icon-store.png)
favicon.png, apple-touch-icon.png   Browser icons
.nojekyll                Serve files as they are
```

## Keeping the policies true

The policies describe the release build as of 2026-10-24: offline only, no account, no ads, no
analytics or crash reporting, saves in app-private storage (Android Auto Backup on), and Google
Play Billing as the only network use (`INTERNET` and `ACCESS_NETWORK_STATE` permissions). Update
the privacy policy, terms, deletion page and support FAQ **before** shipping any build that
changes this, in particular:

- enabling the backend (`CLOUD` in `assets/scripts/platform/CloudConfig.ts`): anonymous accounts,
  cloud saves and server-verified purchases need new privacy sections, an in-game account
  deletion flow, and a real deletion process on `/delete-account/`;
- adding analytics, crash reporting, ads, notifications, or sign-in;
- new volumes, price models, or paid events (terms section 4, support FAQ, homepage note).

When a policy changes, update its "Last updated" date; move "Effective" only when the change
alters what readers agree to.

The operator name (`Ming Zhu`) and the contact address (`wdswmz@gmail.com`) appear on
every page. Search for both when either changes, for example if the game is published by a
company.

Google Play Data safety form, as the build stands: no data collected and no data shared;
purchases are processed by Google Play itself, which the form does not count as developer
collection.

## Preview and deploy

```sh
python -m http.server 3000      # then open http://localhost:3000/
```

Check pages at a phone width as well as desktop. The 404 page only renders correctly under
`/time_traveler_site/`.

GitHub Pages serves the `main` branch root (**Settings → Pages → Source: Deploy from a branch**,
branch `main`, folder `/`). Pushes go live in about a minute.

When the Play listing is live, replace "Coming soon to Google Play." on the homepage with a link
to `https://play.google.com/store/apps/details?id=com.mz.ttlc`.
