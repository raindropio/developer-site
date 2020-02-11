# Single raindrop

{% api-method method="get" host="https://api.raindrop.io" path="/rest/v1/raindrop/{id}" %}
{% api-method-summary %}
Get raindrop
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="number" required=true %}
Existing raindrop ID
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="post" host="https://api.raindrop.io" path="/rest/v1/raindrop" %}
{% api-method-summary %}
Create raindrop
{% endapi-method-summary %}

{% api-method-description %}
Description and possible values of fields described in "Fields"
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-body-parameters %}
{% api-method-parameter name="lastUpdate" type="string" required=false %}

{% endapi-method-parameter %}

{% api-method-parameter name="order" type="number" required=false %}
Specify sort order \(ascending\).  
For example if you want to move raindrop to the first place set this field to **0**
{% endapi-method-parameter %}

{% api-method-parameter name="important" type="boolean" required=false %}

{% endapi-method-parameter %}

{% api-method-parameter name="tags" type="array" required=false %}

{% endapi-method-parameter %}

{% api-method-parameter name="media" type="array" required=false %}

{% endapi-method-parameter %}

{% api-method-parameter name="cover" type="string" required=false %}

{% endapi-method-parameter %}

{% api-method-parameter name="collection" type="object" required=false %}

{% endapi-method-parameter %}

{% api-method-parameter name="type" type="string" required=false %}

{% endapi-method-parameter %}

{% api-method-parameter name="html" type="string" required=false %}

{% endapi-method-parameter %}

{% api-method-parameter name="excerpt" type="string" required=false %}

{% endapi-method-parameter %}

{% api-method-parameter name="title" type="string" required=false %}

{% endapi-method-parameter %}

{% api-method-parameter name="link" type="string" required=false %}

{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
    "result": true,
    "item": {
        ...
    }
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="put" host="https://api.raindrop.io" path="/rest/v1/raindrop/{id}" %}
{% api-method-summary %}
Update raindrop
{% endapi-method-summary %}

{% api-method-description %}
Description and possible values of fields described in "Fields"
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="number" required=true %}
Existing raindrop ID
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-body-parameters %}
{% api-method-parameter name="lastUpdate" type="string" required=false %}

{% endapi-method-parameter %}

{% api-method-parameter name="order" type="number" required=false %}
Specify sort order \(ascending\).  
For example if you want to move raindrop to the first place set this field to **0**
{% endapi-method-parameter %}

{% api-method-parameter name="important" type="boolean" required=false %}

{% endapi-method-parameter %}

{% api-method-parameter name="tags" type="array" required=false %}

{% endapi-method-parameter %}

{% api-method-parameter name="media" type="array" required=false %}

{% endapi-method-parameter %}

{% api-method-parameter name="cover" type="string" required=false %}

{% endapi-method-parameter %}

{% api-method-parameter name="collection" type="object" required=false %}

{% endapi-method-parameter %}

{% api-method-parameter name="type" type="string" required=false %}

{% endapi-method-parameter %}

{% api-method-parameter name="html" type="string" required=false %}

{% endapi-method-parameter %}

{% api-method-parameter name="excerpt" type="string" required=false %}

{% endapi-method-parameter %}

{% api-method-parameter name="title" type="string" required=false %}

{% endapi-method-parameter %}

{% api-method-parameter name="link" type="string" required=false %}

{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
    "result": true,
    "item": {
        ...
    }
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="delete" host="https://api.raindrop.io" path="/rest/v1/raindrop/{id}" %}
{% api-method-summary %}
Remove raindrop
{% endapi-method-summary %}

{% api-method-description %}
When you remove raindrop it will be moved to user `Trash` collection. But if you try to remove raindrop from `Trash`, it will be removed permanently.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="number" required=true %}
Existing raindrop ID
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
    "result": true
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="put" host="https://api.raindrop.io" path="/rest/v1/raindrop/{id}/file" %}
{% api-method-summary %}
Upload file
{% endapi-method-summary %}

{% api-method-description %}
To upload file you need to create single raindrop with any details, and then call this method for this raindrop. Sorry, will be simplified in the future.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="number" required=true %}
Existing raindrop ID
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Content-Type" type="string" required=true %}
multipart/form-data
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-form-data-parameters %}
{% api-method-parameter name="file" type="object" required=true %}
File
{% endapi-method-parameter %}
{% endapi-method-form-data-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

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
{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

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
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="put" host="https://api.raindrop.io" path="/rest/v1/raindrop/{id}/cover" %}
{% api-method-summary %}
Upload cover
{% endapi-method-summary %}

{% api-method-description %}
PNG, GIF or JPEG
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="number" required=true %}
Existing raindrop ID
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Content-Type" type="string" required=true %}
multipart/form-data
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-form-data-parameters %}
{% api-method-parameter name="cover" type="object" required=true %}
File
{% endapi-method-parameter %}
{% endapi-method-form-data-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

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
{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

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
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="https://api.raindrop.io" path="/rest/v1/raindrop/{id}/cache" %}
{% api-method-summary %}
Get permanent copy
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="number" required=true %}
Existing raindrop ID
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=307 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```http
Location: https://s3.aws...
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

