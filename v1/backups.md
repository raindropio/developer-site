# Backups

{% swagger baseUrl="https://api.raindrop.io" path="/rest/v1/backups" method="get" summary="Get all" %}
{% swagger-description %}
Useful to get backup ID's that can be used in `/backup/{ID}.{format}` endpoint.

Sorted by date (new first)
{% endswagger-description %}

{% swagger-response status="200" description="" %}
```json
{
    "result": true,
    "items": [
        {
            "_id": "659d42a35ffbb2eb5ae1cb86",
            "created": "2024-01-09T12:57:07.630Z"
        }
    ]
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger baseUrl="https://api.raindrop.io" path="/rest/v1/backup/{ID}.{format}" method="get" summary="Download file" %}
{% swagger-description %}
For example:

`https://api.raindrop.io/rest/v1/backup/659d42a35ffbb2eb5ae1cb86.csv`
{% endswagger-description %}

{% swagger-parameter in="path" required="true" name="ID" %}
Backup ID
{% endswagger-parameter %}

{% swagger-parameter in="path" name="format" required="true" %}
File format: `html` or `csv`
{% endswagger-parameter %}
{% endswagger %}

{% swagger baseUrl="https://api.raindrop.io" path="/rest/v1/backup" method="get" summary="Generate new" %}
{% swagger-description %}
Useful to create a brand new backup. This requires some time.

New backup will appear in the list of `/backups` endpoint
{% endswagger-description %}

{% swagger-response status="200" description="" %}
```
We will send you email with html export file when it be ready! Time depends on bookmarks count and queue.
```
{% endswagger-response %}
{% endswagger %}
