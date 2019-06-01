---
description: Direct Messaging
---

# Messages

{% api-method method="post" host="http://localhost:8080" path="/api/messages" %}
{% api-method-summary %}
Send a Direct Message
{% endapi-method-summary %}

{% api-method-description %}
Sends a direct message to a user. Supports a user id \(snowflake\) or username\#discriminator.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Authentication" type="string" required=true %}
Authentication Bearer token.
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="user" type="string" required=false %}
User ID or Username\#Discriminator
{% endapi-method-parameter %}

{% api-method-parameter name="message" type="string" required=false %}
Message payload \(can include emojis\).
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Direct message sent successfully.
{% endapi-method-response-example-description %}

```javascript
{
    "result": true
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=404 %}
{% api-method-response-example-description %}
User ID or username\#discriminator not found.
{% endapi-method-response-example-description %}

```javascript
{
    "result": false
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}



