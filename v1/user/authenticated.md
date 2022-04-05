# Authenticated user

{% swagger baseUrl="https://api.raindrop.io" path="/rest/v1/user" method="get" summary="Get user" %}
{% swagger-description %}
Get currently authenticated user details
{% endswagger-description %}

{% swagger-response status="200" description="" %}
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
{% endswagger-response %}

{% swagger-response status="401" description="" %}
```http
Unauthorized
```
{% endswagger-response %}
{% endswagger %}

{% swagger baseUrl="https://api.raindrop.io" path="/rest/v1/user/{id}" method="get" summary="Get user by ID" %}
{% swagger-description %}
Get's publicly available user details
{% endswagger-description %}

{% swagger-parameter in="path" name="id" type="number" %}
User ID
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
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
{% endswagger-response %}

{% swagger-response status="404" description="" %}
```javascript
{
  "error": -1,
  "errorMessage": "not found",
  "result": false
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger baseUrl="https://api.raindrop.io" path="/rest/v1/user" method="put" summary="Update user" %}
{% swagger-description %}
To change email, config, password, etc... you can do it from single endpoint 
{% endswagger-description %}

{% swagger-parameter in="body" name="groups" type="array" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="config" type="object" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="newpassword" type="string" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="oldpassword" type="string" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="fullName" type="string" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="email" type="string" %}

{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```javascript
{
    "result": true,
    "user": {
        ...
    }
}
```
{% endswagger-response %}

{% swagger-response status="400" description="" %}
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
{% endswagger-response %}
{% endswagger %}

{% swagger baseUrl="https://api.raindrop.io" path="/rest/v1/user/connect/{provider}" method="get" summary="Connect social network account" %}
{% swagger-description %}
Connect social network account as sign in authentication option
{% endswagger-description %}

{% swagger-parameter in="path" name="provider" type="string" %}
`facebook`

 

`google`

 

`twitter`

 

`vkontakte`

 

`dropbox`

 or 

`gdrive`
{% endswagger-parameter %}

{% swagger-response status="307" description="" %}
```http
Location: https://some.com/...
```
{% endswagger-response %}
{% endswagger %}

{% swagger baseUrl="https://api.raindrop.io" path="/rest/v1/user/connect/{provider}/revoke" method="get" summary="Disconnect social network account" %}
{% swagger-description %}
Disconnect social network account from available authentication options
{% endswagger-description %}

{% swagger-parameter in="path" name="provider" type="string" %}
`facebook`

 

`google`

 

`twitter`

 

`vkontakte`

 

`dropbox`

 or 

`gdrive`
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
```
{% endswagger-response %}
{% endswagger %}
