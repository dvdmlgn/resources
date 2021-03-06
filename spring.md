**AOP** *(Aspect Orientated Programming)* 

concerned with **Cross-Cutting Functions**; which are conceptually different to *Bussiness Logic*

**DTO** *(Data Transfer Object)*

**FI** *(Financially Impacting)*

**DAO** *(Data Access Object)*

**JPA** *(Java Persistence API)*

**Domain Model**

a domain model is a conceptual model of the domain that incorporates both behavior and data

___

#### Using XML config files with Boot 

As long as you're starting with a base `@Configuration` class to begin with, which it maybe sounds like you are with `@SpringBootApplication`, you can use the `@ImportResource` annotation to include an XML configuration file as well.

``` java
@SpringBootApplication
@ImportResource("classpath:spring-sftp-config.xml")
public class SpringConfiguration {
  //
}
```
[source: stackOverflow](https://stackoverflow.com/a/31677776) 

___

#### RESTful web app/service with spring

##### creating a resource controller

In Spring’s approach to building RESTful web services, HTTP requests are handled by a controller. These components are easily identified by the `@RestController` annotation, and the `GreetingController` class below handles `GET` requests for the `/greeting` route by returning a new instance of the `Greeting` class:

- **value** parameter refers to the **route**
- **method** parameter refers to the **http request type**

``` java
@RestController
public class GreetingController {
	@RequestMapping(value = "/greeting", method = RequestMethod.GET)
    public Greeting greeting(
    	@RequestPara(value = "name", defaultValue = "there,..") String name
 	) {
    	return new Greeting(name);
    }
}
```

The `@RequestMapping` annotation ensures that HTTP requests to `/greeting` are mapped to the `greeting()` method.

`@RequestParam` binds the value of the query string parameter `name` into the `name` parameter of the `greeting()` method. If the `name` parameter is absent in the request, the `defaultValue` of "World" is used.

with **Spring *(ver. 4.6.2)*** semantic annotations you could write the above as:

``` java
@GetMapping(value = "/greeting")
public Greeting greeting(
	@RequestParam(value = "name", defaultValue = "there,..") String name
) {
	return new Greeting(name);
}
```

***Note***: the same is true for `PUT`, `POST`, and `DELETE` requests also

A key difference between a traditional MVC controller and the RESTful web service controller above is the way that the HTTP response body is created. Rather than relying on a view technology to perform server-side rendering of the greeting data to HTML, this RESTful web service controller simply populates and returns a `Greeting` object. The object data will be written directly to the HTTP response as JSON.

This code uses Spring 4’s new `@RestController` annotation, which marks the class as a controller where every method returns a domain object instead of a view. It’s shorthand for `@Controller` and `@ResponseBody` rolled together.

The `Greeting` object must be converted to JSON. Thanks to Spring’s HTTP message converter support, you don’t need to do this conversion manually. Because Jackson 2 is on the classpath, Spring’s `MappingJackson2HttpMessageConverter` is automatically chosen to convert the `Greeting` instance to JSON.

[source: spring.io](https://spring.io/guides/gs/rest-service/)


---
``` java
Set<String> set = people.stream()
                        .map(Person::getName)
                        .collect(Collectors.toCollection(TreeSet::new));
```

This is **method reference**. *Added in Java 8.*

`TreeSet::new` refers to the default constructor of `TreeSet`.

In general `A::B` refers to method `B` in class `A`.

---
#### make http request less painful on java with okhttp
``` java
final OkHttpClient client = new OkHttpClient();

    final Request request = new Request.Builder()
        .url("https://api.spotify.com/v1/browse/categories?country=IE&locale=en_IE&limit=10&offset=0")
        .get()
        .addHeader("Accept", "application/json")
        .addHeader("Content-Type", "application/json")
        .addHeader("Authorization", "Bearer tokenString")
        .build();

    final Response response = client.newCall(request).execute();

    return response.body().string();
```

---
### miscella

``` sh
. ~/.bashrc
```

run this for bash to register any new aliases

``` sh
*/5 * * * * /home/ramesh/backup.sh
```
this cron task will run every 5 minutes

---

## Docker

#### difference between some docker commands

`Create` adds a writeable container on top of your image and sets it up for running whatever command you specified in your `CMD`. The container ID is reported back but it’s not started.

`Start` will start any stopped containers. This includes freshly created containers.

`Run` is a combination of create and start. It creates the container and starts it.

---

## later learning links

[Atomic variables in Java](https://www.baeldung.com/java-atomic-variables)

[post mapping with json](http://appsdeveloperblog.com/postmapping-requestbody-spring-mvc/)

[building executable jar files with spring and maven](https://docs.spring.io/spring-boot/docs/current/reference/html/getting-started-first-application.html)

[server side rendering with React](https://medium.freecodecamp.org/demystifying-reacts-server-side-render-de335d408fe4h)

[spring boot and postgreSQL](https://www.callicoder.com/spring-boot-jpa-hibernate-postgresql-restful-crud-api-example/)

[spring service design pattern](https://www.tutorialspoint.com/spring_boot/spring_boot_service_components.htm)

[spring websockets](https://www.baeldung.com/websockets-spring)

[javadoc](https://www.baeldung.com/javadoc)

[bash cheatsheet](https://devhints.io/bash)

[spring jpa](https://spring.io/guides/gs/accessing-data-jpa/)

[spring jpa with hiberante & postgresql](https://www.callicoder.com/spring-boot-jpa-hibernate-postgresql-restful-crud-api-example/)

[spring web client](https://www.baeldung.com/spring-5-webclient)