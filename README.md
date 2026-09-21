# legal

Legal documents for apps published by Thai Dang Studio, served as a static site through GitHub Pages.

## Live URLs

- Index: https://thai-dang-studio.github.io/legal/
- Conversion Kit privacy policy: https://thai-dang-studio.github.io/legal/conversion-kit/privacy.html
- Draw Kit privacy policy: https://thai-dang-studio.github.io/legal/draw-kit/privacy.html
- Nestbook privacy policy: https://thai-dang-studio.github.io/legal/nestbook/privacy.html
- Nestbook support: https://thai-dang-studio.github.io/legal/nestbook/support.html
- Lifeline privacy policy: https://thai-dang-studio.github.io/legal/lifeline/privacy.html
- Lifeline support: https://thai-dang-studio.github.io/legal/lifeline/support.html

## Structure

- `index.html` — landing page listing every document.
- `conversion-kit/privacy.html` — privacy policy for Conversion Kit, English and Vietnamese on one page.
- `draw-kit/privacy.html` — privacy policy for Draw Kit, English and Vietnamese on one page.
- `nestbook/privacy.html` — privacy policy for Nestbook, English and Vietnamese on one page.
- `nestbook/support.html` — support page for Nestbook. App Store Connect requires a support URL as well as a privacy policy URL, so Nestbook is the first app here with two documents.
- `lifeline/privacy.html` — privacy policy for Lifeline ("Dòng Đời"), English and Vietnamese on one page.
- `lifeline/support.html` — support page for Lifeline. Both URLs are required before the app can be submitted to either store.
- `.nojekyll` — serve files as-is, skip the Jekyll build step.

## Publishing

GitHub Pages is configured in repository Settings, Pages, Deploy from a branch, branch `main`, folder `/ (root)`.

Changes pushed to `main` go live in about a minute.

## Notes

- The privacy policy URL is referenced from Google Play Console and App Store Connect. Keep the path stable; do not rename or move published files.
- Nestbook's support page is referenced as the App Store support URL, so the same rule applies to it.
- Source of truth for Lifeline's wording is `docs/release/PRIVACY_POLICY.md` in the `td-lifeline` repository, which in turn is checked line by line against the app's own manifests and static gates. Change the app's behaviour and both that file and this page change with it. Where the Vietnamese and English versions are understood differently, **the Vietnamese version is the original** — the page says so itself.
- Source of truth for Nestbook's wording is the app itself: it claims no collection, on-device AI only, and iCloud sync through the user's own account. If the app's behaviour changes, this page changes with it.
- Update the "Last updated" date in a document whenever its content changes.
