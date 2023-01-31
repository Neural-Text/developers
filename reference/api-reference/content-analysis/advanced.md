# Advanced

This collection of endpoints will let you to get more results from the content ranking in Google Search or Google News.

**Turnaround time:** up to 1 minute

These endpoints follow the Asynchronous Request-Reply Pattern:

<figure><img src="../../../.gitbook/assets/async-request-fn.jpg" alt=""><figcaption></figcaption></figure>

{% swagger method="post" path="/task/serp/" baseUrl="https://api.neuraltext.com/api/v1" summary="Create task" %}
{% swagger-description %}
Price: **2 API units**

****
{% endswagger-description %}

{% swagger-parameter in="header" name="Authorization" required="true" %}
`Token Your.API.Key`
{% endswagger-parameter %}

{% swagger-parameter in="body" required="true" name="keywords" type="Array" %}
A list of keywords you want to analyze. Maximum length is 

`3`

 .
{% endswagger-parameter %}

{% swagger-parameter in="body" name="country" required="true" %}
2-letters country code.

Default `us`.
{% endswagger-parameter %}

{% swagger-parameter in="body" name="language" required="true" %}
2-letters language code.

Default `en`.
{% endswagger-parameter %}

{% swagger-parameter in="body" name="engine" type="String" %}
`google-search`

 (default) or 

`google-news`
{% endswagger-parameter %}

{% swagger-response status="201: Created" description="Task created" %}
```json
{
    "message": "Task created",
    "id": "3c0a7f54-73da-40f2-b7ed-f39d939424f8",
    "created": "2023-01-12T09:50:31.441600+00:00"
}
```
{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="Bad request" %}
{% code overflow="wrap" %}
```json
{
    "error": "Missing data in payload. This endpoint requires an array of keywords, a country (string, 2-digit country code) and a language (string, 2-digit language code)."
}
```
{% endcode %}
{% endswagger-response %}

{% swagger-response status="401: Unauthorized" description="" %}
```javascript
{
    "error": "Your account is not enabled to perform this action, please contact us."
}
```
{% endswagger-response %}

{% swagger-response status="422: Unprocessable Entity" description="" %}
```javascript
{
  "error": "Insufficient API units"
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger method="get" path="/task/serp/<id>/" baseUrl="https://api.neuraltext.com/api/v1" summary="Get task status" %}
{% swagger-description %}
Price: 

**free**
{% endswagger-description %}

{% swagger-parameter in="header" name="Authorization" required="true" %}
`Token Your.API.Key`
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="Task status" %}
If the status is `loading`

```javascript
{
    "id": "3c0a7f54-73da-40f2-b7ed-f39d939424f8",
    "created": "2023-01-12T09:50:31.441600+00:00",
    "keywords": ["keyword1", "keyword2"],
    "status": "loading",
    "data": {}
}
```

If the status is `completed`

{% code overflow="wrap" %}
```javascript
{
    "id": "3c0a7f54-73da-40f2-b7ed-f39d939424f8",
    "created": "2023-01-12T09:50:31.441600+00:00",
    "keywords": ["keyword1", "keyword2"],
    "status": "completed",
    "data": {
        // Common topics found in search results
        "topics": ["topic1", "topic2"],
        // Questions
        "questions": {
            //From Quora
            "quora": [
                  {"source": 'https://www.quora.com/...",
                   "question": "Question...",
                   "wordcount": 81},
                   ...
                ],
            // From Google Autocomplete and People Also Ask box
            "google_suggest": [
                {"source": "Google Autocomplete",
                "question": "Question2..."},
                ...
                ],
            // Extracted from search results
            "content": [
                {"header": "Question",
                 "domain": "example.com",
                 "title": "Page title",
                 "url": "https://example.com"},
                 ...
            ]
        },
        // Statistics extracted from search results
        "statistics": [
            {"p": ["statitics1", "statisics2"],
             "url": "https://example.com",
             "title": "Page title",
             "domain": "example.com"},
             ...
         ],
       // Search results
       "results": [
           {"title": "Page title",
            "domain": "example.com",
            "url": "https://example.com",
            "description": "Page description",
            "rank": 1,
            "score": 20,
            "wordcount": 200,
            "content": "Page content"},
           ...
       ],
       // List of the page structure for search results
       "outlines": [
           {"title": "Page title",
            "description": "Page description",
            "url": "https://example.com",
            "domain": "example.com",
            "wordcount": 200,
            "rank": 1,
            "score": 20,
            "headers": [
                {"tag": "h1", "text": "Header title"},
                ...
            ]},
           ...
       ],
       // How comprehensive a content should be to have a chance to rank for the query
       // 0 = easy | 100 = difficult
       // https://docs.neuraltext.com/getting-started/document-editor/content-optimization/content-score
       "avg_content_score": 80,
       "avg_wordcount": 80,
       // Average search volume represents the number of times 
       // the keyword was searched on average in the past 12 months
       "avg_search_volume": 800,      
    }
}
```
{% endcode %}
{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="Incomplete payload" %}
```javascript
{
  "error": "Incomplete payload"
}
```
{% endswagger-response %}

{% swagger-response status="401" description="Unathorized request" %}
```javascript
{
    "error": "Your account is not enabled to perform this action, please contact us."
}
```
{% endswagger-response %}

{% swagger-response status="404: Not Found" description="Task not found" %}
```javascript
{
   "error": "Task not found"
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger method="get" path="/task/serp/completed/" baseUrl="https://api.neuraltext.com/api/v1" summary="Get completed tasks" %}
{% swagger-description %}
This endpoint will return all the completed tasks in the last 24 hours.

Price: **free**
{% endswagger-description %}

{% swagger-parameter in="header" name="Authorization" required="true" %}
`Token Your.API.Key`
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="Success response" %}
```javascript
{
  "results": [
      {"id": "3c0a7f54-73da-40f2-b7ed-f39d939424f8",
       "created": "2023-01-12T09:50:31.441600+00:00"},
       ...
       ]
}
```
{% endswagger-response %}

{% swagger-response status="401: Unauthorized" description="Unathorized request" %}
```javascript
{
    "error": "Your account is not enabled to perform this action, please contact us."
}
```
{% endswagger-response %}
{% endswagger %}
