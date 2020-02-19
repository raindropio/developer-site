# Filters

To help users easily find their content you can suggest context aware filters like we have in Raindrop.io app

![Filters right above search field](../.gitbook/assets/filters%20%281%29.png)

### Fields

| Field | Type | Description |
| :--- | :--- | :--- |
| broken | `Object` |  |
| broken.count | `Integer` | Broken links count |
| duplicates | `Object` |  |
| duplicates.count | `Integer` | Duplicate links count |
| important | `Object` |  |
| important.count | `Integer` | Count of raindrops that marked as "favorite" |
| notag | `Object` |  |
| notag.count | `Integer` | Count of raindrops without any tag |
| tags | `Array<Object>` | List of tags in format `{"_id": "tag name", "count": 1}` |
| types | `Array<Object>` | List of types in format `{"_id": "type", "count": 1}` |

{% api-method method="get" host="https://api.raindrop.io" path="/rest/v1/raindrops/{collectionId}/filters" %}
{% api-method-summary %}
Get filters
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="collectionId" type="string" required=true %}
Collection ID. `0` for all
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-query-parameters %}
{% api-method-parameter name="search" type="string" required=false %}
Check "raindrops" documentation for more details
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
  "result": true,
  "broken": {
    "count": 31
  },
  "duplicates": {
    "count": 7
  },
  "important": {
    "count": 59
  },
  "notag": {
    "count": 1366
  },
  "tags": [
    {
      "_id": "performanc",
      "count": 19
    },
    {
      "_id": "guides",
      "count": 9
    }
  ],
  "types": [
    {
      "_id": "article",
      "count": 313
    },
    {
      "_id": "image",
      "count": 143
    },
    {
      "_id": "video",
      "count": 26
    },
    {
      "_id": "document",
      "count": 7
    }
  ]
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

