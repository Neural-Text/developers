# SERP Analysis

### Tasks Ready

{% swagger method="get" path="/ready/" baseUrl="https://api.neuraltext.com/api/v1/tasks" summary="Get ready tasks" %}
{% swagger-description %}
Price: **free**

Get the task ready created in the past 24 hours.
{% endswagger-description %}

{% swagger-parameter in="header" name="Authorization" required="true" %}
`Token Your.API.Key`
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="Success response" %}
```javascript
{
    // Response
}
```
{% endswagger-response %}
{% endswagger %}

### Create task

The task&#x20;

{% swagger method="post" path="/task/create/" baseUrl="https://api.neuraltext.com/api/v1" summary="Start the analysis of SERP" %}
{% swagger-description %}
Price: **2 API units**

****
{% endswagger-description %}

{% swagger-parameter in="header" name="Authorization" required="true" %}
`Token Your.API.Key`
{% endswagger-parameter %}

{% swagger-parameter in="body" required="true" name="keywords" type="Array" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="location" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="language" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="engine" type="String" %}
`google-search`

 (default) or 

`google-news`
{% endswagger-parameter %}

{% swagger-parameter in="body" name="webhook" type="String" %}

{% endswagger-parameter %}
{% endswagger %}

### Task Detail

{% swagger method="get" path="/task/<id>/" baseUrl="https://api.neuraltext.com/api/v1" summary="Get SERP data" %}
{% swagger-description %}
Price: 

**free**
{% endswagger-description %}

{% swagger-parameter in="header" name="Authorization" %}
`Token Your.API.Key`
{% endswagger-parameter %}
{% endswagger %}
