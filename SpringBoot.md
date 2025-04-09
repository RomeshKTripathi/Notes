# Spring Boot

## General Introduction

### Inversion of Control / IOC
In our general Java Programs we used to create objects by own but in *Spring Boot* does it automatically and control of creating object goes to Spring Framework this concept is called Inversion of control. Objects can be accessed through `@Autowired` annotation in Spring.


### Dependency Injection
We know that objects of the `@Component` annoted class is automatically created by Spring Boot. These objects are *Injected* in program at run time this concept is called Dependency Injection
```java
@Autowired
MyClass myClass;
```


### Bean
Objects created by Spring Boot of components are called *Beans*.


### POJO Classes
POJO stands for `Plain Old Java Object`.

## Terminologies
### Annotations
annotations are used to give some information about class/field/method to Spring Boot.


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
