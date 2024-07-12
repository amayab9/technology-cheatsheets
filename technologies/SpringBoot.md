# Spring Boot

Spring Boot is a framework designed to simplify the development of production-ready applications with minimal configuration. It allows developers to focus on writing business logic rather than setting up and configuring infrastructure.

## Key Features and Annotations

- **@SpringBootApplication**: Combines `@Configuration`, `@ComponentScan`, and `@EnableAutoConfiguration`. It configures the application with sensible defaults based on its classpath and other framework settings.

- **@RestController**: Annotates a class to define RESTful web services. It simplifies the creation of REST APIs by combining `@Controller` and `@ResponseBody`.

- **@RequestMapping**, **@GetMapping**, **@PostMapping**, **@PutMapping**, **@DeleteMapping**: Annotations to map HTTP requests to handler methods in controller classes. They specify the HTTP methods supported by the handler methods.

- **@Service**: Marks a class as a service component in Spring. Service classes contain business logic and are typically used in the controller layer.

- **@Repository**: Indicates that a class is a repository component in Spring Data. Repository classes handle data access and interact with the database using Spring Data repositories.

- **@Entity**: Defines a JPA entity. Entities represent tables in a relational database and are managed by Spring Data JPA.

- **@PathVariable**: Extracts values from the URI path in Spring MVC applications. It binds URI template variables to method parameters in controller methods.

- **@RequestBody**: Binds the HTTP request body to a method parameter in controller methods. It handles data sent to the server with HTTP POST requests.

## CRUD Operations

Spring Boot supports CRUD (Create, Read, Update, Delete) operations using these annotations:

- **@PostMapping**: Handles HTTP POST requests to create resources.
- **@GetMapping**: Handles HTTP GET requests to retrieve resources.
- **@PutMapping**: Handles HTTP PUT requests to update resources.
- **@DeleteMapping**: Handles HTTP DELETE requests to delete resources.
- **@PatchMapping**: Handles HTTP PATCH requests to partially update resources.

## Workflow

1. **Request Handling**: Requests are routed to controller classes annotated with `@RestController`.
2. **Business Logic**: Controllers delegate business logic to service classes annotated with `@Service`.
3. **Data Access**: Service classes use repository classes annotated with `@Repository` to perform CRUD operations on the database.
4. **Response Handling**: Responses are returned from controllers back to the client.

## Example Usage

Here’s an example of how Spring Boot can be used to create a simple RESTful API:

```java
@RestController
@RequestMapping("/api")
public class UserController {

    @Autowired
    private UserService userService;

    @GetMapping("/users/{id}")
    public ResponseEntity<User> getUserById(@PathVariable Long id) {
        User user = userService.getUserById(id);
        return ResponseEntity.ok(user);
    }

    @PostMapping("/users")
    public ResponseEntity<User> createUser(@RequestBody User user) {
        User createdUser = userService.createUser(user);
        return ResponseEntity.created(URI.create("/api/users/" + createdUser.getId())).body(createdUser);
    }

    @PutMapping("/users/{id}")
    public ResponseEntity<User> updateUser(@PathVariable Long id, @RequestBody User user) {
        User updatedUser = userService.updateUser(id, user);
        return ResponseEntity.ok(updatedUser);
    }

    @DeleteMapping("/users/{id}")
    public ResponseEntity<Void> deleteUser(@PathVariable Long id) {
        userService.deleteUser(id);
        return ResponseEntity.noContent().build();
    }
}
```
## Technologies I have used with SpringBoot

[Bruno](technologies/Bruno.md)
- To test the endpoints  

[PostgreSQL](technologies/PostgreSQL.md)
- As the database for the application

