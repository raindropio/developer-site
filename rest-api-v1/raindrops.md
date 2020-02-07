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
| domain | `String` | Domain name of link |
| excerpt | `String` | Description |
| lastUpdate | `String` | When bookmark is created. Unfortunately we doesn't have separate `creation` date field yet. |
| link | `String` | URL |
| media | `Array` | ​List of possible covers in format: `[ {"link":"url"} ]` |
| tags | `Array` | Tags list |
| title | `String` | Title |
| type | `String` | `link` `article` `image` `video` `document` or `audio` |
| user | `Object` | ​ |
| user.$id | `Integer` | Owner of raindrop |

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
      <td style="text-align:left">broken</td>
      <td style="text-align:left"><code>Boolean</code>
      </td>
      <td style="text-align:left">Marked as broken (original <code>link</code> is not reachable anymore)</td>
    </tr>
    <tr>
      <td style="text-align:left">cache</td>
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
      <td style="text-align:left">creatorRef</td>
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
      <td style="text-align:left">file</td>
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
      <td style="text-align:left">html</td>
      <td style="text-align:left"><code>String</code>
      </td>
      <td style="text-align:left">
        <p>When raindrop have <code>article</code>, <code>image</code>, <code>video</code> or <code>document</code> type,
          this field will contain preview in HTML format.</p>
        <p>Also to get this field, you need to request single raindrop with <b>?html</b> query
          parameter as described below.</p>
      </td>
    </tr>
  </tbody>
</table>{% hint style="warning" %}
Our API response could contain **other fields**, not described above. It's **unsafe to use** them in your integration! They could be removed or renamed at any time.
{% endhint %}





