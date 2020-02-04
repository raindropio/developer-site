# Overview

This is the official documentation for Raindrop.io API. A reference to the functionality our public API provides with detailed description of each API endpoint, parameters, and examples.

Please note that you must [register your application](https://raindrop.io) and authenticate with OAuth when making requests. Before doing so, be sure to read our [Terms & Guidelines](terms-and-guidelines.md) to learn how the API may be used.

### Request and response format

API endpoints accept arguments either as url-encoded values for non-POST requests or as json-encoded objects encoded in POST request body with `Content-Type: application/json` header.

Where possible, the API strives to use appropriate HTTP verbs for each action.

| Verb | Description |
| :--- | :--- |
| GET | Used for retrieving resources. |
| POST | Used for creating resources. |
| PUT | Used for updating resources, or performing custom actions. |
| DELETE | Used for deleting resources. |

This API relies on standard HTTP response codes to indicate operation result. The table below is a simple reference about the most used status codes:

| Status code | Description |
| ---: | :--- |
| 200 | The request was processed successfully. |
| 204 | The request was processed successfully without any data to return. |
| 4xx | The request was processed with an error and should not be retried unmodified as they won’t be processed any different by an API. |
| 5xx | The request failed due to a server error, it’s safe to retry later. |

All `200 OK` responses have the `Content-type: application/json` and contain a JSON-encoded representation of one or more objects.

Payload of POST requests has to be JSON-encoded and accompanied with `Content-Type: application/json` header.

### Rate Limiting <a id="rate-limiting"></a>

For requests using OAuth, you can make up to 120 requests per minute per authenticated user.

You can check the returned HTTP headers of any API request to see your current per minute rate limit status:

```bash
HTTP/1.1 200 OK
Status: 200 OK
X-RateLimit-Limit: 120
X-RateLimit-Remaining: 59
X-RateLimit-Reset: 1392321600
```



