# Projects

### List or search projects

{% swagger baseUrl="https://api.neuraltext.com/api/v1" method="get" path="/projects/" summary="List or search projects" expanded="true" %}
{% swagger-description %}
This endpoint will show the projects created or shared with you.
{% endswagger-description %}

{% swagger-parameter in="header" name="Authorization" type="" required="true" %}
`Token Your.API.Key`
{% endswagger-parameter %}

{% swagger-parameter in="query" name="search" %}
Search in project name
{% endswagger-parameter %}

{% swagger-response status="200" description="Success" %}
```javascript
{
  "next": null,
  "previous": null,
  "page": 1,
  "per_page": 10
  "count": 2,
  "results": [
    {
      "title": "Default Project",
      "id": "52073298-8060-4bda-b0c6-dfec88ae2cae",
      "owner": "your.account@neuraltext.com"
    },
    {
      "title": "Another Project",
      "id": "32985207-4bda-b0c6-8060-dfec88ae2cae",
      "owner": "your.account@neuraltext.com"
    }
  ]
}
```
{% endswagger-response %}

{% swagger-response status="401" description="Permission denied" %}

{% endswagger-response %}

{% swagger-response status="404: Not Found" description="No project found" %}

{% endswagger-response %}
{% endswagger %}

