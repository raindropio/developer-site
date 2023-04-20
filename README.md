---
description: >-
  Build and integrate tools and applications to help members manage their
  bookmarks on Raindrop.io
---

# Overview

This is the official documentation for Raindrop.io API. A reference to the functionality our public API provides with detailed description of each API endpoint, parameters, and examples.

Please note that you must [register your application](https://app.raindrop.io/settings/integrations) and authenticate with OAuth when making requests. Before doing so, be sure to read our [Terms & Guidelines](terms.md) to learn how the API may be used.

### Format

API endpoints accept arguments either as url-encoded values for non-POST requests or as json-encoded objects encoded in POST request body with `Content-Type: application/json` header.

Where possible, the API strives to use appropriate HTTP verbs for each action.

| Verb   | Description                                                |
| ------ | ---------------------------------------------------------- |
| GET    | Used for retrieving resources.                             |
| POST   | Used for creating resources.                               |
| PUT    | Used for updating resources, or performing custom actions. |
| DELETE | Used for deleting resources.                               |

This API relies on standard HTTP response codes to indicate operation result. The table below is a simple reference about the most used status codes:

| Status code | Description                                                                                                                      |
| ----------: | -------------------------------------------------------------------------------------------------------------------------------- |
|         200 | The request was processed successfully.                                                                                          |
|         204 | The request was processed successfully without any data to return.                                                               |
|         4xx | The request was processed with an error and should not be retried unmodified as they won’t be processed any different by an API. |
|         5xx | The request failed due to a server error, it’s safe to retry later.                                                              |

All `200 OK` responses have the `Content-type: application/json` and contain a JSON-encoded representation of one or more objects.

Payload of POST requests has to be JSON-encoded and accompanied with `Content-Type: application/json` header.

### Timestamps <a href="#timestamps" id="timestamps"></a>

All timestamps are returned in ISO 8601 format:

```bash
YYYY-MM-DDTHH:MM:SSZ
```

### Rate Limiting <a href="#rate-limiting" id="rate-limiting"></a>

For requests using OAuth, you can make up to 120 requests per minute per authenticated user.

The headers tell you everything you need to know about your current rate limit status:

| Header name         | Description                                                                       |
| ------------------- | --------------------------------------------------------------------------------- |
| X-RateLimit-Limit   | The maximum number of requests that the consumer is permitted to make per minute. |
| RateLimit-Remaining | The number of requests remaining in the current rate limit window.                |
| X-RateLimit-Reset   | The time at which the current rate limit window resets in UTC epoch seconds.      |

Once you go over the rate limit you will receive an error response:

```http
HTTP/1.1 429 Too Many Requests
Status: 429 Too Many Requests
X-RateLimit-Limit: 120
X-RateLimit-Remaining: 0
X-RateLimit-Reset: 1392321600 
```

### CORS <a href="#cross-origin-resource-sharing" id="cross-origin-resource-sharing"></a>

The API supports Cross Origin Resource Sharing (CORS) for AJAX requests. You can read the [CORS W3C recommendation](https://www.w3.org/TR/cors/), or [this intro](http://code.google.com/p/html5security/wiki/CrossOriginRequestSecurity) from the HTML 5 Security Guide.

Here’s a sample request sent from a browser hitting `http://example.com`:

```http
HTTP/1.1 200 OK
Access-Control-Allow-Origin: http://example.com
Access-Control-Expose-Headers: ETag, Content-Type, Accept, X-RateLimit-Limit, X-RateLimit-Remaining, X-RateLimit-Reset
Access-Control-Allow-Credentials: true
```
