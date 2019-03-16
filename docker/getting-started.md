# Getting Started

Dockerizing our bot is a relatively simple process and only requires a couple of steps. First we need to define our `Dockerfile` which contains our "build" instructions and then pass it to a `docker build` command which will then build our docker image.

{% hint style="info" %}
If you don't already have Docker installed visit [https://docker.io](https://docker.io) and download the release for your operating system.
{% endhint %}

Once docker is installed issue a `docker ps` command to make sure things are up and running. This will likely return zero results.

