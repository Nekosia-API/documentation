[//]: # (Title: API Endpoints - Nekosia API Docs)
[//]: # (Description: Explore Nekosia's API documentation for seamless access to diverse images and related information. Find detailed descriptions of each endpoint, session management, and more.)
[//]: # (Tags: nekosia, api, nekosia api, api endpoints, api documentation, image access, session management, image tags, API versions, base URL, category tags, shadow category, API sessions)
[//]: # (Canonical: api-endpoints)
[//]: # (Creation date: 2024-07-29)
[//]: # (Last update: 2024-12-11)
[//]: # (Contributors: N/A)

# API Endpoints Overview {#api-endpoints-overview}
Nekosia API offers various endpoints that provide access to a wide range of images and related information. Below is a list of all available endpoints along with a brief description of their functions.

It is also worth familiarizing yourself with the session mechanism, which allows for tracking displayed images for users, helping to avoid showing duplicate images.

## Available API Versions {#available-api-versions}
Click [here](https://nekosia.cat/documentation?page=introduction#api-versions) to see the list of available API versions.

## Base URL Information {#base-url}
All API requests should be directed to the base URL [`api.nekosia.cat/api/v1`](https://api.nekosia.cat/api/v1). This URL serves as the foundation for all endpoint calls within the API.

## Tags and categories {#tags-and-categories}
### Main categories {#main-categories}
`catgirl`, `foxgirl`, `wolf-girl`, `animal-ears`, `tail`, `tail-with-ribbon`, `tail-from-under-skirt`<br>
`cute`, `cuteness-is-justice`, `blue-archive`, `girl`, `young-girl`, `maid`, `maid-uniform`, `vtuber`, `w-sitting`, `lying-down`, `hands-forming-a-heart`, `wink`, `valentine`, `headphones`<br>
`thigh-high-socks`, `knee-high-socks`, `white-tights`, `black-tights`, `heterochromia`, `uniform`, `sailor-uniform`, `hoodie`, `ribbon`, `white-hair`, `blue-hair`, `long-hair`, `blonde`, `blue-eyes`, `purple-eyes`

### Other categories {#other}
`swimwear`, `swimsuit`, `bikini`, `sea`, `swim-ring`<br>
*Ensure that these photos are appropriate for your project and adhere to the platform's guidelines where you plan to publish them. Don't worry, all the photos are SFW (Safe for Work, with no adult content).*

### More tags {#tags}
- You can find the full list of tags on the [Booru website](https://nekosia.cat/booru/tags).
- Endpoint with all tags, anime titles, and characters: [`/tags`](https://api.nekosia.cat/api/v1/tags)


# GET /images/:category {#get-image-category}
This endpoint allows you to fetch random images from a selected category.

## Parameters {#parameters}
> `/images/:category?count={int}&additionalTags={string}&blacklistedTags={string}&rating={string}`
- `:category` - Check the available tags on [our Booru page](https://nekosia.cat/booru/tags). Each image is assigned to one main category.
- `?count` (default: `1`) - The number of images to fetch (default: 1, maximum: 48). The higher the number, the longer the server response time (in milliseconds).
- `&additionalTags` - Additional tags to include when searching for images.
- `&blacklistedTags` - Tags to exclude from the search results.
- `&rating` (default: `safe`) - Image rating: `safe` or `questionable`.

## Response Structure {#response-structure}
```json
{
    "success": Boolean,
    "status": Int,
    "key": undefined || String,
    "count": Int,
    "id": String,
    "colors": { "main": "#Hex", "palette": ["#Hex1", "#Hex2", "#Hex3", "#Hex4", "#Hex5", "#Hex6", "#Hex7", "#Hex8", "#Hex9", "#Hex10", "#Hex11", "#Hex12", "#Hex13", "#Hex14"] },
    "image": {
        "original": { "url": String, "extension": String },
        "compressed": { "url": String, "extension": String }
    },
    "metadata": { "original": { "width": Int, "height": Int, "size": Int, "extension": String }, "compressed": { "width": Int, "height": Int, "size": Int, "extension": String } },
    "category": String,
    "tags": [String, String, String, String, String...],
    "rating": "safe" || "questionable",
    "anime": { "title": String || null, "character": String || null },
    "source": { "url": String || null, "direct": String || null },
    "attribution": { "artist": { "username": String || null, "profile": String || null }, "copyright": String || null }
}
```

## Example Request {#example-request-1}
> **GET** /images/**cute**?**count**=4&**additionalTags**=white-hair,uniform&**blacklistedTags**=short-hair,sad,maid


## Filters {#filters}
Categories (`:category`) are essentially tags, but with additional filters applied to ensure content safety.
These filters protect users from potentially inappropriate content and ensure compliance with our policy.
Therefore, if you request catgirl images (`/images/catgirl`), you will never receive anime girl images in swimsuits, for example.

### How to Bypass Filters? {#bypass-filters}
The Nekosia API offers a special category named `nothing`, which differs in both **its** operation and purpose from standard categories.
Using this category allows you to retrieve images randomly based **only** on user-specified tags, without applying the additional safety filters that are ALWAYS assigned to each category.

The `nothing` category provides complete freedom in content selection, which is particularly useful when a user wants unrestricted access to images without the default constraints.
This means that no automatic filter, which might block some images due to their potentially inappropriate nature, will be applied.
However, you **must** still specify whether you want images with a `safe` rating (default) or `questionable`. The API does not offer (and never will) `nsfw` images.

### Important {#bypass-filters-important}
Keep in mind that bypassing filters means that the full responsibility for the safety and appropriateness of displayed content rests solely with you.

### Example Request {#bypass-filters-example}
> **GET** /images/**nothing**?**count**=3&**additionalTags**=cat-ears,wolf-ears,wolf-ears&**blacklistedTags**=dog-ears
>  <br><br>
> `:category` - Must be set to `nothing`.<br>
> `additionalTags` - Tags to include in the image search. This is a key parameter for this category.


## Sessions {#sessions}
The API supports a session mechanism, which allows for tracking displayed images for users. This way, you can avoid displaying duplicate images.
Sessions can be identified by the user's IP address or a unique session identifier (e.g., an external system user ID, such as Discord).

### Types of Sessions {#session-types}
- `ip` - Session identified based on the user's IP address. This is useful when you do not have a unique user identifier.
- `id` - Session identified based on a unique user identifier passed in the `id` parameter. This can be, for example, a specific person's ID on Discord.

### Session Parameters {#session-parameters}
- `session` - Type of session (`ip` or `id`).
    - `ip` - Session identified based on the user's IP address.
    - `id` (recommended) - Session identified based on a unique user identifier.
- `id` - Unique user identifier if `session` is set to `id`. Otherwise, the parameter is ignored. The identifier must meet the following conditions:
    - Length of 6 to 128 characters.
    - No special characters such as: `!@#$%^&*()_+{}|:"<>?`

### Example Requests {#session-example-requests}
1. Session identified based on the IP address:
   > **GET** /images/catgirl?**session**=ip&**additionalTags**=foxgirl,wolf-girl,tail&**blacklistedTags**=dog-girl

2. Session identified based on a unique user identifier (e.g., from Discord):
   > **GET** /images/catgirl?**session**=id&**id**=437808476106784770&**additionalTags**=foxgirl,wolf-girl,tail&**blacklistedTags**=dog-girl

### Important Notes {#session-important-notes}
1. **Uniqueness of IP-based sessions**:  
   IP-based sessions may not be fully unique, especially in shared networks.

2. **Uniqueness of session identifiers**:  
   Session identifiers (`id`) should be sufficiently long and unique to ensure session uniqueness. Using unique identifiers such as external system user IDs (e.g., Discord) ensures precise session tracking and avoids image duplication.

3. **Session storage time**:  
   Sessions are stored for approximately 8 days, after which they are automatically deleted.

4. **Resetting sessions**:  
   If the user views all available images from a given category, the system automatically resets the session for that user, allowing random images to be displayed again.

5. **Security and privacy**:  
   Session identifiers and IP addresses are stored with the highest standards of security and privacy. This data is used solely for tracking displayed images and is not shared with third parties.

### Use Cases {#session-use-cases}
- `session=ip`: Can be used in cases where the user is not logged in, when the service does not offer a login feature, or when there is no way to identify a specific user.
- `session=id`: Recommended for example for Discord bots. With this solution, the user will never encounter duplicate images.


# GET /getImageById/:id {#get-by-image-id}
Retrieve details about a specific image.

## Example Request {#example-request-2}
> **GET** /getImageById/66bc6b7481a59a1cf2c79db5

## Via curl {#via-curl}
```bash
curl https://api.nekosia.cat/api/v1/getImageById/66bc6b7481a59a1cf2c79db5
```


# GET /tags {#tags-endpoint}
Retrieve a full list of all tags, anime titles, and characters.