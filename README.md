OkRest
======

[![Circle CI](https://circleci.com/gh/LendingClub/okrest.svg?style=svg)](https://circleci.com/gh/LendingClub/okrest) 
[![Download](https://img.shields.io/maven-central/v/io.macgyver.okrest/okrest.svg)](http://search.maven.org/#search%7Cga%7C1%7Cg%3A%22io.macgyver.okrest%22)

OkRest is a fluent REST client that is built on Square's excellent [OkHttp](https://square.github.io/okhttp/) client.

OkRest's API is similar in construction JAX-RS, but without all of the JAX-RS baggage.


Examples
--------

Assuming that a fictitious service with a GET request for ```/api/users/123``` returns:
```json
{
  "id" : 123,
  "name" : "Rob"
}
```

This will get the body as a String:

```java
String body = new OkRestClient()
    .uri("https://api.example.com")
    .path("/api/users/123")
    .get().execute(String.class);
```

And if we want to parse it through Jackson's fluent tree API:

```java
String name = new OkRestClient()
    .uri("https://api.example.com")
    .path("/api/users/123")
    .get().execute(JsonNode.class)
    .path("name").asText();
```
