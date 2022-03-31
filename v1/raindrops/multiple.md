---
description: >-
  In this page you will find how to retrieve, create, update or delete multiple
  raindrops at once.
---

# Multiple raindrops

### Common parameters

To filter, sort or limit raindrops use one of the parameters described below. Check each method for exact list of supported parameters.

| Parameter    | Type             | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| ------------ | ---------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| collectionId | `Integer`        | <p>Path parameter that specify from which collection to get raindrops. Or specify one of system:</p><p><code>0</code> to get all (except Trash)</p><p><code>-1</code> to get from "Unsorted"</p><p><code>-99</code> to get from "Trash"</p><p></p><p>Warning: update or remove methods not support <code>0</code> yet. Will be fixed in future.</p>                                                                                                              |
| search       | `String`         | <p>As text, check all <a href="https://help.raindrop.io/using-search#operators">examples here</a></p><p>You can first test your searches in Raindrop app and if it works correctly, just copy content of search field and use it here</p>                                                                                                                                                                                                                        |
| sort         | `String`         | <p>Query parameter for sorting:</p><p><code>-created</code> by date descending (default)</p><p><code>created</code> by date ascending</p><p><code>score</code> by relevancy (only applicable when search is specified)</p><p><code>-sort</code> by order</p><p><code>title</code> by title (ascending)</p><p><code>-title</code> by title (descending)</p><p><code>domain</code> by hostname (ascending)</p><p><code>-domain</code> by hostname (descending)</p> |
| page         | `Integer`        | Query parameter. 0, 1, 2, 3 ...                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| perpage      | `Integer`        | Query parameter. How many raindrops per page. 50 max                                                                                                                                                                                                                                                                                                                                                                                                             |
| ids          | `Array<Integer>` | You can specify exact raindrop ID's for batch update/remove methods                                                                                                                                                                                                                                                                                                                                                                                              |

{% swagger baseUrl="https://api.raindrop.io" path="/rest/v1/raindrops/{collectionId}" method="get" summary="Get raindrops" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="path" name="collectionId" type="number" required="true" %}
Collection ID
{% endswagger-parameter %}

{% swagger-parameter in="query" name="sort" type="string" %}

{% endswagger-parameter %}

{% swagger-parameter in="query" name="perpage" type="number" %}

{% endswagger-parameter %}

{% swagger-parameter in="query" name="page" type="number" %}

{% endswagger-parameter %}

{% swagger-parameter in="query" name="search" type="string" %}

{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
```
{% endswagger-response %}
{% endswagger %}

{% swagger baseUrl="https://api.raindrop.io" path="/rest/v1/raindrops" method="post" summary="Create many raindrops" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="body" name="items" type="array" required="true" %}
Array of objects. Format of single object described in "Create single raindrop".

\


Maximum 100 objects in array!
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```javascript
{
    "result": true,
    "items": [
        {
            ...
        }
    ]
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger baseUrl="https://api.raindrop.io" path="/rest/v1/raindrops/{collectionId}" method="put" summary="Update many raindrops" %}
{% swagger-description %}
Specify optional 

`search`

 and/or 

`ids`

 parameters to limit raindrops that will be updated.

\


Possible fields that could be updated are described in "Body Parameters"
{% endswagger-description %}

{% swagger-parameter in="path" name="collectionId" type="number" required="true" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="ids" type="array" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="important" type="boolean" %}
TRUE - mark as "favorite"

\


FALSE - unmark as "favorite"
{% endswagger-parameter %}

{% swagger-parameter in="body" name="tags" type="array" %}
Will append specified tags to raindrops.

\


Or will remove all tags from raindrops if 

`[]`

 (empty array) is specified
{% endswagger-parameter %}

{% swagger-parameter in="body" name="media" type="array" %}
Will append specified media items to raindrops.

\


Or will remove all media from raindrops if 

`[]`

 (empty array) is specified
{% endswagger-parameter %}

{% swagger-parameter in="body" name="cover" type="string" %}
Set URL for cover.

\


_Tip:_

 specify 

`<screenshot>`

 to set screenshots for all raindrops
{% endswagger-parameter %}

{% swagger-parameter in="body" name="collection" type="object" %}
Specify 

`{"$id": collectionId}`

 to move raindrops to other collection
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
```
{% endswagger-response %}
{% endswagger %}

{% swagger baseUrl="https://api.raindrop.io" path="/rest/v1/raindrops/{collectionId}" method="delete" summary="Remove many raindrops" %}
{% swagger-description %}
Specify optional 

`search`

 and/or 

`ids`

 parameters to limit raindrops that will be moved to "

**Trash**

"

\


When 

`:collectionId`

 is 

**-99**

, raindrops will be permanently removed!
{% endswagger-description %}

{% swagger-parameter in="path" name="collectionId" type="number" required="true" %}

{% endswagger-parameter %}

{% swagger-parameter in="query" name="search" type="string" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="ids" type="array" %}

{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```javascript
{
    "result": true,
    "modified": 330
}
```
{% endswagger-response %}
{% endswagger %}
