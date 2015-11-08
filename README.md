Apollo
======

Apollo is a set of Java libraries that we use at Spotify when writing backend services. The Apollo
libraries help to simplify the integration of a Spotify backend service with the other parts of our
backend infrastructure. There are three main libraries in Apollo:

* [apollo-standalone](apollo-standalone-service)
* [apollo-api](apollo-api)
* [apollo-core](apollo-core)

### Apollo Standalone
The [apollo-standalone](apollo-standalone-service) library is a standardized bundle of Apollo
modules. It incorporates both apollo-api and apollo-core and ties them together with several other
standard modules to get a standard api service using http for incoming and outgoing communication.

### TODO apollo-standalone-service -> apollo-http-standalone-app?

### Apollo API
The [apollo-api](apollo-api) library is the Apollo library you are most likely to interact with.
It gives you the tools you need to define your service routes and your request/reply handlers.

Here, for example, we define that our service will respond to a GET request on the path `/` with
the string `"hello world"`:
```java
public static void init(Environment environment) {
  environment.routingEngine()
      .registerRoute(Route.sync("GET", "/", requestContext -> "hello world"));
}
```

> Note that, for an Apollo-based service, you can see the routes defined for a service by querying
[`_meta/0/endpoints`](apollo-api-impl/src/main/java/com/spotify/apollo/meta/model).

The apollo-api library uses several Java mechanisms, including classes and method references,
to help you define your request/reply handlers. You can specify how responses should be serialized
(such as to JSON). Read more about this library in the [Apollo API Readme](apollo-api).

### Apollo Core
The [apollo-core](apollo-core) library manages the lifecycle (loading, starting, and stopping) of
your service. You do not usually need to interact directly with apollo-core; think of it merely 
as "plumbing". For more information about this library, see the [Apollo Core Readme](apollo-core).

### Apollo Test
In addition to the three main Apollo libraries listed above, to help you write tests for your
service we have an additional library called [apollo-test](apollo-test). It has helpers to set up
a service for testing, and to mock outgoing request responses.

### Apollo Releases
For releases see the [releases](https://github.com/spotify/apollo/releases) page.

### Getting Started with Apollo
The quickest way to get started with Apollo is by setting up an
[apollo-standalone-service](apollo-standalone-service), and run it directly (`java -jar ...`).