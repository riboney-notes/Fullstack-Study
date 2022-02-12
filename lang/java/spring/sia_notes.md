# Spring Boot in Action Notes

## Chapter 1

Spring container (application context) creates and manages app components (beans)
  * Dependency Injection: wiring beans
  * Container creates and maintains beans and injects those into the beans that need them

`@SpringBootApplication` is a composite annotation made up of:
  * `@SpringBootConfiguration`
  * `@EnableAutoConfiguration`
  * `@ComponentScan`

Classes with `@SpringBootApplication` is the *bootstrap* class and it can be used to configure things *and* bootstrap the Spring application context (i.e. start the app)
  * recommended to offload configs to their own respective classes

`@SpringBootTest` tells JUnit to bootstrap tests with Spring boot
  * `@WebMvcTest` is annoation that runs in context of a Spring MVC app and is used to test requests

Annotating with `@Controller, @Service, @Repository, etc` allows Spring's component scanning to automatically discover the class and create an instance of it as a bean in app context

When method with `@GetMapping()` returns a string, that string is treated as the logical name (`/templates/` + *logical name* + `.html`) of the `view` or HTML file

Spring DevTools Dependency
  * Provides features such as:
    * Automatic app restart when code changes
      * Does this by separating classing loaders for code in `src/main` and libraries
      * When code in `src/main` changes, devtools will reload the appropiate classloader
      * This means that when dependencies change, devtools wont restart and so you will have to do a hard rstart
    * Automatic browser refresh when resoruces change
    * Automatic disabling of template caches
      * disables template caches so you can get new template results instead of stale, cached ones
      * install `livereload` plugin in browser so you don't have to manually refresh browser when template changes
    * Built-in H2 console if H2 is in use
      * `localhost:8080/h2-console`
  * Not an IDE plugin

## Chapter 2

Concepts:
  * Presenting Model data in browser
  * Processing and validating form input
  * Choosing a view template library

Domain
  * the subject area that the app addresses
  * Domain objects represents the models the app will be working with

Controller
  * Handles HTTP requests and hands of the request to a View or writes data to body of a RESTful response
  * Ex:
    * Handle HTTP `GET` request for `/taco`
    * Build a list of ingredients and create taco object
    * Hand the request and taco object data of to a HTML template view (which renders the taco object)

A class can be annotated with `@RequestMapping` for general-purpose of request handling and defining the request path then methods in the class can be annotaed with `@GetMapping, @PostMapping, etc` to handle the specific HTTP requests

`Model` object in controller class is an object that transports data between a controller and the controller's view
  * it seems to be a wrapper for servlet request attributes, which is read by view to render data in HTML
    * To read servlet request attributes, you need a tempalte engine like Thymeleaf

`@ModelAttribute` annotated methods are invoked when its classes is triggered for request handling

When handling POST data from form submissions:
  * Problem: Form data from HTML is only in String, so to convert it to domain objects, you have to use a conversion service
  * Create bean class that implements `Converter<T,U>` and annotated with `@Component` so it is detected and registered to app by app context
    * It will automatically register them with Spring MVC to be used when conversion of request parameters to bound properties is needed
    * I assume that when a `POST` method sees a taco object in a POST request, Spring will automatically convert the string values with the taco converter bean
  * prefixing the view name with `redirect:` tells spring that its a `redirect` view and that after the POST method completes, user's browser should be redirected to the path in `redirect:`

Java Bean Validation API - JSR-303 (currently JSR-380)

Spring validation in Spring MVC
  * Add Spring validation starter to POM
    * Included hibernates implemenation of the Validation API
  * Declare validation rules
  * Specify validation be performed in controller methods that require validation (with the `@Valid` annotation in the methods parameters)
  * modify view to display validation errors

You don't need to create `@Controller` classes for handling requests that should just return a view
  * So instead, you can just create a class that implements `WEbMvcConfigurer` with a method `addViewControllers` that adds the request path and name of the view to serve up when path is requsted

* If not using devtools, you can manually disable template caching

* TODO: Spring convert 

## Ch3 Working with SQL data

Spring support for Jdbc is in the `JdbcTemplate` class
  * Example without JdbcTemplate
    * Create `Connection, PreparedStatement, ResultSet` classes and connect to database and initialize these values
    * Create query, perform query, get results and close db, result set, etc
  * With JdbcTemplate
    * It pretty much handles all the boilerplate code for you...
    * Just use the `.query()` to perform SQL queries on the database
    * Query method accepts the SQL query string and a RowMapper method that returns an object that is mapped from the rows from resultset
  * Need to import `spring-boot-start-jdbc` and a database like `h2` (you can also use spring boots jdbc, which is spring boot data jdbc)
  *  Repository classes are used to house query operations for cRUD
  * For JDBCTemplate repository
    * annotate class with `@Repository`
    * create a `JdbcTemplate` class variable and put it in the constructor for DI

* If you want to have more than one constructor, make sure to put `@Autowired` on the constructor you want Spring to use

* schemas should be in `/src/main/resources/schema.sql` and data in `/src/main/resources/data.sql` 

spring data jdbc comes with crud repoistory interface which will automatically generate implementations for repository interface
  * Also creates tables for you; just need to annotate the proeprties in thedomamin object so Spring Data knows what to hname things 


## Ch4 Spring security

Add spring boot security starter to POM

Adding spring security dependency will autoconfig it for you
  * All HTTP request paths will require authentication (HTTP dialog box to enter ur username and password)
  * user: "user", password is in the app start logs

* Class that creates `WEbSecurityConfgiruerAdapter` is what you use to edit your secrutiy config stuff
  * `@EnableWEbSecurity`
  * override the `configure()` method

Spring security setup
  * Import spring security starter
  * Create class that has `@Configuration` and `@EnableWebSecurity` amd extemds `WebSecurityConfigurerAdapter`
    * Replaces the basic HTTP dialog box with a login page
  * Create user store
    * configure/ create user store by overriding the `protected void configure(AuthenticationMAnagerBiulder auth)` method
    * Build the user store with the `auth` object
    * If using JDBC user store, include queries for getting username and password and authorities
    * stored passwords should be stored and configured with `passwordEncoder()`
      * so stored passwords are encoded
      * when user logs in, the password is encoded and then compared with the encoded password in DB
  * Create User domain class
    * needs to implement `UserDetails`
  * Create User repository interface (which comes with findbyusername())
  * Create userrepositorydetails class that implements `USerDetailsService` and overrides `loadByUsername` method
  * COnfigure this class in the `configure(Auth)` method
  * Create userregistrationcontroller and with DI get PasswordEncoder and User repository
  * Create registration form model class
  * secure web requests with configure method in config class that has parameter HttpSecurity
    * Configures security conditions that needs to be met before allowing a request to be served
    * Cofngiures a custom login page
    * Enables users to log out of application
    * Configures CSRF


JPA stuff
* Relationships
  * one to many, many to one, one to one, many to many
  * Owning & referencing side and bidirectionality
  * Example: One Teacher to many courses
  ```java
  public class Teacher{
    @OneToMany
    @JoinColumn(name="teacher_id", referencedColumnName="id)
    private List<Course> courses;
  }

  public class Courses{
    @ManyToOne
    private Teacher teacher;
  }
  ```
  * Eager vs lazy loading
  * Optionality
  * Cascading operations
* Entity types vs value types
  * component mapping
  * embedded/ embeddable and attribute override
* Reasonable default value
* Cascade
  * cascading the persist operation
  * cascading the delete operation
* uni/bi-directional
  * mappedBy attribute - refers to the foreigh key attribute
  * owner and referring
    * the many side is often the owner (contains foreign key)
      * so if student is many to one with teacher, then student has teacher FK and thus is the owner and when changes to students are made, its propagated to teacher, but when changes to teacher is made its not propagated to student
* orphaned record - record whose FK references a non-existent PK value
  * set orphanRemoval to true to allow `Cascade.REMOVE` to work properly
* Collection TAble/ @ElementCollection

Spring boot project process:

- Create Spring initializer project
- Create Data models
  - Create JPA entities (annotated with `@Entity`)
  - Create no-arg constructor and primary key (annotated with `@Id`)
  - `@Transient` creates fields that wont be persisted
  - https://stackoverflow.com/questions/42135114/how-does-spring-jpa-hibernate-ddl-auto-property-exactly-work-in-spring
  - converting entity to JPA and back: https://stackabuse.com/guide-to-jpa-with-hibernate-basic-mapping/
