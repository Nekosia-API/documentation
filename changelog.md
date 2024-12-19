[//]: # (Title: Changelog - Nekosia API Docs)
[//]: # (Description: Detailed version history of Nekosia API, including updates, new features, and compatibility notes.)
[//]: # (Tags: changelog, changelogs, nekosia changelog, nekosia api changelog, nekosia api version history, nekosia version history, nekosia api docs changelog, version history, api updates, nekosia updates)
[//]: # (Canonical: changelog)
[//]: # (Creation date: 2024-07-29)
[//]: # (Last update: 2024-12-19)
[//]: # (Contributors: N/A)

# Introduction {#introduction}
Nekosia, like Booru, is continuously developed, with each new version introducing new features, significant fixes, and numerous improvements.
To ensure complete transparency and understanding of the changes made, we have prepared a detailed version history of the API.
This document contains detailed descriptions of changes, release dates, and backward compatibility information, allowing users to easily track progress and new features.

# Version History {#version-history}
Using semantic versioning ([learn more](https://nekosia.cat/documentation?page=introduction)) enables tracking changes and updates in a clear and intuitive way.
This ensures that users can always stay up to date with the latest functionalities and changes.
Below is the version history of the API, along with descriptions of the introduced changes and their release dates.


## API v1 {#v1}

### 2024-12-19 {#api-v1-2024-12-19}
1. The required length of the `id` parameter was changed to `<4`. Now: `< 4 || > 128`
2. Updated dependencies.

### 2024-12-16 {#api-v1-2024-12-16}
1. Updated dependencies.
2. Other fixes.

### 2024-11-12 {#api-v1-2024-11-12}
1. Updated `/api/v1/tags`.

### 2024-11-06 {#api-v1-2024-11-07}
1. The `images` field has been removed from the API responses and replaced by `count`.

### 2024-11-06 {#api-v1-2024-11-06}
1. The `identifier` field has been removed from API responses.
2. An `images` field has been added to API responses to show the number of filtered images.
3. `shadow` has been replaced with `nothing`, which serves the same purpose. Click [here](https://nekosia.cat/documentation?page=api-endpoints#filters) for more information.
4. The script managing tag filters has been restructured.
5. Further quality improvements have been implemented.

### 2024-10-04 {#api-v1-2024-10-04}
1. Updated tags.
2. Added `/api/v1/tags`.
3. Updated dependencies.

### 2024-09-07 {#api-v1-2024-09-07}
1. Added a new `rating` parameter for `/images`. The default rating in every response is `safe`.
2. The `key` field in the JSON response can now be `undefined`.
3. Minor adjustments were made.

### 2024-08-19 {#api-v1-2024-08-19}
1. Released the official [nekosia.js](https://www.npmjs.com/package/nekosia.js) module.
2. Website and documentation improvements.
3. Created the `tos.md` document.

### 2024-07-29 {#api-v1-2024-07-29}
- **Initial API + Booru Release**
  - Introduction of basic API functions, enabling full utilization of Nekosia's capabilities.
  - Creation of the official Booru.
  - Availability of complete online documentation, allowing users to easily familiarize themselves with new features and their applications.


## Website {#website}

### v1.2.2 {#website-122}
1. Updated dependencies to the latest version.
2. Small fixes.

### v1.2.1 {#website-121}
1. Resolved issues related to voting functionality.
2. UI improvements.

### v1.2.0 {#website-120}
1. Resolved issues related to voting functionality.
2. Removed specific data caching in booru that had no impact on backend performance.
3. Reset all statistics and votes.
4. Improved responsiveness and made slight UI enhancements in booru.
5. Added the ability to vote on images from their full view.
6. General performance and quality improvements.

### v1.1.4 {#website-114}
1. Bugfixes.

### v1.1.2 {#website-112}
1. Slightly improved the color scheme of profile tabs on Booru.
2. Corrected sentences.
3. Updated all npm modules.
4. Implemented various quality improvements and enhancements.

### v1.1.0 {#website-110}
1. Improved the appearance of photo cards.
2. Added fields for twin images and similar images.
3. Other enhancements.
4. Bug fixes.

### v1.0.2 {#website-102}
1. Added a full image preview feature when clicking on an image (on the Booru page).
2. Minor website and SEO tweaks.
3. Other fixes.