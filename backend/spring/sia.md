# Spring in Action

[link](https://www.manning.com/books/spring-in-action-sixth-edition)

## 1: Getting started with Spring

- Spring application context
  - container that instantiates, assembles, and manages application components (beans) through dependency injection

- Example of ways to "wire up" beans
  - XML files

  ```xml
  <bean id="inventoryService"
        class="com.example.InventoryService" />

  <bean id="productService"
        class="com.example.ProductService" />
    <constructor-arg ref="inventoryService" />
  </bean>
  ```

  - java annotations

  ```java
  @Configuration
  public class ServiceConfiguration {
    @Bean
    public InventoryService inventoryService() {
      return new InventoryService();
    }

    @Bean
    public ProductService productService() {
      return new ProductService(inventoryService());
    }
  }
  ```
  
- Component scanning
  - where Spring can automatically discover components from an application's classpath and create them as beans in the Spring Application context

- Autowiring
  - where Spring automatically injects the components with other beans that they depend on

- Autoconfiguration
  - feature of Spring boot that reduces amount of explicit configuration needed to build an application

- `@SpringBootApplication`
  - Found in `main.java`
  - Composite annotation that combines three annotations:
    - `@SpringBootConfiguration`
      - Designates the class as a configuration class
    - `@EnableAutoConfiguration`
      - Enables Spring Boot automatic configuration that tells Spring boot to automatically configure any components 
    - `@ComponentScan`
      - Allows you to declare other classes with annotations like `@Component, @Controller, @Service` to have Spring automatically discover and register them as components (beans) in the Spring application context

- `run()`
  - performs the bootstrapping of the spring application by creating the application context
  - Parameters passed into it are a configuration class and CLI arguments

- Running Spring application
  - Building and running
    - `./mvnw package` then `java -jar target/app-name-SNAPSHOT.jar`
  
  - Spring boot maven plugin
    - `./mvnw spring-boot:run`

  - Running tests: 
    - `./mvnw test`
