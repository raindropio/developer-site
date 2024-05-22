# Collection methods

## Get root collections

<mark style="color:blue;">`GET`</mark> `https://api.raindrop.io/rest/v1/collections`

Returns JSON-encoded array containing all root collections

{% tabs %}
{% tab title="200 " %}
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
{% endtab %}
{% endtabs %}

## Get child collections

<mark style="color:blue;">`GET`</mark> `https://api.raindrop.io/rest/v1/collections/childrens`

Returns JSON-encoded array containing all nested collections (that have positive `parent.$id`)

{% tabs %}
{% tab title="200 " %}
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
      "parent": { "$id": 1111 },
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
{% endtab %}
{% endtabs %}

## Get collection

<mark style="color:blue;">`GET`</mark> `https://api.raindrop.io/rest/v1/collection/{id}`

#### Path Parameters

| Name | Type   | Description   |
| ---- | ------ | ------------- |
| id   | number | Collection ID |

{% tabs %}
{% tab title="200 " %}
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
{% endtab %}
{% endtabs %}

## Create collection

<mark style="color:green;">`POST`</mark> `https://api.raindrop.io/rest/v1/collection`

Create a new collection

#### Request Body

| Name       | Type    | Description                                                                                                                       |
| ---------- | ------- | --------------------------------------------------------------------------------------------------------------------------------- |
| view       | string  | More details in "Fields"                                                                                                          |
| title      | string  | Name of the collection                                                                                                            |
| sort       | number  | The order of collection (descending). Defines the position of the collection among all the collections with the same `parent.$id` |
| public     | boolean | Collection and raindrops that it contains will be accessible without authentication?                                              |
| parent.$id | integer | The ID of parent collection. Empty for root collections                                                                           |
| cover      | array   | Collection cover url                                                                                                              |

{% tabs %}
{% tab title="200 " %}
```javascript
{
    "result": true,
    "item": {
        ...
    }
}
```
{% endtab %}

{% tab title="400 Incorrect 'view' field value" %}
```javascript
{
    "result": false,
    "error": "view",
    "errorMessage": "Collection validation failed: view: `bla` is not a valid enum value for path `view`."
}
```
{% endtab %}
{% endtabs %}

## Update collection

<mark style="color:orange;">`PUT`</mark> `https://api.raindrop.io/rest/v1/collection/{id}`

Update an existing collection

#### Path Parameters

| Name | Type   | Description            |
| ---- | ------ | ---------------------- |
| id   | number | Existing collection id |

#### Request Body

| Name       | Type    | Description                                                                                                                       |
| ---------- | ------- | --------------------------------------------------------------------------------------------------------------------------------- |
| expanded   | boolean | Whether the collection\`s sub-collections are expanded                                                                            |
| view       | string  | More details in "Fields"                                                                                                          |
| title      | string  | Name of the collection                                                                                                            |
| sort       | number  | The order of collection (descending). Defines the position of the collection among all the collections with the same `parent.$id` |
| public     | boolean | Collection and raindrops that it contains will be accessible without authentication?                                              |
| parent.$id | integer | The ID of parent collection. Empty for root collections                                                                           |
| cover      | array   | Collection cover url                                                                                                              |

{% tabs %}
{% tab title="200 " %}
```javascript
{
    "result": true,
    "item": {
        ...
    }
}
```
{% endtab %}
{% endtabs %}

## Upload cover

<mark style="color:orange;">`PUT`</mark> `https://api.raindrop.io/rest/v1/collection/{id}/cover`

It's possible to upload cover from desktop. PNG, GIF and JPEG supported

#### Path Parameters

| Name | Type   | Description            |
| ---- | ------ | ---------------------- |
| id   | string | Existing collection ID |

#### Headers

| Name         | Type   | Description         |
| ------------ | ------ | ------------------- |
| Content-Type | string | multipart/form-data |

#### Request Body

| Name  | Type   | Description |
| ----- | ------ | ----------- |
| cover | object | File        |

{% tabs %}
{% tab title="200 " %}
```javascript
{
    "result": true,
    "item": {
        ...
    }
}
```
{% endtab %}
{% endtabs %}

## Remove collection

<mark style="color:red;">`DELETE`</mark> `https://api.raindrop.io/rest/v1/collection/{id}`

Remove an existing collection and all its descendants.\
Raindrops will be moved to "Trash" collection

#### Path Parameters

| Name | Type   | Description            |
| ---- | ------ | ---------------------- |
| id   | number | Existing collection ID |

{% tabs %}
{% tab title="200 " %}
```javascript
{
    "result": true
}
```
{% endtab %}
{% endtabs %}

## Remove multiple collections

<mark style="color:red;">`DELETE`</mark> `https://api.raindrop.io/rest/v1/collections`

Remove multiple collections at once.\
Nested collections are ignored (include ID's in `ids` array to remove them)

#### Request Body

| Name | Type  | Description            |
| ---- | ----- | ---------------------- |
| ids  | array | Array of collection ID |

{% tabs %}
{% tab title="200 " %}
```
```
{% endtab %}
{% endtabs %}

## Reorder all collections

<mark style="color:orange;">`PUT`</mark> `https://api.raindrop.io/rest/v1/collections`

Updates order of all collections&#x20;

#### Request Body

| Name | Type   | Description                                                                                                                                                                                          |
| ---- | ------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| sort | string | <p>Change order of all collections.<br>Possible values:<br>"title" - sort alphabetically ascending<br>"-title" - sort alphabetically descending<br>"-count" - sort by raindrops count descending</p> |

{% tabs %}
{% tab title="200 " %}
```javascript
{
    "result": true
}
```
{% endtab %}
{% endtabs %}

## Expand/collapse all collections

<mark style="color:orange;">`PUT`</mark> `https://api.raindrop.io/rest/v1/collections`

#### Path Parameters

| Name     | Type    | Description                                      |
| -------- | ------- | ------------------------------------------------ |
| expanded | boolean | <p>TRUE = expand all<br>FALSE = collapse all</p> |

{% tabs %}
{% tab title="200 " %}
```javascript
{
    "result": true
}
```
{% endtab %}
{% endtabs %}

## Merge collections

<mark style="color:orange;">`PUT`</mark> `https://api.raindrop.io/rest/v1/collections/merge`

Merge multiple collections

#### Request Body

| Name | Type   | Description                                                |
| ---- | ------ | ---------------------------------------------------------- |
| to   | number | Collection ID where listed collection `ids` will be merged |
| ids  | array  | Collection ID's                                            |

{% tabs %}
{% tab title="200 " %}
```
```
{% endtab %}
{% endtabs %}

## Remove all empty collections

<mark style="color:orange;">`PUT`</mark> `https://api.raindrop.io/rest/v1/collections/clean`

{% tabs %}
{% tab title="200 " %}
```javascript
{
    "result": true,
    "count": 3
}
```
{% endtab %}
{% endtabs %}

## Empty Trash

<mark style="color:red;">`DELETE`</mark> `https://api.raindrop.io/rest/v1/collection/-99`

{% tabs %}
{% tab title="200 " %}
```javascript
{
  "result": true
}
```
{% endtab %}
{% endtabs %}

## Get system collections count

<mark style="color:blue;">`GET`</mark> `https://api.raindrop.io/rest/v1/user/stats`

{% tabs %}
{% tab title="200 " %}
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
{% endtab %}
{% endtabs %}

