[//]: # (Title: API Endpoints - Nekosia Docs)
[//]: # (Description: Explore Nekosia's API documentation for seamless access to diverse images and related information. Find detailed descriptions of each endpoint, session management, and more.)
[//]: # (Tags: nekosia, api, nekosia api, api endpoints, api documentation, image access, session management, image tags, API versions, base URL, category tags, shadow category, API sessions)
[//]: # (Canonical: api-endpoints)
[//]: # (Creation date: 2024-07-29)
[//]: # (Last update: 2024-08-09)
[//]: # (Contributors: Sefinek)

# API Endpoints Overview {#api-endpoints-overview}
Nekosia API offers various endpoints that provide access to a wide range of images and related information. Below is a list of all available endpoints along with a brief description of their functions.

It is also worth familiarizing yourself with the session mechanism, which allows for tracking displayed images for users, helping to avoid showing duplicate images.

## Available API Versions {#available-api-versions}
Click [here](https://nekosia.cat/documentation?page=introduction#api-versions) to see the list of available API versions.

## Base URL Information {#base-url}
All API requests should be directed to the base URL: `https://nekosia.cat/api/v1`. This URL serves as the foundation for all endpoint calls within the API.

## Tags and categories {#tags-and-categories}
### Main categories {#main-categories}
`catgirl`, `foxgirl`, `wolf-girl`, `animal-ears`, `tail`, `tail-with-ribbon`, `tail-from-under-skirt`<br>
`cute`, `cuteness-is-justice`, `blue-archive`, `girl`, `young-girl`, `maid`, `maid-uniform`, `vtuber`, `w-sitting`, `lying-down`, `hands-forming-a-heart`, `wink`, `valentine`, `headphones`<br>
`thigh-high-socks`, `knee-high-socks`, `white-tights`, `black-thigs`, `heterochromia`, `uniform`, `sailor-uniform`, `hoodie`, `ribbon`, `white-hair`, `blue-hair`, `long-hair`, `blonde`, `blue-eyes`, `purple-eyes`

#### Other {#other}
`swimwear`, `swimsuit`, `bikini`, `sea`, `swim-ring`<br>
*Ensure that these photos are appropriate for your project and adhere to the platform's guidelines where you plan to publish them. Don't worry, all the photos are SFW (Safe for Work, with no adult content).*

### Tags {#tags}
You can find the full list of tags on the [Booru website](https://nekosia.cat/booru/tags).


# GET /images/:category {#get-image-category}
This endpoint allows you to fetch random images from a selected category.

## Parameters {#parameters}
> /images/:category?count={int}&additionalTags={string}&blacklistedTags={string}
- `:category` - Check available category tags [on our Booru page](https://nekosia.cat/booru/tags). Each image is assigned to one main category.
- `?count` - The number of images to fetch (default: 1, maximum: 48). The higher the number, the longer the server will take to respond (in milliseconds).
- `&additionalTags` - Additional [tags](https://nekosia.cat/booru/tags) to be included when searching for images.
- `&blacklistedTags` - [List of tags](https://nekosia.cat/booru/tags) to be excluded from the search results.

## Example Response {#example-response}
```json
{
    "success": Boolean,
    "status": Int,
    "key": String || null,
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
    "rating": safe || questionable || nsfw,
    "anime": { "title": String || null, "character": String || null },
    "source": { "url": String || null, "direct": String || null },
    "attribution": { "artist": { "username": String || null, "profile": String || null }, "copyright": String || null }
}
```

## Example Request {#example-request-1}
> GET /images/cute?count=4&additionalTags=white-hair,uniform&blacklistedTags=short-hair,sad,maid

## Error Responses {#example-error-response}
```json
{
  "success": false,
  "status": 400,
  "message": "Request missing category parameter."
}
```

## Shadow Category {#shadow}
Nekosia API offers a special `shadow` category, which differs from the others in its operation.
Using this category allows you to fetch random images only from those that match your selected tags.
This is a recommended solution if you do not want to limit yourself to the main categories only.

### Characteristics {#shadow-characteristics}
1. The `shadow` category requires additional tags to be provided in the `additionalTags` parameter, which are used for precise filtering of images.
2. When using `shadow`, the `additionalTags` parameter must be filled with appropriate tags. Note that some tags may be unavailable for safety reasons.

### Parameters {#shadow-parameters}
- `category` - Must be set to `shadow`.
- `count` - The number of images to fetch (default: 1, maximum: 48).
- `additionalTags` - The main tag to be included in the image search. This is crucial for this category.
- `blacklistedTags` - List of tags to be excluded.

### Example Request {#shadow-example-request}
```text
GET /images/shadow?count=3&additionalTags=catgirl,foxgirl,wolf-girl&blacklistedTags=dog-girl
```

The `shadow` category allows for precise image searches matching the selected criteria, offering a more personalized experience.

## Sessions {#sessions}
The API supports a session mechanism, which allows for tracking displayed images for users. This way, you can avoid displaying duplicate images.
Sessions can be identified by the user's IP address or a unique session identifier (e.g., an external system user ID, such as Discord).

### Types of Sessions {#session-types}
- `ip` - Session identified based on the user's IP address. This is useful when you do not have a unique user identifier.
- `id` - Session identified based on a unique user identifier passed in the `id` parameter. This can be, for example, a specific person's ID on Discord.

### Session Parameters {#session-parameters}
- `session` - Type of session (`ip` or `id`).
    - `ip` - Session identified based on the user's IP address.
    - `id` - Session identified based on a unique user identifier.
- `id` - Unique user identifier if `session` is set to `id`. Otherwise, the parameter is ignored. The identifier must meet the following conditions:
    - Length of 6 to 128 characters.
    - No special characters such as `!@#$%^&*()_+{}|:"<>?`.

### Example Requests {#session-example-requests}
1. Session identified based on the IP address:
   > **GET** /images/_catgirl_?**session**=ip&**additionalTags**=foxgirl,wolf-girl,tail&**blacklistedTags**=dog-girl

2. Session identified based on a unique user identifier (e.g., from Discord):
   > **GET** /images/_catgirl_?**session**=id&**id**=561621386569973783&**additionalTags**=foxgirl,wolf-girl,tail&**blacklistedTags**=dog-girl

### Important Notes {#session-important-notes}
1. **Uniqueness of IP-based sessions**:  
   IP-based sessions may not be fully unique, especially in shared networks.

2. **Uniqueness of session identifiers (id)**:  
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
```text
GET /getImageById/66bc6b7481a59a1cf2c79db5
```

## Via curl {#via-curl}
```bash
curl -X GET "https://api.nekosia.cat/api/v1/getImageById/66bc6b7481a59a1cf2c79db5" -H "Content-Type: application/json"
```