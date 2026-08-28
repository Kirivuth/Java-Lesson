# Java 21: From Basics to Advanced

## Course Overview

A complete 42-slide Java 21 course covering Java fundamentals, OOP, collections, modern Java 21 features, concurrency, I/O, JDBC, JVM performance, security, design patterns, Spring Boot, JPA, testing, advanced topics, best practices, and deployment.

> **Java 21 note:** Java 21 is an LTS release. Record Patterns (JEP 440), Pattern Matching for `switch` (JEP 441), Virtual Threads (JEP 444), Sequenced Collections, and Generational ZGC (JEP 439) are finalized Java 21 features. String Templates (JEP 430), Structured Concurrency (JEP 453), and the Foreign Function & Memory API were preview features in Java 21. Project Valhalla is an ongoing/future OpenJDK project.

---

# Section 1: Introduction

## Slide 1: Title — Java 21: From Basics to Advanced

### Objective

Introduce the course and explain the progression from Java fundamentals to modern enterprise Java development.

### Learning Journey

```text
Java Basics
    ↓
Object-Oriented Programming
    ↓
Advanced OOP
    ↓
Collections
    ↓
Modern Java 21
    ↓
Concurrency
    ↓
I/O & Networking
    ↓
Database / JDBC
    ↓
JVM & Performance
    ↓
Security
    ↓
Design Patterns
    ↓
Spring / Hibernate / Testing
    ↓
Advanced Java
    ↓
Deployment
```

### Suggested Subtitle

> From fundamental programming concepts to modern enterprise Java development

---

## Slide 2: What is Java? — JVM, JRE, JDK

### What is Java?

Java is:

- A general-purpose programming language
- Object-oriented
- Strongly typed
- Platform independent
- Garbage collected
- Widely used for backend and enterprise applications

### JVM

The Java Virtual Machine executes Java bytecode.

### JRE

The Java Runtime Environment provides the components required to run Java applications.

### JDK

The Java Development Kit contains the tools required to develop Java applications, including the compiler.

### Relationship

```text
                    JDK
        ┌─────────────────────────┐
        │ Development Tools       │
        │ javac / javadoc / jdb   │
        │                         │
        │          JRE            │
        │     ┌─────────────┐     │
        │     │ JVM         │     │
        │     │ Java APIs   │     │
        │     └─────────────┘     │
        └─────────────────────────┘
```

### Example

```java
public class Hello {

    public static void main(String[] args) {
        System.out.println("Hello Java 21");
    }
}
```

Compile and run:

```bash
javac Hello.java
java Hello
```

### Execution Model

```text
Java Source
    ↓
javac
    ↓
Bytecode (.class)
    ↓
JVM
    ↓
Machine Code
```

---

## Slide 3: Setting Up Java 21 Environment

### Verify Java

```bash
java -version
javac -version
```

### Environment Variables

```text
JAVA_HOME
PATH
```

Example Windows:

```text
JAVA_HOME=C:\Program Files\Java\jdk-21
```

Check:

```cmd
echo %JAVA_HOME%
java -version
javac -version
```

### First Program

```java
public class Main {

    public static void main(String[] args) {
        System.out.println("Welcome to Java 21!");
    }
}
```

### Recommended Tools

- IntelliJ IDEA
- Visual Studio Code
- Eclipse
- Maven
- Gradle
- Git

---

# Section 2: Core Java

## Slide 4: Variables, Data Types, Operators

### Primitive Types

```java
byte b = 10;
short s = 100;
int age = 30;
long population = 8_000_000_000L;

float price = 10.5f;
double salary = 2500.75;

char grade = 'A';
boolean active = true;
```

### Reference Type

```java
String name = "Java";
```

### Arithmetic Operators

```java
int a = 10;
int b = 3;

System.out.println(a + b);
System.out.println(a - b);
System.out.println(a * b);
System.out.println(a / b);
System.out.println(a % b);
```

Output:

```text
13
7
30
3
1
```

### Comparison

```java
System.out.println(a > b);
System.out.println(a == b);
System.out.println(a != b);
```

### Strong Typing

```java
int number = 10;

// Compile error:
// number = "Hello";
```

---

## Slide 5: Control Flow — if, switch, loops

### if / else

```java
int age = 20;

if (age >= 18) {
    System.out.println("Adult");
} else {
    System.out.println("Minor");
}
```

### switch

```java
String role = "ADMIN";

switch (role) {
    case "ADMIN" -> System.out.println("Administrator");
    case "USER" -> System.out.println("User");
    default -> System.out.println("Unknown");
}
```

### for

```java
for (int i = 1; i <= 5; i++) {
    System.out.println(i);
}
```

### Enhanced for

```java
String[] names = {"John", "David", "Mary"};

for (String name : names) {
    System.out.println(name);
}
```

### while

```java
int count = 0;

while (count < 5) {
    System.out.println(count);
    count++;
}
```

---

## Slide 6: Arrays and Strings

### Array

```java
int[] numbers = {10, 20, 30, 40};

System.out.println(numbers[0]);
System.out.println(numbers.length);
```

### Iterate

```java
for (int number : numbers) {
    System.out.println(number);
}
```

### Multidimensional Array

```java
int[][] matrix = {
    {1, 2},
    {3, 4}
};

System.out.println(matrix[1][0]);
```

### String

```java
String name = "Java";

System.out.println(name.length());
System.out.println(name.toUpperCase());
System.out.println(name.contains("av"));
```

### String Comparison

Avoid:

```java
name == "Java";
```

Use:

```java
name.equals("Java");
```

### StringBuilder

```java
StringBuilder builder = new StringBuilder();

builder.append("Java");
builder.append(" ");
builder.append("21");

System.out.println(builder);
```

---

# Section 3: Object-Oriented Programming

## Slide 7: Classes & Objects

A class is a blueprint. An object is an instance of a class.

### Example

```java
public class Account {

    private String accountNumber;
    private double balance;

    public Account(String accountNumber, double balance) {
        this.accountNumber = accountNumber;
        this.balance = balance;
    }

    public void deposit(double amount) {
        balance += amount;
    }

    public double getBalance() {
        return balance;
    }
}
```

### Create Object

```java
public class Main {

    public static void main(String[] args) {

        Account account =
                new Account("ACC001", 1000);

        account.deposit(500);

        System.out.println(account.getBalance());
    }
}
```

Output:

```text
1500.0
```

### Key Concept

```text
Class  → Blueprint
Object → Instance
```

---

## Slide 8: Inheritance & Polymorphism

### Inheritance

```java
class Animal {

    void sound() {
        System.out.println("Animal sound");
    }
}

class Dog extends Animal {

    @Override
    void sound() {
        System.out.println("Woof");
    }
}
```

### Polymorphism

```java
Animal animal = new Dog();

animal.sound();
```

Output:

```text
Woof
```

The reference is `Animal`, but the actual object is `Dog`.

---

## Slide 9: Abstraction & Encapsulation

### Encapsulation

```java
public class Customer {

    private String name;

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }
}
```

### Abstraction

```java
interface PaymentService {

    void pay(double amount);
}
```

Implementation:

```java
class BankPaymentService
        implements PaymentService {

    @Override
    public void pay(double amount) {
        System.out.println(
            "Payment: " + amount
        );
    }
}
```

Usage:

```java
PaymentService service =
        new BankPaymentService();

service.pay(100);
```

### Four OOP Principles

```text
Encapsulation → Hide data/implementation
Abstraction   → Hide unnecessary complexity
Inheritance   → Reuse behavior
Polymorphism  → One interface, many implementations
```

---

# Section 4: Advanced OOP

## Slide 10: Exception Handling — try/catch/finally

### Basic try/catch

```java
try {

    int result = 10 / 0;

} catch (ArithmeticException e) {

    System.out.println(
        "Cannot divide by zero"
    );
}
```

### finally

```java
try {

    System.out.println("Processing");

} catch (Exception e) {

    System.out.println("Error");

} finally {

    System.out.println("Always executed");
}
```

### Custom Exception

```java
class InsufficientBalanceException
        extends RuntimeException {

    public InsufficientBalanceException(
            String message) {

        super(message);
    }
}
```

Usage:

```java
if (balance < amount) {

    throw new InsufficientBalanceException(
        "Insufficient balance"
    );
}
```

---

## Slide 11: Generics & Annotations

### Generics

Without generics:

```java
List list = new ArrayList();

list.add("Java");
list.add(100);
```

With generics:

```java
List<String> names =
        new ArrayList<>();

names.add("John");
names.add("David");

// Compile-time error:
// names.add(100);
```

### Generic Class

```java
class Box<T> {

    private T value;

    public Box(T value) {
        this.value = value;
    }

    public T getValue() {
        return value;
    }
}
```

Usage:

```java
Box<String> box =
        new Box<>("Java");

String value = box.getValue();
```

### Annotation

```java
@Override
public String toString() {
    return "Account";
}
```

### Custom Annotation

```java
@interface Audit {
    String value();
}
```

Usage:

```java
@Audit("CREATE_ACCOUNT")
class AccountService {
}
```

---

## Slide 12: Reflection API

Reflection allows Java applications to inspect classes at runtime.

### Example

```java
class Customer {

    private String name;

    public void hello() {
        System.out.println("Hello");
    }
}
```

### Reflection

```java
Class<?> clazz = Customer.class;

System.out.println(clazz.getName());

for (var field : clazz.getDeclaredFields()) {
    System.out.println(field.getName());
}

for (var method : clazz.getDeclaredMethods()) {
    System.out.println(method.getName());
}
```

Possible output:

```text
Customer
name
hello
```

### Frameworks Using Reflection

```text
Spring
Hibernate
JUnit
Jackson
Dependency Injection
ORM
Serialization
```

---

# Section 5: Collections Framework

## Slide 13: Lists, Sets, Maps

### List

```java
List<String> names =
        new ArrayList<>();

names.add("John");
names.add("David");
names.add("John");

System.out.println(names);
```

### Set

```java
Set<String> names =
        new HashSet<>();

names.add("John");
names.add("David");
names.add("John");

System.out.println(names);
```

### Map

```java
Map<String, Integer> scores =
        new HashMap<>();

scores.put("John", 90);
scores.put("David", 85);

System.out.println(
    scores.get("John")
);
```

### Main Types

```text
List  → Ordered, duplicates allowed
Set   → Unique elements
Map   → Key/value pairs
Queue → Processing-oriented collection
```

---

## Slide 14: Iterators & Streams

### Iterator

```java
List<String> names =
        new ArrayList<>(
            List.of("John", "David", "Mary")
        );

Iterator<String> iterator =
        names.iterator();

while (iterator.hasNext()) {

    String name = iterator.next();

    System.out.println(name);
}
```

### Stream

```java
List<Integer> numbers =
        List.of(1, 2, 3, 4, 5);

numbers.stream()
       .filter(n -> n % 2 == 0)
       .forEach(System.out::println);
```

Output:

```text
2
4
```

### Stream Pipeline

```text
Source
  ↓
filter()
  ↓
map()
  ↓
sorted()
  ↓
collect()
```

Example:

```java
List<String> result =
        names.stream()
             .filter(n -> n.startsWith("J"))
             .map(String::toUpperCase)
             .toList();
```

---

## Slide 15: Sequenced Collections — Java 21

Java 21 introduced:

```text
SequencedCollection
SequencedSet
SequencedMap
```

### Example

```java
SequencedCollection<String> names =
        new ArrayList<>(
            List.of("John", "David", "Mary")
        );

System.out.println(names.getFirst());
System.out.println(names.getLast());
```

Output:

```text
John
Mary
```

### Reverse

```java
System.out.println(
    names.reversed()
);
```

Output:

```text
[Mary, David, John]
```

### Add to Ends

```java
names.addFirst("Alice");
names.addLast("Bob");
```

### Key Takeaway

> Java 21 provides a consistent API for the first, last, and reversed views of sequenced collections.

---

# Section 6: Modern Java 21 Features

## Slide 16: Record Patterns — JEP 440

### Record

```java
record Customer(
        String name,
        int age
) {}
```

### Record Pattern

```java
static void printCustomer(Object obj) {

    if (obj instanceof Customer(String name, int age)) {

        System.out.println(
            name + " is " + age
        );
    }
}
```

### Usage

```java
Customer customer =
        new Customer("John", 30);

printCustomer(customer);
```

### Traditional Approach

```java
if (obj instanceof Customer customer) {

    String name = customer.name();
    int age = customer.age();
}
```

### Key Takeaway

> Record patterns allow record components to be extracted directly during pattern matching.

---

## Slide 17: Pattern Matching for switch — JEP 441

### Traditional

```java
Object value = "Java";

if (value instanceof String s) {
    System.out.println(s.length());
}
```

### Java 21

```java
static String describe(Object obj) {

    return switch (obj) {

        case Integer i ->
                "Integer: " + i;

        case String s ->
                "String: " + s;

        case null ->
                "Null";

        default ->
                "Unknown";
    };
}
```

Usage:

```java
System.out.println(
    describe("Java")
);
```

Output:

```text
String: Java
```

---

## Slide 18: String Templates — JEP 430, Preview

> **Important:** String Templates were a preview feature in Java 21. Clearly mark this slide as **Preview**.

### Concept

```java
String name = "John";
int age = 30;

String message =
        STR."Name: \{name}, Age: \{age}";
```

### Conceptual Model

```text
Template
   +
Expressions
   ↓
String
```

### Preview Compilation

```bash
javac --enable-preview --release 21 Example.java
```

### Important Note

Do not present String Templates as a permanent standard Java 21 API.

---

## Slide 19: Virtual Threads — JEP 444

Virtual threads are lightweight Java threads designed for high-throughput applications, particularly workloads that spend significant time waiting for I/O.

### Basic Example

```java
Thread thread =
        Thread.startVirtualThread(() -> {

            System.out.println(
                "Hello from virtual thread"
            );
        });
```

### Virtual Thread Executor

```java
try (var executor =
        Executors.newVirtualThreadPerTaskExecutor()) {

    for (int i = 0; i < 10_000; i++) {

        executor.submit(() -> {

            Thread.sleep(100);

            return null;
        });
    }
}
```

### Important Concept

> Virtual threads are lightweight, but they are not simply "faster CPU threads". They are especially useful for large numbers of blocking/I/O tasks.

---

# Section 7: Concurrency

## Slide 20: Threads & Executors

### Thread

```java
Thread thread = new Thread(() -> {

    System.out.println("Running");

});

thread.start();
```

### ExecutorService

```java
ExecutorService executor =
        Executors.newFixedThreadPool(4);

executor.submit(() ->
        System.out.println("Task")
);

executor.shutdown();
```

### Callable

```java
ExecutorService executor =
        Executors.newFixedThreadPool(4);

Future<Integer> future =
        executor.submit(() -> 10 + 20);

System.out.println(
    future.get()
);

executor.shutdown();
```

---

## Slide 21: Virtual Threads vs Platform Threads

| Platform Threads | Virtual Threads |
|---|---|
| Backed by OS threads | Managed by Java runtime |
| More expensive | Lightweight |
| Limited practical quantity | Very large numbers possible |
| Good for CPU-bound work | Excellent for I/O-heavy work |
| Traditional concurrency | Modern Java 21 concurrency |

### Example

```java
ExecutorService executor =
        Executors.newVirtualThreadPerTaskExecutor();

for (int i = 0; i < 100_000; i++) {

    executor.submit(() -> {
        Thread.sleep(1000);
        return null;
    });
}

executor.close();
```

### Key Takeaway

> Choose concurrency mechanisms based on workload. Virtual threads are especially useful for high-concurrency I/O-bound workloads.

---

## Slide 22: Structured Concurrency

> **Important:** Structured Concurrency was a preview feature in Java 21 (JEP 453).

### Concept

```text
Parent Task
    │
    ├── Task A
    ├── Task B
    └── Task C
```

### Java 21 Preview Example

```java
try (var scope =
        new StructuredTaskScope.ShutdownOnFailure()) {

    Future<String> user =
        scope.fork(() -> getUser());

    Future<String> account =
        scope.fork(() -> getAccount());

    scope.join();
    scope.throwIfFailed();

    System.out.println(
        user.resultNow()
    );

    System.out.println(
        account.resultNow()
    );
}
```

### Why Structured Concurrency?

```text
Parent
  ├── Child A
  └── Child B

Parent controls child lifecycle.
```

### Key Takeaway

> Structured concurrency treats related concurrent tasks as one logical unit of work.

---

# Section 8: I/O & Networking

## Slide 23: File Handling Basics

### Write

```java
Path path =
        Path.of("hello.txt");

Files.writeString(
        path,
        "Hello Java 21"
);
```

### Read

```java
String content =
        Files.readString(path);

System.out.println(content);
```

### Check Existence

```java
if (Files.exists(path)) {
    System.out.println("File exists");
}
```

### List Directory

```java
try (Stream<Path> files =
        Files.list(Path.of("."))) {

    files.forEach(System.out::println);
}
```

### Useful APIs

```text
Path
Files
InputStream
OutputStream
Reader
Writer
```

---

## Slide 24: HTTP Client API Demo

Java provides the `java.net.http` HTTP Client API.

### GET

```java
HttpClient client =
        HttpClient.newHttpClient();

HttpRequest request =
        HttpRequest.newBuilder()
                .uri(URI.create(
                    "https://api.example.com/users"
                ))
                .GET()
                .build();

HttpResponse<String> response =
        client.send(
            request,
            HttpResponse.BodyHandlers.ofString()
        );

System.out.println(response.statusCode());
System.out.println(response.body());
```

### POST

```java
HttpRequest request =
        HttpRequest.newBuilder()
                .uri(URI.create(
                    "https://api.example.com/users"
                ))
                .header(
                    "Content-Type",
                    "application/json"
                )
                .POST(
                    HttpRequest.BodyPublishers.ofString(
                        "{\"name\":\"John\"}"
                    )
                )
                .build();
```

---

# Section 9: Database Connectivity

## Slide 25: JDBC Basics

### Architecture

```text
Java Application
       ↓
JDBC API
       ↓
JDBC Driver
       ↓
Database
```

### Connection

```java
String url =
    "jdbc:postgresql://localhost:5432/bank";

String username = "postgres";
String password = "password";

Connection connection =
    DriverManager.getConnection(
        url,
        username,
        password
    );
```

### Query

```java
Statement statement =
        connection.createStatement();

ResultSet result =
        statement.executeQuery(
            "SELECT id, name FROM customer"
        );

while (result.next()) {

    System.out.println(
        result.getLong("id")
    );

    System.out.println(
        result.getString("name")
    );
}
```

---

## Slide 26: CRUD Demo with PreparedStatement

### Why PreparedStatement?

Avoid SQL injection and separate SQL structure from parameter values.

### Bad

```java
String sql =
    "SELECT * FROM users WHERE name = '"
    + name
    + "'";
```

### Good

```java
String sql =
    "SELECT * FROM users WHERE name = ?";

PreparedStatement statement =
        connection.prepareStatement(sql);

statement.setString(1, name);

ResultSet result =
        statement.executeQuery();
```

### INSERT

```java
String sql =
    "INSERT INTO customer(name, email) VALUES (?, ?)";

PreparedStatement ps =
        connection.prepareStatement(sql);

ps.setString(1, "John");
ps.setString(2, "john@example.com");

ps.executeUpdate();
```

### UPDATE

```java
String sql =
    "UPDATE customer SET name = ? WHERE id = ?";

PreparedStatement ps =
        connection.prepareStatement(sql);

ps.setString(1, "David");
ps.setLong(2, 1);

ps.executeUpdate();
```

### DELETE

```java
String sql =
    "DELETE FROM customer WHERE id = ?";

PreparedStatement ps =
        connection.prepareStatement(sql);

ps.setLong(1, 1);

ps.executeUpdate();
```

---

# Section 10: JVM & Performance

## Slide 27: Garbage Collection Strategies

### JVM Memory Concept

```text
Application
     ↓
Objects
     ↓
Heap
     ↓
Garbage Collector
     ↓
Unused Objects Reclaimed
```

### Common Collectors

```text
Serial GC
Parallel GC
G1 GC
ZGC
Shenandoah
```

### G1

Good general-purpose collector for many server workloads.

### ZGC

Designed for very low pause times.

### Parallel GC

Strong focus on application throughput.

### Key Takeaway

> GC selection depends on workload, latency requirements, heap size, allocation rate, and operational goals.

---

## Slide 28: Generational ZGC — JEP 439

Java 21 introduced Generational ZGC.

### Concept

```text
ZGC Heap

┌────────────────────────┐
│ Young Generation       │
│ Short-lived objects    │
└────────────────────────┘

┌────────────────────────┐
│ Old Generation         │
│ Long-lived objects     │
└────────────────────────┘
```

### Example Allocation

```java
for (int i = 0; i < 1_000_000; i++) {

    String temporary =
        "Transaction-" + i;
}
```

Many temporary objects quickly become garbage.

### JVM Options

```bash
java -XX:+UseZGC      -XX:+ZGenerational      Application
```

---

# Section 11: Security

## Slide 29: Encryption / Decryption Basics

### Encoding

```text
Encoding
    ↓
Representation
    ↓
Not security
```

### Hashing

```text
Input
  ↓
Hash Function
  ↓
Hash
```

Hashing is designed to be one-way.

### Encryption

```text
Plaintext
    ↓
Encryption + Key
    ↓
Ciphertext
    ↓
Decryption + Key
    ↓
Plaintext
```

### AES Example

```java
KeyGenerator generator =
        KeyGenerator.getInstance("AES");

generator.init(256);

SecretKey key =
        generator.generateKey();

Cipher cipher =
        Cipher.getInstance("AES/GCM/NoPadding");
```

### Password Storage

Do not store passwords using plain encryption or plain SHA-256.

Use a password hashing/KDF approach such as:

```text
Argon2id
bcrypt
scrypt
PBKDF2
```

according to your application's security requirements.

---

## Slide 30: Secure Coding Practices

### Validate Input

```java
String input =
        request.getParameter("name");
```

Validate and constrain input before using it.

### Use PreparedStatement

```java
PreparedStatement ps =
        connection.prepareStatement(
            "SELECT * FROM account WHERE id = ?"
        );
```

### Do Not Hardcode Passwords

Bad:

```java
String password = "123456";
```

Better:

```text
Environment variables
Secrets Manager
Vault
Cloud secret storage
```

### Do Not Log Sensitive Data

Bad:

```java
log.info("Password: {}", password);
```

### Principle of Least Privilege

A service should have only the permissions it needs.

### Keep Dependencies Updated

Regularly patch libraries and frameworks.

---

# Section 12: Design Patterns

## Slide 31: Singleton, Factory, Builder

### Singleton

```java
public class Configuration {

    private static final Configuration INSTANCE =
            new Configuration();

    private Configuration() {}

    public static Configuration getInstance() {
        return INSTANCE;
    }
}
```

> In Spring applications, prefer letting Spring manage singleton-scoped beans instead of manually implementing Singleton.

### Factory

```java
interface Payment {
    void pay();
}
```

```java
class PaymentFactory {

    static Payment create(String type) {

        return switch (type) {

            case "BANK" -> new BankPayment();
            case "CARD" -> new CardPayment();

            default ->
                throw new IllegalArgumentException(
                    "Unknown payment"
                );
        };
    }
}
```

### Builder

```java
Customer customer =
        new CustomerBuilder()
            .name("John")
            .age(30)
            .email("john@example.com")
            .build();
```

---

## Slide 32: Observer, Strategy, Decorator

### Strategy

```java
interface PaymentStrategy {
    void pay(double amount);
}
```

```java
class CardPayment
        implements PaymentStrategy {

    @Override
    public void pay(double amount) {
        System.out.println(
            "Card payment: " + amount
        );
    }
}
```

Usage:

```java
PaymentStrategy strategy =
        new CardPayment();

strategy.pay(100);
```

### Observer

```text
Bank Account
     │
     ├── Notification Service
     ├── Audit Service
     └── Reporting Service
```

### Decorator

```text
BasicService
     ↓
LoggingDecorator
     ↓
SecurityDecorator
     ↓
Service
```

### Key Takeaway

> Use patterns to improve maintainability and flexibility, not simply because a pattern exists.

---

# Section 13: Frameworks & Ecosystem

## Slide 33: Spring Boot Overview

### Architecture

```text
Controller
     ↓
Service
     ↓
Repository
     ↓
Database
```

### REST Controller

```java
@RestController
@RequestMapping("/accounts")
public class AccountController {

    @GetMapping("/{id}")
    public Account getAccount(
            @PathVariable Long id) {

        return new Account(
            id,
            "ACC001"
        );
    }
}
```

### Spring Boot Provides

```text
Dependency Injection
REST APIs
Configuration
Security
Data Access
Actuator
Cloud Integration
```

---

## Slide 34: Hibernate / JPA

### Entity

```java
@Entity
@Table(name = "customer")
public class Customer {

    @Id
    @GeneratedValue
    private Long id;

    private String name;

    private String email;
}
```

### Repository

```java
public interface CustomerRepository
        extends JpaRepository<Customer, Long> {

    List<Customer> findByName(String name);
}
```

### Service

```java
@Service
public class CustomerService {

    private final CustomerRepository repository;

    public CustomerService(
            CustomerRepository repository) {

        this.repository = repository;
    }
}
```

### Architecture

```text
Java Object
     ↕
Hibernate
     ↕
JPA
     ↕
JDBC
     ↕
Database
```

---

## Slide 35: Testing with JUnit & Mockito

### JUnit

```java
class CalculatorTest {

    @Test
    void shouldAddNumbers() {

        Calculator calculator =
                new Calculator();

        int result =
                calculator.add(10, 20);

        assertEquals(30, result);
    }
}
```

### Mockito

```java
@Mock
private AccountRepository repository;

@InjectMocks
private AccountService service;
```

### Mock Behavior

```java
when(repository.findById(1L))
        .thenReturn(
            Optional.of(account)
        );
```

### Test

```java
Account result =
        service.findById(1L);

assertEquals(
    "ACC001",
    result.getAccountNumber()
);
```

---

# Section 14: Advanced Topics

## Slide 36: Project Panama — Native Interop

Project Panama is an OpenJDK project focused on improving interoperability between Java and native code.

The Foreign Function & Memory API was a preview feature in Java 21.

### Concept

```text
Java
  ↓
Foreign Function & Memory API
  ↓
Native Library
  ↓
C / C++ / OS API
```

### Conceptual Example

```java
Arena arena =
        Arena.ofConfined();

MemorySegment memory =
        arena.allocate(100);

memory.set(
    ValueLayout.JAVA_INT,
    0,
    100
);
```

### Potential Use Cases

```text
Native libraries
Operating system APIs
High-performance native integrations
C interoperability
Off-heap memory
```

---

## Slide 37: Project Valhalla — Future Roadmap

Project Valhalla is an ongoing OpenJDK project focused on improving Java's object and value model.

### Traditional Object

```text
Object
 ├── identity
 ├── metadata
 └── fields
```

### Value-Oriented Direction

```text
Value
 ├── data
 └── efficient representation
```

### Motivation

```text
Object overhead
      ↓
Memory pressure
      ↓
CPU cache pressure
      ↓
Performance impact
```

### Important

> Project Valhalla is not a finalized Java 21 feature. Present it as a future/ongoing OpenJDK roadmap topic.

---

# Section 15: Best Practices

## Slide 38: Coding Standards

### Class Naming

```java
CustomerService
AccountController
PaymentRepository
```

### Method Naming

```java
calculateInterest()
processPayment()
findCustomer()
```

### Variable Naming

```java
customerName
accountNumber
transactionAmount
```

### Constants

```java
MAX_RETRY_COUNT
DEFAULT_TIMEOUT
```

### Good Example

```java
public BigDecimal calculateInterest(
        BigDecimal principal,
        BigDecimal rate) {

    return principal
            .multiply(rate)
            .divide(
                BigDecimal.valueOf(100)
            );
}
```

### Poor Example

```java
public BigDecimal x(
        BigDecimal a,
        BigDecimal b) {

    return a.multiply(b)
            .divide(BigDecimal.valueOf(100));
}
```

### Key Takeaway

> Code is written once but read many times.

---

## Slide 39: Debugging & Logging

### Debugging Tools

```text
Breakpoint
Step Over
Step Into
Step Out
Watch
Evaluate Expression
Call Stack
```

### Example

```java
public void transfer(
        Account from,
        Account to,
        BigDecimal amount) {

    // Put breakpoint here

    from.debit(amount);

    to.credit(amount);
}
```

### Logging

```java
private static final Logger log =
        LoggerFactory.getLogger(
            AccountService.class
        );
```

### INFO

```java
log.info(
    "Processing account {}",
    accountId
);
```

### ERROR

```java
log.error(
    "Transfer failed for {}",
    transactionId,
    exception
);
```

### Avoid

```java
System.out.println(...)
```

for production logging.

---

## Slide 40: Deployment Strategies

### Traditional

```text
Java Application
       ↓
JAR
       ↓
Server
```

### Container

```text
Java Application
       ↓
Docker Image
       ↓
Container
       ↓
Cloud
```

### CI/CD

```text
Developer
    ↓
Git
    ↓
CI/CD
    ↓
Build
    ↓
Test
    ↓
Docker Image
    ↓
Container Registry
    ↓
Deployment
```

### Build

```bash
mvn clean package
```

### Run

```bash
java -jar application.jar
```

### Dockerfile

```dockerfile
FROM eclipse-temurin:21-jre

COPY target/app.jar app.jar

ENTRYPOINT ["java", "-jar", "app.jar"]
```

### Docker

```bash
docker build -t java21-app .
docker run -p 8080:8080 java21-app
```

---

# Section 16: Wrap-Up

## Slide 41: Summary of Java 21 Features

### Core Java

```text
OOP
Collections
Streams
Generics
Exceptions
Reflection
```

### Modern Java 21

```text
Record Patterns
Pattern Matching for switch
Virtual Threads
Sequenced Collections
Generational ZGC
```

### Java 21 Preview Topics

```text
String Templates
Structured Concurrency
Foreign Function & Memory API
```

### Enterprise Ecosystem

```text
Spring Boot
Hibernate/JPA
JUnit
Mockito
JDBC
HTTP Client
Docker
Cloud
```

### Main Message

> Java 21 combines the maturity of Java with modern language features, improved concurrency, and improved JVM capabilities.

---

## Slide 42: Q&A

# Thank You

## Questions?

### Discussion Questions

1. Which Java 21 feature do you like most?
2. When should we use virtual threads?
3. How would you apply Java 21 in a real project?
4. When should we use streams instead of traditional loops?
5. What is the difference between JPA and Hibernate?
6. How can Java applications be secured?
7. What is the role of the JVM in Java application performance?

---

# Suggested Course Project

To make the lessons practical, use one continuous project throughout the course.

## Project: Banking Account Management System

### Domain

```text
Customer
   │
   ├── Account
   │      │
   │      ├── Deposit
   │      ├── Withdrawal
   │      └── Transfer
   │
   └── Transaction
```

### Basic Java

```text
Customer
Account
Transaction
```

### OOP

```text
Account
SavingsAccount
CurrentAccount
PaymentService
```

### Collections

```text
List<Transaction>
Set<Customer>
Map<String, Account>
```

### Streams

```java
List<Transaction> successful =
        transactions.stream()
                .filter(Transaction::isSuccessful)
                .toList();
```

### Records

```java
record CustomerSummary(
        String customerName,
        BigDecimal balance
) {}
```

### Virtual Threads

```java
try (var executor =
        Executors.newVirtualThreadPerTaskExecutor()) {

    for (Transaction transaction : transactions) {

        executor.submit(() ->
            processTransaction(transaction)
        );
    }
}
```

### Database

```text
Customer
Account
Transaction
```

### Spring Boot

```text
REST Controller
      ↓
Service
      ↓
Repository
      ↓
PostgreSQL
```

### Deployment

```text
Spring Boot
    ↓
JAR
    ↓
Docker
    ↓
Cloud
```

---

# Java 21 Learning Roadmap

```text
                    JAVA 21
                       │
        ┌──────────────┴──────────────┐
        │                             │
      BASICS                       ADVANCED
        │                             │
   Variables                      Reflection
   Control Flow                   Generics
   Arrays                         Collections
        │                             │
        └──────────────┬──────────────┘
                       │
                      OOP
                       │
          ┌────────────┼────────────┐
          │            │            │
     Inheritance   Abstraction   Polymorphism
          │            │            │
          └────────────┼────────────┘
                       │
                  MODERN JAVA 21
                       │
       ┌───────────────┼────────────────┐
       │               │                │
    Patterns       Virtual Threads    Sequenced
       │               │             Collections
       └───────────────┼────────────────┘
                       │
                  CONCURRENCY
                       │
              I/O + Networking
                       │
                    JDBC
                       │
                 JVM / GC
                       │
                  Security
                       │
               Design Patterns
                       │
            Spring / Hibernate
                       │
             Testing / Deployment
```

---

# Final Learning Objectives

After completing this course, students should be able to:

- Understand the Java/JVM/JDK ecosystem
- Write Java 21 applications
- Apply object-oriented programming
- Use generics and annotations
- Work with Java collections and streams
- Use modern Java 21 language features
- Understand virtual threads and concurrency
- Perform file and HTTP operations
- Connect Java applications to databases using JDBC
- Understand garbage collection and JVM performance
- Apply secure coding practices
- Understand common design patterns
- Build applications with Spring Boot
- Use JPA/Hibernate
- Write unit tests with JUnit and Mockito
- Understand Java's native interoperability direction
- Debug and log Java applications
- Package Java applications
- Deploy Java applications using Docker and cloud infrastructure
