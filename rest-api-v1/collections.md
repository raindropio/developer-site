# Collections

{% api-method method="get" host="https://api.raindrop.io/rest" path="/v1/collections" %}
{% api-method-summary %}
Get all collections
{% endapi-method-summary %}

{% api-method-description %}
Returns JSON-encoded array containing all user collections
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
{
  "result": true,
  "items": [
    {
      "title": "Development",
      "public": false,
      "view": "list",
      "count": 16,
      "cover": [
        "https://up.raindrop.io/collection/thumbs/849/239/3/333ce18769311113836cf93a223a14a3.png"
      ],
      "expanded": false,
      "_id": 8492393,
      "user": {
        "$id": 32,
      },
      "creatorRef": 32,
      "created": "2019-10-09T11:49:53.518Z",
      "lastUpdate": "2019-11-27T17:51:19.085Z",
      "sort": 8492393,
      "color": "#0c797d",
      "collaborators": {
        "$id": "5dc1759a0e123be5f2654b6f",
      },
      "access": {
        "for": 32,
        "level": 4,
        "root": true,
        "draggable": true
      },
      "author": true
    }
  ]
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

