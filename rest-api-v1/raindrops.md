---
description: We call bookmarks (or items) as "raindrops"
---

# Raindrops

### Main properties

| Property | Type | Description |
| :--- | :--- | :--- |
| \_id | `Integer` | Unique identifier |
| collection | `Object` | ​ |
| collection.$id | `Integer` | Collection that the raindrop resides in |
| cover | `String` | Raindrop cover URL |
| domain | `String` | Hostname of a link. Files always have `raindrop.io` hostname |
| excerpt | `String` | Description; max length: 10000 |
| lastUpdate | `String` | Date when bookmark is created. Unfortunately we doesn't have separate `creation` and `update` date fields yet :\( |
| link | `String` | URL |
| media | `Array<Object>` | ​Covers list in format: `[ {"link":"url"} ]` |
| tags | `Array<String>` | Tags list |
| title | `String` | Title; max length: 1000 |
| type | `String` | `link` `article` `image` `video` `document` or `audio` |
| user | `Object` | ​ |
| user.$id | `Integer` | Raindrop owner |

### Other properties

<table>
  <thead>
    <tr>
      <th style="text-align:left">Property</th>
      <th style="text-align:left">Type</th>
      <th style="text-align:left">Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><b>broken</b>
      </td>
      <td style="text-align:left"><code>Boolean</code>
      </td>
      <td style="text-align:left">Marked as broken (original <code>link</code> is not reachable anymore)</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>cache</b>
      </td>
      <td style="text-align:left"><code>Object</code>
      </td>
      <td style="text-align:left">Permanent copy (cached version) details</td>
    </tr>
    <tr>
      <td style="text-align:left">cache.status</td>
      <td style="text-align:left"><code>String</code>
      </td>
      <td style="text-align:left"><code>ready</code>  <code>retry</code>  <code>failed</code>  <code>invalid-origin</code>  <code>invalid-timeout</code> or <code>invalid-size</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">cache.size</td>
      <td style="text-align:left"><code>Integer</code>
      </td>
      <td style="text-align:left">Full size in bytes</td>
    </tr>
    <tr>
      <td style="text-align:left">cache.created</td>
      <td style="text-align:left"><code>String</code>
      </td>
      <td style="text-align:left">Date when copy is successfully made</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>creatorRef</b>
      </td>
      <td style="text-align:left"><code>Object</code>
      </td>
      <td style="text-align:left">Sometime raindrop may belong to other user, not to the one who created
        it.
        <br />For example when this raindrop is created in shared collection by other
        user.
        <br />This object contains info about original author.</td>
    </tr>
    <tr>
      <td style="text-align:left">creatorRef._id</td>
      <td style="text-align:left"><code>Integer</code>
      </td>
      <td style="text-align:left">Original author (user ID) of a raindrop</td>
    </tr>
    <tr>
      <td style="text-align:left">creatorRef.fullName</td>
      <td style="text-align:left"><code>String</code>
      </td>
      <td style="text-align:left">Original author name of a raindrop</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>file</b>
      </td>
      <td style="text-align:left"><code>Object</code>
      </td>
      <td style="text-align:left">This raindrop uploaded from desktop</td>
    </tr>
    <tr>
      <td style="text-align:left">file.name</td>
      <td style="text-align:left"><code>String</code>
      </td>
      <td style="text-align:left">File name</td>
    </tr>
    <tr>
      <td style="text-align:left">file.size</td>
      <td style="text-align:left"><code>Integer</code>
      </td>
      <td style="text-align:left">File size in bytes</td>
    </tr>
    <tr>
      <td style="text-align:left">file.type</td>
      <td style="text-align:left"><code>String</code>
      </td>
      <td style="text-align:left">Mime type</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>important</b>
      </td>
      <td style="text-align:left"><code>Boolean</code>
      </td>
      <td style="text-align:left">Marked as &quot;favorite&quot;</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>html</b>
      </td>
      <td style="text-align:left"><code>String</code>
      </td>
      <td style="text-align:left">
        <p>When raindrop have <code>article</code>, <code>image</code>, <code>video</code> or <code>document</code> type,
          this field will contain preview in HTML format.</p>
        <p>This field send only for single <code>GET</code> raindrop request</p>
      </td>
    </tr>
  </tbody>
</table>{% hint style="warning" %}
Our API response could contain **other fields**, not described above. It's **unsafe to use** them in your integration! They could be removed or renamed at any time.
{% endhint %}

{% api-method method="get" host="https://api.raindrop.io" path="/rest/v1/raindrop/:id" %}
{% api-method-summary %}
Get single raindrop
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

```javascript
{
  "result": true
  "item": {
    "_id": 137816377,
    "cache": {
      "status": "ready",
      "size": 154933,
      "created": "2020-02-06T20:36:06.409Z"
    },
    "collection": {
      "$id": -1
    },
    "cover": "https://catalin.red/dist/img/social.png",
    "creatorRef": {
      "_id": 32,
      "fullName": "Mussabekov Rustem"
    },
    "domain": "catalin.red",
    "excerpt": "How to use an SVG as a favicon for your website, considering the light and dark theme detection in the browser using the CSS prefers-color-scheme media feature, with PNG and ICO fallbacks.",
    "lastUpdate": "2020-02-06T20:34:08.376Z",
    "link": "https://catalin.red/svg-favicon-light-dark-theme/",
    "media": [
      {
        "type": "image",
        "link": "https://catalin.red/dist/img/social.png"
      }
    ],
    "tags": ["svg"],
    "title": "Light and dark themed SVG favicon using the CSS prefers-color-scheme media feature",
    "type": "link",
    "user": {
      "$id": 32
    }
  }
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=403 %}
{% api-method-response-example-description %}
No access
{% endapi-method-response-example-description %}

```javascript
{
    "result": false,
    "errorMessage": "no access permissions for raindrop 1232"
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=404 %}
{% api-method-response-example-description %}
When raindrop is not found
{% endapi-method-response-example-description %}

```javascript
{
    "result": false
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=410 %}
{% api-method-response-example-description %}
When raindrop is removed
{% endapi-method-response-example-description %}

```javascript
{
    "result": false
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

