[//]: # (Title: Getting Started - Nekosia API Docs)
[//]: # (Description: Introductory guide for Nekosia API, covering setup, sending requests, and handling errors.)
[//]: # (Tags: getting started, nekosia api getting started, nekosia api docs, api introduction, api guide, nekosia tutorial, api setup, api integration, api examples)
[//]: # (Canonical: getting-started)
[//]: # (Creation date: 2024-07-29)
[//]: # (Last update: 2024-07-29)
[//]: # (Contributors: Sefinek)

# Getting Started {#getting-started}
1. **Familiarize yourself with the documentation**:  
   Browse the available endpoints, request methods, and response formats to understand how the API works. Remember to handle errors and exceptions correctly in your code.

2. **Sending your first request**:
   - **HTTP Method**: GET
   - **Endpoint**: `/api/v1/images/catgirl`
   - **Description**: Fetches a random anime image.
   - **Sample Request**:
     ```bash
     curl -X GET "https://api.nekosia.cat/api/v1/images/catgirl" -H "Content-Type: application/json"
     ```

3. **Sample response**:
   ```json
   {
      "success": true,
      "status": 200,
      "key": null,
      "count": 1,
      "id": "66aec7b2fbc807afa70f00df",
      "colors": { "main": "#D9CDD3", "palette": ["#35373F", "#8B4964", "#7D7E8B", "#E9E1E5", "#B68495", "#ACAEBA", "#CCADB4", "#846D61", "#C9A199", "#C6C5CF", "#4E738D", "#D2BEB9", "#52B5CA", "#4B8AB4"] },
      "image": {
         "original": { "url": "https://cdn.nekosia.cat/images/catgirl/66aec7b2fbc807afa70f00df.png", "extension": "png" },
         "compressed": { "url": "https://cdn.nekosia.cat/images/catgirl/66aec7b2fbc807afa70f00df-compressed.jpg", "extension": "jpeg" }
      },
      "metadata": { "original": { "width": 3086, "height": 4000, "size": 7901833, "extension": "png" }, "compressed": { "width": 1280, "height": 1659, "size": 378149, "extension": "jpeg" } },
      "category": "catgirl",
      "tags": ["catgirl", "schoolgirl", "cat-ears", "animal-ears", "tail", "cute", "young-girl", "white-hair", "uniform", "school-uniform", "school-girl", "twintails", "elementary-school-student", "heterochromia"],
      "rating": ""metadata":",
      "anime": { "title": null, "character": null },
      "source": { "url": "https://www.pixiv.net/en/artworks/90084095", "direct": "https://i.pximg.net/img-original/img/2021/05/25/12/02/02/90084095_p0.png" },
      "attribution": { "artist": { "username": "rucaco/るかこ", "profile": "https://www.pixiv.net/en/users/9155411" }, "copyright": "Copyright 2021 © by rucaco/るかこ. All Rights Reserved." }
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