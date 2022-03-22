# Read: 13 - Related Resources and Integration Testing

## Introduction

---

The Database include Entities and relation between these Entities.

There are three types of Relationships in database:

1. One-To-One Relationship
2. One-To-Many Relationship
3. Many-To-Many Relationship

- The main goal of these relationship is to reduce unnecessary redundancy.

## how to work with relationships between entities in Spring Data REST

---

### 1. One-to-One Relationship

![1-1 Relationship](https://fmhelp.filemaker.com/help/18/fmp/en/FMP_Help/images/relational.07.03.2.png)

### 1.1 The Data Model

- To Link two classes in Spring boot, for example Library and Address, three Annotations should know about:

1. @OneToOne
2. @JoinToColumn()
3. @RestResource() [optional]  

Library Class                                                                       |  Address Class
:----------------------------------------------------------------------------------:|:----------------------------------------------------------------------------------:
![Library Class](https://i.ibb.co/wCdWYzk/Screenshot-from-2022-03-21-23-30-21.png)  |  ![Address Class](https://i.ibb.co/JmyYth8/Screenshot-from-2022-03-21-23-31-26.png)

- After Created @OnetoOne, the linking of two table will be used @Join to specify another table(class).

### 1.2 The Repositories

- Create Repository interface to use CRUDRepository

![Library and Address Repository](https://i.ibb.co/F6YLGkm/Screenshot-from-2022-03-21-23-42-23.png)

### 1.3 Creating the Resources

 To create Library instance
> curl -i -X POST -H "Content-Type:application/json"
  -d '{"name":"My Library"}' <http://localhost:8080/libraries>

### 1.4 Creating the Associations

To create a relationship by using one of the association resources which is HTTP method PUT. Put method supports text/ur-list.
After make the Library the owner of the association, the address is added to library class

> curl -i -X PUT -d "http://localhost:8080/addresses/1"
  -H "Content-Type:text/uri-list" <http://localhost:8080/libraries/1/libraryAddress>

- to check the Library association resource of the address

> curl -i -X GET <http://localhost:8080/addresses/1/library>

- to remove the association

> curl -i -X Delete <http://localhost:8080/libraries/1/libraryAddress>

### 2. One-to-Many Relationship

There are two types of the One-to-Many: One-to-Many and Many-To-One

2.1 The Data Model

![Image data Model](https://fmhelp.filemaker.com/help/18/fmp/en/FMP_Help/images/relational.07.04.2.png)
2.2 The Repository
Create a repo to Using CRUDRepo for example in library class we can create a book repository whohc is an interface
***'***

2.3 The Association Resource
Firstly, we have to create book instance using the /books collection resource
> curl -i -X POST -d "{\"title\":\"Book1\"}"
  -H "Content-Type:application/json" <http://localhost:8080/books>

-To associate the book with the Library using sending put method
> curl -i -X PUT -H "Content-Type:text/uri-list"
-d "http://localhost:8080/libraries/1" <http://localhost:8080/books/1/library>

- To verify the book using Get method, which is returned jason

> curl -i -X GET <http://localhost:8080/libraries/1/books>

- To remove the association:

> curl -i -X DELETE <http://localhost:8080/books/1/library>

### 3. Many-to-Many Relationship

3.1 The Data model

![Many-to-Many](https://miro.medium.com/max/1166/1*xgq7abp-kEFBlH2Hboling.png)

3.2 The Repository

Create a repo to Using CRUDRepo for example in library class we can create a author repository whohc is an interface.

3.3 The Association Resources
Before, we have to create Author instance by sending a POST requests to the /authors collection resource:
> curl -i -X POST -H "Content-Type:application/json"
  -d "{\"name\":\"author1\"}" http://localhost:8080/authors

- Add book record the database

> curl -i -X POST -H "Content-Type:application/json"
  -d "{\"title\":\"Book 2\"}" http://localhost:8080/books

Now, we ready to create an association between the two records and the Author
> curl -i -X PUT -H "Content-Type:text/uri-list"
  --data-binary @uris.txt <http://localhost:8080/authors/1/books>

- To verify two book have been associated with Author

> curl -i -X GET <http://localhost:8080/authors/1/books>

- To remove an association

> curl -i -X DELETE <http://localhost:8080/authors/1/books/1>

### 4. Testing the Endpoints With TestRestTemplate

![Testing](https://i.ibb.co/WBYvb2c/Screenshot-20220322-010533.jpg)

## Test

---

### Testing

The latest junit-jupiter-engine, junit-jupiter-api, and Spring test dependencies are required

### 2. Spring MVC Test Configuration

2.1. Enable Spring in Tests With JUnit 5

@ExtendWith annotation to run the spring test
@ContextConfiguration to load the context configuration and bootstrap the context that our test will use.
@WebAppConfiguration to load the web application context.

2.2. The WebApplicationContext Object

Using @Autowired to wire the web application context right into the test

2.3 Mocking Web Context Beans

It encapsulates all web application beans and makes them available for testing.

> private MockMvc mockMvc;
@BeforeEach
public void setup() throws Exception {
    this.mockMvc = MockMvcBuilders.webAppContextSetup(this.webApplicationContext).build();
}

2.4. Verify Test Configuration

    @Test
    public void givenWac_whenServletContext_thenItProvidesGreetController() {
    ServletContext servletContext = webApplicationContext.getServletContext();
    
    Assert.assertNotNull(servletContext);
    Assert.assertTrue(servletContext instanceof MockServletContext);
    Assert.assertNotNull(webApplicationContext.getBean("greetController"));
}

### 3. Writing Integration Tests

3.1. Verify View Name
3.2. Verify Response Body
3.3. Send GET Request With Path Variable
3.4. Send GET Request With Query Parameters
3.5. Send POST Request

because Spring prepares a fake web application context to mock the HTTP requests and responses, it may not support all the features of a full-blown Spring application.
