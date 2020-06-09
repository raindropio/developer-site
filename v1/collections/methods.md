# Collection methods

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
Get child collections
{% endapi-method-summary %}

{% api-method-description %}
Returns JSON-encoded array containing all nested collections \(that have positive `parent.$id`\)
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

{% api-method method="get" host="https://api.raindrop.io" path="/rest/v1/collection/{id}" %}
{% api-method-summary %}
Get collection
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
Create collection
{% endapi-method-summary %}

{% api-method-description %}
Create a new collection
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-body-parameters %}
{% api-method-parameter name="view" type="string" required=false %}
More details in "Fields"
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

{% api-method method="put" host="https://api.raindrop.io" path="/rest/v1/collection/{id}" %}
{% api-method-summary %}
Update collection
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
More details in "Fields"
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

{% api-method method="put" host="https://api.raindrop.io" path="/rest/v1/collection/{id}/cover" %}
{% api-method-summary %}
Upload cover
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

{% api-method method="delete" host="https://api.raindrop.io" path="/rest/v1/collection/{id}" %}
{% api-method-summary %}
Remove collection
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

{% api-method method="delete" host="https://api.raindrop.io" path="/rest/v1/collections" %}
{% api-method-summary %}
Remove multiple collections
{% endapi-method-summary %}

{% api-method-description %}
Remove multiple collections at once.  
Nested collections are ignored \(include ID's in `ids` array to remove them\)
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-body-parameters %}
{% api-method-parameter name="ids" type="array" required=true %}
Array of collection ID
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```

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

{% api-method method="put" host="https://api.raindrop.io" path="/rest/v1/collections/merge" %}
{% api-method-summary %}
Merge collections
{% endapi-method-summary %}

{% api-method-description %}
Merge multiple collections
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-body-parameters %}
{% api-method-parameter name="to" type="number" required=false %}
Collection ID where listed collection `ids` will be merged
{% endapi-method-parameter %}

{% api-method-parameter name="ids" type="array" required=false %}
Collection ID's
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```

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

{% api-method method="delete" host="https://api.raindrop.io" path="/rest/v1/collection/-99" %}
{% api-method-summary %}
Empty Trash
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
  "result": true
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="https://api.raindrop.io" path="/rest/v1/user/stats" %}
{% api-method-summary %}
Get system collections count
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
  "items": [
    {
      "_id": 0,
      "count": 1570
    },
    {
      "_id": -1,
      "count": 34
    },
    {
      "_id": -99,
      "count": 543
    }
  ],
  "meta": {
    "pro": true,
    "_id": 32,
    "changedBookmarksDate": "2020-02-11T11:23:43.143Z",
    "duplicates": {
      "count": 3
    },
    "broken": {
      "count": 31
    }
  },
  "result": true
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}



