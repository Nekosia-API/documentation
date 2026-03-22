[//]: # (Title: Introduction - Nekosia API Docs)
[//]: # (Desc: Nekosia is a free Neko API for integrating anime content into your projects. With cute anime images and a dedicated Booru, Nekosia has everything you need!)
[//]: # (Tags: introduction, nekosia api introduction, nekosia api docs introduction, nekosia api overview, nekosia api summary, nekosia api guide, nekosia api documentation, nekosia api intro)
[//]: # (Canonical: introduction)
[//]: # (Creation date: 2024-07-29)
[//]: # (Last update: 2026-03-22)

# Introduction {#introduction}
Welcome to the Nekosia API documentation! Here you will find detailed information about the API interface, including descriptions of available endpoints, request methods, and response formats.

The Nekosia API follows a `RESTful` architecture, meaning all operations are performed according to REST principles.
Requests and responses are transmitted in JSON format, making data integration and processing easier.

The documentation also includes code examples and use cases to help you get started quickly.
Whether you're a developer creating a new application or an integrator looking for an efficient solution, you'll find all the necessary information here.


## Important to Understand {#important}
- **Variety of Content:**
  The Nekosia API provides access to not only neko images but also other categories, offering a wide range of available content.

- **Own Booru:**
  Nekosia offers its own booru.

- **Integration with Booru:**
  The booru is integrated with the API. Users can submit requests to the booru, such as tagging changes or content improvements. After verification by moderators, updated data will be available in the API responses.

- **Avoiding Duplicates in Responses:**
  The API includes session mechanisms (identified by IP address or random identification key) to avoid duplicate responses. This way, Users can receive different images depending on the specific session.

- **No API Key Required:**
  The API does not require authorization keys or tokens, so you don't need to register to use it. This increases accessibility and convenience.

- **Image Hosting:**
  All images are hosted on the Nekosia server, and their availability is ensured by the API, guaranteeing constant access to resources.

- **Safe Content:**
  The API is focused on SFW content. All images are appropriate for general audiences. See the [Content Ratings](https://nekosia.cat/documentation?page=introduction#content-ratings#content-ratings) section below for details.

- **Uptime:**
  The API and website are monitored by an external system 24/7, ensuring availability at all times. Users can use the Service at any time without interruptions. In case of planned maintenance, Users will be informed in advance.

- **User Collaboration:**
  Any comments, suggestions, or issues related to the API can be reported on the Discord server or via email. We are open to feedback and eager to collaborate with Users to further improve our services.

- **Free Usage:**
  The API is free to use, meaning there are no charges or usage restrictions.

> These are just a few key points to understand before starting to use the API. More information on the available features can be found on the [official website](https://nekosia.cat).
> We encourage you to read the full documentation to fully utilize the capabilities offered by the API. Good luck!


## Image Classification {#content-ratings}
Each image in the Nekosia database has an assigned content rating.
It defines the nature of the image and determines whether, and in what context, it can be served via the API. Keep in mind that not all images available on the Booru are served through the API.

The API supports the following classifications:

### ✅ Safe {#rating-safe}
The default classification. Includes images that are fully appropriate for all age groups and all types of use (e.g. applications, Discord bots, websites).

These are mainly aesthetic anime images, usually depicting cute characters in full clothing, without fan service elements.
They do not contain exposed body parts, suggestive poses, or ambiguous details.

This is the largest and most recommended category, containing over a thousand images.

### 🤔 Suggestive {#rating-suggestive}
A category that includes images that are slightly more daring than `safe`, but still do not contain nudity or explicitly sexual content.
It is significantly smaller (fewer than 100 images).

It may include, for example:
- swimwear,
- more revealing outfits,
- more visible thighs,
- less neutral poses.

The `suggestive` category is never returned by default by the API. To include it, you must use the parameter: `&rating=suggestive`.
When the `rating` parameter is set to `suggestive`, images from this category are prioritized, but `safe` images may still appear in the results.


## Semantic Versioning {#semver}
The Nekosia API uses semantic versioning 2.0.0. Each version consists of three numbers `MAJOR`.`MINOR`.`PATCH`. The versioning rules are as follows:
- `MAJOR (x)` - increased when introducing changes that are not backward compatible. Examples include removing or modifying existing features in a way that requires Users to adjust their code.
- `MINOR (y)` - increased when adding new features that are backward compatible. Examples include adding new endpoints or configuration options that do not affect existing functionalities.
- `PATCH (z)` - increased when making fixes, bug corrections, and security improvements. Such changes are usually minor and do not affect backward compatibility.

### Versioning Examples {#semver-examples}
- Version `1.0.0` indicates the first official release of the API.
- Version `1.1.0` indicates that new features compatible with version `1.0.0` have been added. An example might be the addition of a new data retrieval endpoint.
- Version `1.1.1` indicates that bug fixes or security improvements have been made to version `1.1.0`. For example, fixing a user authorization bug.
- Version `2.0.0` indicates that changes not compatible with version `1.1.1` have been introduced. An example might be removing or changing existing features that require Users to adjust their code.

### Available API Versions {#api-versions}
The currently available API version is `v1`, which is the only version. Future versions containing new features and improvements are planned.
In case of changes, the documentation will be updated to reflect the latest changes. Users will also be notified via the Discord server and the Service website.

| API version                  | Released on | Last update                                                       | Recommended | Beta? |
|------------------------------|-------------|:------------------------------------------------------------------|-------------|-------|
| <div align="center">v1</div> | 2024-07-29  | [Click here](https://nekosia.cat/documentation?page=changelog#v1) | ✔️          | ✅     |

### Changelog {#changelog}
You will find it in a separate document [Changelog](https://nekosia.cat/documentation?page=changelog). This document contains detailed information about changes, release dates, and backward compatibility.


## Reporting Issues {#reporting-issues}
If you encounter any issues related to the API, documentation errors, or have improvement suggestions, please contact us!
We are open to all feedback and happy to help resolve any issues.


## Contact and Support {#contact-support}
If you have any questions, need assistance, or would like to report an issue, contact us on the Discord server or via email.
Our support team is ready to help you with any matters related to the Nekosia API.
We strive to respond to messages as quickly as possible to ensure you have the best experience using our service.
Moreover, on our Discord server, you'll find dedicated channels where you can get help from other users and participate in discussions about the development and future of Nekosia.


## Open Source {#open-source}
Currently, neither the website nor the API is available as open-source projects.
However, we plan to release the source code in the future, which will allow the community to actively contribute to the project's development, benefiting both us and all users.
We believe that open-sourcing will accelerate development and the introduction of innovative solutions, while also increasing transparency and trust in the project.
You can find Nekosia's public repositories [here](https://github.com/Nekosia-API).


## Credits and Support {#credits-support}
There is no requirement for attribution when using the Nekosia API.
However, if your project uses this solution, it would be appreciated if a link to the website [nekosia.cat](https://nekosia.cat) is included in the project description or if it's mentioned that the project uses the Nekosia API.

This gesture helps reach more users and supports the growth of the community.
Thank you for the support and for appreciating the work!


## Attribution {#attribution}
When using the API, it's important to credit the username of the author of a specific photo (if the API provides this information) in your project.
This can be done by including the author's name, for example, in the footer (in the case of Discord, in the embed footer).
It's also good practice to include a link to the author's profile (e.g., Pixiv) or the source of the photo to fully acknowledge the artist's work.


## Copyright {#copyright}
The Nekosia API respects the copyrights of all images used, which belong to their rightful owners.
We comply with copyright and intellectual property regulations.

We understand the importance of protecting these rights, so we strive to act in accordance with applicable regulations.
Each image used by the API includes source and author information in its metadata ([EXIF](https://www.npmjs.com/package/exiftool-vendored)).

If you notice any copyright violations, please contact us, so we can take appropriate action to resolve the issue immediately.
Thank you for your understanding and cooperation.<br><br>

The graphics used on this website [nekosia.cat](https://nekosia.cat) are available for review on the [Credits - Nekosia API](https://nekosia.cat/credits) page.
