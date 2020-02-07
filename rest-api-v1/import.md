# Import

{% api-method method="post" host="https://api.raindrop.io" path="/rest/v1/import/file" %}
{% api-method-summary %}
Parse HTML import file
{% endapi-method-summary %}

{% api-method-description %}
Convert HTML bookmarks file to JSON.   
Support Nestcape, Pocket and Instapaper file formats
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Content-Type" type="string" required=false %}
multipart/form-data
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-form-data-parameters %}
{% api-method-parameter name="import" type="string" required=false %}
File
{% endapi-method-parameter %}
{% endapi-method-form-data-parameters %}
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
      "title": "Web",
      "folders": [
        {
          "title": "Default",
          "folders": [],
          "bookmarks": [
            {
              "link": "https://aaa.com/a",
              "title": "Name 1",
              "lastUpdate": "2016-09-13T11:17:09.000Z",
              "tags": ["tag"],
              "excerpt": ""
            }
          ]
        }
      ],
      "bookmarks": [
        {
          "link": "https://bbb.com/b",
          "title": "Name 2",
          "lastUpdate": "2016-09-13T11:17:09.000Z",
          "tags": ["tag"],
          "excerpt": ""
        }
      ]
    },
    {
      "title": "Home",
      "folders": [
        {
          "title": "Inspiration",
          "folders": [],
          "bookmarks": [
            {
              "link": "https://ccc.com/c",
              "title": "Name 3",
              "lastUpdate": "2016-09-13T11:17:09.000Z",
              "tags": ["tag"],
              "excerpt": ""
            }
          ]
        }
      ],
      "bookmarks": []
    }
  ]
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

