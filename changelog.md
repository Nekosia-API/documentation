[//]: # (Title: Changelog - Nekosia API Docs)
[//]: # (Desc: Detailed version history of Nekosia API, including updates, new features, and compatibility notes.)
[//]: # (Tags: changelog, changelogs, nekosia changelog, nekosia api changelog, nekosia api version history, nekosia version history, nekosia api docs changelog, version history, api updates, nekosia updates)
[//]: # (Canonical: changelog)
[//]: # (Creation date: 2024-07-29)
[//]: # (Last update: 2026-03-25)

# Changelog {#changelog}
Nekosia and Booru are continuously developed. Each new version brings new features, important security fixes, and numerous improvements.
Not all changes are documented here; we record only the most significant ones that may affect how the Service or API is used.
We use [semantic versioning](https://nekosia.cat/documentation?page=introduction#semver).

Entries are sorted from newest to oldest. Labels: `[Website]`, `[API]`, `[CDN]`.


### [API] v1.2.6-rc.1+20260326 - 22.03.2026 {#api-20260326}
1. The `rating` parameter is now validated — providing an invalid value results in a `400` response instead of silently falling back to `safe`.
2. The `nothing` category without `additionalTags` now returns a descriptive `400` error instead of a generic "no results found" message.
3. The `/tags` endpoint now returns only tags from images with `published: true`. Previously, it exposed tags from unpublished images.
4. Removed a non-functional category blocking condition that was never satisfied.
5. Code quality improvements and optimizations.

### [Website] v1.3.0-rc.1+20260326 - 22.03.2026 {#20260326}
1. Redesigned and improved the appearance of the homepage and several other pages.
2. Added tag-based image search in Nekosia Booru.
3. Added filtering options in Nekosia Booru.
4. Added the ability to search images by artist name.
5. Login via X (formerly Twitter) now uses OAuth2.
6. Improved error handling. The server now returns dedicated error pages instead of empty responses.
7. Fixed the user menu appearance in the navbar across various display scenarios.
8. Added a Privacy Policy link in the footer.
9. Revised and expanded the documentation: improved clarity, consistency, and coverage.
10. General performance, security, and code quality improvements.

### [Website] v1.2.15-rc.1+20260225 - 25.02.2026 {#20260225}
1. Improved and refined the appearance of the homepage (mainly the cover).
2. Fixed certain issues with `noscript`.
3. Various bug fixes and improvements.
4. Dependencies updated to the latest stable versions.

### [API] v1.2.4-rc.1+20260115 - 15.01.2026 {#20260115}
1. Performance and quality improvements.
2. Dependencies updated to the latest stable versions.
3. Other fixes.

### [API] 24.06.2025 {#20250624}
1. Performance and quality improvements.
2. Dependencies updated to the latest stable versions.
3. Updated EXIF data for each image.

### [API] 18.04.2025 {#20250418}
1. Updated dependencies to the latest version.
2. Added the `random` category. This category is also covered by filters by default.

### [API] 20.03.2025 {#20250320}
1. Updated dependencies to the latest version.
2. Added aliases for the word `ribbon`. From now on, when you use the `ribbon` category, the API will return images with ribbons in various colors.
3. Other fixes.

### [API] 20.01.2025 {#20250120}
1. Updated dependencies to the latest version.

### [API] 19.12.2024 {#20241219}
1. The minimum length of the `id` parameter was changed from 6 to 4 characters. Valid range: 4–128 characters.
2. Updated dependencies.

### [API] 16.12.2024 {#20241216}
1. Updated dependencies.
2. Other fixes.

### [API] 12.11.2024 {#20241112}
1. Updated `/api/v1/tags`.

### [API] 06.11.2024 {#20241106-b}
1. The `images` field has been removed from the API responses and replaced by `count`.

### [API] 06.11.2024 {#20241106-a}
1. The `identifier` field has been removed from API responses.
2. An `images` field has been added to API responses to show the number of filtered images.
3. `shadow` has been replaced with `nothing`, which serves the same purpose. Click [here](https://nekosia.cat/documentation?page=endpoints#filters) for more information.
4. The script managing tag filters has been restructured.
5. Further quality improvements have been implemented.

### [API] 04.10.2024 {#20241004}
1. Updated tags.
2. Added `/api/v1/tags`.
3. Updated dependencies.

### [API] 07.09.2024 {#20240907}
1. Added a new `rating` parameter for `/images`. The default rating in every response is `safe`.
2. The `key` field in the JSON response can now be `undefined`.
3. Minor adjustments were made.

### [API] 19.08.2024 {#20240819}
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

### [Website] v1.2.12 {#website-1212}
1. Performance and quality improvements.
2. Dependencies updated to the latest stable versions.
3. UI improvements.
4. Bugfixes.
5. Documentation improvements.

### [Website] v1.2.9 {#website-129}
1. Performance and quality improvements.
2. Dependencies updated to the latest stable versions.

### [Website] v1.2.8 {#website-128}
1. Other optimizations.
2. Updated dependencies to the latest version.

### [Website] v1.2.7 {#website-127}
1. Updated dependencies to the latest version.
2. Quality fixes.

### [Website] v1.2.6 {#website-126}
1. Updated dependencies to the latest version.

### [Website] v1.2.5 {#website-125}
1. Updated dependencies to the latest version.
2. Other quality fixes.

### [Website] v1.2.4 {#website-124}
1. Updated dependencies to the latest version.
2. Added the Swift wrapper [jezreelbarbosa/NekosiaAPI](https://github.com/jezreelbarbosa/NekosiaAPI) to the official [documentation](https://nekosia.cat/documentation?page=wrappers).

### [Website] v1.2.3 {#website-123}
1. Updated dependencies to the latest version.
2. Other fixes.

### [Website] v1.2.2 {#website-122}
1. Updated dependencies to the latest version.
2. Small fixes.

### [Website] v1.2.1 {#website-121}
1. Resolved issues related to voting functionality.
2. UI improvements.

### [Website] v1.2.0 {#website-120}
1. Resolved issues related to voting functionality.
2. Removed specific data caching in booru that had no impact on backend performance.
3. Reset all statistics and votes.
4. Improved responsiveness and made slight UI enhancements in booru.
5. Added the ability to vote on images from their full view.
6. General performance and quality improvements.

### [Website] v1.1.4 {#website-114}
1. Bugfixes.

### [Website] v1.1.2 {#website-112}
1. Slightly improved the color scheme of profile tabs on Booru.
2. Corrected sentences.
3. Updated all npm modules.
4. Implemented various quality improvements and enhancements.

### [Website] v1.1.0 {#website-110}
1. Improved the appearance of photo cards.
2. Added fields for twin images and similar images.
3. Other enhancements.
4. Bug fixes.

### [Website] v1.0.2 {#website-102}
1. Added a full image preview feature when clicking on an image (on the Booru page).
2. Minor website and SEO tweaks.
3. Other fixes.