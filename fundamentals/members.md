---
description: >-
  To achieve the greatest possible range of users we implemented a simple
  language system.
---

# Language System

{% hint style="info" %}
<mark style="color:blue;">Work in progress</mark>
{% endhint %}

{% swagger method="get" path="" baseUrl="https://language.maax-studios.com" summary="Returns all language strings" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="query" name="package" required="true" %}
Name of the language package
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="" %}
```javascript
{
    // Response
}
```
{% endswagger-response %}

{% swagger-response status="404: Not Found" description="" %}
```javascript
{
  "type":"error",
  "msg":"Language file not found."
}
```
{% endswagger-response %}
{% endswagger %}
