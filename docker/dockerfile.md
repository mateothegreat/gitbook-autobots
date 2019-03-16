# Dockerfile

First let's setup a `.dockerignore` file to prevent our docker build command from copying our node\_modules directory into the image.

{% code-tabs %}
{% code-tabs-item title="/.dockerignore" %}
```text
node_modules
```
{% endcode-tabs-item %}
{% endcode-tabs %}

Now we can create our `Dockerfile`:

{% code-tabs %}
{% code-tabs-item title="/Dockerfile" %}
```typescript
FROM node:alpine AS builder

WORKDIR /app

RUN adduser -S bot

COPY package.json .

RUN npm install

COPY . .

RUN npm run build

#
# Change to a less-privileged user than root in the
# event a request escapes the sandbox
#
USER bot

#
# Starts the bot when the docker container is started
#
ENTRYPOINT ["npm", "start"]
```
{% endcode-tabs-item %}
{% endcode-tabs %}



