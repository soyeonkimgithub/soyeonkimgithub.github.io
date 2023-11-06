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









