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

### Available endpoints

{% content-ref url="write.md" %}
[write.md](write.md)
{% endcontent-ref %}

{% content-ref url="summarize-v.md" %}
[summarize-v.md](summarize-v.md)
{% endcontent-ref %}
