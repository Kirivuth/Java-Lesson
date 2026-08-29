# 📘 Java Errors

## 1. What Are Errors in Java?

When a Java program runs, something can go wrong.

For example:

```text
Invalid input
File not found
Database connection failed
Null value
Division by zero
Network failure
Programming mistake

Java provides mechanisms to detect and handle these problems.

A useful high-level view is:

Java Problems
      |
      +-------------------+
      |                   |
      v                   v
    Error             Exception
      |                   |
      v                   v
Usually serious      Usually can be handled
```

# 2. Error vs Exception

Java has a class hierarchy based on:

```java
Throwable
```

The basic hierarchy is:

```text
Throwable
   |
   +----------------+
   |                |
   v                v
 Error          Exception
```

`Error` usually represents serious problems that applications normally should not try to recover from.

`Exception` usually represents conditions that an application can potentially handle.

---

# 3. Throwable

The root class for Java's error and exception mechanism is:

```java
Throwable
```

Hierarchy:

```text
                 Throwable
                    |
          +---------+---------+
          |                   |
          v                   v
        Error             Exception
          |                   |
          |                   +----------------+
          |                   |                |
          v                   v                v
      Serious             Checked        Unchecked
      Problems           Exceptions      Exceptions
                                               |
                                               v
                                       RuntimeException
```

---

# 4. What Is an Error?

`Error` represents serious problems related to the Java runtime environment or JVM.

Examples include:

```java
OutOfMemoryError
StackOverflowError
NoClassDefFoundError
LinkageError
```

Example:

```java
public class Main {

    public static void main(String[] args) {

        throw new OutOfMemoryError(
                "Memory problem"
        );
    }
}
```

Normally, application code should not catch an `Error` unless there is a very specific reason.

---

# 5. Common Java Errors

Some common subclasses of `Error` are:

| Error                         | Meaning                           |
| ----------------------------- | --------------------------------- |
| `OutOfMemoryError`            | JVM cannot allocate enough memory |
| `StackOverflowError`          | Stack memory has been exhausted   |
| `NoClassDefFoundError`        | Required class cannot be loaded   |
| `ExceptionInInitializerError` | Static initialization failed      |
| `AssertionError`              | An assertion failed               |
| `LinkageError`                | Class loading/linking problem     |

---

# 6. OutOfMemoryError

`OutOfMemoryError` occurs when the JVM cannot allocate enough memory.

Example:

```java
import java.util.ArrayList;
import java.util.List;

public class Main {

    public static void main(String[] args) {

        List<byte[]> data =
                new ArrayList<>();

        while (true) {

            data.add(
                    new byte[1024 * 1024]
            );
        }
    }
}
```

This continuously allocates memory.

Eventually, the JVM may throw:

```text
java.lang.OutOfMemoryError:
Java heap space
```

---

# 7. StackOverflowError

A common cause is infinite recursion.

Example:

```java
public class Main {

    static void recursiveMethod() {

        recursiveMethod();
    }

    public static void main(String[] args) {

        recursiveMethod();
    }
}
```

The method keeps calling itself:

```text
recursiveMethod()
      |
      v
recursiveMethod()
      |
      v
recursiveMethod()
      |
      v
     ...
      |
      v
StackOverflowError
```

---

# 8. Why Does StackOverflowError Happen?

Every method call requires stack memory.

For example:

```text
main()
 |
 +-- recursiveMethod()
       |
       +-- recursiveMethod()
             |
             +-- recursiveMethod()
                   |
                   +-- ...
```

Eventually, the stack cannot hold another method call.

The JVM throws:

```text
StackOverflowError
```

---

# 9. Exception

An `Exception` represents a condition that can often be handled by the application.

Examples:

```java
IOException
SQLException
FileNotFoundException
IllegalArgumentException
NullPointerException
```

For example:

```java
try {

    // Code that may fail

} catch (Exception e) {

    // Handle the problem
}
```

---

# 10. Checked Exceptions

A **checked exception** is checked by the compiler.

Examples:

```java
IOException
SQLException
FileNotFoundException
```

If a method can throw a checked exception, you generally must either:

1. Handle it with `try-catch`

or:

2. Declare it with `throws`

---

# 11. Example of Checked Exception

```java
import java.io.IOException;
import java.nio.file.Files;
import java.nio.file.Path;

public class Main {

    public static void main(String[] args)
            throws IOException {

        String content =
                Files.readString(
                        Path.of("data.txt")
                );

        System.out.println(content);
    }
}
```

The method declares:

```java
throws IOException
```

This tells the caller:

> This method may throw an IOException.

---

# 12. Handling a Checked Exception

Instead of declaring the exception, we can handle it.

```java
import java.io.IOException;
import java.nio.file.Files;
import java.nio.file.Path;

public class Main {

    public static void main(String[] args) {

        try {

            String content =
                    Files.readString(
                            Path.of("data.txt")
                    );

            System.out.println(content);

        } catch (IOException e) {

            System.err.println(
                    "Unable to read file: "
                            + e.getMessage()
            );
        }
    }
}
```

---

# 13. Unchecked Exceptions

Unchecked exceptions are subclasses of:

```java
RuntimeException
```

They are not required to be declared or caught by the compiler.

Examples:

```java
NullPointerException
IllegalArgumentException
ArithmeticException
IndexOutOfBoundsException
NumberFormatException
```

Hierarchy:

```text
RuntimeException
       |
       +-------------------------+
       |            |            |
       v            v            v
NullPointer   IllegalArgument  Arithmetic
Exception      Exception        Exception
```

---

# 14. NullPointerException

One of the most common Java exceptions is:

```java
NullPointerException
```

Example:

```java
String name = null;

System.out.println(
        name.length()
);
```

Because `name` is `null`, Java cannot call:

```java
name.length()
```

The result is:

```text
NullPointerException
```

---

# 15. Avoiding NullPointerException

Instead of:

```java
String name = null;

System.out.println(
        name.length()
);
```

you can check:

```java
String name = null;

if (name != null) {

    System.out.println(
            name.length()
    );
}
```

Or use:

```java
Objects.requireNonNull(
        name,
        "Name must not be null"
);
```

---

# 16. ArithmeticException

Example:

```java
int a = 10;
int b = 0;

int result =
        a / b;
```

This produces:

```text
ArithmeticException
```

because integer division by zero is invalid.

---

# 17. Handling ArithmeticException

```java
try {

    int result =
            10 / 0;

} catch (ArithmeticException e) {

    System.out.println(
            "Cannot divide by zero."
    );
}
```

Output:

```text
Cannot divide by zero.
```

---

# 18. ArrayIndexOutOfBoundsException

Example:

```java
int[] numbers =
        {10, 20, 30};

System.out.println(
        numbers[5]
);
```

The array only has indexes:

```text
0
1
2
```

Trying to access index `5` causes:

```text
ArrayIndexOutOfBoundsException
```

---

# 19. IndexOutOfBoundsException

This can also occur with collections.

Example:

```java
List<String> names =
        List.of(
                "John",
                "David"
        );

System.out.println(
        names.get(5)
);
```

The list only contains indexes:

```text
0
1
```

The result is:

```text
IndexOutOfBoundsException
```

---

# 20. NumberFormatException

This happens when a string cannot be converted into a number.

Example:

```java
String value =
        "ABC";

int number =
        Integer.parseInt(value);
```

Result:

```text
NumberFormatException
```

Correct example:

```java
String value =
        "100";

int number =
        Integer.parseInt(value);

System.out.println(number);
```

Output:

```text
100
```

---

# 21. IllegalArgumentException

This exception is commonly used when a method receives an invalid argument.

Example:

```java
public static void setAge(int age) {

    if (age < 0) {

        throw new IllegalArgumentException(
                "Age cannot be negative"
        );
    }
}
```

Calling:

```java
setAge(-10);
```

produces:

```text
IllegalArgumentException
```

---

# 22. throw

The keyword:

```java
throw
```

is used to explicitly throw an exception.

Example:

```java
public static void withdraw(
        double amount
) {

    if (amount <= 0) {

        throw new IllegalArgumentException(
                "Amount must be greater than zero"
        );
    }
}
```

---

# 23. throws

The keyword:

```java
throws
```

is used in a method declaration to indicate that the method may throw an exception.

Example:

```java
public static String readFile(
        Path path
) throws IOException {

    return Files.readString(path);
}
```

Remember:

```text
throw
  |
  v
Actually throws an exception


throws
  |
  v
Declares possible exceptions
```

---

# 24. throw vs throws

| Keyword                    | Purpose                      |
| -------------------------- | ---------------------------- |
| `throw`                    | Actually throws an exception |
| `throws`                   | Declares possible exceptions |
| Used inside method         | `throw`                      |
| Used in method declaration | `throws`                     |

Example:

```java
throw new IllegalArgumentException(
        "Invalid amount"
);
```

vs:

```java
public void read()
        throws IOException {
}
```

---

# 25. try

The `try` block contains code that may produce an exception.

Example:

```java
try {

    int result =
            10 / 0;

}
```

Usually it is combined with:

```java
catch
```

or:

```java
finally
```

---

# 26. catch

The `catch` block handles an exception.

Example:

```java
try {

    int result =
            10 / 0;

} catch (ArithmeticException e) {

    System.out.println(
            "Division by zero"
    );
}
```

Flow:

```text
try
 |
 | Exception occurs
 v
catch
 |
 v
Handle exception
```

---

# 27. finally

The `finally` block normally executes whether an exception occurs or not.

Example:

```java
try {

    System.out.println(
            "Processing..."
    );

} catch (Exception e) {

    System.out.println(
            "Error"
    );

} finally {

    System.out.println(
            "Finished"
    );
}
```

Possible output:

```text
Processing...
Finished
```

---

# 28. try-catch-finally Flow

```text
                Start
                  |
                  v
                try
                  |
          +-------+-------+
          |               |
      No Error          Error
          |               |
          |               v
          |             catch
          |               |
          +-------+-------+
                  |
                  v
               finally
                  |
                  v
                 End
```

---

# 29. Multiple catch Blocks

You can handle different exceptions separately.

```java
try {

    int number =
            Integer.parseInt(
                    "ABC"
            );

} catch (NumberFormatException e) {

    System.out.println(
            "Invalid number"
    );

} catch (Exception e) {

    System.out.println(
            "Other error"
    );
}
```

The more specific exception should normally come before a more general exception.

---

# 30. Multi-Catch

Java allows multiple exception types in one `catch`.

Example:

```java
try {

    // Code

} catch (
        IOException |
        SQLException e
) {

    System.out.println(
            "I/O or database error"
    );
}
```

This is called:

```text
Multi-Catch
```

---

# 31. Exception Hierarchy

A simplified hierarchy:

```text
                       Throwable
                           |
             +-------------+-------------+
             |                           |
             v                           v
           Error                     Exception
             |                           |
             |                 +---------+---------+
             |                 |                   |
             |                 v                   v
             |          RuntimeException      Other Exceptions
             |                 |
             |       +---------+----------+
             |       |         |          |
             |       v         v          v
             |      NPE       IAE       ArithmeticException
             |
             +--> OutOfMemoryError
             +--> StackOverflowError
```

Where:

```text
NPE = NullPointerException
IAE = IllegalArgumentException
```

---

# 32. Exception Propagation

If a method does not handle an exception, it can propagate to its caller.

Example:

```java
public static void methodC()
        throws IOException {

    throw new IOException(
            "File error"
    );
}
```

Then:

```java
public static void methodB()
        throws IOException {

    methodC();
}
```

Then:

```java
public static void methodA()
        throws IOException {

    methodB();
}
```

Flow:

```text
methodA()
    |
    v
methodB()
    |
    v
methodC()
    |
    v
IOException
    |
    v
methodB()
    |
    v
methodA()
```

---

# 33. Exception Propagation Diagram

```text
Application
    |
    v
Controller
    |
    v
Service
    |
    v
Repository
    |
    v
Database
    |
    X
Database Error
    |
    v
Repository
    |
    v
Service
    |
    v
Controller
    |
    v
Exception Handler
```

This pattern is very common in Spring Boot applications.

---

# 34. Custom Exception

You can create your own exception.

Example:

```java
public class AccountNotFoundException
        extends RuntimeException {

    public AccountNotFoundException(
            String message
    ) {

        super(message);
    }
}
```

Use it:

```java
throw new AccountNotFoundException(
        "Account not found"
);
```

---

# 35. Why Use Custom Exceptions?

Custom exceptions make application errors more meaningful.

Instead of:

```text
RuntimeException
```

you can have:

```text
AccountNotFoundException
InsufficientBalanceException
InvalidTransactionException
CustomerNotFoundException
```

This is particularly useful in business applications.

---

# 36. Banking Application Example

Suppose a customer tries to withdraw more money than their balance.

```java
public void withdraw(
        BigDecimal amount
) {

    if (balance.compareTo(amount) < 0) {

        throw new InsufficientBalanceException(
                "Insufficient account balance"
        );
    }

    balance =
            balance.subtract(amount);
}
```

Custom exception:

```java
public class InsufficientBalanceException
        extends RuntimeException {

    public InsufficientBalanceException(
            String message
    ) {

        super(message);
    }
}
```

Flow:

```text
Customer
   |
   v
Withdraw Request
   |
   v
Check Balance
   |
   +---- Balance OK ------> Withdraw
   |
   +---- Insufficient ----> Exception
                              |
                              v
                         Error Response
```

---

# 37. Exception Handling in Spring Boot

A Spring Boot REST API may return:

```text
HTTP Request
     |
     v
Controller
     |
     v
Service
     |
     v
Exception
     |
     v
Global Exception Handler
     |
     v
HTTP Response
```

For example:

```text
POST /accounts/withdraw
```

could produce:

```json
{
  "status": 400,
  "error": "INSUFFICIENT_BALANCE",
  "message": "Account balance is insufficient"
}
```

---

# 38. Global Exception Handling

Spring Boot commonly uses:

```java
@RestControllerAdvice
```

Example:

```java
@RestControllerAdvice
public class GlobalExceptionHandler {

    @ExceptionHandler(
            InsufficientBalanceException.class
    )
    public ResponseEntity<?> handle(
            InsufficientBalanceException e
    ) {

        return ResponseEntity
                .badRequest()
                .body(
                        Map.of(
                            "error",
                            "INSUFFICIENT_BALANCE",
                            "message",
                            e.getMessage()
                        )
                );
    }
}
```

This allows controllers to remain cleaner.

---

# 39. Error Handling Architecture

A typical Spring Boot application can use:

```text
                 HTTP Request
                      |
                      v
                 Controller
                      |
                      v
                   Service
                      |
                      v
                 Repository
                      |
                      v
                  Database
                      |
                 +----+----+
                 |         |
              Success     Error
                 |         |
                 v         v
             Response   Exception
                           |
                           v
                  Global Exception
                       Handler
                           |
                           v
                    Error Response
```

---

# 40. Exception Message

Every exception can have a message.

Example:

```java
throw new IllegalArgumentException(
        "Amount must be greater than zero"
);
```

Retrieve the message:

```java
catch (IllegalArgumentException e) {

    System.out.println(
            e.getMessage()
    );
}
```

---

# 41. Stack Trace

A stack trace shows where an exception occurred.

Example:

```java
try {

    int result =
            10 / 0;

} catch (ArithmeticException e) {

    e.printStackTrace();
}
```

Example output:

```text
java.lang.ArithmeticException: / by zero
    at Main.calculate(Main.java:10)
    at Main.main(Main.java:5)
```

The stack trace is extremely useful for debugging.

---

# 42. Reading a Stack Trace

Consider:

```text
java.lang.NullPointerException:
Cannot invoke "String.length()"
because "name" is null

    at UserService.getName(UserService.java:25)
    at UserController.getUser(UserController.java:42)
    at Main.main(Main.java:10)
```

Read it from the top:

```text
Exception Type
      |
      v
NullPointerException
      |
      v
First application location
      |
      v
UserService.java:25
```

The first relevant application line is often the best place to start debugging.

---

# 43. Exception Chaining

One exception can contain another exception as its cause.

Example:

```java
try {

    // Database operation

} catch (SQLException e) {

    throw new RuntimeException(
            "Unable to load account",
            e
    );
}
```

The original exception is preserved as the cause.

Conceptually:

```text
RuntimeException
       |
       v
"Unable to load account"
       |
       v
SQLException
       |
       v
Original Database Error
```

---

# 44. getCause()

You can retrieve the original cause.

```java
catch (RuntimeException e) {

    Throwable cause =
            e.getCause();

    System.out.println(
            cause.getMessage()
    );
}
```

---

# 45. Best Practice: Preserve the Cause

Avoid:

```java
catch (SQLException e) {

    throw new RuntimeException(
            "Database error"
    );
}
```

The original exception is lost.

Prefer:

```java
catch (SQLException e) {

    throw new RuntimeException(
            "Database error",
            e
    );
}
```

Now the original cause is preserved.

---

# 46. Don't Catch Everything

Avoid unnecessarily broad handling such as:

```java
try {

    // Everything

} catch (Exception e) {

    // Ignore
}
```

This can hide important problems.

Bad:

```java
catch (Exception e) {

}
```

Better:

```java
catch (IOException e) {

    log.error(
            "Unable to read file",
            e
    );
}
```

---

# 47. Don't Ignore Exceptions

Avoid:

```java
catch (Exception e) {
}
```

This is dangerous because:

```text
Exception
    |
    v
Ignored
    |
    v
Application continues
    |
    v
Unknown incorrect state
```

Always decide what should happen when an exception occurs.

---

# 48. Don't Use Exceptions for Normal Flow

Avoid using exceptions for ordinary control flow.

Bad:

```java
try {

    int value =
            Integer.parseInt(input);

} catch (NumberFormatException e) {

    // Used to check whether input is valid
}
```

Sometimes this is acceptable, but if validation can be performed before parsing, explicit validation may be clearer.

Exceptions should generally represent exceptional conditions.

---

# 49. Validate Input

Instead of allowing invalid values to reach deep application layers:

```text
Controller
    |
    v
Service
    |
    v
Repository
    |
    v
Database
    |
    X
Invalid Input
```

validate early:

```text
HTTP Request
     |
     v
Validation
     |
     +---- Invalid ----> Error Response
     |
     +---- Valid ------> Service
```

---

# 50. Exception Handling Best Practices

### 1. Catch specific exceptions

Prefer:

```java
catch (IOException e)
```

instead of:

```java
catch (Exception e)
```

when possible.

---

### 2. Preserve the original cause

Use:

```java
throw new MyException(
        "Meaningful message",
        e
);
```

---

### 3. Don't ignore exceptions

Avoid:

```java
catch (Exception e) {
}
```

---

### 4. Use meaningful custom exceptions

For example:

```text
AccountNotFoundException
InsufficientBalanceException
InvalidTransactionException
```

---

### 5. Log useful information

Example:

```java
log.error(
        "Failed to process FT {}",
        ftNumber,
        e
);
```

---

### 6. Don't expose sensitive information

Avoid returning internal details such as:

```text
Database password
SQL credentials
Internal server paths
Stack traces
API keys
Tokens
```

to clients.

---

# 51. Error vs Exception Summary

| Concept           | Description                            |
| ----------------- | -------------------------------------- |
| `Throwable`       | Root of Java error/exception hierarchy |
| `Error`           | Serious JVM/runtime problem            |
| `Exception`       | Problem that application may handle    |
| Checked Exception | Compiler requires handling/declaration |
| RuntimeException  | Unchecked exception                    |
| `throw`           | Explicitly throw an exception          |
| `throws`          | Declare possible exceptions            |
| `try`             | Code that may fail                     |
| `catch`           | Handle exception                       |
| `finally`         | Cleanup/final processing               |
| Custom Exception  | Application-specific exception         |

---

# 52. Common Exception Cheat Sheet

| Exception                        | Typical Cause                |
| -------------------------------- | ---------------------------- |
| `NullPointerException`           | Using a `null` reference     |
| `ArithmeticException`            | Invalid arithmetic operation |
| `NumberFormatException`          | Invalid numeric conversion   |
| `IllegalArgumentException`       | Invalid method argument      |
| `IndexOutOfBoundsException`      | Invalid collection index     |
| `ArrayIndexOutOfBoundsException` | Invalid array index          |
| `ClassCastException`             | Invalid object casting       |
| `IOException`                    | I/O operation failed         |
| `SQLException`                   | Database operation failed    |
| `FileNotFoundException`          | File cannot be found/opened  |

---

# 53. Error vs Exception Diagram

```text
                         Throwable
                            |
             +--------------+--------------+
             |                             |
             v                             v
           Error                       Exception
             |                             |
       +-----+-----+              +-------+--------+
       |           |              |                |
       v           v              v                v
OutOfMemory   StackOverflow   RuntimeException   Checked
Error         Error               |             Exceptions
                                  |
                    +-------------+-------------+
                    |             |             |
                    v             v             v
                  NPE           IAE          Arithmetic
              NullPointer   IllegalArgument    Exception
               Exception     Exception
```

---

# 54. Exception Handling Flow

```text
                    Start
                      |
                      v
                   Execute
                      |
                      v
                    try
                      |
             +--------+--------+
             |                 |
          Success            Error
             |                 |
             |                 v
             |              catch
             |                 |
             +--------+--------+
                      |
                      v
                  finally
                      |
                      v
                     End
```

---

# 55. Real-World Banking Error Flow

A banking transaction may look like:

```text
Customer Request
       |
       v
Validate Request
       |
       +------ Invalid ------> Validation Exception
       |
       v
Check Account
       |
       +------ Not Found ---> AccountNotFoundException
       |
       v
Check Balance
       |
       +------ Insufficient -> InsufficientBalanceException
       |
       v
Process Transaction
       |
       +------ Database Error -> SQLException
       |
       v
Commit Transaction
       |
       v
Success Response
```

---

# 56. Complete Custom Exception Example

```java
public class InsufficientBalanceException
        extends RuntimeException {

    public InsufficientBalanceException(
            String message
    ) {

        super(message);
    }
}
```

Service:

```java
public void withdraw(
        BigDecimal amount
) {

    if (amount.compareTo(BigDecimal.ZERO) <= 0) {

        throw new IllegalArgumentException(
                "Amount must be greater than zero"
        );
    }

    if (balance.compareTo(amount) < 0) {

        throw new InsufficientBalanceException(
                "Insufficient account balance"
        );
    }

    balance =
            balance.subtract(amount);
}
```

---

# 57. Complete try-catch Example

```java
import java.util.Scanner;

public class Main {

    public static void main(String[] args) {

        Scanner scanner =
                new Scanner(System.in);

        try {

            System.out.print(
                    "Enter a number: "
            );

            int number =
                    Integer.parseInt(
                            scanner.nextLine()
                    );

            System.out.println(
                    "Number = " + number
            );

        } catch (
                NumberFormatException e
        ) {

            System.err.println(
                    "Please enter a valid number."
            );

        } finally {

            scanner.close();
        }
    }
}
```

---

# 58. Modern Java Exception Handling

Modern Java applications commonly follow this pattern:

```text
Input
  |
  v
Validate
  |
  v
Business Logic
  |
  +---- Expected Business Problem
  |             |
  |             v
  |       Custom Exception
  |
  +---- Technical Problem
                |
                v
          Technical Exception
                |
                v
        Global Error Handler
                |
                v
          API Error Response
```

---

# 59. Key Points to Remember

Remember these important concepts:

```text
Throwable
   |
   +--> Error
   |
   +--> Exception
```

`Error`:

```text
Usually serious JVM/runtime problem
```

`Exception`:

```text
Usually application-level problem
```

Checked exceptions:

```text
Compiler checks them
```

Unchecked exceptions:

```text
RuntimeException
```

Handling:

```text
try
catch
finally
```

Throwing:

```text
throw
```

Declaring:

```text
throws
```

---

# 60. Final Summary

Java provides a powerful mechanism for dealing with problems during program execution.

The most important concepts are:

```text
Error
Exception
Throwable
RuntimeException
Checked Exception
try
catch
finally
throw
throws
Custom Exception
Exception Propagation
Exception Chaining
Stack Trace
```

The basic structure is:

```java
try {

    // Code that may fail

} catch (Exception e) {

    // Handle error

} finally {

    // Cleanup
}
```

For application-specific problems, create meaningful exceptions:

```java
throw new InsufficientBalanceException(
        "Insufficient balance"
);
```

For Spring Boot applications, centralize API error handling:

```text
Controller
    |
    v
Service
    |
    v
Exception
    |
    v
@RestControllerAdvice
    |
    v
HTTP Error Response
```

The most important rule is:

```text
Don't hide errors.

Understand the problem,
handle what you can,
log what you need,
and return a meaningful response.
```
