# Highlights

{% swagger baseUrl="https://api.raindrop.io" path="/rest/v1/raindrop/{id}" method="get" summary="Get highlights of existing raindrop" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="path" name="id" type="number" required="true" %}
Existing raindrop ID
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```javascript
{
    "result": true,
    "item": {
        "_id": 373777232,
        "highlights": [
            {
                "note": "Trully native macOS app",
                "color": "red",
                "text": "Orion is the new WebKit-based browser for Mac",
                "created": "2022-03-21T14:41:34.059Z",
                "lastUpdate": "2022-03-22T14:30:52.004Z",
                "_id": "62388e9e48b63606f41e44a6"
            },
            {
                "note": "",
                "color": "green",
                "text": "Built on WebKit, Orion gives you a fast, smooth and lightweight browsing experience",
                "created": "2022-03-21T15:13:21.128Z",
                "lastUpdate": "2022-03-22T09:15:18.751Z",
                "_id": "62389611058af151c840f667"
            }
        ]
    }
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger baseUrl="https://api.raindrop.io" path="/rest/v1/raindrop/{id}" method="put" summary="Add highlight to existing raindrop" %}
{% swagger-description %}
Just specify a `highlights` array in body with `object` for each highlight

**Fore example:**

`{"highlights": [ { "text": "Some quote", "color": "red", "note": "Some note" } ] }`
{% endswagger-description %}

{% swagger-parameter in="path" name="id" type="number" required="true" %}
Existing raindrop ID
{% endswagger-parameter %}

{% swagger-parameter in="body" name="highlights" type="array" required="true" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="highlights[].text" required="true" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="highlights[].note" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="highlights[].color" %}

{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```javascript
{
    "result": true,
    "item": {
        "_id": 373777232,
        "highlights": [
            {
                "note": "Trully native macOS app",
                "color": "red",
                "text": "Orion is the new WebKit-based browser for Mac",
                "created": "2022-03-21T14:41:34.059Z",
                "lastUpdate": "2022-03-22T14:30:52.004Z",
                "_id": "62388e9e48b63606f41e44a6"
            },
            {
                "note": "",
                "color": "green",
                "text": "Built on WebKit, Orion gives you a fast, smooth and lightweight browsing experience",
                "created": "2022-03-21T15:13:21.128Z",
                "lastUpdate": "2022-03-22T09:15:18.751Z",
                "_id": "62389611058af151c840f667"
            }
        ]
    }
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger baseUrl="https://api.raindrop.io" path="/rest/v1/raindrop/{id}" method="put" summary="Update highlight of existing raindrop" %}
{% swagger-description %}
Just specify a `highlights` array in body with `object` containing particular `_id` of highlight you want to update and all other fields you want to change.

**Fore example:**

`{"highlights": [ { "_id": "62388e9e48b63606f41e44a6", "note": "New note" } ] }`
{% endswagger-description %}

{% swagger-parameter in="path" name="id" type="number" required="true" %}
Existing raindrop ID
{% endswagger-parameter %}

{% swagger-parameter in="body" name="highlights" type="array" required="true" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="highlights[]._id" required="true" %}
Particular highlight _id you want to remove
{% endswagger-parameter %}

{% swagger-parameter in="body" name="highlights[].text" required="false" %}
Should be empty string
{% endswagger-parameter %}

{% swagger-parameter in="body" name="highlights[].note" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="highlights[].color" %}

{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```javascript
{
    "result": true,
    "item": {
        "_id": 373777232,
        "highlights": [
            {
                "note": "Trully native macOS app",
                "color": "red",
                "text": "Orion is the new WebKit-based browser for Mac",
                "created": "2022-03-21T14:41:34.059Z",
                "lastUpdate": "2022-03-22T14:30:52.004Z",
                "_id": "62388e9e48b63606f41e44a6"
            },
            {
                "note": "",
                "color": "green",
                "text": "Built on WebKit, Orion gives you a fast, smooth and lightweight browsing experience",
                "created": "2022-03-21T15:13:21.128Z",
                "lastUpdate": "2022-03-22T09:15:18.751Z",
                "_id": "62389611058af151c840f667"
            }
        ]    }}
```
{% endswagger-response %}
{% endswagger %}

{% swagger baseUrl="https://api.raindrop.io" path="/rest/v1/raindrop/{id}" method="put" summary="Remove highlight from existing raindrop" %}
{% swagger-description %}
Just specify a `highlights` array in body with `object` containing particular `_id` of highlight you want to remove and empty string for `text` field.

**Fore example:**

`{"highlights": [ { "_id": "62388e9e48b63606f41e44a6", "text": "" } ] }`
{% endswagger-description %}

{% swagger-parameter in="path" name="id" type="number" required="true" %}
Existing raindrop ID
{% endswagger-parameter %}

{% swagger-parameter in="body" name="highlights" type="array" required="true" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="highlights[]._id" required="true" %}
Particular highlight _id you want to remove
{% endswagger-parameter %}

{% swagger-parameter in="body" name="highlights[].text" required="true" %}
Should be empty string
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```javascript
{
    "result": true,
    "item": {
        "_id": 373777232,
        "highlights": [
            {
                "note": "Trully native macOS app",
                "color": "red",
                "text": "Orion is the new WebKit-based browser for Mac",
                "created": "2022-03-21T14:41:34.059Z",
                "lastUpdate": "2022-03-22T14:30:52.004Z",
                "_id": "62388e9e48b63606f41e44a6"
            },
            {
                "note": "",
                "color": "green",
                "text": "Built on WebKit, Orion gives you a fast, smooth and lightweight browsing experience",
                "created": "2022-03-21T15:13:21.128Z",
                "lastUpdate": "2022-03-22T09:15:18.751Z",
                "_id": "62389611058af151c840f667"
            }
        ]
    }}
```
{% endswagger-response %}
{% endswagger %}
