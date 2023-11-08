---
layout: post
title: Spring Framework Master Class - Java Spring the Modern Way
categories: others
sitemap: false
hide_last_modified: true
published: true
---

## [Spring] Spring Framework Master Class - Java Spring the Modern Way
spring is a dependency injection framework

#### Dependency
ComplexBusinessService class is depend on SortAlgorithm
SortAlgorithm is dependency of the ComplexBusinessService class.

~~~java
// Before Spring - tight coupling
public class ComplexBusinessService {
    SortAlgorithm sortAlgorithm = new BubbleSortAlgorithm();
}

public class BubbleSortAlgorithm implements SortAlgorithm {
}

// loose coupling
SortAlgorithm sortAlgorithm = new BubbleSortAlgorithm();
ComplexBusinessService businessService = 
                new ComplexBusinessService(sortAlgorithm);

// After Spring
@Component
public class ComplexBusinessService {
    @Autowrired
    SortAlgorithm sortAlgorithm; 
}

@Component
public class BubbleSortAlgorithm implements SortAlgorithm {
}
~~~

#### Beans
Instances that Spring manages, are called Beans.
@Component - Spring would create the instances of this class and start managing

#### Autowiring
The process where Spring identifies the dependencies, identifies the matches for the dependencies and populates them.
@Autowired - Spring would start looking for this dependency among the component it manages.

#### Dependency Injection
Spring injects SortAlgorithm as a dependency into the ComplexBusinessService class.

#### Inversion of Control
The Spring framework is creating the SortAlgorithm instance. We are taking the control from the class that needs the dependency and giving the control to the Spring framework. Spring framework is IOC container which implements IOC.

#### Application Context
Spring framework is the application context Where all the beans are created and managed. That's where all the core logic of Spring framework happens.
@SpringBootApplication - automatically scan the package/sub packages

## Spring Framework Modules
### Data Access/Integration
JDBC, ORM(Hibernate), OXM, JMS, Transactions
### Web
WebSocket, Servlet, Web, Portlet
### Other modules
AOP, Aspects, Instrumentation, Messaging
### Core Container 
Beans, Core, Context, SpEL
### Test
Junit

### Spring Boot 
for developing micro services. Make it easy to develop applications quickly with features like start up projects, auto configuration, actuator. 

#### Dependency Injection
~~~java
@Component
public class TodoBusinessService {

    @Autowired
    TodoDataService dataService;
}

@Component
public class TodoDataService {

    @Autowired
    JdbcTemplate template;
}

~~~

#### Bean scope
- default -> singleton
- singleton : One instance per Spring Context
- prototype : New bean whenever requested (proxy can be used, i.e. proxyMode = ScopedProxyMode.TARGET_CLASS)
- request : One bean per HTTP request
- session : One bean per HTTP session

#### CDI
- Context and Dependency Injection
- Java EE Dependency Injection Standard (JSR-330)
- Spring Supports most annotations
  @Inject (@Autowired), @Named (@Component & @Oualifier), @Singleton (Defines a scope of Singleton)

#### JPA
- JPA : is interface. Java Persistance API
- Hibernate understands the API which is defined by JPA