# Sharing

{% api-method method="get" host="https://api.raindrop.io" path="/rest/v1/collection/:id/sharing" %}
{% api-method-summary %}
Get collaborators of collection
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="number" required=true %}
Existing collection ID
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
  "items": [
    {
      "_id": 373381,
      "email": "some@mail.com",
      "email_MD5": "e12bda18ca265d3f3e30d247adea2549",
      "fullName": "Jakie Future",
      "level": 2,
      "pro": false,
      "registered": "2019-08-18T17:01:43.664Z",
      "role": "viewer"
    }
  ],
  "result": true
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="post" host="https://api.raindrop.io" path="/rest/v1/collection/:id/sharing" %}
{% api-method-summary %}
Share collection
{% endapi-method-summary %}

{% api-method-description %}
Share collection with another user\(s\)
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="number" required=true %}
Existing collection ID
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-body-parameters %}
{% api-method-parameter name="role" type="string" required=true %}
Possible values:  
**`member`** - write access  
**`viewer`** - read only access
{% endapi-method-parameter %}

{% api-method-parameter name="emails" type="array" required=true %}
The user email\(s\) with whom to share the project.  
Maximum 10
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
    "emails": [
        "some@user.com",
        "other@user.com"
    ]
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
//'emails' array is empty
{
    "result": false,
    "errorMessage": "no emails"
}

//'emails' array larger than 10
{
    "result": false,
    "errorMessage": "you cant send more than 10 invites at once"
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=403 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
//When user have more than 100 pending invitations:
{
    "result": false,
    "errorMessage": "you have too many pending invitations, you will be banned if you continue send more"
}

//User doesn't have enought permissions to invite more people
{
    "result": false,
    "errorMessage": "you dont have permissions to invite more people"
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="delete" host="https://api.raindrop.io" path="/rest/v1/collection/:id/sharing" %}
{% api-method-summary %}
Unshare or leave collection
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="number" required=true %}
Existing collection ID
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

