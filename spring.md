**AOP** *(Aspect Orientated Programming)* 

concerned with **Cross-Cutting Functions**; which are conceptually different to *Bussiness Logic*

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
