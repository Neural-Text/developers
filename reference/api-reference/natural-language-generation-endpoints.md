# Natural Language Generation endpoints

{% hint style="info" %}
Tokens can be perceived as segments of words. The API dissects the input into tokens before processing it. Tokens may include trailing spaces and even sub-words, they are not limited to the beginning and end of words.

* 1 token \~= 4 chars in English
* 1 token \~= ¾ words
* 100 tokens \~= 75 words

or

* 1-2 sentence \~= 30 tokens
* 1 paragraph \~= 100 tokens
* 1,500 words \~= 2048 tokens
{% endhint %}

### Write

The capabilities of LLMs can be immense: for instance, you can use it to come up with new concepts or variations of existing content. This could range from narrative ideas to business models, character profiles to advertising taglines.&#x20;

This example will show you how to employ the API to generate ideas on how machine learning can improve education:

```
Generate some ideas combining machine learning and education:
```

{% swagger method="post" path="/write/" baseUrl="https://api.neuraltext.com/api/v1/ai" summary="Complete the provided prompt" expanded="false" %}
{% swagger-description %}
Price: 

**1 API unit every 200 tokens in input/output**
{% endswagger-description %}

{% swagger-parameter in="header" name="Authorization" required="true" %}
`Token Your.API.Key`
{% endswagger-parameter %}

{% swagger-parameter in="body" name="text" required="true" %}
A prompt
{% endswagger-parameter %}

{% swagger-parameter in="body" name="temperature" type="Float" %}
The creativity of the model.

\


A float number ranging from 

`0`

 to 

`1`
{% endswagger-parameter %}

{% swagger-parameter in="body" name="max_tokens" %}
Lenght of the text you want to generated, ranging from `1` to `3000`

Default is `100`
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="Success" %}
```json
{
    "status": "ok",
    "text": "1. Automated grading systems that utilize machine learning to quickly and accurately grade student assignments.\n2. Adaptive learning systems that use machine learning algorithms to tailor educational content to individual students.\n3. Using machine learning to detect early warning signs of academic problems and intervene with personalized support."
}
```
{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="Invalid payload" %}
```javascript
{
    "error": "temperature must be a float number between 0 and 1.",
}
```
{% endswagger-response %}

{% swagger-response status="429: Too Many Requests" description="Rate limit reached" %}
The rate limit for this endpoint is 10 calls per second. If you exceed it, you will get this error.

```javascript
{
    "error": "It seems you are generating text too fast. Please try again in a few moments."
}
```
{% endswagger-response %}
{% endswagger %}

### Summarize (beta)&#x20;

{% hint style="warning" %}
This endpoint is currently only available for custom integrations. [**Contact us**](mailto:humans@neuraltext.com)****
{% endhint %}

{% swagger method="post" path="/summarize/" baseUrl="https://api.neuraltext.com/api/v1/ai" summary="Summarize the provided text" %}
{% swagger-description %}
Price: 

**1 API unit every 200 tokens in input**
{% endswagger-description %}

{% swagger-parameter in="body" name="text" required="true" %}
The text you want to summarize
{% endswagger-parameter %}

{% swagger-parameter in="body" name="sentences" type="Integer" %}
Number of the sentences the summary will have (up to `10`).

Default to `5` .


{% endswagger-parameter %}

{% swagger-parameter in="header" name="Authorization" required="true" %}
`Token Your.API.Key`
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="Success" %}
```javascript
{
    // Response
}
```
{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="Invalid data in payload" %}
If you don't specify `text` in the payload, you will get this message:

```javascript
{
    "error": "Text is required"
}
```
{% endswagger-response %}

{% swagger-response status="401: Unauthorized" description="Account not enabled" %}
```javascript
{
    "error": "Your account is not enabled to perform this action, please contact us."
}
```
{% endswagger-response %}

{% swagger-response status="422: Unprocessable Entity" description="Insufficient API units" %}
```javascript
{
    "error": "Insufficient API units"
}
```
{% endswagger-response %}

{% swagger-response status="503: Service Unavailable" description="Model currently not available" %}
```javascript
{
    "error": "Summary LLM not available"
}
```
{% endswagger-response %}
{% endswagger %}
