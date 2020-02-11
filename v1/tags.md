# Tags

{% api-method method="get" host="https://api.raindrop.io" path="/rest/v1/tags/{collectionId}" %}
{% api-method-summary %}
Get tags
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="collectionId" type="number" required=false %}
Optional collection ID, when not specified all tags from all collections will be retrieved
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
    "items": [
        {
            "_id": "api",
            "count": 100
        }
    ]
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="put" host="https://api.raindrop.io" path="/rest/v1/tags/{collectionId}" %}
{% api-method-summary %}
Rename tag
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="collectionId" type="number" required=false %}
It's possible to restrict rename action to just one collection. It's optional
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-body-parameters %}
{% api-method-parameter name="replace" type="string" required=true %}
New name
{% endapi-method-parameter %}

{% api-method-parameter name="tags" type="array" required=true %}
Specify **array** with **only one** string \(name of a tag\)
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

{% api-method method="put" host="https://api.raindrop.io" path="/rest/v1/tags/{collectionId}" %}
{% api-method-summary %}
Merge tags
{% endapi-method-summary %}

{% api-method-description %}
Basically this action rename bunch of `tags` to new name \(`replace` field\)
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="collectionId" type="string" required=false %}
It's possible to restrict merge action to just one collection. It's optional
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-body-parameters %}
{% api-method-parameter name="replace" type="string" required=true %}
New name
{% endapi-method-parameter %}

{% api-method-parameter name="tags" type="array" required=true %}
List of tags
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

{% api-method method="delete" host="https://api.raindrop.io" path="/rest/v1/tags/{collectionId}" %}
{% api-method-summary %}
Remove tag\(s\)
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="collectionId" type="string" required=false %}
It's possible to restrict remove action to just one collection. It's optional
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-body-parameters %}
{% api-method-parameter name="tags" type="array" required=true %}
List of tags
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

{% api-method method="get" host="https://api.raindrop.io" path="/rest/v1/tags/suggest/{raindropId}" %}
{% api-method-summary %}
Suggest tags
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="raindropId" type="number" required=true %}
Raindrop ID
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
    "tags": [
        "app",
        "development"
    ]
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

