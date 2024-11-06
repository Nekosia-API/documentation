[//]: # (Title: Getting Started - Nekosia API Docs)
[//]: # (Description: Introductory guide for Nekosia API, covering setup, sending requests, and handling errors.)
[//]: # (Tags: getting started, nekosia api getting started, nekosia api docs, api introduction, api guide, nekosia tutorial, api setup, api integration, api examples)
[//]: # (Canonical: getting-started)
[//]: # (Creation date: 2024-07-29)
[//]: # (Last update: 2024-11-06)
[//]: # (Contributors: N/A)

# Getting Started {#getting-started}
1. **Familiarize yourself with the documentation**:  
   Browse the available endpoints, request methods, and response formats to understand how the API works. Remember to handle errors and exceptions correctly in your code.

2. **Sending your first request**:
   - **HTTP Method**: GET
   - **Endpoint**: `/api/v1/images/catgirl`
   - **Description**: Fetches a random anime image.
   - **Sample Request**:
     ```bash
     // Linux
     curl "https://api.nekosia.cat/api/v1/images/catgirl" | jq

     // Windows (PowerShell)
     curl -X GET "https://api.nekosia.cat/api/v1/images/catgirl" -H "Content-Type: application/json" | ConvertFrom-Json | ConvertTo-Json -Depth 10
     ```

3. **Sample response**:
   ```json
   {
      "success": true,
      "status": 200,
      "count": 1,
      "id": "66a77347a4b979c761eb0cde",
      "colors": {
         "main": "#E7C9CF",
         "palette": ["#E8DFE7", "#433740", "#E3495B", "#8F6166", "#100B10", "#A4AECB", "#F99E37", "#695054", "#4D537C", "#310E13", "#8485AF", "#CE7D81", "#3D1126", "#6E6D6B"]
      },
      "image": {
         "original": { "url": "https://cdn.nekosia.cat/images/catgirl/66a77347a4b979c761eb0cde.png", "extension": "png" },
         "compressed": { "url": "https://cdn.nekosia.cat/images/catgirl/66a77347a4b979c761eb0cde-compressed.jpg", "extension": "jpeg" }
      },
      "metadata": {
         "original": { "width": 1536, "height": 2304, "size": 4431989, "extension": "png" },
         "compressed": { "width": 1280, "height": 1920, "size": 698945, "extension": "jpeg" }
      },
      "category": "catgirl",
      "tags": ["catgirl", "animal-ears", "cat-ears", "tail", "cute", "young-girl", "cuteness-is-justice", "thighs", "white-thigh-high-socks", "thigh-high-socks", "red-ribbon", "long-hair"],
      "rating": "safe",
      "anime": { "title": null, "character": null },
      "source": {
         "url": "https://www.pixiv.net/en/artworks/112464629",
         "direct": "https://i.pximg.net/img-original/img/2023/10/11/19/15/45/112464629_p0.png"
      },
      "attribution": {
         "artist": { "username": "AutoINS", "profile": "https://www.pixiv.net/en/users/87833254" },
         "copyright": "Copyright 2023 © by AutoINS. All Rights Reserved."
      }
   }
   ```

4. **Integration with your app**:  
   Use the above sample request and response to integrate the API with your application.
   You can use official wrappers or HTTP libraries available in your chosen programming language, such as `axios` (or `node-fetch`) for JavaScript, `requests` for Python, or `HttpClient` (or `WebClient`) for C#.

5. **Error handling**:  
   Always check the response status to handle potential errors. Sample error response for a request `(GET /api/v1/images/catgirl-test)`:
   ```json
   {
      "success": false,
      "status": 400,
      "message": "No images found for the tags you specified."
   }
   ```


# Examples {#examples}
Below you will find detailed implementation examples using various programming languages and HTTP libraries. Each example includes code to fetch a random anime image from the Nekosia API.

## Node.js: Axios {#nodejs-axios}
Sample implementation in [Node.js](https://nodejs.org) using the [axios](https://www.npmjs.com/package/axios) library to fetch a random image from the API:

```js
const axios = require('axios');

const fetchNekoImage = async () => {
   try {
      const res = await axios.get('https://api.nekosia.cat/api/v1/images/catgirl');
      const json = res.data;

      console.log(json.image.original.url);
   } catch (err) {
      console.error(err.stack);
   }
};

fetchNekoImage();
```

When using the `axios` library, there is no need to manually check the response status, as `axios` automatically handles HTTP errors.
If an error occurs, `axios` will return a complete error object that can be handled in the `catch` block.
This allows the developer to focus on implementing error handling logic rather than worrying about the specifics of checking the HTTP response.
The error object contains information such as status code, error message, and details of the request and response, making it easier to debug and diagnose issues.

## Demo {#demo}

<div style="display: flex;">
    <div style="flex: 1; padding-right: 20px;">
        <div class="code-block">
            <button onclick="fetchNekoImage()">GET api.nekosia.cat/api/v1/images/catgirl</button>
        </div>
        <pre style="margin-top: 10px;"><code class="hljs language-json" id="response-container">Waiting for user to click the button...</code></pre>
    </div>
    <div style="flex: 1; display: flex; justify-content: center; align-items: center;">
        <img id="neko-image" style="max-width:100%;display:none;cursor:pointer;" onclick="openImageInNewTab()">
    </div>
</div>