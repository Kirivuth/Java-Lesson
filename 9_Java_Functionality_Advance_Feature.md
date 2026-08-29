# 📘 Java Wrapper Classes

---

## 1. What Are Wrapper Classes?

In Java, a **Wrapper Class** is a class that provides an object representation of a primitive data type.

Java has 8 primitive data types:

| Primitive Type | Wrapper Class |
| -------------- | ------------- |
| `byte`         | `Byte`        |
| `short`        | `Short`       |
| `int`          | `Integer`     |
| `long`         | `Long`        |
| `float`        | `Float`       |
| `double`       | `Double`      |
| `char`         | `Character`   |
| `boolean`      | `Boolean`     |

For example:

```java
int age = 25;

Integer ageObject = 25;
```

Here:

- `int` is a primitive type.
- `Integer` is a Wrapper Class.
- `Integer` allows an integer value to be treated as an object.

---

## 2. Why Do We Need Wrapper Classes?

Java collections such as `List`, `Set`, and `Map` work with objects.

For example:

```java
List<int> numbers = new ArrayList<>();
```

The above code is invalid because `List` cannot directly use primitive types.

Instead, we use the wrapper class:

```java
List<Integer> numbers = new ArrayList<>();

numbers.add(10);
numbers.add(20);
numbers.add(30);
```

This is one of the most important reasons Wrapper Classes are used.

---

## 3. Primitive Type vs Wrapper Class

```java
int number = 100;

Integer numberObject = 100;
```

The primitive value is stored directly.

The wrapper value is represented as an object.

Conceptually:

```text
Primitive
   |
   v
  int
  100


Wrapper
   |
   v
Integer Object
   |
   +---- value = 100
```

---

## 4. Autoboxing

**Autoboxing** is the automatic conversion from a primitive type to its corresponding wrapper class.

Example:

```java
int number = 100;

Integer numberObject = number;
```

Java automatically converts:

```text
int
 |
 | Autoboxing
 v
Integer
```

The following is also autoboxing:

```java
List<Integer> numbers = new ArrayList<>();

numbers.add(10);
numbers.add(20);
numbers.add(30);
```

The integer values are automatically converted from:

```java
int
```

to:

```java
Integer
```

---

## 5. Unboxing

**Unboxing** is the automatic conversion from a Wrapper Class back to a primitive type.

Example:

```java
Integer numberObject = 100;

int number = numberObject;
```

Java automatically converts:

```text
Integer
   |
   | Unboxing
   v
  int
```

Example:

```java
Integer a = 10;
Integer b = 20;

int result = a + b;

System.out.println(result);
```

Output:

```text
30
```

---

## 6. Manual Conversion

You can also explicitly convert a wrapper object to a primitive.

```java
Integer number = 100;

int value = number.intValue();

System.out.println(value);
```

Output:

```text
100
```

Other examples:

```java
Long number = 100L;

long value = number.longValue();
```

```java
Double number = 10.5;

double value = number.doubleValue();
```

---

## 7. Converting String to Number

Wrapper classes provide useful methods for converting strings into numbers.

Example:

```java
String text = "100";

int number = Integer.parseInt(text);

System.out.println(number);
```

Output:

```text
100
```

Other examples:

```java
long value = Long.parseLong("100000");
```

```java
double value = Double.parseDouble("10.50");
```

```java
boolean active = Boolean.parseBoolean("true");
```

---

## 8. Converting Number to String

You can convert numbers into strings using `String.valueOf()`.

```java
int number = 100;

String text = String.valueOf(number);

System.out.println(text);
```

Output:

```text
100
```

You can also use:

```java
Integer number = 100;

String text = number.toString();
```

---

## 9. Wrapper Classes and null

One important difference between primitives and wrapper classes is that wrapper objects can contain `null`.

Example:

```java
Integer age = null;
```

But this is not possible:

```java
int age = null;
```

This is useful when working with databases because a database column may contain `NULL`.

Example:

```java
Integer customerAge = null;
```

---

## 10. Important Warning About Unboxing null

Be careful when unboxing a `null` wrapper.

```java
Integer number = null;

int value = number;
```

This causes:

```text
NullPointerException
```

Therefore, always check for `null` when necessary.

```java
Integer number = null;

if (number != null) {
    int value = number;
}
```

---

# Java Generics

---

## 1. What Are Generics?

**Generics** allow you to write classes, interfaces, and methods that work with different data types while maintaining type safety.

For example:

```java
List<String> names = new ArrayList<>();
```

The generic type is:

```text
String
```

Therefore, the list is designed to contain `String` values.

---

## 2. Why Use Generics?

Without generics:

```java
List names = new ArrayList();

names.add("John");
names.add(100);
names.add(true);
```

This allows different types of objects.

With generics:

```java
List<String> names = new ArrayList<>();

names.add("John");
names.add("David");
names.add("Michael");
```

Now Java knows that the list should contain only `String`.

This provides:

- Type safety
- Better readability
- Fewer runtime errors
- Less casting

---

## 3. Generic Class

Example:

```java
public class Box<T> {

    private T value;

    public void setValue(T value) {
        this.value = value;
    }

    public T getValue() {
        return value;
    }
}
```

Here:

```text
T
```

is a generic type parameter.

We can create:

```java
Box<String> stringBox = new Box<>();

stringBox.setValue("Hello");

String value = stringBox.getValue();
```

Or:

```java
Box<Integer> integerBox = new Box<>();

integerBox.setValue(100);

Integer value = integerBox.getValue();
```

---

## 4. Generic Method

A method can also define its own generic type.

```java
public static <T> void printValue(T value) {
    System.out.println(value);
}
```

Usage:

```java
printValue("Hello");

printValue(100);

printValue(10.5);

printValue(true);
```

Output:

```text
Hello
100
10.5
true
```

---

## 5. Common Generic Naming Conventions

Java commonly uses:

| Letter | Meaning |
| ------ | ------- |
| `T`    | Type    |
| `E`    | Element |
| `K`    | Key     |
| `V`    | Value   |
| `N`    | Number  |

Example:

```java
Map<String, Integer>
```

Here:

```text
K = String
V = Integer
```

---

## 6. Generic Interface

Example:

```java
public interface Repository<T> {

    void save(T data);

    T findById(Long id);
}
```

Implementation:

```java
public class UserRepository implements Repository<User> {

    @Override
    public void save(User data) {
        System.out.println("Saving user");
    }

    @Override
    public User findById(Long id) {
        return new User();
    }
}
```

---

## 7. Bounded Generics

Sometimes we want to restrict the generic type.

Example:

```java
public class Calculator<T extends Number> {

    private T value;

    public Calculator(T value) {
        this.value = value;
    }

    public T getValue() {
        return value;
    }
}
```

Now the type must extend `Number`.

Valid:

```java
Calculator<Integer> c1 = new Calculator<>(100);

Calculator<Double> c2 = new Calculator<>(10.5);
```

Invalid:

```java
Calculator<String> c3 = new Calculator<>("Hello");
```

---

## 8. Wildcards

Java provides the wildcard:

```java
?
```

Example:

```java
List<?> list;
```

This means:

```text
List of an unknown type
```

Example:

```java
public static void printList(List<?> list) {

    for (Object value : list) {
        System.out.println(value);
    }
}
```

Usage:

```java
printList(List.of("A", "B", "C"));

printList(List.of(1, 2, 3));
```

---

# Java Lambda Expressions

---

## 1. What Is a Lambda Expression?

A **Lambda Expression** allows you to write a short implementation of a functional interface.

Basic syntax:

```java
(parameters) -> expression
```

Example:

```java
(a, b) -> a + b
```

---

## 2. Traditional Approach

Suppose we have:

```java
interface Calculator {
    int calculate(int a, int b);
}
```

Traditional implementation:

```java
Calculator calculator = new Calculator() {

    @Override
    public int calculate(int a, int b) {
        return a + b;
    }
};
```

Lambda version:

```java
Calculator calculator = (a, b) -> a + b;
```

The lambda is much shorter.

---

## 3. Lambda Syntax

One parameter:

```java
name -> System.out.println(name);
```

Multiple parameters:

```java
(a, b) -> a + b;
```

Multiple statements:

```java
(a, b) -> {
    int result = a + b;
    return result;
};
```

---

## 4. Functional Interface

A functional interface contains exactly one abstract method.

Example:

```java
@FunctionalInterface
interface Calculator {

    int calculate(int a, int b);
}
```

Now:

```java
Calculator add = (a, b) -> a + b;

System.out.println(add.calculate(10, 20));
```

Output:

```text
30
```

---

## 5. Built-in Functional Interfaces

Java provides several useful functional interfaces.

### Consumer

Accepts a value but does not return a result.

```java
Consumer<String> consumer =
        name -> System.out.println(name);

consumer.accept("John");
```

### Supplier

Does not accept input but returns a value.

```java
Supplier<String> supplier =
        () -> "Hello";

System.out.println(supplier.get());
```

### Function

Accepts one value and returns another value.

```java
Function<String, Integer> length =
        text -> text.length();

System.out.println(length.apply("Java"));
```

Output:

```text
4
```

### Predicate

Accepts a value and returns `true` or `false`.

```java
Predicate<Integer> positive =
        number -> number > 0;

System.out.println(positive.test(10));
```

Output:

```text
true
```

---

# Java Stream API

---

## 1. What Is Stream API?

The **Stream API** allows you to process collections of data using a functional programming style.

For example:

```java
List<Integer> numbers =
        List.of(1, 2, 3, 4, 5);
```

We can filter even numbers:

```java
List<Integer> result = numbers.stream()
        .filter(n -> n % 2 == 0)
        .toList();
```

Result:

```text
[2, 4]
```

---

## 2. Stream Pipeline

A stream commonly follows this flow:

```text
Collection
    |
    v
 stream()
    |
    v
 Intermediate Operations
    |
    +--> filter()
    |
    +--> map()
    |
    +--> sorted()
    |
    v
 Terminal Operation
    |
    +--> collect()
    +--> toList()
    +--> count()
    +--> forEach()
```

---

## 3. filter()

Filters elements based on a condition.

```java
List<Integer> numbers =
        List.of(1, 2, 3, 4, 5, 6);

List<Integer> evenNumbers =
        numbers.stream()
               .filter(n -> n % 2 == 0)
               .toList();

System.out.println(evenNumbers);
```

Output:

```text
[2, 4, 6]
```

---

## 4. map()

Transforms each element.

```java
List<String> names =
        List.of("john", "david", "michael");

List<String> upperNames =
        names.stream()
             .map(String::toUpperCase)
             .toList();

System.out.println(upperNames);
```

Output:

```text
[JOHN, DAVID, MICHAEL]
```

---

## 5. sorted()

Sorts elements.

```java
List<Integer> numbers =
        List.of(5, 2, 8, 1, 3);

List<Integer> sorted =
        numbers.stream()
               .sorted()
               .toList();

System.out.println(sorted);
```

Output:

```text
[1, 2, 3, 5, 8]
```

---

## 6. forEach()

Processes each element.

```java
numbers.stream()
       .forEach(n -> System.out.println(n));
```

Method reference:

```java
numbers.stream()
       .forEach(System.out::println);
```

---

## 7. count()

Counts elements.

```java
long count = numbers.stream()
        .filter(n -> n > 3)
        .count();

System.out.println(count);
```

---

## 8. reduce()

Combines multiple values into one result.

```java
List<Integer> numbers =
        List.of(1, 2, 3, 4, 5);

int sum = numbers.stream()
        .reduce(0, Integer::sum);

System.out.println(sum);
```

Output:

```text
15
```

---

## 9. Stream Example

```java
List<Integer> numbers =
        List.of(10, 15, 20, 25, 30);

List<Integer> result =
        numbers.stream()
               .filter(n -> n >= 20)
               .map(n -> n * 2)
               .sorted()
               .toList();

System.out.println(result);
```

Output:

```text
[40, 50, 60]
```

The processing flow is:

```text
[10, 15, 20, 25, 30]
             |
             v
       filter >= 20
             |
             v
        [20, 25, 30]
             |
             v
          map * 2
             |
             v
        [40, 50, 60]
             |
             v
          sorted
             |
             v
        [40, 50, 60]
```

---

# Java Records

---

## 1. What Is a Record?

A **Record** is a special type of class designed to represent immutable data.

Records were introduced as a standard feature in Java 16.

Java 21 supports records.

Example:

```java
public record User(
        Long id,
        String name,
        String email
) {
}
```

---

## 2. Creating a Record

```java
User user = new User(
        1L,
        "John",
        "john@example.com"
);
```

Access values:

```java
System.out.println(user.id());
System.out.println(user.name());
System.out.println(user.email());
```

---

## 3. Record vs Traditional Class

Traditional DTO:

```java
public class User {

    private Long id;
    private String name;
    private String email;

    public User(Long id, String name, String email) {
        this.id = id;
        this.name = name;
        this.email = email;
    }

    public Long getId() {
        return id;
    }

    public String getName() {
        return name;
    }

    public String getEmail() {
        return email;
    }
}
```

Record:

```java
public record User(
        Long id,
        String name,
        String email
) {
}
```

Records significantly reduce boilerplate.

---

## 4. Record Accessors

For:

```java
public record User(Long id, String name) {
}
```

Java automatically provides:

```java
user.id();
user.name();
```

Not:

```java
user.getId();
user.getName();
```

---

## 5. Record Constructor Validation

A record can validate its data.

```java
public record User(
        String name,
        int age
) {

    public User {

        if (age < 0) {
            throw new IllegalArgumentException(
                    "Age cannot be negative"
            );
        }
    }
}
```

---

## 6. When Should We Use Records?

Records are useful for:

- DTOs
- API responses
- Request objects
- Value objects
- Immutable data structures
- Configuration data

Example Spring Boot DTO:

```java
public record CustomerResponse(
        Long id,
        String name,
        String email
) {
}
```

---

# Java Virtual Threads

---

## 1. What Are Virtual Threads?

**Virtual Threads** are lightweight threads introduced as a standard feature in Java 21.

Traditional Java threads are associated more closely with operating-system threads.

Virtual threads are managed by the JVM and are much cheaper to create.

Conceptually:

```text
Traditional Threads

Java Thread 1 ----> OS Thread
Java Thread 2 ----> OS Thread
Java Thread 3 ----> OS Thread


Virtual Threads

Virtual Thread 1 --\
Virtual Thread 2 ---\
Virtual Thread 3 ----> JVM Scheduler ---> OS Threads
Virtual Thread 4 ---/
Virtual Thread 5 --/
```

---

## 2. Creating a Virtual Thread

```java
Thread.startVirtualThread(() -> {

    System.out.println(
            "Running in virtual thread"
    );

});
```

---

## 3. Using Thread.ofVirtual()

```java
Thread thread = Thread.ofVirtual()
        .start(() -> {
            System.out.println("Hello Virtual Thread");
        });
```

---

## 4. Virtual Thread Executor

You can use:

```java
try (ExecutorService executor =
        Executors.newVirtualThreadPerTaskExecutor()) {

    executor.submit(() -> {
        System.out.println("Task 1");
    });

    executor.submit(() -> {
        System.out.println("Task 2");
    });
}
```

This creates a virtual thread for each submitted task.

---

## 5. Why Virtual Threads Are Useful

Virtual threads are particularly useful for applications with many concurrent I/O operations.

Examples:

```text
HTTP Requests
     |
     +--> Database
     |
     +--> REST API
     |
     +--> Message Queue
     |
     +--> File System
```

Instead of creating expensive platform threads for every waiting operation, virtual threads can handle a very large number of concurrent tasks.

---

## 6. Virtual Threads in Spring Boot

In modern Spring Boot applications, virtual threads can be enabled with:

```properties
spring.threads.virtual.enabled=true
```

This can be useful for applications that perform many blocking operations.

However, virtual threads do not automatically make CPU-intensive operations faster.

For CPU-heavy work, you still need to consider CPU cores and appropriate concurrency.

---

# Java Regex

---

## 1. What Is Regex?

**Regex**, or Regular Expression, is a pattern used to search, validate, or manipulate text.

Examples:

```text
Email validation
Phone numbers
Account numbers
Transaction IDs
Passwords
Dates
```

---

## 2. Simple Regex

Check whether a string contains only digits:

```java
String text = "12345";

boolean result =
        text.matches("\\d+");

System.out.println(result);
```

Output:

```text
true
```

---

## 3. Common Regex Symbols

| Regex   | Meaning               |
| ------- | --------------------- |
| `.`     | Any character         |
| `\d`    | Digit                 |
| `\D`    | Non-digit             |
| `\w`    | Word character        |
| `\s`    | Whitespace            |
| `+`     | One or more           |
| `*`     | Zero or more          |
| `?`     | Zero or one           |
| `^`     | Beginning             |
| `$`     | End                   |
| `[abc]` | a, b, or c            |
| `[0-9]` | Digit from 0 to 9     |
| `{n}`   | Exactly n times       |
| `{n,m}` | Between n and m times |

---

## 4. Validate a Phone Number

Example:

```java
String phone = "0123456789";

boolean valid =
        phone.matches("\\d{10}");

System.out.println(valid);
```

Output:

```text
true
```

---

## 5. Validate Email

Simple example:

```java
String email =
        "john@example.com";

boolean valid =
        email.matches(
                "^[A-Za-z0-9+_.-]+@[A-Za-z0-9.-]+$"
        );

System.out.println(valid);
```

Output:

```text
true
```

Note:

Regex-based email validation can become complex. In production applications, email validation should usually be combined with appropriate application-level validation rather than relying on one simple regex.

---

## 6. Pattern and Matcher

For more advanced regex processing, use:

```java
Pattern
Matcher
```

Example:

```java
Pattern pattern =
        Pattern.compile("\\d+");

Matcher matcher =
        pattern.matcher("Account 12345");

while (matcher.find()) {

    System.out.println(
            matcher.group()
    );
}
```

Output:

```text
12345
```

---

## 7. Replacing Text

```java
String text =
        "Java is difficult";

String result =
        text.replaceAll(
                "difficult",
                "powerful"
        );

System.out.println(result);
```

Output:

```text
Java is powerful
```

---

# Java Advanced Sorting

---

## 1. Why Advanced Sorting?

Java collections can be sorted using:

- Natural ordering
- Comparator
- Lambda expressions
- Multiple sorting fields
- Reverse ordering
- Null handling

---

## 2. Sorting Numbers

```java
List<Integer> numbers =
        new ArrayList<>(
                List.of(5, 2, 8, 1, 3)
        );

numbers.sort(Integer::compareTo);

System.out.println(numbers);
```

Output:

```text
[1, 2, 3, 5, 8]
```

---

## 3. Reverse Sorting

```java
numbers.sort(
        Comparator.reverseOrder()
);
```

Output:

```text
[8, 5, 3, 2, 1]
```

---

## 4. Sorting Objects

Consider:

```java
public record Employee(
        Long id,
        String name,
        int age,
        double salary
) {
}
```

Create employees:

```java
List<Employee> employees =
        new ArrayList<>(List.of(
                new Employee(1L, "John", 30, 2000),
                new Employee(2L, "David", 25, 2500),
                new Employee(3L, "Michael", 35, 1800)
        ));
```

Sort by age:

```java
employees.sort(
        Comparator.comparing(Employee::age)
);
```

---

## 5. Sort by Salary

```java
employees.sort(
        Comparator.comparing(Employee::salary)
);
```

---

## 6. Sort by Salary Descending

```java
employees.sort(
        Comparator.comparing(
                Employee::salary
        ).reversed()
);
```

---

## 7. Sort by Multiple Fields

Suppose we want:

```text
Age ascending
    |
    v
If age is equal
    |
    v
Salary descending
```

Use:

```java
employees.sort(
        Comparator
                .comparing(Employee::age)
                .thenComparing(
                        Comparator.comparing(
                                Employee::salary
                        ).reversed()
                )
);
```

---

## 8. Sort by Name

```java
employees.sort(
        Comparator.comparing(Employee::name)
);
```

---

## 9. Case-Insensitive Sorting

```java
employees.sort(
        Comparator.comparing(
                Employee::name,
                String.CASE_INSENSITIVE_ORDER
        )
);
```

---

## 10. Null Handling

Sometimes values can be `null`.

Example:

```java
Comparator<Employee> comparator =
        Comparator.comparing(
                Employee::name,
                Comparator.nullsLast(
                        String.CASE_INSENSITIVE_ORDER
                )
        );

employees.sort(comparator);
```

This places `null` names at the end.

For null values first:

```java
Comparator.nullsFirst(...)
```

---

## 11. Sorting with Streams

Instead of modifying the original list:

```java
List<Employee> sortedEmployees =
        employees.stream()
                .sorted(
                        Comparator.comparing(
                                Employee::salary
                        ).reversed()
                )
                .toList();
```

The original collection is not modified by the `sorted()` stream operation.

---

# Combining Lambda, Generics, Streams and Sorting

These Java features become especially powerful when used together.

Example:

```java
List<Employee> employees =
        List.of(
                new Employee(
                        1L,
                        "John",
                        30,
                        2000
                ),
                new Employee(
                        2L,
                        "David",
                        25,
                        2500
                ),
                new Employee(
                        3L,
                        "Michael",
                        35,
                        1800
                ),
                new Employee(
                        4L,
                        "Alex",
                        28,
                        3000
                )
        );
```

Find employees whose salary is greater than 2000 and sort by salary descending:

```java
List<Employee> result =
        employees.stream()
                .filter(
                        employee ->
                                employee.salary() > 2000
                )
                .sorted(
                        Comparator.comparing(
                                Employee::salary
                        ).reversed()
                )
                .toList();
```

The processing flow is:

```text
Employee List
      |
      v
   stream()
      |
      v
   filter()
 salary > 2000
      |
      v
   sorted()
 salary DESC
      |
      v
   toList()
      |
      v
 Result
```

---

# Putting Everything Together

The following example combines:

- Wrapper Classes
- Generics
- Lambda Expressions
- Stream API
- Records
- Advanced Sorting

```java
import java.util.Comparator;
import java.util.List;

public class Main {

    public record Employee(
            Long id,
            String name,
            Integer age,
            Double salary
    ) {
    }

    public static void main(String[] args) {

        List<Employee> employees = List.of(

                new Employee(
                        1L,
                        "John",
                        30,
                        2000.0
                ),

                new Employee(
                        2L,
                        "David",
                        25,
                        2500.0
                ),

                new Employee(
                        3L,
                        "Michael",
                        35,
                        1800.0
                ),

                new Employee(
                        4L,
                        "Alex",
                        28,
                        3000.0
                )
        );

        List<Employee> result =
                employees.stream()

                        // Lambda Expression
                        .filter(
                                employee ->
                                        employee.salary() > 2000
                        )

                        // Advanced Sorting
                        .sorted(
                                Comparator.comparing(
                                        Employee::salary
                                ).reversed()
                        )

                        // Create a new List
                        .toList();

        result.forEach(
                employee ->
                        System.out.println(
                                employee.name()
                                        + " - "
                                        + employee.salary()
                        )
        );
    }
}
```

Output:

```text
Alex - 3000.0
David - 2500.0
```

---

# Summary

| Topic              | Main Purpose                             |
| ------------------ | ---------------------------------------- |
| Wrapper Classes    | Represent primitive values as objects    |
| Generics           | Provide type-safe reusable code          |
| Lambda Expressions | Write concise functional code            |
| Stream API         | Process collections efficiently          |
| Records            | Create concise immutable data carriers   |
| Virtual Threads    | Handle large numbers of concurrent tasks |
| Regex              | Search and validate text patterns        |
| Advanced Sorting   | Sort complex data using Comparator       |

---

# Important Java 21 Concepts

At this stage, you should understand the relationship between these features:

```text
                    Java Application
                           |
          +----------------+----------------+
          |                |                |
          v                v                v
      Generics          Records         Wrapper Classes
          |                |                |
          +----------------+----------------+
                           |
                           v
                    Collection Data
                           |
                           v
                    Stream API
                           |
             +-------------+-------------+
             |             |             |
             v             v             v
          filter()       map()       sorted()
             |             |             |
             +-------------+-------------+
                           |
                           v
                    Lambda Expressions
                           |
                           v
                     Final Result
```

For concurrent applications:

```text
Application
     |
     +--------------------+
     |                    |
     v                    v
 Stream API         Virtual Threads
     |                    |
     v                    v
 Data Processing      Concurrent Tasks
```

These features form an important part of modern Java development and are especially useful when building Spring Boot and enterprise applications.

```

This lesson is a good bridge from **basic Java syntax into modern Java 21 programming**, especially because it introduces the concepts you'll frequently encounter in Spring Boot code.
```
