# Collections

### Properties

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
      <td style="text-align:left">_id</td>
      <td style="text-align:left"><code>Integer</code>
      </td>
      <td style="text-align:left">The id of the collection.</td>
    </tr>
    <tr>
      <td style="text-align:left">access</td>
      <td style="text-align:left"><code>Object</code>
      </td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">access.level</td>
      <td style="text-align:left"><code>Integer</code>
      </td>
      <td style="text-align:left">
        <p></p>
        <ol>
          <li>read only access (equal to <code>public=true</code>)</li>
          <li>collaborator with read only access</li>
          <li>collaborator with write only access</li>
          <li>owner</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">access.draggable</td>
      <td style="text-align:left"><code>Boolean</code>
      </td>
      <td style="text-align:left">Does it possible to change parent of this collection?</td>
    </tr>
    <tr>
      <td style="text-align:left">collaborators</td>
      <td style="text-align:left"><code>Object</code>
      </td>
      <td style="text-align:left">When this object is present, means that collections is shared. Content
        of this object is private and not very useful.
        <br />All sharing API methods <a href="sharing.md">described here</a>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">color</td>
      <td style="text-align:left"><code>String</code>
      </td>
      <td style="text-align:left">Primary color of collection cover as <code>HEX</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">count</td>
      <td style="text-align:left"><code>Integer</code>
      </td>
      <td style="text-align:left">Raindrops count</td>
    </tr>
    <tr>
      <td style="text-align:left">cover</td>
      <td style="text-align:left"><code>Array&lt;String&gt;</code>
      </td>
      <td style="text-align:left">Collection cover.
        <br />This array always have one item due to legacy reasons</td>
    </tr>
    <tr>
      <td style="text-align:left">created</td>
      <td style="text-align:left"><code>String</code>
      </td>
      <td style="text-align:left">When collection is created</td>
    </tr>
    <tr>
      <td style="text-align:left">expanded</td>
      <td style="text-align:left"><code>Boolean</code>
      </td>
      <td style="text-align:left">Whether the collection&#x2019;s sub-collections are expanded</td>
    </tr>
    <tr>
      <td style="text-align:left">lastUpdate</td>
      <td style="text-align:left"><code>String</code>
      </td>
      <td style="text-align:left">When collection is updated</td>
    </tr>
    <tr>
      <td style="text-align:left">parent</td>
      <td style="text-align:left"><code>Object</code>
      </td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">parent.$id</td>
      <td style="text-align:left"><code>Integer</code>
      </td>
      <td style="text-align:left">The id of the parent collection. Empty for root collection</td>
    </tr>
    <tr>
      <td style="text-align:left">public</td>
      <td style="text-align:left"><code>Boolean</code>
      </td>
      <td style="text-align:left">Collection and raindrops that it contains will be accessible without authentication?</td>
    </tr>
    <tr>
      <td style="text-align:left">sort</td>
      <td style="text-align:left"><code>Integer</code>
      </td>
      <td style="text-align:left">The order of collection (descending). Defines the position of the collection
        among all the collections with the same <code>parent.$id</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">title</td>
      <td style="text-align:left"><code>String</code>
      </td>
      <td style="text-align:left">Name of the collection</td>
    </tr>
    <tr>
      <td style="text-align:left">user</td>
      <td style="text-align:left"><code>Object</code>
      </td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">user.$id</td>
      <td style="text-align:left"><code>Integer</code>
      </td>
      <td style="text-align:left">Owner ID</td>
    </tr>
    <tr>
      <td style="text-align:left">view</td>
      <td style="text-align:left"><code>String</code>
      </td>
      <td style="text-align:left">
        <p>View style of collection, can be:</p>
        <ul>
          <li>list (default)</li>
          <li>simple</li>
          <li>grid</li>
          <li>masonry</li>
        </ul>
      </td>
    </tr>
  </tbody>
</table>{% hint style="warning" %}
Our API response could contain **other fields**, not described above. It's **unsafe to use** them in your integration! They could be removed or renamed at any time.
{% endhint %}

### System collections

Every user have several system non-removable collections:

| \_id | Description |
| :--- | :--- |
| **-1** | "**Unsorted**" collection |
| **-99** | "**Trash**" collection |

{% api-method method="get" host="https://api.raindrop.io" path="/rest/v1/collections" %}
{% api-method-summary %}
Get root collections
{% endapi-method-summary %}

{% api-method-description %}
Returns JSON-encoded array containing all root collections
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
  "items": [
    {
      "_id": 8492393,
      "access": {
        "level": 4,
        "draggable": true
      },
      "collaborators": {
        "$id": "5dc1759a0e123be5f2654b6f"
      },
      "color": "#0c797d",
      "count": 16,
      "cover": [
        "https://up.raindrop.io/collection/thumbs/849/239/3/333ce18769311113836cf93a223a14a3.png"
      ],
      "created": "2019-10-09T11:49:53.518Z",
      "expanded": false,
      "lastUpdate": "2019-11-27T17:51:19.085Z",
      "public": false,
      "sort": 8492393,
      "title": "Development",
      "user": {
        "$id": 32
      },
      "view": "list"
    }
  ]
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="https://api.raindrop.io" path="/rest/v1/collections/childrens" %}
{% api-method-summary %}
Get nested collections
{% endapi-method-summary %}

{% api-method-description %}
Returns JSON-encoded array containing all nested collections
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
  "items": [
    {
      "_id": 8492393,
      "access": {
        "level": 4,
        "draggable": true
      },
      "collaborators": {
        "$id": "5dc1759a0e123be5f2654b6f"
      },
      "color": "#0c797d",
      "count": 16,
      "cover": [
        "https://up.raindrop.io/collection/thumbs/849/239/3/333ce18769311113836cf93a223a14a3.png"
      ],
      "created": "2019-10-09T11:49:53.518Z",
      "expanded": false,
      "lastUpdate": "2019-11-27T17:51:19.085Z",
      "parent_id": 1111,
      "public": false,
      "sort": 8492393,
      "title": "Development",
      "user": {
        "$id": 32
      },
      "view": "list"
    }
  ]
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="https://api.raindrop.io" path="/rest/v1/collection/:id" %}
{% api-method-summary %}
Get single collection
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="number" required=true %}
Collection ID
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
  "item": {
    "_id": 8492393,
    "access": {
      "for": 32,
      "level": 4,
      "root": true,
      "draggable": true
    },
    "author": true,
    "collaborators": {
      "$id": "5dc1759a0e123be5f2654b6f"
    },
    "color": "#0c797d",
    "count": 16,
    "cover": [
      "https://up.raindrop.io/collection/thumbs/849/239/3/333ce18769311113836cf93a223a14a3.png"
    ],
    "created": "2019-10-09T11:49:53.518Z",
    "expanded": false,
    "lastUpdate": "2019-11-27T17:51:19.085Z",
    "public": false,
    "sort": 8492393,
    "title": "Development",
    "user": {
      "$id": 32
    },
    "view": "list"
  }
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="post" host="https://api.raindrop.io" path="/rest/v1/collection" %}
{% api-method-summary %}
Create single collection
{% endapi-method-summary %}

{% api-method-description %}
Create a new collection
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-body-parameters %}
{% api-method-parameter name="view" type="string" required=false %}
More details in "Properties"
{% endapi-method-parameter %}

{% api-method-parameter name="title" type="string" required=false %}
Name of the collection
{% endapi-method-parameter %}

{% api-method-parameter name="sort" type="number" required=false %}
The order of collection \(descending\). Defines the position of the collection among all the collections with the same `parent.$id`
{% endapi-method-parameter %}

{% api-method-parameter name="public" type="boolean" required=false %}
Collection and raindrops that it contains will be accessible without authentication?
{% endapi-method-parameter %}

{% api-method-parameter name="parent.$id" type="integer" required=false %}
The ID of parent collection. Empty for root collections
{% endapi-method-parameter %}

{% api-method-parameter name="cover" type="array" required=false %}
Collection cover url
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

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}
Incorrect 'view' field value
{% endapi-method-response-example-description %}

```javascript
{
    "result": false,
    "error": "view",
    "errorMessage": "Collection validation failed: view: `bla` is not a valid enum value for path `view`."
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="put" host="https://api.raindrop.io" path="/rest/v1/collection/:id" %}
{% api-method-summary %}
Update single collection
{% endapi-method-summary %}

{% api-method-description %}
Update an existing collection
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="number" required=true %}
Existing collection id
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-body-parameters %}
{% api-method-parameter name="expanded" type="boolean" required=false %}
Whether the collection\`s sub-collections are expanded
{% endapi-method-parameter %}

{% api-method-parameter name="view" type="string" required=false %}
More details in "Properties"
{% endapi-method-parameter %}

{% api-method-parameter name="title" type="string" required=false %}
Name of the collection
{% endapi-method-parameter %}

{% api-method-parameter name="sort" type="number" required=false %}
The order of collection \(descending\). Defines the position of the collection among all the collections with the same `parent.$id`
{% endapi-method-parameter %}

{% api-method-parameter name="public" type="boolean" required=false %}
Collection and raindrops that it contains will be accessible without authentication?
{% endapi-method-parameter %}

{% api-method-parameter name="parent.$id" type="integer" required=false %}
The ID of parent collection. Empty for root collections
{% endapi-method-parameter %}

{% api-method-parameter name="cover" type="array" required=false %}
Collection cover url
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

{% api-method method="put" host="https://api.raindrop.io" path="/rest/v1/collection/:id/cover" %}
{% api-method-summary %}
Upload cover for single collection
{% endapi-method-summary %}

{% api-method-description %}
It's possible to upload cover from desktop. PNG, GIF and JPEG supported
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
Existing collection ID
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
        ...
    }
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="delete" host="https://api.raindrop.io" path="/rest/v1/collection/:id" %}
{% api-method-summary %}
Remove single collection
{% endapi-method-summary %}

{% api-method-description %}
Remove an existing collection and all its descendants.  
Raindrops will be moved to "Trash" collection
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

{% api-method method="put" host="https://api.raindrop.io" path="/rest/v1/collections" %}
{% api-method-summary %}
Reorder all collections
{% endapi-method-summary %}

{% api-method-description %}
Updates order of all collections 
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-body-parameters %}
{% api-method-parameter name="sort" type="string" required=true %}
Change order of all collections.  
Possible values:  
"title" - sort alphabetically ascending  
"-title" - sort alphabetically descending  
"-count" - sort by raindrops count descending
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

{% api-method method="put" host="https://api.raindrop.io" path="/rest/v1/collections" %}
{% api-method-summary %}
Expand/collapse all collections
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="expanded" type="boolean" required=true %}
TRUE = expand all  
FALSE = collapse all
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

{% api-method method="put" host="https://api.raindrop.io" path="/rest/v1/collections/clean" %}
{% api-method-summary %}
Remove all empty collections
{% endapi-method-summary %}

{% api-method-description %}

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
    "count": 3
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

