---
description: We call bookmarks (or items) as "raindrops"
---

# Raindrops

### Main fields

| Field          | Type            | Description                                                                       |
| -------------- | --------------- | --------------------------------------------------------------------------------- |
| \_id           | `Integer`       | Unique identifier                                                                 |
| collection     | `Object`        | ​                                                                                 |
| collection.$id | `Integer`       | Collection that the raindrop resides in                                           |
| cover          | `String`        | Raindrop cover URL                                                                |
| created        | `String`        | Creation date                                                                     |
| domain         | `String`        | <p>Hostname of a link.<br>Files always have <code>raindrop.io</code> hostname</p> |
| excerpt        | `String`        | Description; max length: 10000                                                    |
| note           | `String`        | Note; max length: 10000                                                           |
| lastUpdate     | `String`        | Update date                                                                       |
| link           | `String`        | URL                                                                               |
| media          | `Array<Object>` | ​Covers list in format: `[ {"link":"url"} ]`                                      |
| tags           | `Array<String>` | Tags list                                                                         |
| title          | `String`        | Title; max length: 1000                                                           |
| type           | `String`        | `link` `article` `image` `video` `document` or `audio`                            |
| user           | `Object`        | ​                                                                                 |
| user.$id       | `Integer`       | Raindrop owner                                                                    |

### Other fields

| Field                 | Type      | Description                                                                                                                                                                                                                                                                                                          |
| --------------------- | --------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| broken                | `Boolean` | Marked as broken (original `link` is not reachable anymore)                                                                                                                                                                                                                                                          |
| cache                 | `Object`  | Permanent copy (cached version) details                                                                                                                                                                                                                                                                              |
| cache.status          | `String`  | `ready` `retry` `failed` `invalid-origin` `invalid-timeout` or `invalid-size`                                                                                                                                                                                                                                        |
| cache.size            | `Integer` | Full size in bytes                                                                                                                                                                                                                                                                                                   |
| cache.created         | `String`  | Date when copy is successfully made                                                                                                                                                                                                                                                                                  |
| creatorRef            | `Object`  | <p>Sometime raindrop may belong to other user, not to the one who created it. <br>For example when this raindrop is created in shared collection by other user.<br>This object contains info about original author.</p>                                                                                              |
| creatorRef.\_id       | `Integer` | Original author (user ID) of a raindrop                                                                                                                                                                                                                                                                              |
| creatorRef.fullName   | `String`  | Original author name of a raindrop                                                                                                                                                                                                                                                                                   |
| file                  | `Object`  | <p>This raindrop uploaded from desktop</p><p><a href="https://help.raindrop.io/article/48-uploading-files">Supported file formats</a></p>                                                                                                                                                                            |
| file.name             | `String`  | File name                                                                                                                                                                                                                                                                                                            |
| file.size             | `Integer` | File size in bytes                                                                                                                                                                                                                                                                                                   |
| file.type             | `String`  | Mime type                                                                                                                                                                                                                                                                                                            |
| important             | `Boolean` | Marked as "favorite"                                                                                                                                                                                                                                                                                                 |
| highlights            | `Array`   |                                                                                                                                                                                                                                                                                                                      |
| highlights\[].\_id    | `String`  | Unique id of highlight                                                                                                                                                                                                                                                                                               |
| highlights\[].text    | `String`  | Text of highlight (required)                                                                                                                                                                                                                                                                                         |
| highlights\[].color   | `String`  | <p>Color of highlight. <br>Default <code>yellow</code><br><br>Can be <code>blue</code>, <code>brown</code>, <code>cyan</code>, <code>gray</code>, <code>green</code>, <code>indigo</code>, <code>orange</code>, <code>pink</code>, <code>purple</code>, <code>red</code>, <code>teal</code>, <code>yellow</code></p> |
| highlights\[].note    | `String`  | Optional note for highlight                                                                                                                                                                                                                                                                                          |
| highlights\[].created | `String`  | Creation date of highlight                                                                                                                                                                                                                                                                                           |

{% hint style="warning" %}
Our API response could contain **other fields**, not described above. It's **unsafe to use** them in your integration! They could be removed or renamed at any time.
{% endhint %}
