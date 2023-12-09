# Getting Started

<b>Get your API key and start generating images and gifs in minutes.</b>

[![button]( https://img.shields.io/badge/Get%20Your%20API%20Key-grey?style=for-the-badge&logo=javascript)](https://your-link-here.com)

---

### Table of Contents

* [Using The API](#using-the-api)
* [Media Width and Height](#media-width-and-height)
* [Support](#support)

---

## Using The API

### Authentication

* You need to pass your API key as a `authorization` header in all the requests. You can get your API key from the [dashboard](https://your-link-here.com).
* Treat your API key as a password. Do not share it with anyone. If you think your API key has been compromised, you can delete it from the dashboard and create a new one.

### Creating a Image

Make a HTTP request to the following endpoint to create a image.

```
POST https://api.medify.com/image
```

<b>Parameters</b>

| Parameter | Type | Description |
| :--- | :--- | :--- |
| `html` <span style="color:red">*</span> | `string` | HTML code to be converted to image. You can send HTML snippets (`<div>...</div>`) or full HTML documents (`<html>...</html>`) |
| `css` | `string` | CSS code to be applied to the HTML. |
| `width` | `number` | Width of the viewport in pixels. |
| `height` | `number` | Height of the viewport in pixels. |
| `quality` | `number` | Quality of the image. Can be a number between 0 and 100. |
| `template` <span style="color:red">*</span> | `string` | ID of the template to be used. |
| `variables` | `object` | Variables to be used in the template. |
| `url` <span style="color:red">*</span> | `string` | URL of the webpage to be converted to image. |

| Required Parameters | Description |
| :--- | :--- |
| `html`, `url`, or `template` | You need to send either `html`, `url` or `template` parameter. |
| `variables` | You need to send `variables` parameter if you are using a template. |

<b>Example Response</b>

`STATUS: 200 OK`

```json
{
    "url": "https://htgf.s3.amazonaws.com/9tv83-1698983654151.png"
}
```

`STATUS: 401 Unauthorized`

```json
{
    "message": "Invalid Request"
}
```

`STATUS: 429 Too Many Requests`

```json
{
    "message": "You have exhausted your plan limit"
}
```

### Creating a GIF

Make a HTTP request to the following endpoint to create a GIF.

```
POST https://api.medify.com/gif
```

<b>Parameters</b>

| Parameter | Type | Description |
| :--- | :--- | :--- |
| `html` <span style="color:red">*</span> | `string` | HTML code to be converted to GIF. You can send HTML snippets (`<div>...</div>`) or full HTML documents (`<html>...</html>`) |
| `css` | `string` | CSS code to be applied to the HTML. |
| `width` | `number` | Width of the viewport in pixels. |
| `height` | `number` | Height of the viewport in pixels. |
| `quality` | `number` | Quality of the GIF. Can be a number between 0 and 100. |
| `duration` | `number` | Duration of the GIF in seconds. |
| `template` <span style="color:red">*</span> | `string` | ID of the template to be used. |
| `variables` | `object` | Variables to be used in the template. |
| `url` <span style="color:red">*</span> | `string` | URL of the webpage to be converted to GIF. |

| Required Parameters | Description |
| :--- | :--- |
| `html`, `url`, or `template` | You need to send either `html`, `url` or `template` parameter. |
| `variables` | You need to send `variables` parameter if you are using a template. |


<b>Example Response</b>

`STATUS: 200 OK`

```json
{
    "url": "https://htgf.s3.amazonaws.com/zry20-1698593673023.gif"
}
```

`STATUS: 401 Unauthorized`

```json
{
    "message": "Invalid Request"
}
```

`STATUS: 429 Too Many Requests`

```json
{
    "message": "You have exhausted your plan limit"
}
```
### Getting a Image/GIF

Make a HTTP request to the following endpoint to get a image.

```
GET https://media.medify.com/:id
```

<b>Parameters</b>

After creating a image/gif, you will get a `url` in the response. You can use this `url` to fetch the image/gif. It's automatically cached and optimized via a CDN.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| `id` <span style="color:red">*</span> | `string` | ID of the image/gif to be fetched. |

<b>File Formats</b>

Images are served in the following formats:

* `png`
* `jpg`
* `webp`

By default, the API will serve the image in `png` format if not format is being specified. You can specify the format in the URL.

```
GET https://media.medify.com/:id.png
```

```
GET https://media.medify.com/:id.jpg
```

```
GET https://media.medify.com/:id.webp
```

### Deleting a Image/GIF

Make a HTTP request to the following endpoint to delete a image/gif.

```
DELETE https://api.medify.com/:id
```

<b>Parameters</b>

| Parameter | Type | Description |
| :--- | :--- | :--- |
| `id` <span style="color:red">*</span> | `string` | ID of the image/gif to be deleted. |

<b>Example Response</b>

`STATUS: 200 OK`

```json
{
    "message": "deleted successfully"
}
```

### Creating a Template

Make a HTTP request to the following endpoint to create a template.

```
POST https://api.medify.com/template
```

<b>Parameters</b>

| Parameter | Type | Description |
| :--- | :--- | :--- |
| `html` <span style="color:red">*</span> | `string` | HTML code to be converted to image. The variables in the HTML should be wrapped in double curly braces. For example,  `<div>Hello {{name}}</div>` |
| `name` | `string` | Name of the template. |
| `width` | `number` | Default width of the viewport in pixels. Width can be overridden while creating a image/gif. |
| `height` | `number` | Default height of the viewport in pixels. Height can be overridden while creating a image/gif. |


<b>Example Response</b>

`STATUS: 200 OK`

```json
{
    "template": {
        "id": "9tv83",
        "name": "My Template",
        "html": "<div>Hello {{name}}</div>",
        "width": 1200,
        "height": 630,
        "createdAt": "2021-04-01T12:00:00.000Z",
        "updatedAt": "2021-04-01T12:00:00.000Z"
    }
}
```

### Updating a Template

Make a HTTP request to the following endpoint to update a template.

```
PUT https://api.medify.com/template/:id
```

<b>Parameters</b>

| Parameter | Type | Description |
| :--- | :--- | :--- |
| `id` <span style="color:red">*</span> | `string` | ID of the template to be updated. |
| `html` | `string` | HTML code to be converted to image. The variables in the HTML should be wrapped in double curly braces. For example,  `<div>Hello {{name}}</div>` |
| `name` | `string` | Name of the template. |
| `width` | `number` | Default width of the viewport in pixels. Width can be overridden while creating a image/gif. |
| `height` | `number` | Default height of the viewport in pixels. Height can be overridden while creating a image/gif. |

<b>Example Response</b>

`STATUS: 200 OK`

```json
{
    "template": {
        "id": "9tv83",
        "name": "My Template",
        "html": "<div>Hello {{name}}</div>",
        "width": 1200,
        "height": 630,
        "createdAt": "2021-04-01T12:00:00.000Z",
        "updatedAt": "2021-04-01T12:00:00.000Z"
    }
}
```

### Deleting a Template

Make a HTTP request to the following endpoint to delete a template.

```
DELETE https://api.medify.com/template/:id
```

<b>Parameters</b>

| Parameter | Type | Description |
| :--- | :--- | :--- |
| `id` <span style="color:red">*</span> | `string` | ID of the template to be deleted. |

<b>Example Response</b>

`STATUS: 200 OK`

```json
{
    "message": "deleted successfully"
}
```



---

## Media Width and Height

We generate the image/gif by rendering the HTML in a instance of Chrome in one of our servers. The width and height of the viewport is automatically calculated by evaluating the outermost element in the HTML. You can override the width and height by passing the `width` and `height` parameters in the request.


### Example

```html
<div style = "height:500px; width:300px background-color:blue">
  
</div>

```

This image generated from the above HTML will be a blue rectangle of size `300px` x `500px`. We auto-crop the image to remove any extra whitespace.

Although, you can override the width and height by passing the `width` and `height` parameters in the request. This will not change the HTML, but will change the viewport size.

<img src="https://res.cloudinary.com/diroilukd/image/upload/v1702068271/Cphq3_jv8ftl.png" style="padding: 10px; border: 1px solid #ccc; background-color: #eeeefe;">

```json
{
    "html": "<div style = 'height:500px; width:300px background-color:blue'></div>",
    "width": 800,
    "height": 900
}
```

<img src="https://res.cloudinary.com/diroilukd/image/upload/v1702068271/Rt5h3_1701980470736_ory4th.png" style="padding: 10px; border: 1px solid #ccc; background-color: #eeeefe;">

This will make the viewport size `800px` x `900px`. The rendered image will be similar to how you see the HTML in the browser of size `800px` x `900px`.

---


## Creating media from a URL

You can also create media from a URL. We will fetch the HTML from the URL and render it in a instance of Chrome in one of our servers. It is better to provide the width and height of the viewport in this case. If you need to create image/gif of a certain part of webpage, you can use the `selector` parameter to specify the element to be captured.

```json
{
    "url": "https://www.wikipedia.org/",
    "width": 1200,
    "height": 630,
    "selector": ".central-featured"
}
```
<img src="https://res.cloudinary.com/diroilukd/image/upload/v1702116869/SJP03_sbuahn.png" style="padding: 10px; border: 1px solid #ccc; background-color: #eeeefe;">

<span style="color:red">*</span> We don't support URLs that require authentication. You can use our API to create media from a URL only if the URL is publicly accessible.

## Need Help?

If you need any help, feel free to reach out to us at [support@medify.com](mailto:support@medify.com)














