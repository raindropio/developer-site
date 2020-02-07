---
description: >-
  Collection can be shared with other users, which are then called
  collaborators, and this section describes the different commands that are
  related to sharing.
---

# Sharing

### Collaborators

Every user who shares at least one collection with another user, has a collaborators record in the API response. The record contains a restricted subset of user-specific fields.

<table>
  <thead>
    <tr>
      <th style="text-align:left">Field</th>
      <th style="text-align:left">Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">_id</td>
      <td style="text-align:left">User ID of the collaborator</td>
    </tr>
    <tr>
      <td style="text-align:left">email</td>
      <td style="text-align:left">
        <p>Email of the collaborator</p>
        <p>Empty when authorized user have read-only access</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">email_MD5</td>
      <td style="text-align:left">MD5 hash of collaborator email. Useful for using with Gravatar for example</td>
    </tr>
    <tr>
      <td style="text-align:left">fullName</td>
      <td style="text-align:left">Full name of the collaborator</td>
    </tr>
    <tr>
      <td style="text-align:left">role</td>
      <td style="text-align:left">
        <p>Access level:</p>
        <p><b><code>member</code></b> have write access and can invite more users</p>
        <p><b><code>viewer</code></b> read-only access</p>
      </td>
    </tr>
  </tbody>
</table>{% api-method method="post" host="https://api.raindrop.io" path="/rest/v1/collection/:id/sharing" %}
{% api-method-summary %}
Share collection
{% endapi-method-summary %}

{% api-method-description %}
Share collection with another user\(s\). As result invitation\(s\) will be send to specified email\(s\) with link to join collection.
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
Access level. Possible values:  
**`member`**  
**`viewer`**
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

{% api-method method="get" host="https://api.raindrop.io" path="/rest/v1/collection/:id/sharing" %}
{% api-method-summary %}
Get collaborators list of collection
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

{% api-method method="delete" host="https://api.raindrop.io" path="/rest/v1/collection/:id/sharing" %}
{% api-method-summary %}
Unshare or leave collection
{% endapi-method-summary %}

{% api-method-description %}
There two possible results of calling this method, depends on who authenticated user is:  
- **Owner**: collection will be unshared and all collaborators will be removed  
- **Member or viewer**: authenticated user will be removed from collaborators list
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

{% api-method method="put" host="https://api.raindrop.io" path="/rest/v1/collection/:id/sharing/:userId" %}
{% api-method-summary %}
Change access level of collaborator
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="userId" type="number" required=false %}
User ID of collaborator
{% endapi-method-parameter %}

{% api-method-parameter name="id" type="number" required=true %}
Existing collection ID
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-body-parameters %}
{% api-method-parameter name="role" type="string" required=true %}
**`member`** or **`viewer`**
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
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

{% api-method method="delete" host="https://api.raindrop.io" path="/rest/v1/collection/:id/sharing/:userId" %}
{% api-method-summary %}
Delete a collaborator
{% endapi-method-summary %}

{% api-method-description %}
Remove an user from shared collection
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="userId" type="number" required=false %}
User ID of collaborator
{% endapi-method-parameter %}

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

{% api-method method="post" host="https://api.raindrop.io" path="/rest/v1/collection/:id/join" %}
{% api-method-summary %}
Accept an invitation
{% endapi-method-summary %}

{% api-method-description %}
Accept an invitation to join a shared collection
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="number" required=true %}
Existing collection ID
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-body-parameters %}
{% api-method-parameter name="token" type="string" required=true %}
Secret token from email
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
    "role": "member"
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

