# Spring Boot

## General Introduction

### Inversion of Control / IOC
### Dependency Injection
### Bean
### POJO Classes

## Terminologies
### Annotations
### Beans
### Mapping


## Annotations

### @SpringBootApplication
1. `@SpringBootApplication` annotation is used for *Entry Point* of the program
2. This annotation Scans all the components within package and sub packages and adds all the Classes to `IOC Container` which are annoted as *beans*.
3. `@SpringBootApplication` enables *Auto Configuration* in application. ex- Database configuration
4. This Annotation also configures all the classes annoted as `@Configure`.

### @Component
This Annotation declares that a particular class is a bean class and should be added to `IOC Container`.
```java
@Component
public class MyComponent{
  // Code
}
```
