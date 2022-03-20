# Read12 - Data Spring JPA

## Introduction

---

- JPA stands for Java Persistent API.  

Spring Data JPA is a framework that abstract all of complexity to interact Java IDE with the database.

- JPA is a specification to manage the data between the java object.  

- JPA is the abstraction on top the Hibernate and JPA which means that it is make it easy to work with application which need to access to Database.  

- Hibernate is a Java interface implementation and it takes any java object so, the java class can map to database

- JPA benefits:

1. reduces the boilerplate code.
2. access to the database without having to write single line of SQL.
3. gives a lot og generated queries.  

## How to Build

---

Initialize the project with properties and its dependencies **we can use [Spring Initializr](https://start.spring.io/)**.

### Define a Simple Entity

To Create Entity in java, we need to import `import javax.persistence.Entity;` and the following packages:

`import javax.persistence.GeneratedValue;`
`import javax.persistence.GenerationType;`
`import javax.persistence.Id;`

For example:

![example of Entity](https://i.ibb.co/3mXCzn5/Screenshot-from-2022-03-20-02-34-31.png)  

- The `@id` for recognizes it as the object’s ID.

- The `@GeneratedValue` to indicate that the ID should be generated automatically.

## Create Simple Queries

---

Spring Data JPA focuses on using JPA to store data in a relational database. Its most compelling feature is the ability to create repository implementations automatically, at runtime, from a repository interface.

- we can extend some Repo in java like: CRUD Repository which includes some methods or define other query methods by declaring their method signature.

## Create an Application Class

---

we can run the simple class for the application which comes with Spring initializr. It contains `@SpringBootApplication` or use the three annotation:  
`@Configuration` then
`@EnableAutoConfiguration` and
`@ComponentScan`.

Next, the simple class from spring Initlizr will modify to be like the function requires.

we can save some customer or fetch an individual/all customers or fetch the customer by searching about the last name.  

$$ Example$$

![example of creating a few customer](https://i.ibb.co/ggF4Mjg/Screenshot-from-2022-03-20-02-52-44.png)

## Build an executable JAR

---

If you use Gradle, you can run the application by using `./gradlew bootRun`.

## Spring Data repository interfaces

---

There are a lot of Spring Data repository interfaces:

1. `CrudRepository` which provides CRUD functions
2. `PagingAndSortingRepository` provides methods to do pagination and sort records
3. `JpaRepository`provides JPA related methods like delete records in a batch.

**CrudRepository**

- The CRUD functionality consists save(…), findOne(…), findAll(), count(), delete(…), and exists(…)

**PagingAndSortingRepository**
This interface provides a method findAll(Pageable pageable), which is the key to implementing Pagination.

When using Pageable, we create a Pageable object with certain properties and we've to specify at least:

Page size
Current page number
Sorting

**JpaRepository**

The JPA Repo consists save(…), findOne(…), findAll(), flush(), saveAndFlush(…), and deleteInBatch(…).  

## Downsides of Spring Data Repositories

---

There are some basic downsides of directly depending on these as well:

1. we couple our code to the library and to its specific abstractions, such as `Page` or `Pageable`

2. by extending e.g. CrudRepository, we expose a complete set of persistence method at once

$$ Recourses $$

---

- [Resoucre 1](https://spring.io/guides/gs/accessing-data-jpa/)

- [Resources 2](https://www.baeldung.com/spring-data-repositories)  
