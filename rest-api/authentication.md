---
description: Authenticating against the API.
---

# Authentication

{% api-method method="get" host="http://localhost:8080" path="/api/login" %}
{% api-method-summary %}
Login
{% endapi-method-summary %}

{% api-method-description %}
This endpoint will return a JWT token that is required for all other queries.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-body-parameters %}
{% api-method-parameter name="username" type="string" required=true %}
Username \(1-255 characters\).
{% endapi-method-parameter %}

{% api-method-parameter name="password" type="string" required=true %}
Password \(8-255 characters\).
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Successful login.
{% endapi-method-response-example-description %}

```javascript
{
    "token": "eyJhbGciOiJIUzUxMiJ9.eyJzdWIiOiJiYXNzZXR0QHN0cmVhbW52ci5jb20iLCJleHAiOjE1NTk3MTEwMzd9.0UrGZwAfYg6Q7qs3JnCAnopSCwFnWwasdfasdfasdf4N09XvR6YBV5KEfkW95iv3MC0I_tZRPAbGDy0j88_AluymQ"
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=401 %}
{% api-method-response-example-description %}
Returned when an invalid username or password is supplied.
{% endapi-method-response-example-description %}

```javascript
{
    "message": "Ain't no cake like that."
}    
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}



