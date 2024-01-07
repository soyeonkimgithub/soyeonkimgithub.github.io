---
layout: post
title: Java Characteristics
categories: languages
sitemap: false
hide_last_modified: true
published: true

---
## [Java] Characteristics

Object Oriented Programming is programming paradigm centred around the concept of objects which are instances of classes.

### Encapsulation
is bundling data(attributes) and methods(functions) that work on the data into a single object(class), preventing outside access.

~~~java
public class Car {
    private String brand;
    private int year;
    
    public String getBrand() {
        return brand;
    }
    
    public void setBrand(String brand) {
        this.brand = brand;
    }
    
    public int getYear() {
        return year;
    }
    
    public void setYear(int year) {
        this.year = year;
    }
}
~~~

### Inheritance
is a mechanism where a new class inherits properties and behaviours from an existing class, enabling the reusability of code.

~~~java
public class Animal {
    public void eat() {
        System.out.println("Animal is eating.");
    }
}

public class Dog extends Animal {
    public void bark() {
        System.out.println("Dog is barking.");
    }
}
~~~

### Polymorphism
allows objects to be treated as instances of their parent class, but still behave like instances of their actual class, allowing for flexibility and multiple forms of behaviour.

~~~java
public class Shape {
    void draw();
}

public class Circle implements Shape {
    @Override
    void draw() {
        System.out.println("Drawing a circle");
    }
}

public class Square implements Shape {
    @Override
    void draw() {
        System.out.println("Drawing a square");
    }
}

// Circle, Square classes implement the Shape interface. 
// you can use polymorphism to treat them both as 'Shape' objects
Shape circle = new Circle();
Shape square = new Square();
circle.draw();
square.drqw();

~~~

### Abstract
involves hiding the complex implementation details and showing only the essential features of an object allowing for more manageable and understandable code.

~~~java
public abstract class Shape {
    abstract void draw();
}

// Shape is an abstract class with an abstract method.
// The concrete classes Circle and Square provide their own implementation.
// Objects of the abstract class cannot be instantiated, enforcing the idea of abstraction.
public class Circle extends Shape {
    @Override
    void draw() {
        System.out.println("Drawing a circle");
    }
}

public class Square extends Shape {
    @Override
    void draw() {
        System.out.println("Drawing a square");
    }
}
~~~
### Java ver. 8, 13, 17
* 8: massive release 

  1) language features: 
  - Lambda: Before Java8, whenever you wanted to instantiate a new Runnable, you had to write an anonymous inner class

~~~java
 Runnable runnable = new Runnable(){
       @Override
       public void run(){
         System.out.println("Hello world !");
       }
     };

 // With lambdas the same code looks like this
 Runnable runnable = () -> System.out.println("Hello world !");    
~~~  

  - Collection & Stream: In Java 8 you also got functional-style operations for collections, also known as the Stream API. 

~~~java
List<String> list = Arrays.asList("franz", "ferdinand", "fiel", "vom", "pferd");

//Now pre-Java 8 you basically had to write for-loops to do something with that list.
//With the Streams API, you can do the following:
list.stream()
    .filter(name -> name.startsWith("f"))
    .map(String::toUpperCase)
    .sorted()
    .forEach(System.out::println);
 ~~~

* 13

  1) Switch expression can now return a value, and can use lambda-style syntax for expressions 

~~~java
// old switch statements
switch(status) {
  case SUBSCRIBER:
    // code block
    break;
  case FREE_TRIAL:
    // code block
    break;
  default:
    // code block
}
// new
boolean result = switch (status) {
    case SUBSCRIBER -> true;
    case FREE_TRIAL -> false;
    default -> throw new IllegalArgumentException("something is murky!");
};
~~~

  2) Multiline strings are possible 

~~~java
String htmlBeforeJava13 = "<html>\n" +
              "    <body>\n" +
              "        <p>Hello, world</p>\n" +
              "    </body>\n" +
              "</html>\n";

String htmlWithJava13 = """
              <html>
                  <body>
                      <p>Hello, world</p>
                  </body>
              </html>
              """;
~~~

* 17: new long-term support (LTS) release 

  1) Pattern matching for switch (preview)

~~~java
public String test(Object obj) {
    return switch(obj) {
    case Integer i -> "An integer";
    case String s -> "A string";
    case Cat c -> "A Cat";
    default -> "I don't know what it is";
    };
}
~~~  

  2) Sealed classes (finalized) : If you ever wanted to have an even closer grip on who is allowed to subclass your classes, there’s now the sealed feature.

~~~java
public abstract sealed class Shape
    permits Circle, Rectangle, Square {...}
~~~

ref. https://www.marcobehler.com/guides/a-guide-to-java-versions-and-features

### Java ver. 18/19

- preview features:
those are complete or almost complete language features ready to try out, think beta-testing.
published to collect feedback without committing to maintaining its backward compatibility.
need to use the -enable-preview compiler flag.

- experimental features:
represent early versions of VM-level features, which can be risky, incomplete, or even unstable.
they need to be enabled using dedicated flags.
an experimental feature is considered 25% “done”, then a preview feature should be at least 95% “done”.

- incubating features
experimental APIs distributed in a form of separate modules.

1. AIP Updates
 1) Charset - can set default char set as second parameter
 2) Duration
 3) HttpClient
 4) Future - concurrent class

2. Deprecation of Finalization
- clean up external resources an object holds
- finalize() method deprecated since 9, and now deprecated for removal in 18
- reason
  1) unpredictable: no control over when finalization runs, no cancellation possible
  2) unconstrained: finalizer can do anything including resurrecting the original object!
  3) unclear: hard to implement correctly, possibility for deadlocks
  4) unsafe: security issues, especially when combined with serialization
- alternatives: try-with-resources --> automatically calls close(), class should implement AutoCloseable
              : Cleaner API (java.lang.ref.Cleaner, since 9) --> manually register Cleaner for object

3. Code snippets in JavaDoc - code block, copy, or external snippets (with @start and @end), or highlighting

4. Simple Web Server - jwebserver or java -m jdk.httpserver command

5. Platform changes
  1) DNS platform changes: used to use InetAddress -> OS's Native resolver, now use InetAddressResolver
  2) Reimplementation of Reflection APIs with method handlers
  - Reflection: the ability to work with and inspect Java classes in a generic manner without directly referencing the types in your code.
  3) UTF-8 by Default
  - Charset.defaultCharset() : UTF-8(Mac), windows-1252(Window)


### Collections
* Set/List/Map
Set is an unordered collection of unique elements(HashSet)
List is an ordered collection that allows duplicate elements(ArrayList, LinedList)
Map is a collection of key-value pairs(HashMap)

* String/StringBuffer/StringBuilder
String: immutable, operation leads to waste of space and decrease of performance, reason: String can be reused frequently, JVM creates ‘string constant pool’ and shares this with other objects, performance getting better, but it cannot be changed
StringBuffer: mutable, having inner space ‘buffer’, thread-safe -> for single thread, can have performance issue, then use StringBuilder
StringBuilder: mutable, not thread-safe, lighter than StringBuffer, commonly used

* Lambda expression
provides a concise way to express instances of single-method interfaces (functional interfaces)