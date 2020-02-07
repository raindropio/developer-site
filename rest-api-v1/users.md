# Users

### Main fields

| Field | Publicly visible | Type | Description |
| :--- | :--- | :--- | :--- |
| \_id | **Yes** | Integer | Unique user ID |
| config | No | Object | More details in "Config fields" |
| email | No | String | Only visible for you |
| email\_MD5 | **Yes** | String | MD5 hash of email. Useful for using with Gravatar for example |
| files.used | No | Integer |  |
| files.size | No | Integer |  |
| files.lastCheckPoint | No | String |  |
| fullName | **Yes** | String | Full name |
| groups | No | Array | More details below in "Groups format" |
| password | No | Boolean | Does user have set a password |
| pro | **Yes** | Boolean |  |
| proExpire | No | String | When PRO plan will expire |
| registered | No | String | Registration date |

### Config fields

| Field | Publicly visible | Type | Description |
| :--- | :--- | :--- | :--- |
| config.broken\_level | No | Boolean |  |
| config.font\_color | No | Boolean |  |
| config.font\_size | No | String |  |
| config.lang | No | String |  |
| config.last\_collection | No | Integer |  |
| config.raindrops\_sort | No | String |  |
| config.raindrops\_view | No | String |  |

### Additional fields

| Field | Publicly visible | Type | Description |
| :--- | :--- | :--- | :--- |
| dropbox.enabled | No | Boolean |  |
| gdrive.enabled | No | Boolean |  |

{% hint style="warning" %}
Our API response could contain **other fields**, not described above. It's **unsafe to use** them in your integration! They could be removed or renamed at any time.
{% endhint %}

### Groups format

jjkkj

{% api-method method="get" host="https://api.raindrop.io" path="/rest/v1/user" %}
{% api-method-summary %}
Authenticated user
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
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}



