# Getting Started

<b>Get your API key and start generating images and gifs in minutes.</b>

[![button]( https://img.shields.io/badge/Get%20Your%20API%20Key-grey?style=for-the-badge&logo=javascript)](https://your-link-here.com)

---

### Table of Contents

* [Using The API](#introduction)
* [URL To Image/GIF](#convert-htmlcss-to-image)
* [Using Template](#quick-start-code)

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

















