[//]: # (Title: Changelog - Nekosia API Docs)
[//]: # (Desc: Detailed version history of Nekosia API, including updates, new features, and compatibility notes.)
[//]: # (Tags: changelog, changelogs, nekosia changelog, nekosia api changelog, nekosia api version history, nekosia version history, nekosia api docs changelog, version history, api updates, nekosia updates)
[//]: # (Canonical: changelog)
[//]: # (Creation date: 2024-07-29)
[//]: # (Last update: 2026-02-25)
[//]: # (Contributors: N/A)

# Introduction {#introduction}
Nekosia, like Booru, is continuously developed, with each new version introducing new features, important fixes, and numerous improvements.
Not all changes and/or new features are documented here, only the most important ones.

# Version History {#version-history}
Using semantic versioning ([learn more](https://nekosia.cat/documentation?page=introduction#semver)) enables tracking changes and updates in a clear and intuitive way.
This ensures that users can always stay up to date with the latest functionalities and changes.
Below is the version history of the API, along with descriptions of the introduced changes and their release dates.


## API v1 {#v1}
### v1.2.4-rc.1+20260115 / 15.01.2026 {#api-124-rc.1+20260115}
1. Performance and quality improvements.
2. Dependencies updated to the latest stable versions.
3. Other fixes.

### v-.-.- / 24.06.2025 {#api-24062025}
1. Performance and quality improvements.
2. Dependencies updated to the latest stable versions.
3. Updated EXIF data for each image.

### v-.-.- / 18.04.2025 {#api-18042025}
1. Updated dependencies to the latest version.
2. Added the `random` category. This category is also covered by filters by default.

### v-.-.- / 20.03.2025 {#api-20032025}
1. Updated dependencies to the latest version.
2. Added aliases for the word `ribbon`. From now on, when you use the `ribbon` category, the API will return images with ribbons in various colors.
3. Other fixes.

### v-.-.- / 20.01.2025 {#api-20012025}
1. Updated dependencies to the latest version.

### v-.-.- / 19.12.2024 {#api-19122024}
1. The required length of the `id` parameter was changed to `<4`. Now: `< 4 || > 128`
2. Updated dependencies.

### v-.-.- / 16.12.2024 {#api-16122024}
1. Updated dependencies.
2. Other fixes.

### v-.-.- / 12.11.2024 {#api-12112024}
1. Updated `/api/v1/tags`.

### v-.-.- / 06.11.2024 {#api-06112024-a}
1. The `images` field has been removed from the API responses and replaced by `count`.

### v-.-.- / 06.11.2024 {#api-06112024-b}
1. The `identifier` field has been removed from API responses.
2. An `images` field has been added to API responses to show the number of filtered images.
3. `shadow` has been replaced with `nothing`, which serves the same purpose. Click [here](https://nekosia.cat/documentation?page=endpoints#filters) for more information.
4. The script managing tag filters has been restructured.
5. Further quality improvements have been implemented.

### v-.-.- / 04.10.2024 {#api-04102024}
1. Updated tags.
2. Added `/api/v1/tags`.
3. Updated dependencies.

### v-.-.- / 07.09.2024 {#api-07092024}
1. Added a new `rating` parameter for `/images`. The default rating in every response is `safe`.
2. The `key` field in the JSON response can now be `undefined`.
3. Minor adjustments were made.

### v-.-.- / 19.08.2024 {#api-19082024}
1. Released the official [nekosia.js](https://www.npmjs.com/package/nekosia.js) module.
2. Website and documentation improvements.
3. Created the `tos.md` document.


## Website {#website}

### v1.3.0-rc.1+20260320 / 20.03.2026 {#website-1216-rc.1+20260320}
1. Improved and enhanced the appearance of the main page.
2. Added tag search in Nekosia Booru.
3. Frontend and backend optimizations.
4. The server now properly renders error pages instead of returning an empty response; API endpoints return JSON with `success`, `status`, and `message` fields.
5. Fixed the user menu appearance in the navbar, the background now correctly adapts to the navbar state.
6. Unified error responses across Booru controllers, all API endpoints return JSON, page routes render a dedicated error view.
7. Fixed various bugs and minor issues in the frontend.

### v1.2.15-rc.1+20260225 / 25.02.2026 {#website-1215-rc.1+20260225}
1. Improved and refined the appearance of the homepage (mainly the cover).
2. Fixed certain issues with `noscript`.
3. Various bug fixes and improvements.
4. Dependencies updated to the latest stable versions.

### v1.2.12 / - {#website-1212}
1. Performance and quality improvements.
2. Dependencies updated to the latest stable versions.
3. UI improvements.
4. Bugfixes.
5. Documentation improvements.

### v1.2.9 / - {#website-129}
1. Performance and quality improvements.
2. Dependencies updated to the latest stable versions.

### v1.2.8 / - {#website-128}
1. Other optimizations.
2. Updated dependencies to the latest version.

### v1.2.7 / - {#website-127}
1. Updated dependencies to the latest version.
2. Quality fixes.

### v1.2.6 / - {#website-126}
1. Updated dependencies to the latest version.

### v1.2.5 / - {#website-125}
1. Updated dependencies to the latest version.
2. Other quality fixes.

### v1.2.4 / - {#website-124}
1. Updated dependencies to the latest version.
2. Added the Swift wrapper [jezreelbarbosa/NekosiaAPI](https://github.com/jezreelbarbosa/NekosiaAPI) to the official [documentation](https://nekosia.cat/documentation?page=wrappers).

### v1.2.3 / - {#website-123}
1. Updated dependencies to the latest version.
2. Other fixes.

### v1.2.2 / - {#website-122}
1. Updated dependencies to the latest version.
2. Small fixes.

### v1.2.1 / - {#website-121}
1. Resolved issues related to voting functionality.
2. UI improvements.

### v1.2.0 / - {#website-120}
1. Resolved issues related to voting functionality.
2. Removed specific data caching in booru that had no impact on backend performance.
3. Reset all statistics and votes.
4. Improved responsiveness and made slight UI enhancements in booru.
5. Added the ability to vote on images from their full view.
6. General performance and quality improvements.

### v1.1.4 / - {#website-114}
1. Bugfixes.

### v1.1.2 / - {#website-112}
1. Slightly improved the color scheme of profile tabs on Booru.
2. Corrected sentences.
3. Updated all npm modules.
4. Implemented various quality improvements and enhancements.

### v1.1.0 / - {#website-110}
1. Improved the appearance of photo cards.
2. Added fields for twin images and similar images.
3. Other enhancements.
4. Bug fixes.

### v1.0.2 / - {#website-102}
1. Added a full image preview feature when clicking on an image (on the Booru page).
2. Minor website and SEO tweaks.
3. Other fixes.


## CDN {#cdn}

### v2.2.4 / - {#cdn-224}
1. Resolved an issue where the server would crash when a client attempted to download a large file.
2. Updated dependencies to the latest version.

### v2.2.1 / - {#cdn-221}
1. Resolved an issue where a worker in the cluster would suddenly restart when handling too many requests at the same time.
2. Updated dependencies to the latest version.
3. Other fixes.