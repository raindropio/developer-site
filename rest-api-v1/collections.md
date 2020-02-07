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
      <td style="text-align:left">The id of the collection</td>
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
      <td style="text-align:left">collaborators.$id</td>
      <td style="text-align:left"><code>String</code>
      </td>
      <td style="text-align:left">Id of collaboration object</td>
    </tr>
    <tr>
      <td style="text-align:left">color</td>
      <td style="text-align:left"><code>String</code>
      </td>
      <td style="text-align:left">Primary color of collection icon as <code>HEX</code>
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
      <td style="text-align:left">Collection icon.
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
</table>{% api-method method="get" host="https://api.raindrop.io" path="/rest/v1/collections" %}
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
{% api-method-parameter name="id" type="number" required=false %}
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
Create collection
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

{% api-method-parameter name="title" type="string" required=true %}
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
Collection icon url
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
        
    }
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="put" host="https://api.raindrop.io" path="/rest/v1/collection/:id" %}
{% api-method-summary %}
Update collection
{% endapi-method-summary %}

{% api-method-description %}
Update an existing collection
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="number" required=false %}
Existing collection id
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

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
Collection icon url
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
        
    }
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}



