* Diff b/w requestDispatcher.forward and response.sendRedirect
    + forward . pass req&resp to next servlet
    + redirect . discard req . ask client to call
* what is controller, abstractcontroller?
    + 
- Can I have multiple urls rendered from Same Controller?
 Why @ResponseBody?
package com.in28minutes.springmvc;

import org.springframework.stereotype.Controller;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.ResponseBody;

@Controller
public class LoginController {

	@RequestMapping(value = "/login")
	@ResponseBody
	public String sayHello() {
		return "Hello World dummy";
	}
}

`` Spring MVC Request Flow
- DispatcherServlet receives HTTP Request. 
- DispatcherServlet identifies the right Controller based on the URL.
- Controller executes Business Logic.
- Controller returns a) Model b) View Name Back to DispatcherServlet.
- DispatcherServlet identifies the correct view (ViewResolver).
- DispatcherServlet makes the model available to view and executes it.
- DispatcherServlet returns HTTP Response Back.

logging in ur app?
@RequestParam
- Session vs Model vs Request.
- Be cautious about what you use Session for.
- @SessionAttributes("name") and how it works?
Importance of redirect:/list-todos
model.clear()?
html5 form validations?
- Add Validations
- The JSR 303 and JSR 349 defines specification for the Bean Validation API (version 1.0 and 1.1, respectively), and Hibernate Validator is the reference implementation.
@Valid, BindignResult, InitBinder
logout functionality?
exception handling?
 Exception Handling is a cross cutting concern
- Do not handle exceptions in Controllers or Services, if you cannot add value to them.
- Bit of refactoring on the controllers
- @ControllerAdvice and Controller Specific Exception Handling
- Handling Errors thrown from Views
internaltionalization
interceptor?
@PathVariable?

Handle exception resolver??