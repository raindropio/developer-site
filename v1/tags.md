# Tags

{% swagger baseUrl="https://api.raindrop.io" path="/rest/v1/tags/{collectionId}" method="get" summary="Get tags" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="path" name="collectionId" type="number" %}
Optional collection ID, when not specified all tags from all collections will be retrieved
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```javascript
{
    "result": true,
    "items": [
        {
            "_id": "api",
            "count": 100
        }
    ]
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger baseUrl="https://api.raindrop.io" path="/rest/v1/tags/{collectionId}" method="put" summary="Rename tag" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="path" name="collectionId" type="number" %}
It's possible to restrict rename action to just one collection. It's optional
{% endswagger-parameter %}

{% swagger-parameter in="body" name="replace" type="string" %}
New name
{% endswagger-parameter %}

{% swagger-parameter in="body" name="tags" type="array" %}
Specify 

**array**

 with 

**only one**

 string (name of a tag)
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```javascript
{
    "result": true
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger baseUrl="https://api.raindrop.io" path="/rest/v1/tags/{collectionId}" method="put" summary="Merge tags" %}
{% swagger-description %}
Basically this action rename bunch of 

`tags`

 to new name (

`replace`

 field)
{% endswagger-description %}

{% swagger-parameter in="path" name="collectionId" type="string" %}
It's possible to restrict merge action to just one collection. It's optional
{% endswagger-parameter %}

{% swagger-parameter in="body" name="replace" type="string" %}
New name
{% endswagger-parameter %}

{% swagger-parameter in="body" name="tags" type="array" %}
List of tags
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```javascript
{
    "result": true
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger baseUrl="https://api.raindrop.io" path="/rest/v1/tags/{collectionId}" method="delete" summary="Remove tag(s)" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="path" name="collectionId" type="string" %}
It's possible to restrict remove action to just one collection. It's optional
{% endswagger-parameter %}

{% swagger-parameter in="body" name="tags" type="array" %}
List of tags
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```javascript
{
    "result": true
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger baseUrl="https://api.raindrop.io" path="/rest/v1/tags/suggest/{raindropId}" method="get" summary="Suggest tags" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="path" name="raindropId" type="number" %}
Raindrop ID
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```javascript
{
    "result": true,
    "tags": [
        "app",
        "development"
    ]
}
```
{% endswagger-response %}
{% endswagger %}
