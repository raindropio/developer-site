# Collection methods

{% swagger baseUrl="https://api.raindrop.io" path="/rest/v1/collections" method="get" summary="Get root collections" %}
{% swagger-description %}
Returns JSON-encoded array containing all root collections
{% endswagger-description %}

{% swagger-response status="200" description="" %}
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
{% endswagger-response %}
{% endswagger %}

{% swagger baseUrl="https://api.raindrop.io" path="/rest/v1/collections/childrens" method="get" summary="Get child collections" %}
{% swagger-description %}
Returns JSON-encoded array containing all nested collections (that have positive 

`parent.$id`

)
{% endswagger-description %}

{% swagger-response status="200" description="" %}
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
{% endswagger-response %}
{% endswagger %}

{% swagger baseUrl="https://api.raindrop.io" path="/rest/v1/collection/{id}" method="get" summary="Get collection" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="path" name="id" type="number" %}
Collection ID
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
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
{% endswagger-response %}
{% endswagger %}

{% swagger baseUrl="https://api.raindrop.io" path="/rest/v1/collection" method="post" summary="Create collection" %}
{% swagger-description %}
Create a new collection
{% endswagger-description %}

{% swagger-parameter in="body" name="view" type="string" %}
More details in "Fields"
{% endswagger-parameter %}

{% swagger-parameter in="body" name="title" type="string" %}
Name of the collection
{% endswagger-parameter %}

{% swagger-parameter in="body" name="sort" type="number" %}
The order of collection (descending). Defines the position of the collection among all the collections with the same 

`parent.$id`
{% endswagger-parameter %}

{% swagger-parameter in="body" name="public" type="boolean" %}
Collection and raindrops that it contains will be accessible without authentication?
{% endswagger-parameter %}

{% swagger-parameter in="body" name="parent.$id" type="integer" %}
The ID of parent collection. Empty for root collections
{% endswagger-parameter %}

{% swagger-parameter in="body" name="cover" type="array" %}
Collection cover url
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```javascript
{
    "result": true,
    "item": {
        ...
    }
}
```
{% endswagger-response %}

{% swagger-response status="400" description="Incorrect 'view' field value" %}
```javascript
{
    "result": false,
    "error": "view",
    "errorMessage": "Collection validation failed: view: `bla` is not a valid enum value for path `view`."
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger baseUrl="https://api.raindrop.io" path="/rest/v1/collection/{id}" method="put" summary="Update collection" %}
{% swagger-description %}
Update an existing collection
{% endswagger-description %}

{% swagger-parameter in="path" name="id" type="number" %}
Existing collection id
{% endswagger-parameter %}

{% swagger-parameter in="body" name="expanded" type="boolean" %}
Whether the collection`s sub-collections are expanded
{% endswagger-parameter %}

{% swagger-parameter in="body" name="view" type="string" %}
More details in "Fields"
{% endswagger-parameter %}

{% swagger-parameter in="body" name="title" type="string" %}
Name of the collection
{% endswagger-parameter %}

{% swagger-parameter in="body" name="sort" type="number" %}
The order of collection (descending). Defines the position of the collection among all the collections with the same 

`parent.$id`
{% endswagger-parameter %}

{% swagger-parameter in="body" name="public" type="boolean" %}
Collection and raindrops that it contains will be accessible without authentication?
{% endswagger-parameter %}

{% swagger-parameter in="body" name="parent.$id" type="integer" %}
The ID of parent collection. Empty for root collections
{% endswagger-parameter %}

{% swagger-parameter in="body" name="cover" type="array" %}
Collection cover url
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```javascript
{
    "result": true,
    "item": {
        ...
    }
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger baseUrl="https://api.raindrop.io" path="/rest/v1/collection/{id}/cover" method="put" summary="Upload cover" %}
{% swagger-description %}
It's possible to upload cover from desktop. PNG, GIF and JPEG supported
{% endswagger-description %}

{% swagger-parameter in="path" name="id" type="string" %}
Existing collection ID
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Content-Type" type="string" %}
multipart/form-data
{% endswagger-parameter %}

{% swagger-parameter in="body" name="cover" type="object" %}
File
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```javascript
{
    "result": true,
    "item": {
        ...
    }
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger baseUrl="https://api.raindrop.io" path="/rest/v1/collection/{id}" method="delete" summary="Remove collection" %}
{% swagger-description %}
Remove an existing collection and all its descendants.

\


Raindrops will be moved to "Trash" collection
{% endswagger-description %}

{% swagger-parameter in="path" name="id" type="number" %}
Existing collection ID
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```javascript
{
    "result": true
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger baseUrl="https://api.raindrop.io" path="/rest/v1/collections" method="delete" summary="Remove multiple collections" %}
{% swagger-description %}
Remove multiple collections at once.

\


Nested collections are ignored (include ID's in 

`ids`

 array to remove them)
{% endswagger-description %}

{% swagger-parameter in="body" name="ids" type="array" %}
Array of collection ID
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
```
{% endswagger-response %}
{% endswagger %}

{% swagger baseUrl="https://api.raindrop.io" path="/rest/v1/collections" method="put" summary="Reorder all collections" %}
{% swagger-description %}
Updates order of all collections 
{% endswagger-description %}

{% swagger-parameter in="body" name="sort" type="string" %}
Change order of all collections.

\


Possible values:

\


"title" - sort alphabetically ascending

\


"-title" - sort alphabetically descending

\


"-count" - sort by raindrops count descending
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```javascript
{
    "result": true
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger baseUrl="https://api.raindrop.io" path="/rest/v1/collections" method="put" summary="Expand/collapse all collections" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="path" name="expanded" type="boolean" %}
TRUE = expand all

\


FALSE = collapse all
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```javascript
{
    "result": true
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger baseUrl="https://api.raindrop.io" path="/rest/v1/collections/merge" method="put" summary="Merge collections" %}
{% swagger-description %}
Merge multiple collections
{% endswagger-description %}

{% swagger-parameter in="body" name="to" type="number" %}
Collection ID where listed collection 

`ids`

 will be merged
{% endswagger-parameter %}

{% swagger-parameter in="body" name="ids" type="array" %}
Collection ID's
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
```
{% endswagger-response %}
{% endswagger %}

{% swagger baseUrl="https://api.raindrop.io" path="/rest/v1/collections/clean" method="put" summary="Remove all empty collections" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-response status="200" description="" %}
```javascript
{
    "result": true,
    "count": 3
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger baseUrl="https://api.raindrop.io" path="/rest/v1/collection/-99" method="delete" summary="Empty Trash" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-response status="200" description="" %}
```javascript
{
  "result": true
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger baseUrl="https://api.raindrop.io" path="/rest/v1/user/stats" method="get" summary="Get system collections count" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-response status="200" description="" %}
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
{% endswagger-response %}
{% endswagger %}

