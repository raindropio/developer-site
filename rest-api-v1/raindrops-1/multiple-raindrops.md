# Multiple raindrops

{% api-method method="post" host="https://api.raindrop.io" path="/rest/v1/raindrops" %}
{% api-method-summary %}
Create many raindrops
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-body-parameters %}
{% api-method-parameter name="items" type="array" required=false %}
Array of objects. Format of single object described in "Create single raindrop".  
Maximum 100 objects in array!
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
    "items": [
        {
            ...
        }
    ]
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="put" host="https://api.raindrop.io" path="/rest/v1/raindrops/:collectionId" %}
{% api-method-summary %}
Update many raindrops
{% endapi-method-summary %}

{% api-method-description %}
Specify optional `search` and/or `ids` parameters to limit raindrops that will be updated.  
Possible fields that could be updated are described in "Body Parameters"
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="collectionId" type="number" required=true %}
Collection ID
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-query-parameters %}
{% api-method-parameter name="search" type="string" required=false %}
Format of this parameter described in "Get raindrops" method
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}

{% api-method-body-parameters %}
{% api-method-parameter name="ids" type="array" required=false %}
Exact raindrop ID's ****to be updated
{% endapi-method-parameter %}

{% api-method-parameter name="important" type="boolean" required=false %}
TRUE - mark as "favorite"  
FALSE - unmark as "favorite"
{% endapi-method-parameter %}

{% api-method-parameter name="tags" type="array" required=false %}
Will append specified tags to raindrops.  
Or remove all tags from raindrops if `[]` \(empty array\) is specified
{% endapi-method-parameter %}

{% api-method-parameter name="media" type="array" required=false %}
Will append specified media items to raindrops.  
Or remove all media from raindrops if `[]` \(empty array\) is specified
{% endapi-method-parameter %}

{% api-method-parameter name="cover" type="string" required=false %}
_Tip:_ specify `<screenshot>` to set screenshots for all raindrops
{% endapi-method-parameter %}

{% api-method-parameter name="collection" type="object" required=false %}
Specify `{"$id": collectionId}` to move raindrops to other collection
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

{% api-method method="delete" host="https://api.raindrop.io" path="/rest/v1/raindrops/:collectionId" %}
{% api-method-summary %}
Remove many raindrops
{% endapi-method-summary %}

{% api-method-description %}
Specify optional `search` and/or `ids` parameters to limit raindrops that will be moved to "**Trash**"  
When `:collectionId` is **-99**, raindrops will be permanently removed!
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="collectionId" type="number" required=true %}
Collection ID
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-query-parameters %}
{% api-method-parameter name="search" type="string" required=false %}
Format of this parameter described in "Get raindrops" method
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}

{% api-method-body-parameters %}
{% api-method-parameter name="ids" type="array" required=false %}
Exact raindrop ID's to remove
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
    "modified": 330
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

