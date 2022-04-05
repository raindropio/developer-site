---
description: Handy methods to implement import functionality
---

# Import

{% swagger baseUrl="https://api.raindrop.io" path="/rest/v1/import/url/parse" method="get" summary="Parse URL" %}
{% swagger-description %}
Parse and extract useful info from any URL
{% endswagger-description %}

{% swagger-parameter in="query" name="url" type="string" %}
URL
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```javascript
//Success
{
  "item": {
    "title": "Яндекс",
    "excerpt": "Найдётся всё",
    "media": [
      {
        "type": "image",
        "link": "http://yastatic.net/s3/home/logos/share/share-logo_ru.png"
      }
    ],
    "type": "link",
    "meta": {
      "possibleArticle": false,
      "canonical": "https://ya.ru",
      "site": "Яндекс",
      "tags": []
    }
  },
  "result": true
}

//Invalid URL
{
  "error": "not_found",
  "errorMessage": "invalid_url",
  "item": {
    "title": "Fdfdfdf",
    "excerpt": "",
    "media": [
      {
        "link": "<screenshot>"
      }
    ],
    "type": "link",
    "parser": "local",
    "meta": {
      "possibleArticle": false,
      "tags": []
    }
  },
  "result": true
}

//Not found
{
  "error": "not_found",
  "errorMessage": "url_status_404",
  "item": {
    "title": "Some",
    "excerpt": "",
    "media": [
      {
        "link": "<screenshot>"
      }
    ],
    "type": "link",
    "parser": "local",
    "meta": {
      "possibleArticle": false,
      "tags": []
    }
  },
  "result": true
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger baseUrl="https://api.raindrop.io" path="/rest/v1/import/url/exists" method="post" summary="Check URL(s) existence " %}
{% swagger-description %}
Does specified URL's are already saved?
{% endswagger-description %}

{% swagger-parameter in="body" name="urls" type="array" %}
URL's
{% endswagger-parameter %}

{% swagger-response status="200" description="ids array contains ID of existing bookmarks" %}
```javascript
//Found
{
    "result": true,
    "ids": [
        3322,
        12323
    ]
}

//Not found
{
    "result": false,
    "ids": []
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger baseUrl="https://api.raindrop.io" path="/rest/v1/import/file" method="post" summary="Parse HTML import file" %}
{% swagger-description %}
Convert HTML bookmark file to JSON. 

\


Support Nestcape, Pocket and Instapaper file formats
{% endswagger-description %}

{% swagger-parameter in="header" name="Content-Type" type="string" %}
multipart/form-data
{% endswagger-parameter %}

{% swagger-parameter in="body" name="import" type="string" %}
File
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
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
{% endswagger-response %}
{% endswagger %}
