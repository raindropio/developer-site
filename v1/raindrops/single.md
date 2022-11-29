---
description: >-
  In this page you will find how to retrieve, create, update or delete single
  raindrop.
---

# Single raindrop

{% swagger baseUrl="https://api.raindrop.io" path="/rest/v1/raindrop/{id}" method="get" summary="Get raindrop" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="path" name="id" type="number" required="true" %}
Existing raindrop ID
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
```
{% endswagger-response %}
{% endswagger %}

{% swagger baseUrl="https://api.raindrop.io" path="/rest/v1/raindrop" method="post" summary="Create raindrop" %}
{% swagger-description %}
Description and possible values of fields described in "Fields"
{% endswagger-description %}

{% swagger-parameter in="body" name="pleaseParse" type="object" %}
Specify empty object to automatically parse meta data (cover, description, html) in the background
{% endswagger-parameter %}

{% swagger-parameter in="body" name="created" type="string" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="lastUpdate" type="string" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="order" type="number" %}
Specify sort order (ascending).

\


For example if you want to move raindrop to the first place set this field to 

**0**
{% endswagger-parameter %}

{% swagger-parameter in="body" name="important" type="boolean" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="tags" type="array" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="media" type="array" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="cover" type="string" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="collection" type="object" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="type" type="string" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="excerpt" type="string" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="title" type="string" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="link" type="string" required="true" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="highlights" type="array" %}

{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```javascript
{
    "result": true,
    "item": {
        ...
    }
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger baseUrl="https://api.raindrop.io" path="/rest/v1/raindrop/{id}" method="put" summary="Update raindrop" %}
{% swagger-description %}
Description and possible values of fields described in "Fields"
{% endswagger-description %}

{% swagger-parameter in="path" name="id" type="number" required="true" %}
Existing raindrop ID
{% endswagger-parameter %}

{% swagger-parameter in="body" name="created" type="string" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="lastUpdate" type="string" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="pleaseParse" type="object" %}
Specify empty object to re-parse link meta data (cover, type, html) in the background
{% endswagger-parameter %}

{% swagger-parameter in="body" name="order" type="number" %}
Specify sort order (ascending).

\


For example if you want to move raindrop to the first place set this field to 

**0**
{% endswagger-parameter %}

{% swagger-parameter in="body" name="important" type="boolean" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="tags" type="array" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="media" type="array" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="cover" type="string" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="collection" type="object" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="type" type="string" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="excerpt" type="string" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="title" type="string" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="highlights" type="array" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="link" type="string" %}

{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```javascript
{
    "result": true,
    "item": {
        ...
    }
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger baseUrl="https://api.raindrop.io" path="/rest/v1/raindrop/{id}" method="delete" summary="Remove raindrop" %}
{% swagger-description %}
When you remove raindrop it will be moved to user 

`Trash`

 collection. But if you try to remove raindrop from 

`Trash`

, it will be removed permanently.
{% endswagger-description %}

{% swagger-parameter in="path" name="id" type="number" required="true" %}
Existing raindrop ID
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```javascript
{
    "result": true
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger baseUrl="https://api.raindrop.io" path="/rest/v1/raindrop/file" method="put" summary="Upload file" %}
{% swagger-description %}
Make sure to send PUT request with 

[multipart/form-data](https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods/POST#example)

 body
{% endswagger-description %}

{% swagger-parameter in="header" name="Content-Type" type="string" required="true" %}
multipart/form-data
{% endswagger-parameter %}

{% swagger-parameter in="body" name="file" type="object" required="true" %}
File
{% endswagger-parameter %}

{% swagger-parameter in="body" name="collectionId" %}
Collection Id
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```javascript
{
    "result": true,
    "item": {
        "title": "File name",
        "type": "image",
        "link": "https://up.raindrop.io/raindrop/111/file.jpeg",
        "domain": "raindrop.io",
        "file": {
            "name": "File name.jpeg",
            "size": 10000
        }
        ...
    }
}
```
{% endswagger-response %}

{% swagger-response status="400" description="" %}
```javascript
//file is not specified
{
  "result": false,
  "error": -1,
  "errorMessage": "no file"
}

//unsupported file format
{
  "result": false,
  "error": "file_invalid",
  "errorMessage": "File is invalid"
}

//file size is big
{
  "result": false,
  "error": "file_size_limit",
  "errorMessage": "File size limit"
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger baseUrl="https://api.raindrop.io" path="/rest/v1/raindrop/{id}/cover" method="put" summary="Upload cover" %}
{% swagger-description %}
PNG, GIF or JPEG
{% endswagger-description %}

{% swagger-parameter in="path" name="id" type="number" required="true" %}
Existing raindrop ID
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Content-Type" type="string" required="true" %}
multipart/form-data
{% endswagger-parameter %}

{% swagger-parameter in="body" name="cover" type="object" required="true" %}
File
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```javascript
{
    "result": true,
    "item": {
        "cover": "https://up.raindrop.io/raindrop/...",
        "media": [
            {
                "link": "https://up.raindrop.io/raindrop/..."
            }
        ]
        ...
    }
}
```
{% endswagger-response %}

{% swagger-response status="400" description="" %}
```javascript
//file is not specified
{
  "result": false,
  "error": -1,
  "errorMessage": "no file"
}

//unsupported file format
{
  "result": false,
  "error": "file_invalid",
  "errorMessage": "File is invalid"
}

//file size is big
{
  "result": false,
  "error": "file_size_limit",
  "errorMessage": "File size limit"
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger baseUrl="https://api.raindrop.io" path="/rest/v1/raindrop/{id}/cache" method="get" summary="Get permanent copy" %}
{% swagger-description %}
Links permanently saved with all content (only in PRO plan). Using this method you can navigate to this copy.
{% endswagger-description %}

{% swagger-parameter in="path" name="id" type="number" required="true" %}
Existing raindrop ID
{% endswagger-parameter %}

{% swagger-response status="307" description="" %}
```http
Location: https://s3.aws...
```
{% endswagger-response %}
{% endswagger %}
