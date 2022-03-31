# Read: 17 - Spring Authorization

## Introduction  

---

Authorization is a permission after access the application. Authorization do that to limit some people access something.

- It starts with a simple, single-provider single-sign on, and works up to a client with a choice of authentication providers: GitHub or Google.

- The OAuth 2.0 is used to make the Authorization  
There are several samples building on each other, adding new features at each step:

1. simple: a very basic static app with just a home page and unconditional login via Spring Boot’s OAuth 2.0 configuration properties (if you visit the home page, you will be automatically redirected to GitHub).

2. click: adds an explicit link that the user has to click to login.

3. logout: adds a logout link as well for authenticated users.

4. two-providers: adds a second login provider so the user can choose on the home page which one to use.

5. custom-error: adds an error message for unauthenticated users, and a custom authentication based on GitHub’s API.

## Single Sign On With GitHub

---

### Creating a New Project

- we can use Spring initializr to create empty project or use the instruction below in terminal

>~$ `mkdir ui && cd ui`

>~$ `curl https://start.spring.io/starter.tgz -d style=web -d name=simple | tar -xzvf -`

### Add a Home Page

Create index.html in the src/main/resources/static in the project and some css style and JS

- we need to add jQuery, bootstrap, and webjars-locator-core Dependencies

### Securing the Application with GitHub and Spring Security

spring-boot-starter-oauth2-client dependency Since you’re wanting to do a "social" login (delegate to GitHub)

Next, you need to configure your app to use GitHub as the authentication provider. To achieve this, do the following:

1. **Add a New GitHub app:** create OAuth 2.0 from <https://github.com/settings/developers> Select "New OAuth App" and then the "Register a new OAuth application" page is presented. Enter an app name and description. Then, enter your app’s home page, which should be <http://localhost:8080>, in this case. Finally, indicate the Authorization callback URL as <http://localhost:8080/login/oauth2/code/github> and click Register Application.

2. **Configure application.yml** to make linking with github

3. **Boot up the application**you can run your app again and visit the home page at <http://localhost:8080>. Now, instead of the home page, you should be redirected to login with GitHub.

## Add a Welcome Page

---

Instead of being redirected immediately, the new link will be visible on the home page, and the user can choose to login or to stay unauthenticated. Only when the user has clicked on the link will the secure content be rendered.

### Adding a Logout Endpoint

Spring Security has built in support for a /logout endpoint which will do the right thing for us (clear the session and invalidate the cookie). To configure the endpoint we simply extend the existing configure() method in our WebSecurityConfigureAdapter:

![configuration](https://i.ibb.co/K7QsRPM/Screenshot-from-2022-03-31-11-42-16.png)

The `/logout` endpoint requires us to POST to it, and to protect the user from Cross Site Request Forgery (CSRF, pronounced "sea surf"), it requires a token to be included in the request. The value of the token is linked to the current session, which is what provides the protection, so we need a way to get that data into our JavaScript app.

### Adding the CSRF Token in the Client

Since we are not using a higher level framework in this sample, you’ll need to explicitly add the CSRF token, which you just made available as a cookie from the backend. To make the code a bit simpler, include the js-cookie library so, we need to add js-cookie dependency.

### Login with GitHub

 you must set up a project in the Google API Console to obtain OAuth 2.0 credentials.

### Adding the Client Registration

Because Spring Security is built with multiple clients in mind, you can add our Google credentials alongside the ones you created for GitHub.

### Adding the Login Link

add another link in index.html

![add link in index.html](https://i.ibb.co/9rmdhqG/Screenshot-from-2022-03-31-11-49-08.png)

### How to Add a Local User Database

Many applications need to hold data about their users locally, even if authentication is delegated to an external provider. We don't show the code here, but it is easy to do in two steps:

1. Choose a backend for your database, and set up some repositories for a custom User object that suits your needs.
2. Implement and expose OAuth2UserService to call the Authorization Server as well as your database. Your implementation can delegate to the default implementation, which will do the heavy lifting of calling the authorization server.

### Generating a 401 in the Server

 You can use the GitHub API to find out more about the user, so you'll just need to plug that into the right part of the authentication process. If you declare a @Bean of type OAuth2UserService, it will be used to identify the user principal. You can use that hook to assert the the user is in the correct organization, and throw an exception if not.

SocialApplication.java

 ![SocialApplication.java
](https://i.ibb.co/SBHpfvm/Screenshot-from-2022-03-31-11-54-32.png)

 The WebClient has to be created as a bean as well, but that’s trivial because its ingredients are all auto-wirable by virtue of having used spring-boot-starter-oauth2-client

 ![](https://i.ibb.co/9qPxYtN/Screenshot-from-2022-03-31-11-55-25.png)
