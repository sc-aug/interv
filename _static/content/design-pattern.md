# Design Pattern

* Why use design pattern
    + predesigned solution for common problem
    + no need to reinvent
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
    + publish-subscribe
