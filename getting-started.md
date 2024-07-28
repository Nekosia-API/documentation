[//]: # (Title: Getting Started - Nekosia API Docs)
[//]: # (Description: Introductory guide for Nekosia API, covering setup, sending requests, and handling errors.)
[//]: # (Tags: getting started, nekosia api getting started, nekosia api docs, api introduction, api guide, nekosia tutorial, api setup, api integration, api examples)
[//]: # (Canonical: getting-started)
[//]: # (Creation date: 2024-07-28)
[//]: # (Last update: 2024-07-28)
[//]: # (Contributors: Sefinek)

# Getting Started {#getting-started}
1. **Familiarize Yourself with the Documentation**:  
   Browse the available endpoints, request methods, and response formats to understand how the API works. Remember to handle errors and exceptions correctly in your code.

2. **Sending Your First Request**:
   - **HTTP Method**: GET
   - **Endpoint**: `/api/v1/images/catgirl`
   - **Description**: Fetches a random anime image.
   - **Sample Request**:
     ```bash
     curl -X GET "https://api.nekosia.cat/api/v1/images/catgirl" -H "Content-Type: application/json"
     ```

3. **Sample Response**:
   <details>
      <summary>Click here to see.</summary>
   ```json
   {
      "success": true,
      "status": 200,
      "key": null,
      "count": 1,
      "id": "66a0373e653c7ad0d46cbf23",
      "colors": { "main": "#DECBC9", "palette": ["#DDCAC8", "#A37976", "#301D23", "#7E4F4A", "#8E645B", "#F9F1EA", "#C19E9D", "#BA948B", "#C5ACA3", "#BAB0B2", "#90A9B3", "#5BA5C5", "#52799E", "#7C5C74"] },
      "image": {
         "original": { "url": "http://127.0.0.1:7843/images/catgirl/66a0373e653c7ad0d46cbf23.jpg", "bytes": 2558328 },
         "compressed": { "url": "http://127.0.0.1:7843/images/catgirl/66a0373e653c7ad0d46cbf23-compressed.jpg", "bytes": 715895 }
      },
      "bytes": { "original": { "width": 3908, "height": 5661, "size": 2558328, "extension": "jpeg" }, "compressed": { "width": 1280, "height": 1854, "size": 715895, "extension": "jpeg" } },
      "category": "catgirl",
      "tags": ["catgirl", "animal-ears", "maid", "maid-uniform"],
      "rating": "safe",
      "anime": { "title": null, "character": null },
      "source": { "url": "https://www.pixiv.net/en/artworks/120537148", "direct": "https://i.pximg.net/img-original/img/2024/07/15/00/26/23/120537148_p0.jpg" },
      "attribution": { "artist": { "username": "フィア", "profile": "https://www.pixiv.net/en/users/12173021" }, "copyright": "Copyright 2024 © by フィア. All Rights Reserved." }
   }
   </details>

4. **Integration with Your Application**:  
   Use the above sample request and response to integrate the API with your application.
   You can use official wrappers or HTTP libraries available in your chosen programming language, such as `axios` (or `node-fetch`) for JavaScript, `requests` for Python, or `HttpClient` (or `WebClient`) for C#.

5. **Error Handling**:  
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
        <pre style="margin-top: 10px;"><code class="hljs language-json" id="response-container">Waiting for user to click the button...<br>If this doesn't work, try refreshing the page.</code></pre>
    </div>
    <div style="flex: 1; display: flex; justify-content: center; align-items: center;">
        <img alt="Neko image" id="neko-image" style="max-width: 98%; display: none; cursor: pointer;" onclick="openImageInNewTab()">
    </div>
</div>