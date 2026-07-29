# legal

Legal documents for apps published by Thai Dang Studio, served as a static site through GitHub Pages.

## Live URLs

- Index: https://thai-dang-studio.github.io/legal/
- Conversion Kit privacy policy: https://thai-dang-studio.github.io/legal/conversion-kit/privacy.html

## Structure

- `index.html` — landing page listing every document.
- `conversion-kit/privacy.html` — privacy policy for Conversion Kit, English and Vietnamese on one page.
- `.nojekyll` — serve files as-is, skip the Jekyll build step.

## Publishing

GitHub Pages is configured in repository Settings, Pages, Deploy from a branch, branch `main`, folder `/ (root)`.

Changes pushed to `main` go live in about a minute.

## Notes

- The privacy policy URL is referenced from Google Play Console and App Store Connect. Keep the path stable; do not rename or move published files.
- Update the "Last updated" date in a document whenever its content changes.
