# legal

Legal documents for apps published by Thai Dang Studio, served as a static site through GitHub Pages.

## Live URLs

- Index: https://thai-dang-studio.github.io/legal/
- Conversion Kit privacy policy: https://thai-dang-studio.github.io/legal/conversion-kit/privacy.html
- Coloriso (formerly Draw Kit) privacy policy: https://thai-dang-studio.github.io/legal/draw-kit/privacy.html
- Nestbook privacy policy: https://thai-dang-studio.github.io/legal/nestbook/privacy.html
- Nestbook support: https://thai-dang-studio.github.io/legal/nestbook/support.html
- Lifeline privacy policy: https://thai-dang-studio.github.io/legal/lifeline/privacy.html
- Lifeline support: https://thai-dang-studio.github.io/legal/lifeline/support.html

## Structure

- `index.html` — landing page listing every document.
- `conversion-kit/privacy.html` — privacy policy for Conversion Kit, English and Vietnamese on one page.
- `draw-kit/privacy.html` — privacy policy for Coloriso, English and Vietnamese on one page. The app was renamed from Draw Kit on 17 August 2026; the path keeps the old name because it is registered in both store consoles.
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
- Source of truth for Nestbook's wording is the app itself: it claims no collection, on-device AI only, and iCloud sync through the user's own account. If the app's behaviour changes, this page changes with it.
- Update the "Last updated" date in a document whenever its content changes.

## Lifeline — keeping the policy true

`lifeline/privacy.html` is the **only copy** of Lifeline's privacy policy. The draft that used to live
in the `td-lifeline` repository (`docs/release/PRIVACY_POLICY.md`) was deleted on 21 September 2026,
once this page was published. Edit the page here; there is nothing to keep in sync.

- Where the Vietnamese and English versions are understood differently, **the Vietnamese version is
  the original** — the page says so itself. Edit both versions in the same change.
- When the policy changes in substance (not a typo), keep the earlier version at an archive URL and
  update both dates — section 12 of the policy promises exactly that.

### What the policy must never say

| Never | Why |
|---|---|
| "never a server" / "không bao giờ có máy chủ" | a later version may send data the user **chooses** to share; section 12 covers that |
| "free forever" / "always free" / "miễn phí mãi mãi" | the commitment is "free to download, no ads" |
| AI, a Pro tier, a price | none of it exists yet; promising it early is promising what is not there |
| cookies, analytics, ads, "we may share with partners" | the app has none of these — template text would contradict the rest of the page |
| the life table's source by name | it is read from the app's data and changes with each release; the page says Settings names it |

Before publishing an edit, search the page text (accents and case removed) for these patterns — the
same ones the app's own `tool/check_strings.dart` blocks: `khong bao gio.{0,20}may chu`,
`never.{0,20}server`, `no server.{0,10}ever`, `mien phi (mai mai|vinh vien|tron doi)`,
`(free forever|forever free)`, `always (be )?free`. On 21 September 2026 all three pages had 0 hits.

### Every claim is tied to the app

If the app changes so that one of these stops being true, the matching sentence changes in the same
pass. Paths are in the `td-lifeline` repository.

| Claim on the page | What makes it true |
|---|---|
| At most two permissions asked, each at first use: notifications and the camera | Notifications are asked only when the first reminder switch is turned on (AC-73; the plugin is initialised with every `request…Permission` flag off). `app/ios/Runner/Info.plist` has only `NSCameraUsageDescription`. `AndroidManifest.xml` declares `CAMERA` and `RECEIVE_BOOT_COMPLETED` — the second is install-time, with no prompt, and exists so reminders survive a restart (AC-181, D-75); `POST_NOTIFICATIONS` is merged in by the notification plugin and prompts on Android 13+. `app/tool/check_permissions.dart` blocks the photo-library, microphone, storage and exact-alarm permissions |
| The Android release has no internet permission | `AndroidManifest.xml` removes `android.permission.INTERNET` |
| No analytics, crash-reporting or tracking SDK | `app/tool/check_deps.dart`, run on every commit |
| The app never calls the network; the life table ships inside | `app/assets/data/life_tables.json`; `app/tool/audit_network.dart` |
| Settings names the data source and year | `life_tables.json` meta — `is_placeholder: false` (on 21 Sep 2026: WHO/UN, 2023) |
| OS cloud backup is off by default | Android `LifelineBackupAgent` + `dataExtractionRules`; iOS `NSURLIsExcludedFromBackupKey` |
| Export and import go through the system share sheet / picker | every "save outside the app" path uses the share sheet |
| A share card with another person needs consent | the two-step consent gate of the card flow |
| Under 13: the app stops and stores nothing | the age check at the first onboarding step |
| Crisis lines always available, no conditions | `app/assets/data/crisis_links.json`, in Settings and on the memorial screen |

