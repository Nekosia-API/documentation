[//]: # (Title: Changelog - Nekosia API Docs)
[//]: # (Desc: Detailed version history of Nekosia API, including updates, new features, and compatibility notes.)
[//]: # (Tags: changelog, changelogs, nekosia changelog, nekosia api changelog, nekosia api version history, nekosia version history, nekosia api docs changelog, version history, api updates, nekosia updates)
[//]: # (Canonical: changelog)

# Changelog {#changelog}
Nekosia and Booru are continuously developed. Each new version brings new features, important security fixes, and numerous improvements.
Not all changes are documented here; we record only the most significant ones that may affect how the Service or API is used.
We use [semantic versioning](https://nekosia.cat/documentation?page=introduction#semver).

Entries are sorted from newest to oldest. Labels: `[WWW]`, `[API]`, `[CDN]`, `[CRON]`.

### [WWW] v1.4.1-rc.1+20260421 {#www-20260421}
1. Improved SEO for Booru image pages.
2. Fixed image info panel layout — shadows and hover animations were being clipped.
3. Improved live statistics on the home page (WebSocket).
4. Consolidated SVG icons into a single sprite file for faster loading.
5. Improved dialog and toast notification handling.
6. Various bug fixes and improvements.

### [WWW] v1.4.0-rc.1+20260414 {#www-20260414}
1. Removed the comments feature from Nekosia Booru.
2. Added animated particle backgrounds to role badges.
3. Added the Contributor role — awarded automatically when a modification request is accepted.
4. Various improvements and cleanup.

### [CDN] v2.3.0-rc.1+20260414 {#cdn-20260414}
1. Performance and reliability improvements.
2. Various bug fixes and code quality improvements.

### [WWW] v1.3.2-rc.1+20260407 {#www-20260407}
1. Added a newsletter system in the admin panel.
2. Added a dedicated unsubscribe page with one-click unsubscribe support (RFC 8058).
3. Replaced the markdown-based email pipeline with direct HTML templates.
4. Improved email appearance.
5. Improved role styling.
6. Improved user profile settings, reordered options and added a link to the privacy policy section on email correspondence.
7. Added a hidden Easter egg on the home page. 🐾
8. Various bug fixes and code quality improvements.

### [WWW] v1.3.1-rc.1+20260406 {#www-20260406}
1. Improved the appearance of the main page.
2. Improved error page styling.
3. Added a role system.
4. Updated the color palette for each image.
5. Added a dedicated script for toasts and dialogs.
6. Page title now cycles through cute kawaii messages while the tab is in the background.

### [WWW] v1.3.0-rc.1+20260402 {#www-20260402}
1. Redesigned and improved the appearance of the homepage and several other pages.
2. Fixed the user menu appearance in the navbar across various display scenarios.
3. Added tag-based image search in Nekosia Booru.
4. Added filtering options in Nekosia Booru.
5. Improved user settings in Nekosia Booru.
6. Added the ability to search images by artist name.
7. Introduced AI-powered image tagging (images can still only be uploaded by the administrator).
8. Login via X (formerly Twitter) now uses OAuth2.
9. Various improvements to other authentication services.
10. Improved error handling - the server now returns dedicated error pages instead of empty responses.
11. ~~Production builds now serve only minified and optimized code for faster loading.~~
12. Introduced a new metrics system available exclusively to administrators.
13. Cleaned up the database schema and collections to improve performance and workflow quality.
14. Added a Privacy Policy link in the footer.
15. Minor documentation improvements - enhanced clarity and consistency.
16. General improvements to performance, security, and code quality.

### [API] v1.2.6-rc.1+20260402 {#api-20260402}
1. The `rating` parameter is now validated — providing an invalid value results in a `400` response instead of silently falling back to `safe`.
2. The `nothing` category without `additionalTags` now returns a descriptive `400` error instead of a generic "no results found" message.
3. The `/tags` endpoint now returns only tags from images with `published: true`. Previously, it exposed tags from unpublished images.
4. Removed a non-functional category blocking condition that was never satisfied.
5. Code quality improvements and optimizations.

### [CRON] 2.4.3-rc.1+20260402 {#cron-#20260402}
1. Detection of similar images has been improved.
2. General improvements to performance and code quality.

### [WWW] v1.2.15-rc.1+20260225 {#www=20260225}
1. Improved and refined the appearance of the homepage (mainly the cover).
2. Fixed certain issues with `noscript`.
3. Various bug fixes and improvements.
4. Dependencies updated to the latest stable versions.

### [WWW] v1.2.4-rc.1+20260115 {#api-20260115}
1. Performance and quality improvements.
2. Dependencies updated to the latest stable versions.
3. Other fixes.

### [WWW] 24.06.2025 {#api-20250624}
1. Performance and quality improvements.
2. Dependencies updated to the latest stable versions.
3. Updated EXIF data for each image.

### [API] 18.04.2025 {#api-20250418}
1. Updated dependencies to the latest version.
2. Added the `random` category. This category is also covered by filters by default.

### [API] 20.03.2025 {#api-20250320}
1. Updated dependencies to the latest version.
2. Added aliases for the word `ribbon`. From now on, when you use the `ribbon` category, the API will return images with ribbons in various colors.
3. Other fixes.

### [API] 20.01.2025 {#api-20250120}
1. Updated dependencies to the latest version.

### [API] 19.12.2024 {#api-20241219}
1. The minimum length of the `id` parameter was changed from 6 to 4 characters. Valid range: 4–128 characters.
2. Updated dependencies.

### [WWW] 16.12.2024 {#api-20241216}
1. Updated dependencies.
2. Other fixes.

### [API] 12.11.2024 {#api-20241112}
1. Updated `/api/v1/tags`.

### [API] 06.11.2024 {#api-20241106-b}
1. The `images` field has been removed from the API responses and replaced by `count`.

### [API] 06.11.2024 {#api-20241106-a}
1. The `identifier` field has been removed from API responses.
2. An `images` field has been added to API responses to show the number of filtered images.
3. `shadow` has been replaced with `nothing`, which serves the same purpose. Click [here](https://nekosia.cat/documentation?page=endpoints#filters) for more information.
4. The script managing tag filters has been restructured.
5. Further quality improvements have been implemented.

### [API] 04.10.2024 {#api-20241004}
1. Updated tags.
2. Added `/api/v1/tags`.
3. Updated dependencies.

### [API] 07.09.2024 {#api-20240907}
1. Added a new `rating` parameter for `/images`. The default rating in every response is `safe`.
2. The `key` field in the JSON response can now be `undefined`.
3. Minor adjustments were made.

### [WWW] 19.08.2024 {#api-20240819}
1. Released the official [nekosia.js](https://www.npmjs.com/package/nekosia.js) module.
2. Website and documentation improvements.
3. Created the `tos.md` document.

---

*The following entries have no recorded release date.*

### [CDN] v2.2.4 {#cdn-224}
1. Resolved an issue where the server would crash when a client attempted to download a large file.
2. Updated dependencies to the latest version.

### [CDN] v2.2.1 {#cdn-221}
1. Resolved an issue where a worker in the cluster would suddenly restart when handling too many requests at the same time.
2. Updated dependencies to the latest version.
3. Other fixes.

### [WWW] v1.2.12 {#www-1212}
1. Performance and quality improvements.
2. Dependencies updated to the latest stable versions.
3. UI improvements.
4. Bugfixes.
5. Documentation improvements.

### [WWW] v1.2.9 {#www-129}
1. Performance and quality improvements.
2. Dependencies updated to the latest stable versions.

### [WWW] v1.2.8 {#www-128}
1. Other optimizations.
2. Updated dependencies to the latest version.

### [WWW] v1.2.7 {#www-127}
1. Updated dependencies to the latest version.
2. Quality fixes.

### [WWW] v1.2.6 {#www-126}
1. Updated dependencies to the latest version.

### [WWW] v1.2.5 {#www-125}
1. Updated dependencies to the latest version.
2. Other quality fixes.

### [WWW] v1.2.4 {#www-124}
1. Updated dependencies to the latest version.
2. Added the Swift wrapper [jezreelbarbosa/NekosiaAPI](https://github.com/jezreelbarbosa/NekosiaAPI) to the official [documentation](https://nekosia.cat/documentation?page=wrappers).

### [WWW] v1.2.3 {#www-123}
1. Updated dependencies to the latest version.
2. Other fixes.

### [WWW] v1.2.2 {#www-122}
1. Updated dependencies to the latest version.
2. Small fixes.

### [WWW] v1.2.1 {#www-121}
1. Resolved issues related to voting functionality.
2. UI improvements.

### [WWW] v1.2.0 {#www-120}
1. Resolved issues related to voting functionality.
2. Removed specific data caching in booru that had no impact on backend performance.
3. Reset all statistics and votes.
4. Improved responsiveness and made slight UI enhancements in booru.
5. Added the ability to vote on images from their full view.
6. General performance and quality improvements.

### [WWW] v1.1.4 {#www-114}
1. Bugfixes.

### [WWW] v1.1.2 {#www-112}
1. Slightly improved the color scheme of profile tabs on Booru.
2. Corrected sentences.
3. Updated all npm modules.
4. Implemented various quality improvements and enhancements.

### [WWW] v1.1.0 {#www-110}
1. Improved the appearance of photo cards.
2. Added fields for twin images and similar images.
3. Other enhancements.
4. Bug fixes.

### [WWW] v1.0.2 {#www-102}
1. Added a full image preview feature when clicking on an image (on the Booru page).
2. Minor website and SEO tweaks.
3. Other fixes.