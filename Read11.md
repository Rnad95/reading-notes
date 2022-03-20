# Read 11 - Spring Framework

## Introduction

---

Spring is a powerful framework to design and create a web applications

We can using spring mvs in microservices, reactive, even driven, cloud, web Applications.

Spring mvs is built for creating everything in Web Applications.

## How to build Web content with Spring MVC

---

### Create a Web Controller

Spring MVC prepare a modal map and determine the way to render it

1. Identify the controller annotation then, handle Get Request

2. Request Parameter
If we have a controller

        `@Controller
        public class SomeController {
            @RequestMapping("/")
            public String redirect() {
                return "redirect:/query?q=Thymeleaf+Is+Great!";
            }
        }`

The parameters can be accessed the param
>`<p th:text="${param.q}">Test</p>`

- Another way to access request parameters is by using the special #request object that gives you direct access to the javax.servlet.http.HttpServletRequest object:

3. Spring model attributes
Then, we need to add mySessionAttribute. Like A Request Param, the attribute can be accessed using prefix session

> `<p th:text="${session.mySessionAttribute}" th:unless="${session == null}">[...]</p>`

4. ServletContext attributes

This attribute shared between the request and session

    <table>
                <tr>
                    <td>My context attribute</td>
                    <!-- Retrieves the ServletContext attribute 'myContextAttribute' -->
                    <td th:text="${#servletContext.getAttribute('myContextAttribute')}">42</td>
                </tr>
                <tr th:each="attr : ${#servletContext.getAttributeNames()}">
                    <td th:text="${attr}">javax.servlet.context.tempdir</td>
                    <td th:text="${#servletContext.getAttribute(attr)}">/tmp</td>
                </tr>
            </table>

5. Spring beans
Accessing beans which is registered in spring web applications  

> `<div th:text="${@urlService.getApplicationUrl()}">...</div>`

For example :

![2](https://i.ibb.co/vYXZJwX/img.jpg)

## Build a web Applications

---

- To build A web Applications using spring we need to create the steps and as Figure shos shown below:

![spring web application](https://java2blog.com/wp-content/uploads/2017/07/SpringMVCTuto-1.png)

1. Create web controller

2. Restarting the Program

3. Once you restart your App the spring create an application class and we can run the application

4. Build an executable Jar which contains all the dependencies, and we can use `. /gradle bootRun`. Then, run `java -jar build/libs/gs-serving-web-content-0.1.0.jar` command in terminal

5. Test the application by open the local host `https://localhost:8080/getMapping_name` or `https://localhost:8080/getMapping_name?User=Name`

6. Add Home page : static resources including the html, css, and JavaScript can be served from spring root application by adding it to the resources with path `src/main/resources/static/index.html`
