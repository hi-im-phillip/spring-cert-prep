
<h1 style="color: cornflowerblue;
    align-content: center">Spring certification exam prep stuff</h1>




<h1 style="color: cornflowerblue;"> Table of Contents </h1>

- [Basically about exam](#intro)
- [Exam Details](#exam-details)
- [Container, Dependency, and IoC](#Module-1)
- [Aspect Oriented Programming](#Module-2)
- [Data Management: JDBC, Transactions, Spring Data JPA](#Module-3)
- [Spring Boot, Spring Boot Auto configuration, Spring Boot Actuator, Spring Boot Testing](#Module-4)
- [Spring MVC and the Web Layer](#Module-5)
- [Spring Security](#Module-6)
- [Spring REST](#Module-7)
- [Spring Testing](#Module-8)
- [Spring Certified Professional - Badge](#spring-badge)


<hr style="border:2px solid gray"> </hr>


<h1 id="intro" style="color: cornflowerblue;"> Basically about exam </h1>

This repository contains notes and questions designed to assist you in preparing 
for the [Spring Professional Certification exam](https://www.vmware.com/learning/certification/spring-pro-develop-exam.html). 

I prepared for about a month for this exam, based on the instructional videos available on [Udemy by Dominik Cebula](https://www.udemy.com/user/dominik-cebula/). 
These resources are highly valuable, and I recommend checking out his courses. 
Personally, I found that watching the videos and taking notes greatly enhanced my understanding of the concepts.

I went through the series twice: first, by taking notes (can be found in notes/modules), and then by engaging more with the code examples. 
Please note that I am not affiliated with Dominik Cebula or Udemy; I am simply a programmer who found his courses to be very helpful.

Mock exams can be found in the mock-exams folder. Just to clarify, the mocks are designed to resemble
the real exam in concept only, not in difficulty. I encountered maybe two questions similar to those in the mock exams
during the actual test. The real exam was more challenging, so it's best not to rely too heavily on the mock
exams. Last few days before the exam, I studied using the mock exams along with other resources to cover
all basses.

Additionally, I have prior experience working with Spring Boot, which gave me a good foundation and understanding of Spring technologies.

<hr style="border:2px solid gray"> </hr>

<h1 id="exam-details" style="color: cornflowerblue;"> Exam details </h1>

- **Exam Name**: Exam 2V0-72.22 : Spring Professional Develop
- **Exam Duration**: 130 minutes
- **Number of Questions**: 60
- **Passing Score**: 300/500


<hr style="border:2px solid gray"> </hr>


<h1 id="Module-1" style="color: cornflowerblue;">Container, Dependency, and IoC</h1>



### <span style="color: #99ff99;"> 1. What is dependency injection and what are the advantages?</span>
Dependency injection is a technique of creating software in which objects do not create
their dependencies on itself, instead objects declare dependencies that they need and it is external object job or framework to provide concrete dependencies to objects

Types of Dependency Injection:
- Constructor injection
- Setter injection
- Interface injection

Advantages of using dependency injection is:
- Increases code usability
- Increases code readability
- Increases code maintainability
- Increases code testability
- Reduces coupling
- Increases cohesion

### <span style="color: #99ff99;"> 2. What is a pattern? What is an anti-pattern? Is dependency injection a pattern?</span>

A software Design Pattern is a reusable solution to often, commonly occurring problem in
software design. It is a high level description on how to solve the problem, that can be used in different situations. Design patterns often represent best practises that developers can use to solve common problems.

Some examples of commonly used design patterns from GoF Design Patterns:
- Factory Method
- Builder
- Template Method
- Strategy
- Observer
- Visitor
- Facade
- Composite

Dependency Injection is a pattern that solves problem of flexible dependencies creation.

Anti-pattern is ineffective and counter-productive solution to often occurring problem.

Examples of Anti-patterns in Object Oriented Programming:
- God Object (large number of variables)
- Sequential coupling (change order of methods and they are broken)
- Circular dependency
- Constant interface

### <span style="color: #99ff99;"> 3. What is an interface and what are the advantages of making use of them in Java? Why are they recommended for Spring beans?</span>

OOP Definition - An interface is a description of actions that object can do, it is a way to enforce actions on object that implements the interface.

Advantages of using interfaces in Java:
- Allows decoupling between contract and its implementation
- Allows declaring contract between callee and caller
- Increases interchangeability
- Increases testability

Advantages of using interfaces in Spring:
- Allows for use of JDK Dynamic Proxy
- Allows implementation hiding
- Allows to easily switch beans

### <span style="color: #99ff99;"> 4. What is meant by "application-context"?</span>

Application context is a central part of Spring application. It holds bean definitions and contains registry of application components. It allows you to retrieve assembled and configured beans.

Application context:
- initiates Beans
- Configures Beans
- Assemblies Beans
- Manages Beans Lifecycle
- Is a Bean Factory
- Is a Resource Loader
- Has ability to push events to registered event listeners
- Exposes Environment which allows to resolve properties

Common Application Context types:
- AnnotationConfigApplicationContext
- AnnotationConfigWebApplicationContext
- ClassPathXmlApplicationContext
- FileSystemXmlApplicationContext
- XmlWebApplicationContext

### <span style="color: #99ff99;"> 5. What is concept of a "container" and what is its lifecycle?</span>

Container is an execution environment which provides additional technical services for your code to use. Usually containers use IoC technique, that allows you to focus on creating buisness aspect of the code, while technical aspects like communication details (HTTP, REST, SOAP) are provided by execution environment.

Spring provides a container for beans. It manages lifecycle of the beans and also provides additional services through usage of Application Context.

Spring Container Lifecycle:
1. Application is started
2. Spring container is created
3. Containers read configuration
4. Beans definitions are created from configuration
5. BeanFactoryPostProcessors are processing bean definitions.
6. Instances of Spring Beans are created.
7. Spring Beans are configured and assembled - resolve property values and inject dependencies
8. BeanPostProcessor are called.
9. Application Runs.
10. Application gets shutdown.
11. Spring Context is closed.
12. Destruction callbacks are invoked.

### <span style="color: #99ff99;"> 6. How are you going to create a new instance of an ApplicationContext?</span>

Non-Web Applications:
- AnnotationConfigApplicationContext
- ClassPathXmlApplicationContext
- FileSystemXmlApplicationContext

Web Applications:
- Servlet 2 - web.xml, ContextLoaderListener, DispatchServlet
- Servlet 3 - XmlWebApplicationContext
- Servlet 3 - AnnotationConfigWebApplicationContext

Spring Boot:
- SpringBootConsoleApplication - CommandLineRunner
- SpringBootWebApplication - Embedded Tomcat

### <span style="color: #99ff99;"> 7. Can you describe the lifecycle of a Spring Bean in an ApplicationContext?</span>

Context is Created:
1. Beans Definitions are created based on Spring Bean Configuration.
2. BeanFactoryPostProcessors are invoked

Bean is Created:
1. Instance of Bean is Created.
2. Properties and Dependencies are set.
3. BeanPostProcessor::postProcessBeforeInitialization gets called
4. @PostConstruct method gets called
5. InitializingBean::afterPropertiesSet method gets called.
6. @Bean(initMethod) method gets called
7. BeanPostProcessor::postProcessAfterInitialization gets called

Bean us Ready to use.

Bean is destroyed:
1. @PreDestroy
2. DisposableBean::destroy method gets called
3. @Bean(destroyMethod) method gets called

### <span style="color: #99ff99;"> 8. How are you going to create an ApplicationContext in a standalone Java application?</span>

```java
public class MyApp {
    public static void main(String[] args) {
        ApplicationContext context = new ClassPathXmlApplicationContext("applicationContext.xml");
        // Now you can retrieve your beans
        MyBean bean = context.getBean(MyBean.class);
        // Use your bean...
    }
}
```
You'll also need an applicationContext.xml file in your classpath to define your beans.


### <span style="color: #99ff99;"> 9. What is component-scanning and how does Spring use it?</span>

@ComponentScan is used with @Configuration classes to specify base packages to scan for Spring managed components.

It searches for Spring managed components annotated with @Component, @Service, @Repository, @Controller, and other custom annotations and registers them as Spring Beans.

@Configuration classes that are annotated with @ComponentScan can specify a base package to restrict the component scanning to a specific package or set of packages.


### <span style="color: #99ff99;">9. What is the preferred way to close an application context? Does Spring Boot do this for you?</span>

Standalone Non-Web Applications
- Register Shutdown hook by calling ConfigurableApplicationContext#registerShutdownHook - Recommended
- Call ConfigurableApplicationContext#close
Web Application
- ContextLoaderListener will automatically close context when web container will stop web application
Spring Boot
- Application Context will be automatically closed
- Shutdown hook will be automatically registered
- ContextLoaderListener applies to Spring Boot Web Applications as well

### <span style="color: #99ff99;">10. Can you describe: Dependency injection using Java configuration? Dependency injection using annotations(@Component, @Autowired)? Component scanning, Stereotypes and Meta-Annotations? Scopes for Spring beans? What is the default scope?</span>

DI Java configuration
When using Dependency Injection using Java Configuration you need to explicitly define all your beans and you need to use @Autowired
on @Bean method level to inject dependencies.

DI Annotations
Create classes annotated with @Component annotations.
Define dependencies when required.
Create configuration with Component scanning enabled.

Component Scanning
Process in which Spring is scanning Classpath in search for classes annotated with stereotypes annotations (@Component, @Repository, @Service, @Controller)
and based on those creates beans definitions.

Meta-Annotations
Meta-annotations are annotations that can be used to create new annotations.
Example @RestController annotation is using @Controller and @ResponseBody to define its behavior.

Scopes of Spring Beans
Singleton - Single Bean per Spring container - default
Prototype - New instance each time Bean is requested
Request - New instance per each HTTP Request
Session - New instance per each HTTP Session
Application - One instance per each ServletContext
WebSocket - one instance per each WebSocket

### <span style="color: #99ff99;">11. Are beans lazily or eagerly instantiated by default? How do you alter this behavior?</span>

Lazy and Eager instance Creation vs Scope Type:
- Singleton Beans are eagerly instantiated by default
- Prototype Beans are lazily instantiated by default (instance is created when bean is requested)
- if Singleton Bean has dependency on Prototype Bean, then Prototype Bean instance will be created eagerly to satisfy dependencies for Singleton Bean

Altering Behavior:
You can change default behavior for all beans by @ComponentScan annotation (lazyInit)
- Setting lazyInit to true, will make all beans lazy, even Singleton Beans
- Setting lazyInit to false (default), will create Singleton Beans Eagerly and Prototype Beans Lazily

You can also change default behavior by using @Lazy annotation:
- @Lazy annotation takes one parameter - Whether lazy initialization should occur
- You can use @Lazy(false) to force Eager Instantiation - use case for @ComponentScan(lazyInit = true) when some beans always needs to be instantiated eagerly

@Lazy an be applied to:
- Classed annotated with @Component - makes bean Lazy or as specified by @Lazy parameter
- Classes annotated with @Configuration annotation - make all beans provided by configuration lazy or as specified by @Lazy parameter
- Method annotated with @Bean annotation - makes bean created by method Lazy or as specified by parameter

### <span style="color: #99ff99;">12. What is a property source? How would you use @PropertySource?</span>

PropertySource is Spring Abstraction on Environment Key-Value pairs, which can come from:
- JVM Properties
- System Environmental Variables
- JNDI Properties
- Servlet Parameters
- Properties File Located on Filesystem
- Properties File Located on Classpath

You read properties with usage of @PropertySource or @PropertySources annotation.
You access properties with usage of @Value annotation.

### <span style="color: #99ff99;">13. What is a BeanFactoryPostProcessor and what is it used for? When is it invoked? Why would you define a static @Bean method? What is a PropertysourcePlaceholderConfigurer used for?</span>

BeanFactoryPostProcessor is an interface that contains single method postProcessBeanFactory, implementing it allows you to create logic that will modify Spring Bean Metadata before any Bean is created. BeanFactoryPostProcessor does not create any bean, however it can access and alter Metadata that is used later to create Beans.

BeanFactoryPostProcessor is invoked after Spring will read or discover Bean Definitions, but before any Spring Bean is created.

Because BeanFactoryPostProcessor is also a Spring Bean, but a special kind of Bean that should be invoked before other types of beans get created,
Spring needs to have ability to create it before any other beans. This is why BeanFactoryPostProcessors needs to be registered from static method level.

PropertySourcesPlaceholderConfigurer is a BeanFactoryPostProcessor that is used to resolve properties placeholder in Spring Beans on fields annotated with
@Value("${}").

### <span style="color: #99ff99;">14. What is a BeanPostProcessor and how is it different to a BeanFactoryPostProcessor? What do they do? When are they called?</span>

BeanPostProcessor is an interface that allows you to create extensions to Spring Framework that will modify Spring Beans objects during initialization.
This interface contains two methods:
- postProcessBeforeInitialization()
- postProcessAfterInitialization()
  Implementing those methods allows you to modify created and assembled bean objects or even switch object that will represent the bean.

Main difference compared to BeanFactoryPostProcessor is that BeanFactoryPostProcessor works with Bean Definitions while BeanPostProcessor works with Bean Objects.

BeanFactoryPostProcessor and BeanPostProcessor in Spring Container Lifecycle
1. Beans Definitions are created based on Spring Bean Configuration.
2. BeanFactoryPostProcessors are invoked !!
3. Instance of Bean is created.
4. Properties and Dependencies are set.
5. BeanPostProcessor::postProcessBeforeInitilazion gets called !!
6. @PostConstruct method gets called.
7. InitializingBean::afterPropertiesSet method gets called.
8. @Bean(initMethod) method gets called
9. BeanPostProcessor::postProcessAfterInitialization gets called !!

Recommended way to define BeanPostProcessor is through static @Bean method in Application Configuration. This is because BeanPostProcessor should be created early, before other Beans Objects are ready. It's also possible to create it through regular registration in Application Configuratiom or through Component Scanning, however becaouse in that case bean can be created late in processes, recommended way is options provided above.

### <span style="color: #99ff99;">What is an initialization method and how is it declared on a Spring bean?</span>

Initialization model is a method that you can write for Spring Bean if you need to perform some initialization code that depends on properties and/or dependencies injected into Spring Bean.

You can declare Initialization method in three ways:
1. Create method in Spring Bean annotated with @PostConstruct
2. Implement InitializingBean::afterPropertiesSet
3. Create Bean In Configuration class with @Bean method and use @Bean(initMethod)

### <span style="color: #99ff99;">What is a destroy method, how is it declared?</span>

Destroy Method is a method in Spring Bean that you can use to implement any cleanup logic for resources used by the Bean. Method will be called when Spring Bean will be taken out of use, this usually happening when Spring Context is closed.

You can declare destroy method in following ways:
1. Create method annotated wih @PreDestroy annotation
2. Implement DisposableBean::destroy
3. Create Bean in Configuration class with @Bean method and use @Bean(destroyMethod)

### <span style="color: #99ff99;">Consider how you enable JSR-250 annotations like @PostConstruct and @PreDestroy?</span>

When using AnnotationConfigApplicationContext support for @PostConstruct and @PreDestroy is added automatically.
Those annotations are handled by CommonAnnotationBeanPostProcessor which is automatically registered by AnnotationConfigApplicationContext.

### <span style="color: #99ff99;">When/how will they (initialization, destroy methods) get called?</span>

Context is Created:
1. Beans Definitions are created based on Spring Bean Configuration
2. BeanFactoryPostProcessors are invoked.

Bean is Created:
1. Instance of Bean is Created.
2. Properties and Dependencies are set.
3. BeanPostProcessor::postProcessBeforeInitialization gets called
4. @PostConstruct method gets called. !!
5. InitializingBean::afterPropertiesSet method gets called. !!
6. @Bean(initMethod) method gets called !!
7. BeanPostProcessor::postProcessAfterInitialization gets called.

Bean is Ready to use.

Bean is Destroyed (usually when context is closed):
1. @PreDestroy method gets called.
2. DisposableBean::destroy method gets called.
3. @Bean(destroyMethod) method gets called

### <span style="color: #99ff99;">15. What does component-scanning do?</span>

Process in which Spring is scanning Classpath in search for classes annotated with stereotypes annotations
(@Component, @Service, @Controller) and based on those creates beans definitions.

Simple component scanning within Configuration package and all subpackages. @ComponentScan

Advanced Component Scanning Rules
@ComponentScan(basePackages, includeFilters, excludeFilters)

### <span style="color: #99ff99;">16. What is the behavior of the annotation @Autowired with regards to field injection, constructor injection and method injection?</span>

@Autowired is an annotation that is processed by AutowiredAnnotationBeanPostProcessor, which can be put onto class constructor, field,
setter method or config method. Using this annotation enables automatic Spring Dependency Resolution that is primary based on types.

@Autowired has a property required which can be used to tell Spring if dependency is required or optional. By default dependency is required.
If @Autowired with required dependency is used on top of constructor or method that contains multiple arguments, then all arguments are considered
required dependency unless argument is of type Optional, is marked as @Nullable, or is marked as @Autowired(required=false).

If @Autowired is used on top of Collection or Map then Spring will inject all beans matching the type into Collection and key-value pairs as BeanName-Name
into Map. Order of elements depends on usage of @Order, @Priority annotations and implementation of Ordered interface.

@Autowired uses following steps when resolving dependency.
1. Match exactly by type, if only one found, finish.
2. If multiple beans of same type found, check if any contains @Primary annotation, if yes, inject @Primary bean and finish
3. If no exactly one match exists, check if @Qualifier exists for field, if yes use @Qualifier to find matching bean
4. If still no exactly one bean found, narrow the search by using bean name.
5. If still no exactly one bean found, throw exception.

Field injection
- Autowired fields can have any visibility level
- Injection is happening after Bean is created but before any init method(PostConstruct, InitializingBean, Bean(initMethod))
- By default field is required, however you can use Optional, Nullable or Autowired(required=false)

Constructor injection
- If there is only one constructor in class, there is no need to use @Autowired on top of it, Spring will use this default constructor anyway
  and will inject dependencies into it.
- If class defines multiple constructor, then you are obligated to use @Autowired to tell Spring which constructor should be used to create Spring
  Bean. If you will have a class with multiple constructor without any of constructor marked as Autowired then spring will throw exception.
- By default all arguments in constructor are required, however you can use Optional, Nullable or Autowired to indicate that parameter is not required.

Setter injection
- same rules as former.


### <span style="color: #99ff99;">17. What do you have to do, if you would like to inject something into a private field? How does this impact testing?</span>

Injection of dependency into private field can be done with autowired annotation.
Injection of property into private field can be done with value annotation.

Private Field cannot be accessed from outside of the class, to resolve this when writing Unit Test you can use following solutions:
- Use SpringRunner with ContextConfiguration and @MockBean
- Use ReflectionTestUtils to modify private fields
- Use MockitoJUnitRunner to inject mocks
- Use @TestPropertySource to inject test properties into private fields

### <span style="color: #99ff99;">18. How does the @Qualifier annotation complement the use of @Autowired?</span>

@Qualified annotation gives you additional control on which bean will be injected, when multiple beans of the same type are found.
By adding additional information on which bean you want to inject, @Qualifier resolves issues with NoUniqueDefExc.

Usage of Qualifier in three ways:
- At injection point with bean name as value
- At injection and bean definition point
- Custom Qualifier Annotation Definition

### <span style="color: #99ff99;">19. What is a proxy object and what are the two different types of proxies Spring can create? What are the limitations of these proxies (per type)? What is the power of a proxy object and where are the disadvantages?</span>

Proxy object is an object that adds additional logic on top of object that is being proxies without having to modify code of proxied object.
Proxy object has the same public methods as object that is being proxied and it should be as much as possible indistinguishable from proxied object.
When method is invoked on Proxy Object, additional code, usually before and after sections are invoked, also code from proxied object is invoked by Proxy Object

Two kind of proxies:
- JDK Dynamic Proxy - used by default if target object implements interface
- CGLIB Proxy - use when target does not implement any interface

Limitations of JDK Dynamic Proxy:
- Requires proxy object to implement the interface
- Only interface methods will be proxied
- No support for self-invocation

Limitations of CGLIB Proxy:
- Does not work for final classes
- Does not work for final methods
- No support for self-invocation

Proxy Advantages:
- Ability to change behavior of existing beans without changing original code
- Separation of concerns (logging, transaction, security)

Proxy Disadvantages:
- May create code hard to debug
- Needs to use unchecked exception for exceptions not declared in original method
- My cause performance issues if before/after section in proxy code is using IO (Network Disk)
- May cause unexpected equals operator (==) results since Proxy Object and Proxied Object are two different objects

### <span style="color: #99ff99;">20. What are the advantages of Java Config? What are the limitations?</span>

Advantages of Java Config over XML Config:
- Compile-Time Feedback due to Type-checking
- Refactoring Tools for Java without special support/plugins work out of the box with Java Config

Advantages of Java Config over Annotation Based Config:
- Separation of concerns - beans configuration is separated from beans implementation
- Technology agnostic - beans may not depend on concrete IoC/DI implementation - makes it easier to switch technology
- Ability to integrate Spring with external libraries
- More centralized location of bean list

Limitations of Java Config:
- Configuration class cannot be final
- Configuration class methods cannot be final
- All Beans have to be listed, for big applications, it might be a challenge compared to Component Scanning

### <span style="color: #99ff99;">21. What does the @Bean annotation do?</span>

Bean annotation is used in @Configuration class to inform Spring that instance of class returned by method annotated with Bean will return bean that will be manageded by Spring

Bean allows you to:
- Specify init method - will be called after instance is created and assembled
- Specify destroy method - will be called when bean is discarded (usually when context is getting closed)
- Specify name for the bean - by default bean has name autogenerated based on method name, however this can be overrriden
- Specify alias/aliases for the bean
- Specify if Bean should be used as candidate for injection into other beans - default true
- Configure Autowiring mode - by name or type (deprecated)

### <span style="color: #99ff99;">22. What is the default bean id if you only use @Bean? How can you override this?</span>

When using @Bean without specifying name or alias, default bean id will be created based on name of the method which was annotated with @Bean

It can be overridden by specifying name or aliases for the bean

### <span style="color: #99ff99;">23. Why are you not allowed to annotate a final class with @Configuration? How do @Configuration annotated classes support singleton beans? Why can't @Bean methods be final either?</span>

Class annotated with Configuration cannot be final because Spring will use CGLIB to create a proxy for @Configuration class. CGLIB creates subclasses
for each class that is supposed to be proxied, however since final class cannot have subclass CGLIB will fail. This is also a reason why methods cannot
be final, Spring needs to override methods from parent class for proxy to work correctly, however final method cannot be overriden, having such a method
will make CGLIB fail.

If Configuration class will be final or will have final method, Spring will throw BeanDefParsExc.

Spring supports Singleton beans in @Configuration class by creating CGLIB proxy that intercepts calls to the method. Before method is executed from the proxied
class, proxy intercept a call and checks if instance of the bean already exists, if instance of the bean exists, then call to method is not allowed and already
existing instance is returned, if instance does not exists, then call is allowed, bean is created ans instance is returned and saved for future reuse.
To make method call interception CGLIB proxy needs to create subclass and also needs to override methods.


### <span style="color: #99ff99;">24. How do you configure profiles? What are possible use cases where they might be useful?</span>

Spring Profiles are configured by:
- Specifying which beans are part of which profile
- Specifying which profiles are active

You can specify beans being part of profile in following ways:
- Use @Profile annotation at @Component class level - bean will be part of profile/s specified annotation
- Use @Profile at @Configuration class level - all beans from this configuration will be part of profile/s specified annotation
- Use @Profile at @Bean method of @Configuration class - instance of bean returned by this method will be part of profile/s specified in annotation
- Use @Profile annotation to define custom annotation will be part of profile/s spec in annotation

If bean does not have profile specified in any way, it will be created in every profile.
It can be used "!" to specify in which profile bean should not be created

To activate profiles in following way:
- Programmatically with usage of ConfigurableEnvironment
- By using spring.profiles.active property
- On JUnit Test level by using @ActiveProfiles
- In Spring Boot programmatically by usage of SpringApplicationBuilder
- In Spring Boot by application.properties or on yml level

Spring Profiles are useful in following cases:
- Changing Behavior of the system in Different Environments by changing set of Beans that are part
  of specific environments, for example prod, cert, dev
- Changing Behavior of the system for different customers
- Development and Testing environments
- Additional debugging

### <span style="color: #99ff99;">25. Can you use @Bean together with @Profile?</span>

Yes, @Bean can be used together with @Profile inside class annotated with @Configuration on top of method that
returns instance of the bean

If method annotated with @Bean does not have @Profile, that means that this bean will exists in all profiles.

### <span style="color: #99ff99;">26. Can you use @Component together with @Profile?</span>

Yes, @Profile can be used together with @Component on top of class representing spring bean.

If class annotated with @Component does not have @Profile, that means that this bean will exists in all profiles.

### <span style="color: #99ff99;">27. How many profiles can you have?</span>

Spring Framework does not specify any explicit limit on number of profiles, however since some of the classes in framework,
like ActiveProfilesUtils used by default implementation of ActiveProfilesResolver are using array to iterate over profiles, this
enforces inexplicit limit that is equal to maximum number of elements in array that you can have in Java, which is
Integer.MAX_VALUE.

### <span style="color: #99ff99;">28. How do you inject scalar/literal values into Spring beans?</span>

To inject scalar/literal values into Spring Beans, you need to use @Value.

@Value has one field value that accepts:
- Simple value
- Property reference
- SpEL String

@Value can be used on top of:
- Field
- Constructor Parameter
- Method - all fields will have injected the same value
- Method parameter - Injection will not be performer automatically if @Value is not present on method level or if @Autowired is not present
- Annotation type

### <span style="color: #99ff99;">29. What is @Value used for?</span>

Value is used for:
- Setting simple values of Spring Bean Fields, method Parameters, Constructor Parameters
- Injecting property/environment values into Spring Bean Fields, Method Parameters, Constructor Parameters
- Injecting result of SpEL expressions into Spring Bean Fields, Method Parameters, Constructor Parameters
- Injecting values from other Spring Beans into Spring Bean fields, Method Parameters, -||-
- Injecting values into collections from literals
- Setting default values of Spring Bean

### <span style="color: #99ff99;">30. What is Spring Expression Language (SpEL)?</span>

Spring Expression Language is an expression language that allows you to query and manipulate objects graphs during the runtime. SpEL is used
in different products across Spring portfolio.

SpEL can be used independently with usage of ExpressionParser and EvaluationContext or can be used on top of fields, method parameters, constructor
arguments via @Value

SpEL expression are usually interpreted during runtime, this is good since it provides a lot of dynamic features.

Compilation of Spring Expression is done by creating real Java Class that embodies expression, this results in much faster Expression Evaluation.
Because during compilation, reference types of properties are unknown, Compiled Expression are best to use when types of referenced types are not changing.

Compiler is turned of by default, you can turn it on by:
- Parser Configuration
- System Property - spring.expression.compiler.mode
- modes - immediate, mixed

### <span style="color: #99ff99;">31. What is the Environment abstraction in Spring?</span>

Environment Abstraction is part of Spring Container that models two key aspect of application environment:
- Profiles
- Properties

Environment Abstraction is represent on code level by classes that implements Environment interface. This interface allows you to resolve
properties and also to list profiles. You can receive reference to class that implements Environment by calling EnvironmentCapableClass, implemented by ApplicationContext. Properties can also be retrieved by using @Value($"") annotation.

Environment Abstraction role in context of properties is to provide convenient, standard and generic service that allows to resolve properties and also
to configure property sources. Properties may come from following sources:
- Properties files
- JVM Environment Variables
- System Environment Variables
- JNDI
- Servlet Config
- Servlet Context Parameters

To add additional properties files as property sources you can use @PropertySource annotation.

### <span style="color: #99ff99;">32. Where can properties in the environment come from - there are many sources for properties.</span>

Property sources in Spring Application vary based on type of applications that is being executed:
- Standalone Application
- Servlet Container Application
- Spring Boot Application

Standalone Spring Framework application:
- Properties files
- JVM system properties
- System Environment Variables

Servlet Container:
- Properties files
- JVM system properties
- System Environment Variables
- JNDI
- ServletConfig init parameters
- ServletContext init parameters

Spring Boot application:
- Devtool properties from ~/.spring-boot-devtools.properties
- @TestPropertySource annotations on test
- Properties attribute in @SpringBootTest test
- Command line arguments
- Properties from SPRING_APPLICATION_JSON property
- ServletConfig init parameters
- ServletContext init parameters
- JNDI attributes from java:comp/env
- JVM system properties
- System Environment Variables
- RandomValuePropertySource - ${random.*}
- application-{profile}.properties and YAML variants - outside of jar and inside jar
- application.properties and YAML variants - outside of jar and inside jar
- @PropertySource annotations on @Configuration classes
- Default properties - SpringApplication.setDefaultProperties


### <span style="color: #99ff99;">33. What can you reference using SpEL?</span>

You can reference the following using SpEL:
- Static Fields from a class: `T(com.example.Person).DEFAULT_NAME`
- Static Methods from a class: `T(com.example.Person).getDefaultName()`
- Spring Bean Property: `@person.name`
- Spring Bean Method: `@person.getName()`
- SpEL Variables: `#personName`
- Object property on reference assigned to SpEL variables: `#person.name`
- Object method on reference assigned to SpEL variables: `#person.getName()`
- Spring Application Environment Properties: `environment['app.file.property']`
- System Properties: `systemProperties['app.vm.property']`
- System Environment Properties: `systemEnvironment['JAVA_HOME']`

### <span style="color: #99ff99;">34. What is the difference between $ and # in @Value expression?</span>

@Value supports two types of expressions:
- $: Used to reference a property in Spring Environment Abstraction.
- #: SpEL expression parsed and evaluated by SpEL.

<br><br>

<hr style="border:2px solid gray"> </hr>

<h1 id="Module-2" style="color: cornflowerblue;">Aspect Oriented Programming</h1>


### <span style="color: #99ff99;">1. What is the concept of AOP?</span>

AOP, or Aspect Oriented Programming, is a programming paradigm that complements Object-oriented Programming by separating cross-cutting concerns from business logic. It allows developers to add additional behavior to the code without modifying the code itself. This is achieved by specifying:
- Pointcut: The location in the code where the behavior should be altered, matched with a join point.
- Advice: The code that implements the cross-cutting concern.
  AOP solves problems such as code duplication, mixing of concerns, and enables cleaner, more modular code.

Typical cross-cutting concerns include logging, performance logging, caching, security, transactions, and monitoring.

If cross-cutting concerns are not solved via AOP, problems such as code duplication and mixing of concerns arise, leading to less maintainable and harder to understand code.

### <span style="color: #99ff99;">2. What is a pointcut, a join point, an advice, an aspect, weaving?</span>

- **Join Point**: A point in the execution of a program where additional behavior can be inserted. In Spring AOP, join points are always method invocations.
- **Pointcut**: A predicate used to match join points. It specifies the locations in the code where advice should be applied. Spring AOP uses AspectJ pointcut expressions.
- **Advice**: Additional behavior that is inserted at join points matched by a pointcut. It can be executed before, after, or around the join point.
- **Aspect**: The combination of a pointcut and advice. It represents a single cross-cutting concern.
- **Weaving**: The process of applying aspects to the code, modifying its behavior at join points matched by pointcuts. It can be done at compile time, load time, or runtime.

### <span style="color: #99ff99;">3. How does Spring solve (implement) a cross-cutting concern?</span>

Spring implements cross-cutting concerns using Spring AOP module. Spring AOP uses AspectJ expression syntax for defining pointcuts, which match join points in the code. Advices, which contain the additional behavior, are applied at these join points. Spring AOP uses runtime weaving to intercept method calls and apply the advices. It creates proxy objects for beans subject to aspects, allowing the interception of method invocations.

### <span style="color: #99ff99;">4. Which are the limitations of the two proxy-types? What visibility must Spring bean methods have to be proxied using Spring AOP?</span>

- **JDK Dynamic Proxy**:
    - Does not support self-invocation.
    - Requires the target class to implement an interface.
    - Only methods defined in the interface will be proxied.
- **CGLIB Proxy**:
    - Does not support self-invocation.
    - The target class cannot be final.
    - The proxied method cannot be final.
    - Only public/protected/package methods will be proxied.

Spring bean methods must have at least public visibility to be proxied using Spring AOP.

### <span style="color: #99ff99;">5. How many advice types does Spring support? Can you name each one? What are they used for? Which two advices can you use if you would like to try and catch an exception?</span>

Spring supports five advice types:
- **@Before**: Executed before a join point.
- **@After**: Executed after a join point.
- **@AfterThrowing**: Executed when an exception is thrown from a join point.
- **@AfterReturning**: Executed after a successful execution of a join point.
- **@Around**: Allows full control over a join point, including exception handling.

**@AfterThrowing** and **@Around** are typically used to try and catch exceptions.

### <span style="color: #99ff99;">6. What do you have to do to enable the detection of the @Aspect annotation? What does @EnableAspectJAutoProxy do?</span>

To enable the detection of the @Aspect annotation, you need to:
- Include a @Configuration class with @EnableAspectJAutoProxy.
- Ensure beans for @Aspect annotated classes are created either via component scanning or manually.
- Have the aspectJweaver/spring-aop dependency on the classpath.

**@EnableAspectJAutoProxy** enables the detection of @Aspect classes and creates proxy objects for beans subject to aspects. It allows Spring to intercept method calls and apply the advices. Without @EnableAspectJAutoProxy, Spring will not scan for @Aspect annotations.

### <span style="color: #99ff99;">7. If shown pointcut expressions, would you understand them?</span>

Pointcut designator types supported by Spring AOP:
- execution
- within
- args
- bean
- this
- target
- @annotation
- @args
- @within
- @target

Pointcut designator - execution - matches method execution

General form
- execution([visibility modifiers] [return type] [package].class.method([arguments]) [throws exception])

within - matches execution within specified class/classes, optionally you can specify class package

- withing([package].[class])
- may be used with .. wildcard (includes all sub-packages)

- args - matches execution of method with matching arguments

- args([parameter_type1, parameter_type2, ... n])
- indicate zero or more args - ..

- bean - matches execution of method with matching Spring Bean name

- bean([beanName])

- this - matches execution against type of proxy that was generated by Spring AOP

- this([type])
- type of the proxy, matches if generated proxy is of specified type

- target - matches execution against type of the target object invoked by proxy

- target([type])
- type of the target object invoked by proxy, matches if target object is of specified type

this - this is proxy
target - impl or class

- @annotation - matches method execution annotated with specified annotation
- @annotation([annotation_type])

- type of annotation used to annotated method which should match pointcut expression

- @args - matches method execution with argument, which types (classes) are annotated with specified annotation type, note that class should be annotated,
  not the argument of method itself
- @args([annotation_type])
- type of annotation used on top of class, which represents type of argument

@within - matches method executions inside classes annotated with specified annotation
- @within([annotation_type])
- type of annotation used on top of class, inside which method execution should be matched

@target - matches method executions inside proxied target class that is annotated with specific annotation
- @target([annotation_type])
- type of annotation used on top of proxied class, inside which method execution should be matched

Pointcut expressions can be combined together with usages of logical operators:
- ! negation
- || logical or
- && logical and

What would be the correct pointcut expression to match both getter and setter methods?

Expression that will match getters and setter can look like this:
execution(* com.beans.EmployeeBean.get*()) || execution(* com.beans.EmployeeBean.set*(*))

### <span style="color: #99ff99;">8. What is the JoinPoint argument used for?</span>

JoinPoint argument is an object that can be used to retrieve additional information about join point during execution.
JoinPoint needs to be the first parameter of Advice, only in that case Spring Framework will inject JoinPoint into advice method.

Join Point is supported in following advice types:
- Before
- After
- After Returning
- After Throwing

Examples of information that you can retrieve from JoinPoint:
- String representation of Join Point
- Arguments of Join Point (method arguments)
- Signature of Join Point (method signature)
- Kind / Type of Join Point
- Target / This object being proxied


### <span style="color: #99ff99;">9. What is a ProceedingJoinPoint? When is it used?</span>

ProceedingJoinPoint is an object that can be provided to @Around advice as first argument, it is a type of JoinPoint which can be used to change method arguments during method execution in runtime or block execution of original method entirely.

ProceedingJoinPoint is used in @Around advice, it contains all methods from JoinPoint and also adds:
- proceed - executes original method
- proceed(args) - executes original method with provided arguments

ProceedingJoinPoint can be used in following use cases:
- Conditionally block method execution
- Filter arguments
- Inject additional argument

<br><br>

<hr style="border:2px solid gray"> </hr>

<h1 id="Module-3" style="color: cornflowerblue;">Data Management: JDBC, Transactions, Spring Data JPA</h1>


### <span style="color: #99ff99;">1. What is the difference between checked and unchecked exceptions? Why does Spring prefer unchecked exceptions? What is the data access exception hierarchy?</span>

Checked exceptions are exceptions that extend java.lang.Exception and must be explicitly declared in the throws clause of a method signature or handled by the calling code. Unchecked exceptions, on the other hand, extend java.lang.RuntimeException and do not need to be explicitly declared or handled.

Spring prefers unchecked exceptions because they allow for cleaner code with less boilerplate exception handling. Unchecked exceptions provide flexibility and reduce the coupling between the caller and callee.

The data access exception hierarchy in Spring includes the following classes:
- DataAccessException (top-level exception for all data access exceptions)
    - CannotAcquireLockException
    - CannotCreateRecordException
    - DataIntegrityViolationException

### <span style="color: #99ff99;">2. How do you configure a DataSource in Spring? Which bean is very useful for development/test databases?</span>

Configuration of a DataSource in Spring depends on the type of application being executed. For standalone applications, the DataSource can be configured in a @Configuration class and created as a bean of one of the supported DataSource types. In Spring Boot applications, the DataSource is typically configured via application.properties. For applications deployed on an application server, the DataSource can be fetched from JNDI.

When working with development/test databases, the EmbeddedDatabaseBuilder bean is very useful. It allows for easy configuration of H2/HSQLDB embedded databases with schema and data initialization scripts.

### <span style="color: #99ff99;">3. What is the Template design pattern and what is the JdbcTemplate?</span>

The Template design pattern is a behavioral design pattern that encapsulates an algorithm's structure in a template method, allowing subclasses to redefine certain steps of the algorithm without changing its structure. In Java, this pattern is often implemented using abstract classes with template methods.

JdbcTemplate is a class provided by Spring in the org.springframework.jdbc.core package. It simplifies JDBC usage by providing a higher-level abstraction for common JDBC operations. JdbcTemplate handles aspects such as executing SQL queries or updates, iterating over ResultSet, and exception handling.

### <span style="color: #99ff99;">4. What is a callback? What are the three JdbcTemplate callback interfaces that can be used with queries? What is each used for?</span>

A callback is a reference to executable code that is passed as an argument to another function. In Java, callbacks are often implemented using interfaces or lambda expressions.

JdbcTemplate provides three callback interfaces for working with queries:
- RowMapper: Used to map each row of a ResultSet to an object. It is typically used for SELECT queries.
- RowCallbackHandler: Used to process each row of a ResultSet without returning a result. It is useful for tasks like logging or aggregation.
- ResultSetExtractor: Used to process the entire ResultSet and return a result. It is suitable for cases where the entire ResultSet needs to be processed, such as aggregate queries or custom result handling.


### <span style="color: #99ff99;">5. Can you execute a plain SQL statement with the JdbcTemplate?</span>

Yes, the JdbcTemplate allows the execution of plain SQL statements using methods such as:
- query
- queryForList
- queryForObject
- queryForMap
- queryForRowSet
- execute
- update
- batchUpdate

### <span style="color: #99ff99;">6. When does the JdbcTemplate acquire (and release) a connection, for every method called or once per template? Why?</span>

The JdbcTemplate acquires and releases a connection based on whether a transaction is involved or not. If the JdbcTemplate is used without a transaction, then a connection is acquired and released for every method call to minimize the time a resource (connection) is held. If the JdbcTemplate is used within a transaction, the connection is reused between method calls as long as the transaction is not committed or rolled back. This strategy optimizes resource usage and ensures that connections are not closed prematurely.

### <span style="color: #99ff99;">7. How does the JdbcTemplate support generic queries? How does it return objects and lists/maps of objects?</span>

The JdbcTemplate supports generic queries through methods such as:
- queryForObject: Returns a single object.
- queryForList: Returns a list of objects.
- queryForMap: Returns a map of objects.

These methods use callback interfaces such as RowMapper to map rows of a ResultSet to objects. The JdbcTemplate internally handles the processing of the ResultSet and the mapping of data to objects based on the provided callback interface.

### <span style="color: #99ff99;">8. What is a transaction? What is the difference between a local and global transaction?</span>

A transaction is a unit of work that consists of a series of tasks, all of which must either succeed or fail together. Transactions follow the ACID principles (Atomicity, Consistency, Isolation, Durability).

- Local Transaction: A transaction that is specific to a single resource, such as a database. It does not span multiple transactional resources.
- Global Transaction: A transaction that spans multiple transactional resources, such as databases or message queues. It coordinates updates across multiple resources and ensures that either all updates succeed or none of them do.

### <span style="color: #99ff99;">9. Is a transaction a cross-cutting concern? How is it implemented by Spring?</span>

Yes, a transaction is a cross-cutting concern because it affects multiple layers of an application and cuts across the business logic.

Spring implements transactions using the @Transactional annotation. When this annotation is used, Spring proxies the annotated class or method and applies transactional behavior, such as starting and committing transactions, around the method calls. This is achieved using AOP (Aspect-Oriented Programming) and Spring's declarative transaction management.

### <span style="color: #99ff99;">10. How do you define a transaction in Spring? What does @Transactional do? What is the PlatformTransactionManager?</span>

To define a transaction in Spring, you need to:
- Enable transaction management using @EnableTransactionManagement in your configuration class.
- Create a bean method in the configuration class that returns an implementation of PlatformTransactionManager, such as DataSourceTransactionManager.
- Use the @Transactional annotation on classes or methods where transactions should be applied.

The @Transactional annotation enables declarative transaction management in Spring. It allows you to specify transaction attributes such as isolation level, propagation behavior, timeout, read-only status, and rollback rules.

The PlatformTransactionManager is an interface used by Spring's transaction management to manage transactions. It provides methods for starting, committing, and rolling back transactions, and it is responsible for coordinating transactional behavior across different transactional resources.

### <span style="color: #99ff99;">11. Is the Jdbc template able to participate in an existing transaction?</span>

Yes, Jdbc template is able to participate in existing transaction. It will support both, transaction created with @transactional and also programmatically created transaction.

Jdbc template is able to participate in existing transaction by usage of DataSourceUtils and TransactionSynchronizationManager.
TransactionInterceptor and TransactionAspectSupport are also using PlatformTransactionManager together with DataSourceTransactionManager which will set transaction in TransactionSynchronizationManager for Jdbc Template to reuse.


### <span style="color: #99ff99;">12. What is a transaction isolation level? How many do we have and how are they ordered?</span>

Transaction isolation determines how changes made under one transaction are visible in other transactions and other users of the system. Higher isolation level means that changes from one transaction are not visible and lower isolation level means that changes from one transaction may slip into selects executed under other transaction.

Higher transaction isolation level make data being visible in more consistent way, lower transaction isolation level makes data less consistent but increases overall throughput and concurrency of the system.

Three challenges that may occur due to Transaction isolation level:
- phantom read
- non repeatable read
- dirty read

Phantom read:
- Transaction A - first read
    - select * from person where id between 5 and 10
- Transaction B - write
    - insert into person values(7, 'test', 'test');
- Transaction A - second read
    - select * from person where id between 5 and 10

High isolation level will make second read returning same values as first read, lower isolation level will include new row with id 7 in second read
To prevent phantom read, you need to pick isolation level that uses range locks.


Non-repeatable read:
- Transaction A - first read
    - select * from person where id = 5
- Transaction B - write & commit
    - update person set last_name = 'Doe' where id = 5
- Transaction A - second read
    - select * from person where id = 5

High isolation level will make second read returning same values as first read, lower isolation level will read new values for record 5
To prevent non repeatable reads you need to use isolation level that uses read-write locks on data being processed


Dirty read:
- Transaction A - first read
    - select * from person where id = 5
- Transaction B - write (commit does not have to happen)
    - update person set last_name = 'Doe' where id = 5
- Transaction A - second read
    - select * from person where id = 5

High isolation level will make second read returning same values as first read, lower isolation level will read new values for record 5, even if Transaction B will not commit the data.

To prevent dirty reads you need to use isolation level that prevents uncommitted changes by other transaction being visible in your transaction.


Most relational databases support 4 transaction levels:
- Serializable:
    - Highest isolation level
    - read-write locks held until end of transaction
    - range locks held until end of transaction
    - not possible: phantom read, non-repeatable read, dirty read
    - concurrency: very poor
- Repeatable read
    - read-write locks held until end of transaction
    - not possible: non repeatable read, dirty read
    - concurrency: poor
- Read committed
    - read locks held until ned of select statement
    - write locks held until end of transaction
    - not possible: dirty read
    - concurrency: good
- Read uncommitted
    - lowest isolation level
    - it is possible to see changes from other transactions that are not committed
    - not possible -
    - concurrency: very good

### <span style="color: #99ff99;">13. What is @EnableTransactionManagement for?</span>

Annotation is used on top of @Configuration class to enable annotation-driven transaction management by @Transactional annotation in Spring framework.

When @EnableTransactionManagement is used, TransactionalInterceptor and TransactionAspectSupport will be used to proxy each call to @Transactional class or
method, which will use PlatformTransactionManager to manage transaction.

@EnableTransactionManagement allows to specify following values:
- mode - set advice mode for @transactional, indicates how calls to methods should be intercepted, PROXY is default mode, you can switch it to more advanced ASPECTJ weaving advice, which supports local calls
- order - indicates order of advice execution when more then one advice applies to @Transactional join point
- proxyTargetClass - indicates whether CGLIB Proxy classes should be created or if JDK Proxies should be created, this field is used only when Mode is set to Proxy


### <span style="color: #99ff99;">14. What does transaction propagation mean?</span>

Transaction propagation defines how existing transaction is re-used when calling @Transactional method with transaction already running.

Transaction propagation can be defined in annotation in propagation field as one of following:
- REQUIRED - support a current transaction, create a new one if none exists
- SUPPORTS - support a current transaction, execute non-transactional if none exists
- MANDATORY - support a current transaction, throw an exception if none exists
- REQUIRES_NEW - create a new transaction, and suspend the current transaction if one exists
- NOT_SUPPORTED - execute non-transactional, suspend the current transaction if one exists
- NEVER - execute non transactional, throw exception if a transaction exists
- NESTED - execute within a nested transaction if a current transaction exists, behave lik required else


### <span style="color: #99ff99;">15. What happens if one @Transactional annotated method is calling another @Transactional method on the same object instance?</span>

Jdk proxy and cglib proxy in spring beans AOP do not support self invocation, so when one method with @Transactional calls different method with @Transactional from the same class, nothing happens, transaction interceptor will not be called.

To enable self invocation support, you need to configure Spring Aspects with AspectJ, to do that you need to:
- have dependency to spring-aspects
- include aspectj-maven-plugin
- configure transaction support with: @EnableTransactionManagement(mode = AdviceMode.ASPECTJ)


### <span style="color: #99ff99;">16. Where can the @Transactional be used? What is a typical usage if you put it at class level?</span>

@Transactional can be used on top of class or method, in classes or interfaces.

If used on top of class, it applies to all public methods in this class.

If used on top of method, it needs to have public access modifier, otherwise transaction management will not be applied

### <span style="color: #99ff99;">17. What does declarative transaction management mean?</span>

Declarative transaction management means that instead of handling transactions manually through the code, methods which should be executed in transactions are declared with @Transactional annotation.


### <span style="color: #99ff99;">18. What is the default rollback policy? How can you override it?</span>

Default rollback policy in Spring Framework is set to automatic rollback, but only when unchecked exception is being thrown from the method annotated with @Transactional. When checked exception is being thrown from the method, transaction is not being rolled back.

You can override this policy by setting rollbackFor | rollbackForClassName or noRollbackFor | noRollbackForClassName field in @Transactional.

### <span style="color: #99ff99;">19. What is default rollback policy in a JUnit test, when you use the @RunWith(SpringJUnit4ClassRunner.class) in JUnit 4 or @ExtendWith(SpringExtension.class) in JUnit 5, and annotate your @Test method with @Transactional?</span>

Default rollback policy in @Test methods with @Transactional is always rollback. This means that after test execution transaction will always be rolled back. The reason for this is that each test method should be able to change state of database or call other classes that will change state of the database, however for the tests to be repeatable, changes should be reverted after @Test method execution.

You can change this behavior by using @Rollback set to false.


### <span style="color: #99ff99;">20. Why is the term "unit of work" so important and why does JDBC AutoCommit violate this pattern?</span>

Unit of work is a generic term to describe, set of tasks that are performing some changes needs to be performed, or no changes should be performed at all.

In Relational Databases, Unit of Work can be represented by Database Transaction, which Atomic nature describes "all-or-nothing" behavior described above.

In context of JPa|Hibernate, Unit of work tracks all changes made to the data Objects representing entries in the database, and once done, ORM figures out all changes that needs to be applied to the database. This way amount of calls to the database can be minimized by aggregating all changes into one call.

Jdbc AutoCommit violates Unit of Work, because it makes every SQL statement being invoked in a separate transaction that is committed after SQL is executed, this makes impossible to implement Unit of Work consisting of multiple SQL operations.


### <span style="color: #99ff99;">21. What do you need to do in Spring if you would like to work with JPA?</span>

Following steps are required to work with JPA in Spring Framework:
- Declare maven dependencies:
    - JPA API - javax.persistence
    - Spring ORM - org.springframework
    - ORM of your choice - org.hibernate:hibernate-core
    - Database Driver - org.hsqldb
    - Optionally, Spring Data JPA - org.springframework.data
- Define DataSource Bean
- Define PlatformTransactionManager, in case of JPA JpaTransactionManager
- Define EntityManagerFactoryBean
    - LocalContainerEntityManagerFactoryBean for standalone application
    - EntityManagerFactory from JNDI
    - LocalEntityManagerFactoryBean for Test purposes
- Define @Entity classes with at least on @Id field
- Define DAO classes, or use Spring Data JPA repositories


### <span style="color: #99ff99;">22. Are you able to participate in a given transaction in Spring while working with JPA?</span>

Yes, JPA in Spring uses JpaTransactionManager, which supports cases when DataSource is used directly, so it allows mixing JPA and JDBC code under one transaction.

When using Spring Framework on Java EE platform, it is possible to reuse existing transaction as well by using JtaTransactionManager, which will delegate transaction management to Java EE container.


### <span style="color: #99ff99;">23. Which PlatformTransactionManager can you use with JPA?</span>

JPA can work with following transaction managers:
- JpaTransactionManager - recommend when working with one database and one Entity Manager
- JtaTransactionManager - recommended when working with multiple databases and Entity Managers, or when working with multiple databases and other transactional resources, for example one transaction needs to span Database and JMS Topic

Usage of JpaTransactionManager in case of multiple Databases / Transaction Resources / Entity Managers will cause each transaction, span only one resource, this is why JtaTransactionManager is required in this case.

Multiple Databases / Entity Managers Scenario with incorrectly used JpaTransactionManager for this case use JtaTransactionManager


### <span style="color: #99ff99;">24. What do you have to configure to use JPA with Spring? How does Spring Boot make this easier?</span>

Following steps are required to work with JPA in Spring Framework:
- Declare maven dependencies:
    - JPA API - javax.persistence
    - Spring ORM - org.springframework
    - ORM of your choice - org.hibernate:hibernate-core
    - Database Driver - org.hsqldb
    - Optionally, Spring Data JPA - org.springframework.data
- Define DataSource Bean
- Define PlatformTransactionManager, in case of JPA JpaTransactionManager
- Define EntityManagerFactoryBean
    - LocalContainerEntityManagerFactoryBean for standalone application
    - EntityManagerFactory from JNDI
    - LocalEntityManagerFactoryBean for Test purposes
- Define @Entity classes with at least on @Id field
- Define DAO classes, or use Spring Data JPA repositories

Spring Boot simplifies JPA setup by:
- Providing spring-boot-starter-data-jpa dependency which includes all required dependencies
- Providing auto-configuration for JPA
- Automatically defines PlatformTransactionManager, EntityManager and other required beans
- Allows Data Source to be configured via properties
- Provides out-of-the-box support for Hikari Connection Pool
- Automatically creates DAO beans for Repositories.


### <span style="color: #99ff99;">25. What is a Repository interface?</span>

Repository interface is a Java interface that describes Dao with expected behaviors, based on which Spring Data will automatically generate Dao logic. Repository interface takes Domain class and ID type to manage.

Custom repository interface needs to extend one of following interface:
- Repository - basic marker repository
- CrudRepository - adds generic methods for CRUD operations
- PagingAndSortingRepository - adds findAll methods for paging/sorting
- JpaRepository - JPA specific extension of Repository


### <span style="color: #99ff99;">26. How do you define Repository interface? Why is it an interface not a class?</span>

To define Repository interface, you need to follow those steps:
- Create Java interface that extend one of: Repository, CrudRepository, PagingAndSortingRepository, JpaRepository
- Create class with @Entity
- Inside @Entity class create a simple primary key with @Id or create a class that represent complex key with @EmbeddedId at field level and @Embeddable at key class definition level.
- Use @EnableJpaRepositories to point out package to scan for Repositories

Repositories interface is an interface, not a class for Spring DAta to be able to use JDK Dynamic Proxy to intercept all calls to repository and also to allow creation of custom base repositories for every Dao based on SimpleJpaRepository configured at @EnableJpaRepositories level


### <span style="color: #99ff99;">27. What is the naming convention for finder methods in a Repository interface?</span>

find[limit]By[property/properties expression][comparison][ordering operator]

limit - result of the query can be limited by usage of first/top keyword
- findFirst10ByLastName

property/properties expression - result will be filtered based on property of entity, multiple properties can be used with usage of And, Or keyword
- FindByLastnameOrFirstname

comparison - comparison mode can be specified after specify property used for filtering
- findByStartDateBetween

ordering operator - optionally you can specify ordering operator at the end of method name
- findByLastNameOrderByFirstnameDesc


### <span style="color: #99ff99;">28. How are Spring Data repositories implemented by Spring at runtime?</span>

Spring Repositories are implemented at runtime by SimpleJpaRepository by default.

When application context is starting up, Spring will scan for all classes annotated with @Configuration.
When @Configuration class with @EnableJpaRepositories will be detected, JpaRepositoriesRegistrar with JpaRepositoryConfigExtension will be used to create beans for repositories in packages pointed out by basePackages field in @EnableJpaRepositories. JpaRepositoryFactoryBean will use JpaRepositoryFactory to create beans based on bean definitions and by default will create instance of SimpleJpaRepository class for each Repository interface.

Class used implementation of Repository interface can be customized on:
- Global level, by using repositoryBaseClass field from @EnableJpaRepositories
- Single Dao/Repository by creating separate interface and Impl class for behavior that you want to customize


### <span style="color: #99ff99;">29. What is @Query used for?</span>

@Query can be used on top of Repository method and with it you can specify query that should be used by JPA. When declaring one on top of finder method, specified query will be used, instead of generating one automatically based on finder method name.

Using @Query allows you to achieve more control and flexibility of the JPA query that will be executed.

<br><br>

<hr style="border:2px solid gray"> </hr>

<h1 id="Module-4" style="color: cornflowerblue;"> Spring Boot, Spring Boot Auto Configuration, Spring Boot Actuator, Spring Boot Testing </h1>


### <span style="color: #99ff99;">1. What is Spring boot?</span>

Spring boot is a Java Framework that allows you to easily create stand alone, production grade Spring based Java applications. It is often used in microservice architecture because of simplicity that it allows.

Applications created with spring boot can be executed with simple java -jar command and also allows traditional war deployment. Spring boot supports following embedded containers:
- Tomcat
- Jetty
- Undertow

Simplicity of deployment and execution has many advantages, for example, it allows for Dev/Prod parity which increases product quality.

Spring Boot provides number of features that can be used to fulfill non functional requirements for the project.

Spring boot provides many modules under common umbrella:
- spring boot devtools - live-reload to speed-up development
- spring boot actuator - monitoring and management of application
- spring boot starters - dependency set for technologies to minimize setup time
- spring boot autoconfiguration - configuration templates for technologies to minimize setup time

On top of it, you can use all spring framework technologies, like:
- Spring web - spring mvc framework
- Template Engines - server side rendering engines for web pages
- Spring security - authentication and authorization framework
- Spring Data MongoDb - nosql database client


### <span style="color: #99ff99;">2. What are advantages of using Spring Boot?</span>

- Maximizes productivity
- Simplifies deployment, by allowing to create executable jar and also supports traditional deployment on top of application server
- provides automatic configuration which reduces boilerplate configuration, and allows easy customization when defaults are not sufficient


### <span style="color: #99ff99;">3. Why is it opinionated?</span>

Spring boot is opinionated framework because it comes with general idea on how application should be organized, provides default configurations and modules setups for technology related aspect of application.

In comparison with Spring framework, spring boot provides starters and autoconfiguration which intelligently fits default configuration based on defined dependencies.

Main advantages on how spring boot approaches "opinionated" style is that you can always override default configuration if it does not fit your use case.

Opinionated has following advantages:
- simplifies application setup
- maximizes productivity by allowing you to focus on business code instead of setup of technology related code
- allows you to write configuration only in case when defaults are not a good fit for your case

The main disadvantage of opinionated framework is that if your application does not fall into most use cases supported by framework, you will have to override most of default setup, configurations and project organization, which might harm your productivity


### <span style="color: #99ff99;">4. What things affect what spring boot sets up?</span>

Spring boot uses autoconfiguration to detect dependencies on the class path, based on detected dependencies, spring beans are configured to allow integration with technologies, like JPA, Data sources, embedded databases, template rendering engines etc.

Spring boot searches for META-INF/spring.factories on classpath that should contain entry EnableAutoConfiguration that lists all autoconfiguration classes provided by the autoconfiguration module.

Autoconfiguration class is using @ConditionalOn annotations to specify under which conditions, certain AutoConfiguration should be applied

Spring boot supports following conditional annotations for AutoConfiguration classes:
- conditionalOnBean - presence of spring bean
- conditionalOnMissingBean - absence of spring bean
- conditionalOnClass - presence of class on classpath
- conditionalOnMissingClass - absence of class on classpath
- conditionalOnCloudPlatform - if specified cloud platform is active - for example Cloud Foundry
- conditionalOnProperty
- ConditionalOnResource


### <span style="color: #99ff99;">5. What is a Spring boot starter POM? Why is it useful?</span>

Spring starter POM is a maven module that represents empty jar with set of dependencies required to work with specified technology. Spring starter may also provide autoconfiguration to create beans required to integrate project with technologies that you intend to use.

Spring starters are useful, because they simplify project setup by assuring that all dependencies in correct versions are set. If starter provides autoconfiguration as well, it integrates technology with Spring framework.


### <span style="color: #99ff99;">6. Spring boot supports both properties and yml files. Would you recognize and understand them if you saw them?</span>

Spring boot allows you to externalize configuration for the application by using properties stored in properties files that can be in format:
- yaml
- java properties file

YAML is a superset of JSON and it is convenience for specifying hierarchical data. Spring boot supports YAML properties with usage of SnakeYAML lib, which is included by default by spring-boot-starter.

You can transform application properties between YAML and Java properties format.



### <span style="color: #99ff99;">7. Can you control logging with Spring boot? How?</span>

Spring boot allows you to configure following aspects of logging:
- levels
- pattern
- colors
- output - console, file
- rotation
- groups
- system used (logback, log4j, jdk)
- system specific configuration

Logging level can be set via application.properties or by using logging system specific configuration (logback-spring.xml).


### <span style="color: #99ff99;">8. Where does Spring boot look for property file by default?</span>

Spring boot looks for properties in following locations:
- Profile Specific
    - Outside of Jar:
        - application-{profile}.properties and yml outside of jar in /config subdirectory
        - application-{profile}.properties and yml outside of jar in current directory
    - Inside Jar:
        - application-{profile}.properties and yml inside of jar in /config package on classpath
        - application-{profile}.properties and yml inside of jar in classpath root package
- Application Specific
    - Outside of Jar:
        - application-{profile}.properties and yml outside of jar in /config subdirectory
        - application-{profile}.properties and yml outside of jar in current directory
    - Inside Jar:
        - application-{profile}.properties and yml inside of jar in /config package on classpath
        - application-{profile}.properties and yml inside of jar in classpath root package

You can change name of default configuration file with usage of spring.config.name property:
```maven
$ java -jar myproject.jar --spring.config.location=classpath:/default.properties
  ```
You can also explicitly point location of configuration file with usage of spring.config.location property:

```maven
$ java -jar myproject.jar --spring.location=classpath:/default.properties
  ```

### <span style="color: #99ff99;">9. How do you define profile specific property files?</span>

Spring boot allows you to define profile specific property files in two ways:
- Dedicated property file per profile:
    - application-{profile}.properties
    - application-{profile}.yml
        - also can be used application-default.properties or application-default.yml for property to be used when no profile is active

<br>
- Multi-profile YAML Document <br>
  server: <br>
  url: http://local.service.com/ <br>
--- <br>
spring: <br>
profiles: dev <br>
server: <br>
url: http://dev.service.com <br>
--- <br>
spring: <br>
profiles: prod <br>
server: <br>
url: http://prod.service.com/ <br>


### <span style="color: #99ff99;">10. How do you access the properties defined in the property files?</span>

Spring boot allows you to access properties defined in property files in following ways:
- @Value("${property_name}") - inject properties into fields

- @ConfigurationProperties
- you can define Data Object which will hold properties for defined prefix, you also need to register Configuration Properties Data Object with usage of EnableConfigurationProperties

- Environment property resolver - inject and use Environment object


### <span style="color: #99ff99;">11. What properties do you have to define in order to configure external MySQL?</span>

To configure external MySql in Spring Boot you need to specify URL, Username, Password for Data Source by defining properties
spring.datasource.uri , .username, .password

Optionally, you can also explicitly specify JDBC driver - spring.datasource.driver-class-name=

To initialize Database during application startup via data.sql and schema.sql you need to specify property:
- spring.datasource.initialization-mode=always

Need to specify connector dependency: mysql-connector-java

Access to database, simplest approach is to use JDBC: spring-boot-starter-data-jdbc


### <span style="color: #99ff99;">12. How do you configure default schema and initial data?</span>

Spring boot uses following scripts to configure default schema and initial data:
- schema.sql - contains DDL for db objects creation
- data.sql - contains data that should be inserted upon db initialization

Spring boot will also load:
- schema-{platform}.sql
- data-${platform}.sql
  platform value of spring.datasource.platform property, this allows you to switch between database vendor specific scripts.

Spring boot will automatically initialize only embedded databases, if you want to initialize regular database as well, you need to set property:
spring.datasource.initialization-mode=always

If change name of schema.sql or/and data.sql script names you can use spring.datasource.schema and .data properties


### <span style="color: #99ff99;">13. What is a fat jar? How is it different from the original jar?</span>

Fat jar, also called "executable jar" is a jar that contains compiled code for your application and also all dependencies. Spring boot uses nested jars approach, that mean that fat jar contains all dependencies as nested jars. This differs from other approach, which is uber jar that packs all dependencies into single jar archive. Uber jar approach is problematic because it is hard to see application dependencies and also causes issues when same filename in the same context is used in different jars.

In fat jar Spring boot will generate MANIFEST.MF file which contains Main-class and Start-class entries together with JarLauncher code. This manifest together with launcher code will be used to execute standalone jar.

To create fat jar in your project, you need to use spring-boot-maven-plugin.
Executing application is as simple as executing one command:
java -jar spring-boot-application-1.0-SNAPSHOT.jar

The differences in comparison to original jar are following:
- original jar does not contain all dependencies
- original jar is not executable by default


### <span style="color: #99ff99;">14. What is the difference between an embedded container and a WAR?</span>

WAR (Web application archive) is a file that represents web module. WAR cannot be executed in standalone mode, it needs to be deployed to Application Server like Tomcat or WildFly.

Embedded container is used to execute executable jars. Embedded container is packed asd dependency in executable jar and will be responsible for executing only single application. War approach on the other hand uses Application Server which might be used to execute multiple applications at the same time.

WAR file has following structure:
- Assembly root:
    - JSP pages, static HTML pages
    - META INF
        - MANIFEST.MF
    - WEB-INF
        - web.xml - not required for Servlet 3+
        - lib
        - classes
        - tags

Spring boot Executable JAR has following structure:
- Assembly root:
    - BOOT-INF
        - classes
        - lib
            - tomcat-embedded-core-9...jar
    - META-INF
        - MANIFEST.MF
    - org.springframework.boot.loader
        - JarLauncher.class


To create WAR file with Spring boot, you need to:
- specify war packaging method:
    - <packaging>war</packaging>
- specify required dependencies:
    - spring-boot-starter-web
    - spring-boot-starter-tomcat (<scope>provided</scope>)
- use war plugin
    - maven-war-plugin

To create Executable JAR file with embedded container in Spring Boot, you need to:
- specify required dependencies
    - spring-boot-starter-web
- use spring boot maven plugin
    - spring-boot-maven-plugin
    - <goal>repackage</goal>


### <span style="color: #99ff99;">15. What embedded containers does Spring boot support?</span>

Spring boot supports following embedded containers:
- Tomcat
- Jetty
- Undertow

Tomcat is used as default embedded container, it will be automatically included when application is using spring-boot-starter-web.

To use Jetty embedded container you need to exclude spring-boot-starter-tomcat and include spring-boot-starter-jetty

To use Undertow embedded container you need to exclude spring-boot-starter-tomcat and include spring-boot-starter-undertow


### <span style="color: #99ff99;">16. How does Spring boot know what to configure?</span>

Spring boot knows what to configure by usage of Auto Configuration classes defined in starter modules. Spring boot searches for META-INF/spring.factories on classpath, whenever entry org.springframework.boot.autoconfigure.EnableAutoConfiguration is encountered in this file, Auto Configuration Class pointer by this property is loaded.

Auto Configuration class is a regular @Configuration class annotated with @ConditionalOn which specifies under which conditions @Configuration class should be loaded.

When conditions from @ConditionalOn are matched, @Configuration class is loaded which provides beans that integrates your application with specified technology.

Auto Configuration is often used with starter modules. Starter module provides set of dependencies, and optionally may provide Auto configuration classes.


### <span style="color: #99ff99;">17. What does @EnableAutoConfiguration do?</span>

@EnableAutoConf turns auto configuration of spring context. Auto configuration tries to guess Spring beans that should be created for your application based on configured dependencies and configurations with @ConditionalOn.

When auto-configuration is turned on, Spring will search for META-INF/spring.factories on classpath, whenever entry EnableAutoConfiguration is encountered in this file, Auto Configuration Class pointed by this property is loaded. When condition present in @ConditionalOn is matched, beans pointed out by this configuration are created.

When using Spring Boot with @SpringBootApplication, @EnableAutoConfiguration is not required because auto-configuration is turned on by default.


### <span style="color: #99ff99;">18. What does @SpringBootApplication do?</span>

Its used on top of the class and  it was introduced for convenience. Usage of @springBootApplication is equivalent to usage of following three annotations:
- @Configuration - allows additional bean registration
- @EnableAutoConfiguration - enables context auto-configuration
- @ComponentScan - turns on scanning for @Component classes


### <span style="color: #99ff99;">19. Does Spring boot do component scanning? Where does it look by default?</span>

Yes, spring boot is performing component scan, because @SpringBootApplication is enabling component scanning with usage of @ComponentScan.

By default, spring boot will search for @Component classes within the same root package as @SpringBootApplication class.

You can change this behavior by adding additional packages to scan with scanBasePackages or type-safe version of it scanBasePackageClasses within @springBootApplication.


### <span style="color: #99ff99;">20. How are DataSource and JDBCTemplate auto-configured?</span>

DataSource and JdbcTemplate are configured by Auto Configuration classes defined in spring-boot-autoconfigure module.

DataSource is configured by DataSourceAutoConfiguration, JdbcTemplate is configured by JdbcTemplateAutoConfiguration.
DataSourceAutoConf required some properties to be defined, example below shows Mysql configuration.
- spring.datasource.url , .username, .password

Above properties will be injected into DataSourceProperties by the prefix spring.datasource and used by DataSourceAutoConfiguration.


### <span style="color: #99ff99;">21. What is spring.factories file for?</span>

spring.factories file, located in META-INF/spring.factories location on the classpath, is used by Auto Configuration mechanism to locate Auto Configuration Classes. Each module that provides Auto Configuration class needs to have META-INF/spring.factories file with EnableAutoConfiguration
entry that will point Auto configuration classes.

META-INF/spring.factories file is consumed by SpringFactoriesLoader class, which is used by AutoConfigurationImportSelector enabled by @EnableAutoConfiguration used by default in SpringBootApplication.

Auto configuration use case for spring.factories file is probably most popular one, it also allows you to define other entries and achieve context customization with following classes: ApplicationContextInitializer, ApplicationListener...


### <span style="color: #99ff99;">22. How do you customize Spring auto configuration?</span>

You can customize Spring auto configuration by creating your own auto-configuration module with auto configuration class.

To do that you need to create java jar module which wil contain META-INF/spring.factories file that contains EnableAutoConfiguration entry, which points to your auto configuration class.

Auto configuration class is a class with @Configuration, usually used together with ConditionalOnClass. Additionally you can use @PropertySource annotation with EnableConfigurationProperties and ConfigurationProperties to introduce custom properties for your auto-configuration module.


### <span style="color: #99ff99;">23. What are the examples of @Conditional annotations? How are they used?</span>

Spring boot support following conditional annotations for auto configuration classes:
- conditionalOnBean
- conditionalOnMissingBean
- conditionalOnClass
- conditionalOnMissingClass
- conditionalOnCloudPlatform
- conditionalOnJava
- conditionalOnProperty
- ...

@Conditional annotations are used together with Auto configuration classes, to indicate under which conditions specific @Configuration class should apply.


### <span style="color: #99ff99;">24. What value does Spring boot actuator provide?</span>

Spring boot actuator provides features tat are required for your application to be viewed as production read product:
- monitoring
- health-checks
- metrics
- audit events

Advantage of using spring boot actuator is that you can use those features in your product without having to code them on your own and enabling it is as simple as putting dependency in your project
- /actuator/health
- -||-/info


### <span style="color: #99ff99;">25. What are the two protocols you can use to access actuator endpoints?</span>

Spring boot actuator supports two protocols:
- http
- jmx

Http endpoints can be accessed by any HTTP client like CURL or web browser by default following are enabled:
- actuator/info and /health

JMX allows you to access actuator Mbeans under org.springframework.boot group. You can access it with any tool that supports JMX protocol. One of the tool that you can use is JConsole which come with JDK. You can access JMX:
- locally by PID
- remotely via socket after enabling it with following Java VM flags
    - Dcom.sun.management.jmxremote.local.only=false
    - Dcom.sun.management.jmxremote.port= 9010
    - Dcom.sun.management.jmxremote.authenticate=false
    - Dcom.sun.management.jmxremote.ssl=false


### <span style="color: #99ff99;">26. What are the actuator endpoints that are provided out of the box?</span>

Every one of the endpoint is enabled on by default except the shutdown. On JMX are all enabled by default except those who runs on web application (promethous, heapdump, jolokia, logfile). Default exposure via web are info and health endpoint.

You can enable or disable actuator endpoints with usage of property:
```properties
management.endpoint.${ENDPOINT_NAME}.enable=true
```

For example:
```properties
management.endpoint.shutdown.enabled=true
```

You can also disable "Enabled by default" behavior with usage of property:
```properties
management.endpoints.enabled-by-default=false
```
Endpoints exposure with usage of properties
```properties
management.endpoints.jmx.exposure.exclude/include=*
management.endpoints.web.exposure.exclude/include=info,health,env
```
Navigation through actuator endpoints can be enabled by usage of HATEOAS
- to enable navigation, add dependency to project


### <span style="color: #99ff99;">27. What is info endpoint for? How do you supply data?</span>

Spring boot actuator info endpoint is used to provide arbitrary non sensitive custom defined data available at runtime that can provide additional information about started application.

info endpoint is exposed by default via protocols:
- http at actuator/info
- jmx at org.springframework.boot/Endpoint/Info

It can be supplied data to spring boot by using following methods:
- with usage of property files by defining info.* properties
- by implementing InfoContributor bean


### <span style="color: #99ff99;">28. How do you change logging level of a package using loggers endpoint?</span>

Spring actuator allows you to list currently configured loggers with their levels in following ways:
- via http by visiting /actuator/loggers endpoint
- via jmx by executing org.springframework.boot/Endpoint/Loggers/Operators/loggers

loggers endpoint is exposed by default via JMX, to use it via HTTP you need to expose it by setting following property:
```properties
management.endpoints.web.exposure.include=loggers
```

Logging level
- via http
  - /actuator/loggers/${LOGGER_NAME}
- via JMX by executing 
  - /Endpoint/Loggers/Operations/loggerLevels with provided parameter

You can change logging level by:
- http post /actuator/loggers/${LOGGER_NAME}: {"configuredLevel": "TRACE"}
- jmx /Endpoint/Loggers/Operations/loggerLevels with provided parameter


### <span style="color: #99ff99;">29. How do you access an endpoint using a tag?</span>

Access an endpoint using a tag by defining it as part of the request in following way: tag=KEY:VALUE

example:
```http
/actuator/metrics/http.server.requests?tag=status:200
```
Multiple tag in one query with usage of &:
tag=KEY1:VALUE1&tag=KEY2:VALUE2


### <span style="color: #99ff99;">30. What is metrics for?</span>

Spring actuator provides metrics endpoint which can be used to examine metrics collected by the application during runtime.

metrics endpoint allows you to view information about specific metric by visiting metric uri,
```http
/actuator/metrics/jvm.memory.used?tag=area:heap
```
metrics endpoint:
- cpu usage, cpu core count
- memory usage, max memory available
- threads info
- garbage collector statistics
- http request info
- embedded tomcat related metrics

metric is not exposed by default via web, need to add following properties: management.endpoints.web.exposure.include=metrics


### <span style="color: #99ff99;">31. How do you create a custom metric with or without tags?</span>

Spring boot actuator allows you to create custom metrics with usage of MeterRegistry from Micrometer Application Metrics Facade.
Micrometer used by spring boot actuator allows you to register meter primitives that can be exposed via actuator/metrics endpoint

Registration of metric can be done via method inside MeterRegistry
```java
meterRegistry.counter("storage.object.count", "type", "db")
```
  or via builder
```java
- Counter.builder("storage.object.count").tag().register()
```


### <span style="color: #99ff99;">32. What is health indicator?</span>

Health indicator is a component used by /actuator/health endpoint to check if system is in a state which can be used to successfully handle requests.

/actuator/health endpoint is returning aggregated information on system status by evaluating all health indicators registered in HealthIndicatorRegistry.

endpoint is exposed by default via both jmx and web, exposing by default only minimal set of information

This endpoint is used usually by monitoring software to periodically check system status, upon receiving failed status, automated alert is sent to product support team.

- it can be used by load balancer to check which instances are healthy

To change level of details exposed by /actuator/health endpoint, following properties can be used:
```properties
 management.endpoint.health.show-details=...
 management.endpoint.health.show.components=never,when-authorized, always
```
To create custom Health Indicator, spring bean has to be created that implements HealthIndicator interface


### <span style="color: #99ff99;">33. What are the health indicators that are provided out of the box?</span>

Spring actuator provides following health indicators that are configured when proper dependencies are found:
- applicationHealthIndicator - default implementation, always up
- diskSpaceHealthIndicator
- dataSourceHealthIndicator
- RabbitHealthIndicator

Spring actuator also provides Reactive health indicators for reactive applications, like those using spring webFlux:
- redisReactiveHealthIndicator - checks that a redis server is up
- mongoReactiveHealthIndicator


### <span style="color: #99ff99;">34. What is the health indicator status?</span>

Health indicator status is used by health indicators to inform spring actuator if system component checked by them is working correctly or not.

Each health indicator is expected to return status that represents guarded component state, status can be one of following
- up, down, out of service, unknown, custom defined

Spring actuator is also using HealthAggregator, especially OrderedHealthAggregator to aggregate statuses from all health indicators and decide on final status. Ordering status from worst to best.


### <span style="color: #99ff99;">35. What are the health indicator statuses that are provided out of the box?</span>

Spring actuator provides following health indicator statuses out of the box:
- up, down, out of service, unknown


Based on health indicator statuses from above, spring will also perform default mapping of status to http response code with usage pf healthStatusHttpMapper that follows configuration:
- up - 200
- unknown - 200
- down - 503
- out of service - 503

Default mapping can be changed with usage of management.health.status.http-mapping=501 property


### <span style="color: #99ff99;">36. How do you change the Health indicator status severity order?</span>

Spring actuator allows you to change health indicator status severity order with usage of property management.health.status.order:
management.health.status.order=system-halted, DOWN, OUT OF SERVICE, UP...

This property will be injected into HealthIndicatorProperties and used by OrderedHealthAggregator to resolve final status for application.


### <span style="color: #99ff99;">37. Why do you want to leverage 3rd party external monitoring system?</span>

It is a good idea to use external monitoring system, because this way you can use monitoring functionalities without having to spend time coding them.

Configuring external monitoring system is as easy as adding dependency:
micrometer-registry-${monitoring-system-name}


### <span style="color: #99ff99;">38. When do you want to use @SpringBootTest annotation?</span>

You should use @SpringBootTest whenever writing JUnit integration test for product that is using spring boot.

Spring boot approach to integration testing simplifies it by eliminating requirement of application deployment or establishing connection to other infrastructure.

To use @SpringBootTest, need to add @RunWith(SpringRunner.class) on top of test class, this is required only for JUNIT 4, for JUnit 5 @ExtendWith(SpringExtension.class) is already contained in SpringBootTest.


### <span style="color: #99ff99;">39. What does @SpringBootTest auto-configure?</span>

SpringBootTest will auto configure:
- applicationContext for testing
- test itself with tools used for testing

ApplicationContext is configured by searching for @SpringBootApplication or SpringBootConfiguration classes, based od those bean definition will be created

It is possible to test only slice of the application with usage one of following:
- @SpringBootTest#classes
- @ContextConfiguration#classes
- @AutoConfigure annotations

@AutoConfigure allows you to configure specific environment and tools for testing, for example @AutoConfigureMockMvc will configure Mock Mvc that can be used for Controllers testing


### <span style="color: #99ff99;">40. What dependencies does spring-boot-starter-test brings to the classpath?</span>

- JUnit - unit testing
- spring test - spring framework support for testing
- spring boot test - utilities and integration test support
- assesrtJ - fluent assertion library
- hamcrest - matchers library
- mockito - mocking framework
- JSONAssert - JSON assertion library
- JsonPath - XPath for JSON
- XMLUnit - Tools for xml verification

To see all dependencies with versions for maven module by running: mvn dependency:tree


### <span style="color: #99ff99;">41. How do you perform integration testing with @SpringBootTest for a web application?</span>

Integration Test by definition, should check interactions between few components of the system to check if those components are delivering expected functionalities when working together. In each case when writing integration test you should decide how many components should interact in the test for it to be meaningful. Usually you should decide on smallest possible amount of components that are enaugh to test specific functionality. Components that are not meaningful can be omitted or mocked with usage of @MockBean.

Web components tests if tested in integration way, should be written in a way for test to make a http request and check http response. This kind of approach results in meaningful test, which delivers feedback that actually checks if component works correctly.


### <span style="color: #99ff99;">42. When do you want to use @WebMvcTest? What does it auto-configure?</span>

You should use @WebMvcTest when you want to write Integration test that is focused on web layer of your application. @WebMvcTest approach will create ApplicationContext that contains only web components and omits any other components that are not part of web layer. Other components, if required for the test, can be mocked with usage of @MockBean or delivered by @Configuration class importef with usage of @Import.

@webMvcTest supports two cases:
- single controller auto configuration - annotate test by providing Controller class
- multiple Controllers auto-configuration - just annotate test with @WebMvcTest

@WebMvcTest will auto-configure:
- Mock Mvc
- @ControllerAdvice
- @JsonComponent
- @Converter
- @GenericConverter
- @Filter
- @WebMvcConfigurer
- @HandlerMethodArgumentResolver


### <span style="color: #99ff99;">43. What are the differences between @MockBean and @Mock?</span>

@Mock comes from Mockito Framework which allows for easy Mock creation. This annotation is used by MockitoJUnitRunner, each field annotated with it will have Mock for specified class created. This annotation does not inject mocks into tested class on itself, to use injection you need to have target class annotated with @InjectMocks.

@MockBean comes from spring-boot-test, it creates Mockito Mock and also injects it into Application Context created by @SpringBootTest. All beans which refers to mocked class via @Autowired will get this mock injected instead of real class.

Main difference between @MockBean and @Mock is that @MockBean creates mock and injects it into ApplicationContext, while @Mock annotation only creates it.


### <span style="color: #99ff99;">44. When do you want use @DataJpaTest for? What does it auto-configure?</span>

You want to use @DataJpaTest whenever writing an integration test for jpa related components of your application like Entities and Repositories.

@DataJpaTest configures:
- in memory embedded database - can be disabled @AutoConfigureTestDatabase(replace = Replace.NONE)
- Scans and configures @Entity beans
- scans and configures spring data repositories
- configure testEntityManager
- does not load @Components, @Service, @Controller

Every @DataJpaTest is transactional by default after each test transaction is rolled back. You can use @Transactional to modify behavior.

When using @DataJpaTest you can access TestEntityManager, which contains subset of EntityManager methods.

<br><br>

<hr style="border:2px solid gray"> </hr>

<h1 id="Module-5" style="color: cornflowerblue;"> Spring MVC and the Web Layer </h1>

### <span style="color: #99ff99;">1. MVC is an abbreviation for design pattern. What does it stand for and what is the idea behind it?</span>

MVC stand for Model view controller it is design pattern which divides application into three main interconnected component types.

Model
- data access
- data structures
- business logic
- crud logic

View
- data representation to the user
- multiple representations of the same data are possible

Controller
- accepts requests from the users
- issues command to model
- modifies the model
- decides on view to use


User -> Request -> Controller -> Manipulates -> Model -> Data to be displayed -> View -> Response -> User

Spring MVC introduces ready to use components
Model
- Spring Data jpa
- spring data jdbc
- spring data mongodb

View
- thymeleaf
- freemarker
- velocity
- groovy
- jsp

Controller
- controller classes
- restcontroller classes


### <span style="color: #99ff99;">2. What is the DispatcherServlet and what is it used for?</span>

DispatcherServlet is an internal Spring MVC component that implements HttpServlet from Java servlet api and Front Controller design pattern. It is used to handle all requests to the application, based on servlet mapping, delegate those requests to the application, based on servlet mapping, delegate those requests to controllers and produce response based on identified view.

DispatcherServlet has following responsibilities:
- Delegate received requests to Controllers
- Uses view resolvers to resolve views pointed out by controllers
- Produces response that is sent to user
- handles shared concerns, like exception mapping, error handling, security

Front controller design pattern allows you to implement shared algorithm for entire application responsible for request processing and handling shared concerns.

user (request) -> Front Controller (Delegate request)-> Controllers (Model - Delegate view rendering)-> Front Controller (Render view)-> View Rendering (Find view)-> Views (Get view)-> View rendering (Rendered view)-> Front controller (Response)-> User

Servlet is a Java technology used to create Web applications on java platform with usage of application servers. It is a set of interfaces, classes, and documentation allowing you to extend capabilities of Application servers. Servlet is protocol independent, however usually it is used to process HTTP requests with usage of custom implementation of httpServlet class. Servlet can be registered via web.xml, or programmatically via annotations since Servlet 3. Servlet registration requires url-patterns which informs application server which requests should be mapped to your servlet.
Application Server
User (Requests)-> /app-a/ - > Servlet 1 -> (Response) User


### <span style="color: #99ff99;">3. What is a web application context? What extra scopes does it offer?</span>

Web application context is a spring application context for web application that runs under Embedded or standalone application server that supports servlet api and acts as servlet container.

Web application context is described by Web applicationContext interface and it allows you to access servletContext interface from servlet api.

Web application context provides four additional scopes:
- request scope
- session scope
- application scope
- websocket scope

Request scope
- defined by @RequestScope
- bean lifecycle is tightly coupled with HTTP request lifecycle
- new bean instance is created for each request

Session scope
- defined by @SessionScope
- lifecycle coupled with HTTP session lifecycle
- new bean is created for each new session and bean instance lives as long as http session alive

Application scope
- defined by @ApplicationScope
- bean lifecycle is tightly coupled with servletContext
- one bean instance available per entire web application - servletContext
- difference compared to singleton bean:
  - singleton per servlet context, not per Spring application Context (one web application may have server spring application context)
  - exposed via attribute of servletContext

Websocket scope
- defined by @Scope with specified properties:
  - scopeName, proxyMode
- bean lifecycle is coupled with lifecycle of webSocket session, however bean usually lives longer then webSocket session


### <span style="color: #99ff99;">4. What is the @Controller used for?</span>

@Controller is used to indicate that annotated class is a Controller from Model-View-Controller design pattern, and should be considered a candidate for request handling when DispatcherServlet searches for component to which work can be delegated.

@controller is a specialization of @Component, this allows spring to autodetect controllers during classpath scanning

Controllers in Spring do not have to implement any interface or extend any base class, spring uses annotation-based programming model with @controller being part of it. Controllers have flexible methods signatures with mapping expressed via annotations like @RequestMapping, @GetMapping.


### <span style="color: #99ff99;">5. How is an incoming request mapped to a controller and mapped to a method?</span>

Incoming request is mapped to a controller and a method by DispatcherServlet, which uses HandlerMapping and HandlerAdapter components for this purpose.

When request is performed against the server following steps are executed:

1. Application server searches for servlet that can handle request, DispatcherServlet is selected based on Servlet Registration and url-pattern
2. DispatcherServlet uses HandlerMapping classes to get request mapping information and HandlerAdapter.
3. DispatcherServlet uses HandlerAdapter to execute controller method that will handle request.
4. DispatcherServlet interprets results of method execution and renders View with help of ViewResolver classes.

@RequestMapping allows you to specify conditions that request has to match for a method to be used as request handler. @RequestMapping can be used at class or method level, when used at the class level, all method level mapping inherit this primary mapping, narrowing it to a specific handler method.

Spring MVC also supports composed annotations for request mapping:
- @GetMapping
- @PostMapping
- @PutMapping
- @PatchMapping
- @DeleteMapping

Each of those annotations allows you to specify same conditions as @RequestMapping except for Http method field, following fields in @Mapping are aliases to @RequestMapping: path, params, headers, consumes, produces.


### <span style="color: #99ff99;">6. What is the difference between @RequestMapping and @GetMapping?</span>

The main difference between @RequestMapping and @GetMapping is that first one can be used to map any HTTP method requests and second one can be used to map only http get method request. getMapping is less flexible but easier to use.


### <span style="color: #99ff99;">7. What is @RequestParam used for?</span>

@RequestParam is used to bind web request parameters to controller method parameter.

/index?name=John&city=NYC&country=US

- name - the name of request parameter to bind
- required - whether the parameter is required or not
  - by default parameter is required
- defaultValue - allows you to specify default value to use in case of absence of optional parameter
- RequestParam also supports Optional

- mapping all request parameters to map or list is available


### <span style="color: #99ff99;">8. What are the differences between @RequestParam and @PathVariable?</span>

PathVariable is responsible for mapping parts of URI, marked with usage of URI templates variables to controller method parameters. URI templates are identifiers surrounded with curly brackets.

RequestParam is used to bind web request parameters to controller method parameter.

RequestParam allows you to specify defaultValue property, @PathVariable doesn't.

- specify name of variable to bind
- mark variables as required or optional
- use optional
- map parameters to map
- map list of values for parameter to collection


### <span style="color: #99ff99;">9. What are some of the parameter types for a controller method?</span>

WebRequest, NativeWebRequest - Access to HTTP request details, parameters, also request and session attributes, without direct use of the Servlet API

javax.servlet.ServletRequest - object to provide client request information, allows access to parameters, attributes and other request details without direct use of spring interfaces

-||-.ServletResponse - object created by servlet container, passed to service method of servlet, used by servlet to send a response to the client

javax.servlet.http.HttpSession - allows access to session information and attributes also enforces http session for request

-||-.PushBuilder - Servlet 4.0 push builder api for programmatic http/2 resources pushes, allows resources to be delivered in advance by the server, resulting in faster load time

java.security.Principal - currently authenticated user

HttpMethod - http method used for request, one of GET, HEAD, POST, PUT..

java.util.Locale - request locale, determined by the most specific LocaleResolver

java.util.TimeZone + ZoneId - time zone associated with the current request, as determined by LocaleContextResolver

java.io.InputStream, java.io.Reader - allows access to raw request body as exposed by the Servlet API

java.io.OutPutStream, java.io.Writer - allows to create raw response as exposed by the Servlet API

HttpEntity<B> - container object that exposes request headers and body, body is converted with usage of HttpMessageConverter

java.util.Map, org.springframework.ui.Model, org.springframework.ui.ModelMap - used to expose data to templates as part of view rendering

RedirectAttributes - specify attributes to use in case of redirect, regular attributes will be added to query string and flash attributes will be kept temporarily until end of request, flash attributes are kept typically in the session and are removed immediately after request is completed

Errors, BindingResult - used to gain access to form validation and binding data results, can be used with @ModelAttribute, RequestBody, or RequestPart argument, errors and bindingResult argument must be declared immediately after the validated method argument

SessionStatus + class level @SessionAttributes - useful for multistep form processing, @SessionAttributes allows to keep @ModelAttribute objects between request and SessionStatus allows to clean session variables when form processing is done

UriComponentsBuilder - used to build URLs relative to current scheme, host, port, contextPath etc.

- any other argument - if a method argument is not matched against types defined before, and it is a simply type, it is treated as @RequestParam, if it is complex type, it is treated as @ModelAttribute


### <span style="color: #99ff99;">10. What other annotations might you use on a controller method parameter?</span>

- @RequestParam - access to the servlet request parameters, including multipart files, parameters will be automatically converted to declared method argument types, parameters can be made optional with usage of required attribute or optional, for optional request parameters defaultValue can be set as well

- PathVariable - access to URI template variables, parameters can be made optional with usage of required attribute or optional

- @MatrixVariable - access to name-value pairs in URI path segments as described in RFC 3986, allows mapping variables from requests like
  /employees/id=1;name=John

- @CookieValue - bind the value of an http cookie to a method argument in a controller, you can bind against simple types or Cookie class, cookie can be set with usage of HttpServletResponse, cookie can be set as required or optional via required attribute

- @RequestHeader - access request header values or all header key and values when binding against a map

- @RequestBody - allows access to http request body, content will be converted to method controller type by HttpMessageConverter, request body can be made optional with usage of required attribute or Java8 optional, can be used with @Valid for bean validation

- @RequestPart - allows to bind multipart Http request to method parameter, content will be converted to method controller type, request part can be made optional with usage of required attribute or java8 optional, can be used with @Valid

- @RequestAttribute - allows access to http request attributes populated on server side during http request  by filter or interceptor, can be made optional with usage of required attribute or optional from java8

- @ModelAttribute - access to an existing attribute in the model (instantiated if not present) with data binding and validation applied

- @SessionAttribute - access to pre-existing session attributes that are managed globally, can be made optional with usage of required attribute or java8 optional

- @SessionAttributes - used to store model attributes in the http servlet session between requests, useful for multi step from processing


### <span style="color: #99ff99;">11. What are some of the valid return types of a controller method?</span>

- @ResponseBody - binds method return value to web response body, complex types will be converted with usage of HttpMessageConverter

- HttpEntity<B>, ResponseEntity<B> - allows to specify full response with headers and body, ResponseEntity<B> additionally allows to specify Http status code

- HttpHeaders - allows to return response only with headers, without body

- String - allows to return logical name of view to use when rendering response, view will be resolved by ViewResolver, usually used with implicit model through @ModelAttribute parameters or explicit model by declaring Model method parameter

- View - allows to return instance of view, like JstlView, ThymeleafView, FreeMarketView, usually used with implicit model through @ModelAttribute parameters or explicit model by declaring Model method parameter

- Map, Model - allows you to specify attributes to be added to the implicit model, with the view name implicitly determined through a RequestToViewNameTranslator

- @ModelAndView - view and model attributes to use and optionally a response status, view can be specified by logical name or instance of view can be passed, model can be specified as named object or Map

- void - method that returns void can correctly handle request by using ServletResponse or OutputStream as parameter, or @ResponseStatus, if none of previous are used RequestToViewNameTranslator will identify view based on request, void return type can also indicate no response body

- DeferredResult<V> - allows to specify result for controller asynchronously from different Thread or as result of some event callback, part of integration with servlet 3.0 asynchronous request

- Callable<V> - allows to produce return value asynchronously in a Spring MVC-managed thread

- ListenableFuture<V>, CompletableFuture<V>, CompletionStage<V> - allows to return set of chained asynchronous operations with callbacks and transformations

- ResponseBodyEmitter, SseEmitter - allows to send objects in stream asynchronously, objects will be converted with usage of HttpMessageConverter, can be used with ResponseEntity, both classes have the same goal, however SseEmitter uses Server-Sent events standardized with W3C spec

- StreamingResponseBody - allows to write to the response OutputStream asynchronously

- Reactive types - allows to use Reactive types for streaming scenarios, handled by ReactiveAdapterRegistry

<br><br>

<hr style="border:2px solid gray"> </hr>

<h1 id="Module-6" style="color: cornflowerblue;"> Spring Security</h1>


### <span style="color: #99ff99;">1. What are authentication and authorization? Which must come first?</span>

Authentication is a process of verifying that user, device or external system is who it claims to be. It involves validation that submitted proof of identity is true.

Authentication may take different forms, the simplest one uses username as identity and password as credential.

Spring security provides following support for auth:
- username/password auth
  - form login
  - basic auth
  - digest auth
- remember me
- openid support
- cas auth (single sign-on)
- x.509 certificate auth
- oauth 2.0 login
- saml2

storage mechanism
- simple storage with in memory auth
- relational databases with jdbc auth
- ldap storage with ldap auth

password encoders:
- bcrypt
- pbkdf2
- scrypt
- argon2
- sha256

Authorization is a process of determine whether an authenticated user is allowed to access certain resources within the system or allowed to perform a certain action within the application

Spring security allows you to implement authorization within your application on two levels:
- web security level with usage of expression
  - mvcMatchers("/admin/**").hasRole("admin")
- method security level
  - @secured
  - @preauthorize
  - jsr 250
    - @RolesAllowed
    - @PermitAll
    - @DenyAll

Authentication needs to be executed first, before authorization, because for authorization process to know which roles can be granted for particular user, system needs to be sure that user is who it claims to be.


### <span style="color: #99ff99;">2. Is security a cross cutting concern? How is it implemented internally?</span>

Yes, security is a cross cutting concern.

Cross cutting concern - functionality of a program not immediately associated with the business logic, applicable throughout the application and affecting multiple parts of the system?

Security spring on two levels:
- web level - based on servlet filters
- method security level - based on spring aop

Each aspect of Security - Authentication and Authorization is handled on both of those levels with different set of components:
- Authentication:
  - AuthenticationManager
  - ProviderManager
  - AuthenticationProvider
  - UserDetailsService
- Authorization
  - AccessDecisionManager
    - AccesssDecisionVoter
  - AfterInvocationManager
  - Authorities

Web level spring security uses servlet filters to analyze each request made to the system, and based on rules specified through WebSecurityConfigurerAdapter and HttpSecurity object, performs certain decision against authentication or authorization.

To enable method level security you need to use @EnableGlobalMethodSecurity and enable support to one of annotation types:
- prePostEnabled - Security pre post annotations - @PreAuthorize
- securedEnabled - @Secured - Spring security @Secured
- jsr250Enabled - @RolesAllowed, @PermitAll, @DenyAll...

AuthenticationManager - APi that defines how Spring Security filter perform authentication, usually implemented by ProviderManager
ProviderManager - is an AuthenticationManager that delegates to list of AuthenticationProviders, if at least AuthenticationProvider will successfully authenticate user, user is logged into the system

AccessDecisionManager - called by SecurityInterceptors before executing method/action, used for authorization to check if user is allowed to perform certain action or access certain resource in the system based on GrantedAuthority object

AfterInvocationManager - called after executing method, used for authorization to ensure the principal is permitted to access the domain object instance returned by a service layer bean


### <span style="color: #99ff99;">3. What is the delegating filter proxy?</span>

DelegatingFilterProxy is an internal Spring Framework class located in package org.springframework.web.filter of spring-web module.

This class acts as a Proxy between standard Servlet Filter and Spring-managed Bean that implements Servlet Filter. DelegatingFilterProxy is registered within application container and delegates all calls to Bean registered within Spring application context.

DelegatingFilterProxy can be registered in following ways:
- Servlet 3 - via AbstractSecurityWebApplicationInitializer
  - method insertSpringSecurityFilterChain will register DFP

- Servlet 2 - via web.xml
  - springSecurityFilterChain is a default name for filter chain proxy

- spring boot
  - uses delegatingFilterProxyRegistrationBean instead of regular DelegatingFilterProxy to create specialized version of DFP
  - register by SecurityFilterAutoConfiguration

Role of DFP is to delegate all calls to FilterChainPRoxy, which contains SecurityFilterChain responsible for Web level authentication and authorization


### <span style="color: #99ff99;">4. What is security filter chain?</span>

Security filter chain is a collection of spring managed filters that are responsible for authentication and authorization. Usually they include functionalities like username and password authentication, logout management, session management, security interceptors.

FilterChainProxy holds list of SecurityFilterChains and upon request searches for the first SecurityFilterChain that matches the request.

Upon request being matched, SecurityFilterChain is picked up and list of Filters is being fetched from SecurityFilterChain.

Spring provides API to customize list of used Security Filters, by extending WebSecurityConfigurerAdapter and overriding configure method.


### <span style="color: #99ff99;">5. What is a security context?</span>

SecurityContext is an interface, allowing you to access security information associated with the current thread of execution. Interface provides two methods:
- getAuthentication - provides currently authenticated principal or an authentication request token
- setAuthentication - sets currently authenticated principal, or removes the authentication

SecurityContext can be accessed via SecurityContextHolder, which allows access in three modes:
- MODE_THREADLOCAL
- MODE_INHERITABLETHREADLOCAL
- MODE_GLOBAL

MODE_THREADLOCAL by default, it allows each Thread to access its own dedicated SecurityContext
MODE_INHERITABLETHREADLOCAL child threads are allowed to access same SecurityContext as parent Thread
MODE_GLOBAL all threads within JVM are accessing same SecurityContext, this is usually used by standalone desktop application.

mode of SecurityContextHolder can be changed by:
- property - spring.security.strategy
- programmatically


### <span style="color: #99ff99;">6. ** pattern in antMatcher and mvcMatcher matches zero or more path segments until the end of path</span>

antMatcher and mvcMatcher support following rules:
- ? - matches one character
- * - matches zero or more characters within a path segment
- ** - matches zero or more path segments until the end of the path
- Regexps are supported for Path Variables
  - {spring:[a-z]+}

Example, url - /departments/delete/5
- /departments/delete/* matches
- /departments/delete/** matches
- /*/5 - not matches
- /**/5 matches
- /departments/dele??/* matches


### <span style="color: #99ff99;">7. Why is the usage of mvcMatcher recommended over antMatcher?</span>

mvcMatcher is more flexible and forgiving when writing down rules for Spring Security configuration, thus making mistakes when securing application harder.

- mvcMatchers("/employees")
- antMatchers("/employees")

They look very similar, they will work differently when executed against URI /employees

- /employees/
  - mvcMatcher - matches
  - antMatchers - not matching


### <span style="color: #99ff99;">8. Does Spring security support password hashing? What is salting?</span>

Yes, Spring security supports password hashing through PasswordEncoder interface and has built in support for following encoders:
- bcrypt
- pbdkdf2
- scrypt
- argon2
- shas256

Upon registration password is encoded (hashed) and never stored in cleartext.
Upon login, provided password is encoded again and compared with one stored in database.

Spring security also provides DelegatingPasswordEncoder, which uses one of the selected PasswordEncoder to encode password and list of provided passwords decoders to verify password upon login.

DelegatingPasswordEncoder is usefully as it provides flexibility and ability to easily switch between PasswordEncoders while keeping backward compatibility, for already stored hash values of passwords.

Password salting is a security mechanism invented to protect against reversing cryptographic hash functions, with usage of a precomputed tables like rainbow tables.


### <span style="color: #99ff99;">9. Why do we need method security? What type of object is typically secured at the method level?</span>

Method level security is needed whenever more granular security rules needs to be expressed for the application. In some cases having web based rules, written based on URI patterns, might not be detail enough, and additional set of rules needs to be applied to the application service layer.


### <span style="color: #99ff99;">10. What @PreAuthorized and @RolesAllowed annotations do? What is the difference between them?</span>

@RolesAllowed is very similar to @Secured, and both of those allows to specify list of roles that currently authenticated user needs to have assigned to be allowed to execute guarded method. @RolesAllowed is part of jsr250 standard.

@PreAuthorized allows you to specify conditions under which user is allowed to execute method, with usage of SpEL expressions. Expression is evaluated before method is executed.

Difference between those annotation is that @rolesAllowed allows you to specify list of required roles, and @PreAuthorized allows to specify rule with usage of SpEL expression

SpEL expressions that can be used with @PreAuthorized
- hasRole
- hasAnyRole
- hasAuthority
- isAnonymous
- isRememberMe


### <span style="color: #99ff99;">11. How are @PreAuthorized and @RolesAllowed are implemented with usage of Spring AOP and AccessDecisionVoter.</span>

AccessDecisionVoter are called by AccessDecisionManager, which is called by MethodSecurityInterceptor, which are registered by one of AdvisorAutoProxyCreator. PointCut and Advices for AOP are pointed by MethodSecurityMetadataSourceAdvisor. Currently used MethodSecurityInterceptor is pointed by GlobalMethodSecurityConfiguration#methodSecurityInterceptor.

@rolesAllowed is implemented by Jsr250Voter.

@PreAuthorized is implemented by PReInvocationAuthorizationAdviceVoter


### <span style="color: #99ff99;">12. In which security annotation are you allowed to use SpEL=</span>

- @PreAuthorize
- @PostAuthorize
- @PreFilter
- @PostFilter

Main difference between @PreAuthorize / @PostAuthorize are used to create expression that will check if method can be executed, @PreFilter / @PostFilter are used to filter collections based on security rules


<br><br>

<hr style="border:2px solid gray"> </hr>

<h1 id="Module-7" style="color: cornflowerblue;"> Spring REST </h1>


### <span style="color: #99ff99;">1. What does REST stand for?</span>

REST stands for Representational State Transfer

Most implementation of REST services are using HTTP as the application protocol, and JSON as format that moves data between caller and callee. However REST is not necessarily tied to HTTP or JSON

URI versioning
- /api/v1/products
  Query string versioning
- /api/products?version=1
  Header versioning
- /api/products
- Header - accepts-version 1.0
  Media type content negation version
- /api/products
  Header - Accept: application/vnd.my-app.v1+json


### <span style="color: #99ff99;">2. What is resource?</span>

Resource is a named information available via URI. It can be a document, image, video, text file, etc. Rest uses different form of presentation of resources, and client can specify format in which Resource should be made available, for example JSON, XML, Text, Html..

REST usually provides set of methods that can be used to manipulate resources like http get, post, put, delete


### <span style="color: #99ff99;">3. What does CRUD mean?</span>

Create, read, update, delete.

create - post, put
read - get
update - put, patch
delete - delete


### <span style="color: #99ff99;">4. Is REST secure? What can you do to secure it?</span>

REST as an architectural style of developing distributed applications, does not enforce any security rules or solutions on its own, so by default rest is not secured.

To secure RESt api you can do following:

- protect in-transit traffic by using https protocol
- use some form of authentication (basic, json tokens)
- use some form of authorization (spring roles)


### <span style="color: #99ff99;">5. Is REST scalable and or interoperable?</span>

Scalability of Restful service is a result of developing software with following characteristics in mind:

- statelessness - each request to the system should be design in a way for example, we want to avoid keeping information in http session related to user conversation with the system, this way we can delegate request to any backend node that can process the request without having to introduce share state between nodes
- layered approach - layered approach to the system design means that we can introduce new parts of the system in a way for it to be transparent to the client, resulting in ability to change system without having to modify client, example of this can be introduction of application load balancer, api gateway, security layers, web application firewall without having to change client at all
- cacheability - allows to create response for repeatable requests, without having to process them on service side, caching is introduced to improve response time and to reduce load on the service

REST service is interoperable because:
- access to rest service and resources available by uris is standardized and not coupled with any specific technology, allowing you to consume rest service in any technology of choice, like JavaScript, Python, Java, C++
- data for the requested resource can be sent to client in different formats specified by the client, in case of http protocol this can be done with usage of accept header, for example accept: application/json or accept: application/xml
- all crud operations can be handled with standardized approach, in case of restful service implemented with http protocol, standardized http methods get, put, patch, post, delete are used


### <span style="color: #99ff99;">6. Which Http methods does rest use?</span>

HTTP GET - used to implement read operations - fetch existing resource or list of resources
HTTP POST - used to implement Create operations - adding new element
HTTP PUT - used to implement create or update operations - bulk update or update existing resource
HTTP PATCH - partial update of existing resource of the system, for example, when wanting to update only first name
HTTP DELETE - delete existing resource


### <span style="color: #99ff99;">7. What is an HttpMessageConverter?</span>

It's a interface used by Spring to convert data between different formats.

Rest client can specify expected format in which data should be retrieved by usage of Accept Header (application/json). Client can also specify format in which data will be send by usage of Content-Type Header, for example Content-Type: application/xml

Request mapping contains produces and consumes fields which can be used to specify MediaType which method can handle.


### <span style="color: #99ff99;">8. Yes, REST is normally stateless.</span>

Stateless basic constraint for RESTful architecture.

If some kind of state is required for the request, client should send this state with each request, however this state should not be kept on server side, not be kept in HTTP session.


### <span style="color: #99ff99;">9. What does @RequestMapping do?</span>

Allows to specify conditions that request has to match for a method to be used as request handler. @RequestMapping can be used at class or method level, when used at the class level, all method level mappings inherit this primary mapping, narrowing it to a specific handler method.

- criteria for request:
- path
- method
- params
- headers
- consumes
- produces


### <span style="color: #99ff99;">10. IS @Controller a stereotype? Is @RestController a stereotype? What is a stereotype annotation? What does that mean?</span>

@Controller annotation and @RestController are stereotypes.

Stereotypes are annotations applied to classes to describe role which will be performed by this class.

Types of stereotypes:
- @Component - generic component in the system, root stereotype, candidate for auto scanning
- @Service - class will contain business logic
- @Repository - class is a data repository (used for data access objects, persistence)
- @Controller - class is a controller, usually a web controller
- @RestController - class is a controller that will implement REST service Endpoints, usually consuming and producing json


### <span style="color: #99ff99;">11. What is the difference between @Controller and @RestController</span>

@Controller indicates that class will be assigned with Controller role of MVC pattern and usually it is expected from it to return Model and View that will be used to render response, with usage of configured template engine (thymeleaf)

@RestController indicates that class will be used to handle REST service endpoint request, it is expected from it to correctly handle requests input and produce outputs in acceptable format like JSON/XML etc. Serialized output is sent directly to the client.

@RestController = @Controller + @ResponseBody

@ResponseBody indicated that method return value should be bound to the web response body, it's return value will be serialized into response in requested format.


### <span style="color: #99ff99;">12. When do you need @ResponseBody?</span>

@ResponseBody is needed whenever you want spring to return serialized response of controller method return value, instead of returning model and view that will be used by template engine to produce response. @ResponseBody bounds method return value to the web response body, produced by HttpMessageConverter


### <span style="color: #99ff99;">13. What are the HTTP status return codes for a successful GET, POST, PUT Or DELETE operation?</span>

GET
- 200 OK - when asked about existing resource for which content is returned
  POST
- 201 (created) - when new resources was created
- 200 OK - when some processing was executed but resources were not created
- 204 No content - when some processing was executed, but no response is retrieved
  PUT
- 201 Created - when new resource is created
- 200 OK - when resources was updated, and updated content is returned
- 204 No content - when resource was updated and no content is returned
  DELETE
- 204 No content - when resource was successfully deleted

In case of asynchronous operations, 202 (Accepted) may be returned with Location header indicating URI that can be used for pooling.


### <span style="color: #99ff99;">14. When do you need @ResponseStatus?</span>

@ResponseStatus is required whenever you want to override default HTTP status returned from controller handler method.

This can be achieved by applying @ResponseStatus to:
- Controller class
- Controller method
- Exception being thrown from controller

@ResponseStatus allows you to set:
- Https status code
- Reason message to be used in response in case of error


### <span style="color: #99ff99;">15. Where do you need @ResponseBody? What about @RequestBody?</span>

@ResponseBody is needed whenever you want to return serialized response of controller handler method, instead of returning model and view that will be used by template engine to produce response. @ResponseBody will bind method return value to web response body and will use HttpMessageConverter.

@RequestBody is needed whenever you want to bind web request body to controller parameter. HttpMessageConverter is used to convert of request body. Optionally can be used with @Valid to invoke automatic bean validation.

@ResponseBody can be used:
- on top of class
- on top of method
- on top of other annotations

@RequestBody can be used:
- on top of controller method parameter


### <span style="color: #99ff99;">16. If you saw example controller code, would you understand what it is doing? Could you tell if it was annotated correctly?</span>

Controller can be defined in one of following ways:
- @Controller
- @RestController

Controller mapping can be defined with usage of one of following annotations:
- @GetMapping
- @PostMapping
- @PutMapping
- @PatchMapping
- @DeleteMapping

Request parameter body can be mapped with usage of:
- @RequestBody
- additionally @Valid can be added

Response can be bound to web response by:
- usage of @ResponseBody on top of @Controller or controller method
- usage of @RestController

Custom HTTP Status can be provided for controller methods and exception with usage of @ResponseStatus

Request and URI parameters can be accessed with:
- @RequestPAram - Servlet request parameters
- @PathVariable - access ot URI template variables
- @MatrixVariable - access to name-value pairs in URI path segments, allows mapping variables from request
- @CookieValue - bind the value of an HTTP cookie to a method argument in a controller
- @RequestHeader - access request header values or all header key and values when binding against map

Calls to controller can be intercepted and custom exception handling can be implemented:
- @ExceptionHandler - when applied at controller level method acts as controller level exception handler
- @ControllerAdvice - used together with @ExceptionHandler - global exception handler for all controllers, acts as global annotation driven call interceptor


### <span style="color: #99ff99;">17. Do you need Spring MVC in your classpath?</span>

Yes, you need Spring MVC on classpath for REST API to work correctly.

Spring MVC is not required for compilation time, but is required during runtime.

REST API in Spring is build with usage of annotations like:
- RestController
- RequestBody
- RequestMapping
- GetMapping

All of those are available in spring-web module which is not dependent on spring-webmvc

However for request to be mapped to RestController, DispatcherServlet has to be initialized which is part of spring-webmvc module.


### <span style="color: #99ff99;">18. What Spring boot starter would you use for a Spring REST application?</span>

To create Spring REST application, use Spring Boot Web Starter.

Spring boot web starter will automatically include:
- spring-web
- spring-webmvc
- spring-boot-starter-json
- spring-boot-starter-tomcat


### <span style="color: #99ff99;">19. What are the advantages of the RestTemplate?</span>

RestTemplate is a synchronous HTTP client wrapper to perform HTTP requests. It exposes simple API over underlying HTTP client libraries:
- JDK HttpURLConnection
- Apache HttpComponents
- OkHttp

RestTemplate has following advantages:
- Simplicity
- Automatic Object Serialization/Deserialization
- High-level API allows you to focus on business side of operations
- provides support for common HTTP get,post,put, patch, head, options, delete operations
- Flexibility - allows custom error management
- Extensibility - allows to register custom HttpMessageConverter and to register custom ClientHttpRequestFactory
- URI Templates support

Because of it's simplicity, REST Template is often used in testing code, however it can be used as general purpose HTTP Client.


### <span style="color: #99ff99;">20. If you saw an example using RestTemplate would you understand what it is doing?</span>

RestTemplate API allows you to receive answer from Service being called by returning:
- Object that represents transferred data
- ResponseEntity
  - Status code
  - HTTP Headers
  - Response Body
- HTTP Headers
- URI of created/posted object
- List of Allowed HttpMethods by using HTTP OPTIONS request

RestTemplate API can be categorized by HTTP request type, below is a list of commonly used operations:
- Generic
  - exchange
  - execute
     HTTP GET
  - getForObject
  - getForEntity
     HTTP HEAD
  - headForHeaders
     HTTP POST
  - postForLocation
  - postForObject
  - postForEntity
     HTTP PUT
     HTTP PATCH
     HTTP DELETE
     HTTP OPTIONS

<br><br>


<hr style="border:2px solid gray"> </hr>

<h1 id="Module-8" style="color: cornflowerblue;"> Spring Testing </h1>

### <span style="color: #99ff99;">1. Do you use Spring in a unit test?</span>

Spring framework is usually not used in unit tests, however Spring contains some support for unit testing within following packages:
- org.springframework.test.util
  - ReflectionTestUtils
    - ORM Entities related testing - set value for private field, normally handled by ORM
    - Manual dependency injection into private field, normally handled by @Autowired, @Inject
    - @PostConstruct and @PreDestroy lifecycle callback methods testing
  - AopTestUtils - Aspect Oriented Programming related testing
- org.springframework.test.web
  - ModelAndViewAssert - Unit Testing for Spring MVC Controllers
    - mock implementations of the Environment and PropertySource
    - MockEnvironment, MockPropertySource
- org.springframework.mock.jndi
  - Mock implementation of JNDI SPI - usually used for Java EE
- org.springframework.mock.web
  - Servlet API mock objects

Unit Tests should test one unit of functionality in isolation. This unit of functionality can be defined as single method, class, module, component. In OOP unit of functionality is usually defined as single class.
All class collaborates should be mocked as well. Testing should be performed outside of container, that means that IoC/DI should not be required to create instances of objects under test.

Integration tests should test multiple modules or components that are combined together. Ioc/Di Container is used for this kind of testing, with some simplification upon deployment.

System tests
- slow, expensive, easy to set system case, hard to test detailed case
  Integration tests
- medium-to-slow, medium to high cost, details testing is a challenge, easy to test integration between components
  Unit tests
- fast, cheap, impossible to test integration system case, easy to test detailed case


### <span style="color: #99ff99;">2. What type of tests typically use Spring?</span>

Integration tests are type of tests that typically use Spring. Reason for it because we want to test multiple components that are combined together.

Annotations for integration testing:

@ContextConfiguration
- allows to specify how to load and configure ApplicationContext for integration test
- specify @Configuration classes that will be used during ApplicationContext loading
@BootstrapWith
- allows for low level control on how Context for tests is created
- used at class level
@DirtiesContext
- marks test as one that modifies state of context, and it means that context should be recreated prior next test execution because otherwise modified context state might affect test execution
- when used at class level you can specify following modes:
- before_class, before_each_test_method, after_each_test_method, after_class
- when used at method level:
- before_method, after_method
@WebAppConfiguration
- class-level annotation triggers creation of MockServletContext, which serves as the ServletContext for the test's WebApplicationContext
- indicates that ApplicationContext loaded for an integration test should be a WebApplicationContext
@ContextHierarchy
- used when hierarchy of application contexts has to be used for integration test
@Rollback
- class or method annotation that indicates that transaction should be rolled back after test executing
- even if @Rollback is not explicitly defined, all transactions under tests will be rolled back by default


### <span style="color: #99ff99;">3. How can you create a shared application context in a JUnit integration test?</span>

Shared application context can be considered as:
- Sharing context Definition
- Sharing context Instance

Context definition can be shared between tests in following way:
- use base class for all tests which will contain @ContextConfiguration and other annotations, like for example @ActiveProfiles etc.
- use Custom Annotation that will contain context configuration
- use test configuration that inherits application configuration
- use base interface for all tests that will contain context configuration

Context Instance is shared by default between all tests, as long as requested context matches one that is already cached.
Context will be reused as long as @ContextConfiguration (locations, classes, initializers, ...) @ActiveProfiles, @TestPropertySource attributes are matched. To see full list of attributes that needs to be matches you can look at MergedContextConfiguration class that is used as key to ContextCache.
You can use @DirtiesContext to force Spring to create new instance of context for test


### <span style="color: #99ff99;">4. When and where do you use @Transactional in testing?</span>

When - use @Transactional in testing whenever you want to run some part of the code that can alter state of transactional resource, for example database. Usage of this annotation allows you to mark code that should execute under transaction and allows to rollback all changes made by test, allowing other tests to pick from clear state.

By default, transaction will be rolled-back for each test which was executed with @Transactional annotation.

Where - it can be used:
- on top of the class - each test method in class will be executed in transaction
- on top of the method - test method will be executed


### <span style="color: #99ff99;">5. How are mock frameworks such as Mockito or EasyMock used?</span>

Mock Framework like Mockito or EasyMock are used mainly during Unit Testing to mock collaborators of classes under test. Mockito or EasyMock can be also used during Integration testing when goal is to check cooperation between objects.

Mock created with Mockito or EasyMock is a dynamic object, which can "pretend" real object and return predefined results when invoking method on it.


### <span style="color: #99ff99;">6. How is @ContextConfiguration used?</span>

@ContextConfiguration is used on top of the class that represents Integration test, and it's purpose is to specify how to load and configure Application Context for integration test

@ContextConfiguration can be used in two basic modes:
- Annotated classes based approach
- XML based approach

Additionally @ContextConfiguration also allows you to specify:
- initializers: list of ApplicationContextInitializer, used within cases that require some programmatic initialization of the application context
- loader - usually not used and default DelegatingSmartContextLoader is used, if required, this field allows you to specify custom context loader
- name . name of the context hierarchy level represented by this configuration, only applicable when used within a test class hierarchy configured using @ContextHierarchy


### <span style="color: #99ff99;">7. How does Spring Boot simplify writing tests?</span>

Spring boot simplifies writing tests in following way:
- provides @SpringBootTest - alternative to @ContextConfiguration, creates ApplicationContext through SpringApplication, Enables tests Auto-configuration, enables spring boot test features
- provides @MockBean - easy creation and injection of Mockito mock
- provides @SpyBean - easy creation and injection of Mockito spy
- provides @WebMvcTest - useful when test focuses only on Spring MVC components, disables full auto-configuration and applies only configuration relevant to MVC tests
- provides Web environments:
  - MOCK (default)
  - RANDOM_PORT
  - DEFINED_PORT
  - NONE

Allows to explicitly use Auto-configuration:
- @JsonTest - Auto-configured JSON Tests
- @WebMvcTest - Auto-configured Spring MVC Tests
- @JdbcTest - Auto-configured JDBC tests
- @DataJpaTest - auto configured data jpa test

Provides spring-boot-starter-test module:
- JUnit
- Spring Test
- Spring Boot Test
- AssertJ - fluent assertion library
- Hamcrest - library of matcher object
- Mockito - mocking framework
- JSONAssert - an assertion lib for JSON
- JsonPath - Xpath for JSON


### <span style="color: #99ff99;">8. What does @SpringBootTest do? How does it interact with @SpringBootApplication and @SpringBootConfiguration?</span>

@SpringBootTest provides following features over regular Spring Test context:
- automatically searches for @SpringBootConfiguration
-unless nested @Configuration is detected or explicit @SpringBootTest(classes=...) is specified
- in most cases @SpringBootConfiguration is not explicitly used, it is inherited from @SpringBootApplication
used in production code to indicate starting place for application
- sets default ContextLoader to SpringBootContextLoader
- unless one is explicitly specified in @ContextConfiguration(loader=...)
- SpringBootContextLoader is specific ContextLoader that starts tests using SpringApplication
- provides Web environments
- MOCK
- RANDOM_PORT
- DEFINED_PORT
- NONE
- allows to easily define Environment properties
- properties field of @SpringBootTest can be used to define key=value pairs that will be added to Environment
- Register TestRestTemplate and WebTestClient


@SpringBootTest allows you to set following fields:
- classes - classes to use for loading an ApplicationContext
- if not set @SpringBootTest will automatically search for @SpringBootConfiguration which is inherited from @SpringBootApplication
- properties - key=value pairs that will be added to Environment before test execution
- webEnvironment - one of specified web environments used for web layer testing

@SpringBootTest interacts with @SpringBootApplication and @SpringBootConfiguration through SpringBootTestContextBootstrapper and SpringBootContextLoader

Goal of SpringBootContextLoader is to transform initial ContextConfiguration to ApplicationContext. SpringBootContextLoader will get as input class annotated with @SpringBootConfiguration, which will be located by SpringBootTestContextStrapper

<hr style="border:2px solid gray"> </hr>

<h2 id="spring-badge" style="color: cornflowerblue;"> Spring Certified Professional - Badge </h2>

The Spring Certified Professional certification validates a candidate's expertise with major features of Spring and Spring Boot and the candidate’s ability to apply Spring’s features to quickly build and deliver production ready applications.

[![Spring Certified Professional](/images/spring-certified-professional-2024.png)](https://www.credly.com/badges/4e19bf0c-5c72-4780-8227-e3af1cb6c6dd/public_url)