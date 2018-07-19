# Web

## General

* What are differences between REST and other webservices.
    + SOAP vs REST
    + [ref](https://restfulapi.net/statelessness/) Statelessness means that every HTTP request happens in **complete isolation**. When the client makes an HTTP request, **it includes all information necessary for the server to fulfill that request**. **The server never relies on information from previous requests**. If that information was important, the client would have sent it again in this request.
* Name at least 2 frameworks that use the MVC pattern.
    + 
## J2EE

* What's the difference between the Java SE and the Java EE platform.
    + JavaSE(Standard Edition): core Java programming platform. It contains the basic libraries and APIs (java.lang, java.io, java.math, java.net, java.util, etc...)
    + JavaEE(Enterprise Edition): Java EE is built on top of Java SE, and it is used for developing web applications and large-scale enterprise applications. (servlet, websocket, javaserver faces, dependency injection, ejb, persistence, transaction, jms, batch api)
* What is a JAR File? What is a WAR file ? What is an EAR file? When would you use each?
    + 
* What are the benefits/features of J2EE?
    + 

## Servlet & JSP

* Describe the servlet lifecycle.
    + servlets are **controlled** by web container
    + when a servlet based web app deployed on a web container
    + web container read `web.xml` to get servlet info & (servlet context + servlet conf)
    + web container load **servlet class**
    + web container create servlet instance
    + web container use servlet configure `init()` servlet, create/allocate thread for servlet
    + when request come web container forward request to servlet `service()`
    + web container call `destroy()` when web container stops or deallocate servlet
* What is the role of JSP in the MVC pattern?
    + JSP acting as a role of View in MVC
    + JSP provides html template, when it renders to real html, java data will be inserted into the template
    + JSP also provides some control, by using **JSTL**
* What technologies have you personally used to implement REST?
    + expressjs(javascript based), flask(python), spring mvc
* Can you describe what a RESTful web service looks like from the perspective of a client? Partial 
    + 

* What is a "resource" as it pertains to REST? Partial
* What is the difference between a POST and a PUT? Incorrect
* What are some best practices around error codes in a RESTful environment? Give at least two examples. Partial
* Please explain how you've implemented RESTful services in the past? Did you use any particular tools? Did you use doPost() as the service method or something else? Partial
* just Spring
