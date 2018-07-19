Java All
++++++++


Design Pattern
==============
* **Design Pattern in Spring**
    + singleton
    + factory
    + builder (ClientBuilder) [ref](https://www.geeksforgeeks.org/builder-design-pattern/)
        - complex object
        - seperate construction of a complex object
        - Product & Builder & Concrete Builder & Director
        - good:
            - constructor are reduced
            - no need to pass in null for optional parameters to the constructor.
            - Object is always instantiated in a complete state
            - Immutable objects can be build without much complex logic in object building process.
        - bad:
            - The number of lines of code increase (but much more readable code.)
            - Requires creating a separate ConcreteBuilder for each different type of Product.
    + service locator design pattern (service locator / RMI / fetch ) ??
        - https://iamninad.com/service-factory-using-spring-framework/
        - https://steveschols.wordpress.com/2012/05/14/dependency-injection-vs-service-locator/
        - https://netjs.blogspot.com/2018/03/servicelocatorfactorybean-in-spring.html
        - https://dzone.com/articles/a-beginners-tutorial-for-understanding-and-impleme

Spring Core
===========
* Bean life cycle
    + constructor > setter injection
    + BeanNameAware > BeanFactoryAware > ApplicationContextAware
    + BeanPostProcessor.`postProcessBeforeInitialization`
    + InitializingBean.`afterPropertiesSet()`
    + BeanPostProcessor.`postProcessAfterInitialization`
    + DisposableBean.`destroy`
* 

Web
===

* What are differences between REST and other webservices.
    + SOAP vs REST
    + [ref](https://restfulapi.net/statelessness/) Statelessness means that every HTTP request happens in **complete isolation**. When the client makes an HTTP request, **it includes all information necessary for the server to fulfill that request**. **The server never relies on information from previous requests**. If that information was important, the client would have sent it again in this request.

Hibernate
=========

* lock @Version (optimisic) @Lockmode (passive)
* hibernate session dirty
    + hibernate session
    + https://stackoverflow.com/questions/10804676/what-is-a-hibernate-dirty-session/35220231

Alogrithm
=========

* Write a program to find the first hundred primes, then optimize
    + [ref](https://program-think.blogspot.com/2011/12/prime-algorithm-1.html)
