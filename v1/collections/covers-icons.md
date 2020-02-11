# Covers/icons

In your UI implementation you could easily make icon/cover selector from more than 10 000 icons.

{% api-method method="get" host="https://api.raindrop.io" path="/rest/v1/collections/covers/{text}" %}
{% api-method-summary %}
Search for cover
{% endapi-method-summary %}

{% api-method-description %}
Search for specific cover \(icon\)
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="text" type="string" required=false %}
For example "pokemon"
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
  "items": [
    {
      "title": "Icons8",
      "icons": [
        {
          "png": "https://rd-icons-icons8.gumlet.com/color/5x/mystic-pokemon.png?fill-color=transparent"
        }
      ]
    },
    {
      "title": "Iconfinder",
      "icons": [
        {
          "png": "https://cdn4.iconfinder.com/data/icons/pokemon-go/512/Pokemon_Go-01-128.png",
          "svg": "https://api.iconfinder.com/v2/icons/1320040/formats/svg/1760420/download"
        }
      ]
    }
  ],
  "result": true
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="https://api.raindrop.io" path="/rest/v1/collections/covers" %}
{% api-method-summary %}
Featured covers
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="" type="string" required=false %}

{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
  "items": [
    {
      "title": "Colors circle",
      "icons": [
        {
          "png": "https://up.raindrop.io/collection/templates/colors/ios1.png"
        }
      ]
    },
    {
      "title": "Hockey",
      "icons": [
        {
          "png": "https://up.raindrop.io/collection/templates/hockey-18/12i.png"
        }
      ]
    }
  ]
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

