# Authenticated user

{% api-method method="get" host="https://api.raindrop.io" path="/rest/v1/user" %}
{% api-method-summary %}
Get user
{% endapi-method-summary %}

{% api-method-description %}
Get currently authenticated user details
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
    "result": true,
    "user": {
      "_id": 32,
      "config": {
        "broken_level": "strict",
        "font_color": "",
        "font_size": 0,
        "lang": "ru_RU",
        "last_collection": 8492393,
        "raindrops_sort": "-lastUpdate",
        "raindrops_view": "list"
      },
      "dropbox": {
        "enabled": true
      },
      "email": "some@email.com",
      "email_MD5": "13a0a20681d8781912e5314150694bf7",
      "files": {
        "used": 6766094,
        "size": 10000000000,
        "lastCheckPoint": "2020-01-26T23:53:19.676Z"
      },
      "fullName": "Mussabekov Rustem",
      "gdrive": {
        "enabled": true
      },
      "groups": [
        {
          "title": "My Collections",
          "hidden": false,
          "sort": 0,
          "collections": [
            8364483,
            8364403,
            66
          ]
        }
      ],
      "password": true,
      "pro": true,
      "proExpire": "2028-09-27T22:00:00.000Z",
      "registered": "2014-09-30T07:51:15.406Z"
  }
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=401 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```http
Unauthorized
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="https://api.raindrop.io" path="/rest/v1/user/:id" %}
{% api-method-summary %}
Get user by ID
{% endapi-method-summary %}

{% api-method-description %}
Get's publicly available user details
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="number" required=true %}
User ID
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
  "result": true,
  "user": {
    "_id": 32,
    "email_MD5": "13a0a20681d8781912e5314150694bf7",
    "fullName": "Mussabekov Rustem",
    "pro": true,
    "registered": "2014-09-30T07:51:15.406Z"
  }
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=404 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
  "error": -1,
  "errorMessage": "not found",
  "result": false
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="put" host="https://api.raindrop.io" path="/rest/v1/user" %}
{% api-method-summary %}
Update user
{% endapi-method-summary %}

{% api-method-description %}
To change email, config, password, etc... you can do it from single endpoint 
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-body-parameters %}
{% api-method-parameter name="groups" type="array" required=false %}

{% endapi-method-parameter %}

{% api-method-parameter name="config" type="object" required=false %}

{% endapi-method-parameter %}

{% api-method-parameter name="newpassword" type="string" required=false %}

{% endapi-method-parameter %}

{% api-method-parameter name="oldpassword" type="string" required=false %}

{% endapi-method-parameter %}

{% api-method-parameter name="fullName" type="string" required=false %}

{% endapi-method-parameter %}

{% api-method-parameter name="email" type="string" required=false %}

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
    "user": {
        ...
    }
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
//email specified but empty
{
  "result": false,
  "error": 1,
  "errorMessage": "email required"
}

//fullName specified but empty
{
  "result": false,
  "error": 2,
  "errorMessage": "User validation failed: fullName: is required"
}

//newpassword specified, but oldpassword is empty
{
  "result": false,
  "error": 3,
  "errorMessage": "oldpassword incorrect"
}

//incorrect config key value
{
  "result": false,
  "error": "config.raindrops_sort",
  "errorMessage": "User validation failed: config.raindrops_sort: `1` is not a valid enum value for path `raindrops_sort`., config: Validation failed: raindrops_sort: `1` is not a valid enum value for path `raindrops_sort`."
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="https://api.raindrop.io" path="/rest/v1/user/connect/:provider" %}
{% api-method-summary %}
Connect social network account
{% endapi-method-summary %}

{% api-method-description %}
Connect social network account as sign in authentication option
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="provider" type="string" required=false %}
`facebook` `google` `twitter` `vkontakte` `dropbox` or `gdrive`
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=307 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```http
Location: https://some.com/...
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="https://api.raindrop.io" path="/rest/v1/user/connect/:provider/revoke" %}
{% api-method-summary %}
Disconnect social network account
{% endapi-method-summary %}

{% api-method-description %}
Disconnect social network account from available authentication options
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="provider" type="string" required=false %}
`facebook` `google` `twitter` `vkontakte` `dropbox` or `gdrive`
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

