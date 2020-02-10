# Users

### Main fields

| Field | Publicly visible | Type | Description |
| :--- | :--- | :--- | :--- |
| \_id | **Yes** | `Integer` | Unique user ID |
| config | No | `Object` | More details in "Config fields" |
| email | No | `String` | Only visible for you |
| email\_MD5 | **Yes** | `String` | MD5 hash of email. Useful for using with Gravatar for example |
| files.used | No | `Integer` | How much space used for files this month |
| files.size | No | `Integer` | Total space for file uploads  |
| files.lastCheckPoint | No | `String` | When space for file uploads is reseted last time |
| fullName | **Yes** | `String` | Full name, max 1000 chars |
| groups | No | `Array<Object>` | More details below in "Groups" |
| password | No | `Boolean` | Does user have a password |
| pro | **Yes** | `Boolean` | PRO subscription |
| proExpire | No | `String` | When PRO subscription will expire |
| registered | No | `String` | Registration date |

### Config fields

<table>
  <thead>
    <tr>
      <th style="text-align:left">Field</th>
      <th style="text-align:left">Publicly visible</th>
      <th style="text-align:left">Type</th>
      <th style="text-align:left">Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">config.broken_level</td>
      <td style="text-align:left">No</td>
      <td style="text-align:left"><code>String</code>
      </td>
      <td style="text-align:left">
        <p>Broken links finder configuration, possible values:</p>
        <p><code>basic</code>  <code>default</code>  <code>strict</code> or <code>off</code>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">config.font_color</td>
      <td style="text-align:left">No</td>
      <td style="text-align:left"><code>String</code>
      </td>
      <td style="text-align:left">Bookmark preview style: <code>sunset</code>  <code>night</code> or empty</td>
    </tr>
    <tr>
      <td style="text-align:left">config.font_size</td>
      <td style="text-align:left">No</td>
      <td style="text-align:left"><code>Integer</code>
      </td>
      <td style="text-align:left">Bookmark preview font size: from 0 to 9</td>
    </tr>
    <tr>
      <td style="text-align:left">config.lang</td>
      <td style="text-align:left">No</td>
      <td style="text-align:left"><code>String</code>
      </td>
      <td style="text-align:left">UI language in 2 char code</td>
    </tr>
    <tr>
      <td style="text-align:left">config.last_collection</td>
      <td style="text-align:left">No</td>
      <td style="text-align:left"><code>Integer</code>
      </td>
      <td style="text-align:left">Last viewed collection ID</td>
    </tr>
    <tr>
      <td style="text-align:left">config.raindrops_sort</td>
      <td style="text-align:left">No</td>
      <td style="text-align:left"><code>String</code>
      </td>
      <td style="text-align:left">
        <p>Default bookmark sort:</p>
        <p><code>title</code>  <code>-title</code>  <code>-sort</code>  <code>domain</code>  <code>-domain</code>  <code>+lastUpdate</code> or <code>-lastUpdate</code>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">config.raindrops_view</td>
      <td style="text-align:left">No</td>
      <td style="text-align:left"><code>String</code>
      </td>
      <td style="text-align:left">
        <p>Default bookmark view:</p>
        <p><code>grid</code>  <code>list</code>  <code>simple</code> or <code>masonry</code>
        </p>
      </td>
    </tr>
  </tbody>
</table>### Additional fields

| Field | Publicly visible | Type | Description |
| :--- | :--- | :--- | :--- |
| facebook.enabled | No | `Boolean` | Does Facebook account is linked |
| twitter.enabled | No | `Boolean` | Does Twitter account is linked |
| vkontakte.enabled | No | `Boolean` | Does Vkontakte account is linked |
| google.enabled | No | `Boolean` | Does Google account is linked |
| dropbox.enabled | No | `Boolean` | Does Dropbox backup is enabled |
| gdrive.enabled | No | `Boolean` | Does Google Drive backup is enabled |

{% hint style="warning" %}
Our API response could contain **other fields**, not described above. It's **unsafe to use** them in your integration! They could be removed or renamed at any time.
{% endhint %}

### Groups

If you look into Raindrop UI you will notice a sidebar in left corner, where collections are located. Collections itself divided by groups. They useful to create separate sets of collections, for example "Home", "Work", etc.

`Groups` array is a single place where user **root** collection list and order is persisted. Why just not to save order position inside collection item itself? Because collections can be shared and they group and order can vary from user to user.

Typically groups array looks like this:

```javascript
{
  "groups": [
    {
      "title": "Home",
      "hidden": false,
      "sort": 0,
      "collections": [
        8364483,
        8364403,
        66
      ]
    },
    {
      "title": "Work",
      "hidden": false,
      "sort": 1,
      "collections": [
        8492393
      ]
    }
  ]
}
```

#### Group object fields

| Field | Type | Description |
| :--- | :--- | :--- |
| title | `String` | Name of group |
| hidden | `Boolean` | Does group is collapsed |
| sort | `Integer` | Ascending order position |
| collections | `Array<Integer>` | Collection ID's in order |

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
Update authenticated user
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
{% api-method-response-example httpCode=307 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```http
Location: https://app.raindrop.io/...
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

