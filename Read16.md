# Read: 16 - Spring Authentication

## Introduction

---
A Basic guide for Spring security which offers insight into the design and basic building blocks of the framework. we can use it if we need a high-level understanding of how a secure application works, or need to learn how to think about application security.

## Authentication and Access Control

---
**authentication** (who are you?) and **authorization** (what are you allowed to do?). Sometimes we can called authorization as access control because “authorization” is overloaded in other places.

The main strategy interface for `authentication` is AuthenticationManager as shown below:

![AuthenticationManager](https://i.ibb.co/8KW744B/Screenshot-from-2022-03-28-22-38-51.png)

The hierarchy by ProviderManager

![AuthenticationManager hierarchy using ProviderManager](https://i.ibb.co/R4zjD2n/Screenshot-from-2022-03-28-22-41-14.png)

## Customizing Authentication Managers

---
The most commonly used helper is the `AuthenticationManagerBuilder`, which is great for setting up in-memory, JDBC, or LDAP user details.

![AuthenticationManagerBuilder](https://i.ibb.co/gSGdxxL/Screenshot-from-2022-03-28-22-43-25.png)

Note that the `AuthenticationManagerBuilder` is `@Autowired` into a method in a `@Bean` — that is what makes it build the global (parent) AuthenticationManager

![@Autowired](https://i.ibb.co/47QXYcS/Screenshot-from-2022-03-28-22-45-37.png)

## Authorization or Access Control

---
Once authentication is successful, we can move on to authorization, and the strategy now is AccessDecisionManager.

## Web Security

---
Spring Security in the web tier (for UIs and HTTP back ends) is based on Servlet Filters, so it is helpful to first look at the role of Filters generally.

- The typical layering of the handlers for a single HTTP request shown in the figure below:

![typical layering of HTTP single request](https://i.ibb.co/PCrHm60/Screenshot-from-2022-03-28-22-49-13.png)

Spring Security is installed as a single Filter in the chain. In a Spring Boot application, the security filter is a @Bean in the ApplicationContext. It is installed at a position defined by SecurityProperties. DEFAULT_FILTER_ORDER, anchored by FilterRegistrationBean. REQUEST_WRAPPER_filter_MAX_ORDer.

![Relationship](https://i.ibb.co/qD1SXVb/Screenshot-from-2022-03-28-22-55-07.png)

The Spring Security filter contains a list of filter chains and dispatches a request to the first chain that matches it. There can be multiple filter chains all managed by Spring Security in the same top level FilterChain proxy. The most important feature of this dispatch process is that only one chain ever handles a request.

![list of filter](https://i.ibb.co/XsJ5ZZz/Screenshot-from-2022-03-28-23-02-20.png)

A vanilla Spring Boot application with no custom security configuration has a several (call it n) filter chains, where usually n=6. The last chain matches the catch-all path (/**) and is more active, containing logic for authentication, authorization, exception handling, header writing, and so on.

**NOTE**

![Note](https://i.ibb.co/HKQfg6g/Screenshot-from-2022-03-28-23-04-56.png)

## Creating and Customizing Filter Chains

---

The default fallback filter chain in a Spring Boot application has a predefined order of `SecurityProperties.BASIC_AUTH_ORDER`. You can switch it off completely by setting security.basic.enabled=false, or you can use it as a fallback and define other access rules with a lower order.

Many applications have completely different access rules for one set of resources compared to another. If the matching rules overlap, the earliest ordered filter chain wins. Each resource has its own WebSecurityConfigurer. Adapter with a unique order and its own request matcher. For example, an application that hosts a UI and an API might support cookie-based authentication for login.

![Coding](https://i.ibb.co/njMPjrF/Screenshot-from-2022-03-28-23-10-10.png)

## Request Matching for Dispatch and Authorization

---

A security filter chain has a request matcher that is used to decide whether to apply it to an HTTP request. Configuring a security filter chain allows you to fine-grained control of authorization.

One of the easiest mistakes to make when configuring Spring Security is to forget that these matchers apply to different processes. One is a request matcher for the whole filter chain, and the other is only to choose the access rule to apply.

## Combining Application Security Rules with Actuator Rules

---

Spring Boot Actuator allows you to add a security filter chain that applies only to the actuator endpoints in a secure application. It has an order of ManagementServerProperties. BASIC_AUTH_ORDER, which is 5 fewer than the default SecurityProperties fallback filter, so it is consulted before the fallback. If you prefer the default security settings, the easiest thing to do is to add your own filter chain later than the initial one and that has a request matcher that includes all actuators.

![Coding](https://i.ibb.co/fNy09r1/Screenshot-from-2022-03-28-23-15-39.png)

**NOTE**
![Note](https://i.ibb.co/xqt7cp8/Screenshot-from-2022-03-28-23-16-45.png)

## Method Security

---
It offers support for applying access rules to Java method executions. For users, it means the access rules are declared using the same format as roles or expressions but in a different place in your code. If access is denied, the caller gets an AccessDeniedException instead of the actual method result. There are other annotations that you can use on methods to enforce security constraints.

## Working with Threads

---
Spring Security is fundamentally thread-bound, because it needs to make the current authenticated principal available to a wide variety of downstream consumers. The basic building block is the SecurityContext, which may contain an Authentication (and when a user is logged in it is an Authentication that is explicitly authenticated). You can always access and manipulate the Security Context through static convenience methods in SecurityContextHolder. This can be useful if you, for instance, need to write a custom authentication filter.

![Code](https://i.ibb.co/MNj425s/Screenshot-from-2022-03-28-23-19-51.png)

![Code](https://i.ibb.co/SrmhcDD/Screenshot-from-2022-03-28-23-21-28.png)

## Processing Secure Methods Asynchronously

---
The SecurityContext is the context that runs in the background when a task (Runnable, Callable, and so on) is executed. Spring Security provides some helpers to make this easier, such as wrappers for Runnable and Callable. To propagate the SecurityContext to `@Async` methods, you need to supply an `AsyncConfigurer` and ensure the Executor is of the correct type.

![Coding](https://i.ibb.co/PMQyd2N/Screenshot-from-2022-03-28-23-22-25.png)

## Spring Auth Steps

---

1. set up a user model and repo
2. create a controller for that model
3. UserDetailsServiceImpl implements UserDetailsService
4. ApplicationUser implements UserDetails
5. WebSecurityConfig extends WebSecurityConfigurerAdapter
6. registration page
7. login page
