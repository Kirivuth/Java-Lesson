# 📘Java Variables

## 1. What Is a Java Variable?

A **variable** in Java is a named location used by a program to store or refer to a value.

You can think of a variable as a **container** that has:

- A name
- A data type
- A value
- A scope
- A lifetime

For example:

```java
int age = 25;
```

Here:

- `int` → data type
- `age` → variable name
- `=` → assignment operator
- `25` → value
- `;` → end of the Java statement

The variable `age` stores the integer value `25`.

### Simple Example

```java
public class Main {

    public static void main(String[] args) {

        int age = 25;

        System.out.println(age);
    }
}
```

Output:

```text
25
```

---

# 2. Why Do We Need Variables?

Variables allow a program to store and manipulate data.

For example, a banking application may need to store:

```java
String customerName = "John";
int accountNumber = 10001;
double balance = 2500.50;
boolean active = true;
```

Without variables, a program would have difficulty working with changing information.

Variables allow us to:

- Store data
- Reuse data
- Change data
- Perform calculations
- Compare values
- Pass values to methods
- Return values from methods
- Temporarily store processing results

For example:

```java
int price = 100;
int quantity = 5;

int total = price * quantity;

System.out.println(total);
```

Output:

```text
500
```

---

# 3. Basic Syntax of a Java Variable

The basic syntax is:

```java
dataType variableName = value;
```

For example:

```java
int age = 30;
```

Another example:

```java
String name = "John";
```

The general structure is:

```text
data type + variable name + assignment operator + value
```

Example:

```java
double salary = 1500.75;
```

| Part      | Meaning             |
| --------- | ------------------- |
| `double`  | Data type           |
| `salary`  | Variable name       |
| `=`       | Assignment operator |
| `1500.75` | Value               |
| `;`       | End of statement    |

---

# 4. Declaring a Variable

Declaring a variable means telling Java that a variable exists and specifying its type.

Example:

```java
int age;
```

At this point, we have declared `age`, but we have not assigned a value to it.

We can assign a value later:

```java
age = 25;
```

Complete example:

```java
public class Main {

    public static void main(String[] args) {

        int age;

        age = 25;

        System.out.println(age);
    }
}
```

Output:

```text
25
```

---

# 5. Initializing a Variable

Initializing a variable means assigning its initial value.

Example:

```java
int age = 25;
```

This statement performs both:

1. Declaration
2. Initialization

You can also separate them:

```java
int age;

age = 25;
```

Both approaches are valid.

Usually, if the initial value is already known, this is preferred:

```java
int age = 25;
```

---

# 6. Declaration vs Initialization vs Assignment

These concepts are related but different.

## Declaration

```java
int age;
```

You tell Java that `age` is an integer variable.

## Initialization

```java
int age = 25;
```

You declare the variable and give it its first value.

## Assignment

```java
age = 30;
```

You assign another value to an existing variable.

Example:

```java
int age = 25;

age = 30;
```

The value changes from:

```text
25
```

to:

```text
30
```

---

# 7. Changing a Variable's Value

A normal variable can be reassigned.

Example:

```java
int age = 25;

age = 26;

System.out.println(age);
```

Output:

```text
26
```

Another example:

```java
double balance = 1000.00;

balance = 1500.00;

System.out.println(balance);
```

Output:

```text
1500.0
```

The previous value is replaced.

---

# 8. Java Variable Types

Java variables can be broadly divided into two categories:

```text
Java Variables
│
├── Primitive variables
│
└── Reference variables
```

Primitive types include:

```text
byte
short
int
long
float
double
char
boolean
```

Reference types include:

```text
String
Array
Class
Interface
Enum
Record
Object
```

---

# 9. Primitive Data Types

Java has eight primitive data types.

| Type      | Description           | Example                     |
| --------- | --------------------- | --------------------------- |
| `byte`    | 8-bit signed integer  | `byte age = 25;`            |
| `short`   | 16-bit signed integer | `short year = 2026;`        |
| `int`     | 32-bit signed integer | `int count = 100;`          |
| `long`    | 64-bit signed integer | `long id = 100000L;`        |
| `float`   | 32-bit floating point | `float price = 10.5F;`      |
| `double`  | 64-bit floating point | `double balance = 1000.50;` |
| `char`    | UTF-16 code unit      | `char grade = 'A';`         |
| `boolean` | Logical value         | `boolean active = true;`    |

---

# 10. int Variables

`int` is the most commonly used integer type in Java.

Example:

```java
int age = 25;
int quantity = 100;
int accountNumber = 12345;
```

Example program:

```java
public class Main {

    public static void main(String[] args) {

        int age = 30;

        System.out.println("Age: " + age);
    }
}
```

Output:

```text
Age: 30
```

An `int` can store values from:

```text
-2,147,483,648
```

to:

```text
2,147,483,647
```

For most normal integer values, `int` is the appropriate choice.

---

# 11. long Variables

Use `long` when an integer value may exceed the range of `int`.

Example:

```java
long transactionId = 9876543210L;
```

Notice the `L` suffix.

```java
long number = 10000000000L;
```

The `L` tells Java that the numeric literal is a `long`.

Example:

```java
public class Main {

    public static void main(String[] args) {

        long transactionId = 9876543210L;

        System.out.println(transactionId);
    }
}
```

Output:

```text
9876543210
```

A `long` can store:

```text
-9,223,372,036,854,775,808
```

to:

```text
9,223,372,036,854,775,807
```

---

# 12. byte Variables

`byte` is an 8-bit signed integer.

Its range is:

```text
-128 to 127
```

Example:

```java
byte age = 25;
byte temperature = -10;
```

Example:

```java
byte value = 100;

System.out.println(value);
```

Output:

```text
100
```

`byte` is useful when:

- Working with binary data
- Working with byte arrays
- Memory usage is important
- APIs specifically require byte values

---

# 13. short Variables

`short` is a 16-bit signed integer.

Its range is:

```text
-32,768 to 32,767
```

Example:

```java
short year = 2026;
```

In typical business applications, `int` is usually more common than `short`.

---

# 14. double Variables

`double` represents a 64-bit floating-point number.

Example:

```java
double balance = 2500.75;
double interestRate = 5.25;
double temperature = 36.5;
```

Example:

```java
public class Main {

    public static void main(String[] args) {

        double balance = 2500.75;

        System.out.println("Balance: " + balance);
    }
}
```

Output:

```text
Balance: 2500.75
```

A `double` provides more precision than a `float`.

---

# 15. float Variables

`float` represents a 32-bit floating-point number.

Example:

```java
float price = 10.5F;
```

Notice the `F` suffix.

This is valid:

```java
float price = 10.5F;
```

This is not normally valid:

```java
float price = 10.5;
```

because decimal literals are `double` by default.

You can explicitly cast:

```java
float price = (float) 10.5;
```

But using:

```java
10.5F
```

is clearer.

---

# 16. Important: Do Not Normally Use double for Money

For financial and banking applications, you should generally avoid using `float` or `double` for exact monetary calculations.

For example:

```java
double amount = 0.1 + 0.2;

System.out.println(amount);
```

The result may be:

```text
0.30000000000000004
```

rather than exactly:

```text
0.3
```

This happens because floating-point numbers use binary floating-point representation.

For financial values, `BigDecimal` is generally preferred.

Example:

```java
import java.math.BigDecimal;

public class Main {

    public static void main(String[] args) {

        BigDecimal amount1 =
                new BigDecimal("0.10");

        BigDecimal amount2 =
                new BigDecimal("0.20");

        BigDecimal total =
                amount1.add(amount2);

        System.out.println(total);
    }
}
```

Output:

```text
0.30
```

For banking systems, accounting systems, payment systems, and financial applications, `BigDecimal` is generally the appropriate choice when exact decimal arithmetic is required.

---

# 17. char Variables

`char` represents a single UTF-16 code unit.

A character is written using single quotes:

```java
char grade = 'A';
```

Examples:

```java
char firstLetter = 'J';
char symbol = '$';
char number = '5';
```

A `char` stores a single character/code unit.

Correct:

```java
char grade = 'A';
```

Incorrect:

```java
char grade = "A";
```

Double quotes are used for strings.

---

# 18. String Variables

`String` is not a primitive type.

It is a reference type representing a sequence of characters.

Example:

```java
String name = "John";
```

Other examples:

```java
String customerName = "John Smith";
String country = "Cambodia";
String message = "Hello Java";
```

Example:

```java
public class Main {

    public static void main(String[] args) {

        String customerName = "John Smith";

        System.out.println(customerName);
    }
}
```

Output:

```text
John Smith
```

Strings use double quotes:

```java
String name = "John";
```

Characters use single quotes:

```java
char firstLetter = 'J';
```

---

# 19. boolean Variables

A `boolean` represents a logical value.

It can contain:

```text
true
false
```

Example:

```java
boolean active = true;
boolean completed = false;
boolean authenticated = true;
```

Example:

```java
public class Main {

    public static void main(String[] args) {

        boolean accountActive = true;

        System.out.println(accountActive);
    }
}
```

Output:

```text
true
```

Boolean variables are commonly used in conditions.

Example:

```java
boolean authenticated = true;

if (authenticated) {

    System.out.println("User is authenticated");
}
```

Output:

```text
User is authenticated
```

---

# 20. Reference Variables

A reference variable holds a reference to an object.

For example:

```java
String name = "John";
```

`name` is a reference variable.

Another example:

```java
Customer customer = new Customer();
```

Here:

```text
Customer
```

is the type.

```text
customer
```

is the reference variable.

```text
new Customer()
```

creates an object.

Example:

```java
class Customer {

    String name;
}

public class Main {

    public static void main(String[] args) {

        Customer customer = new Customer();

        customer.name = "John";

        System.out.println(customer.name);
    }
}
```

Output:

```text
John
```

---

# 21. null and Reference Variables

Reference variables can contain `null`.

Example:

```java
String name = null;
```

`null` means the reference does not currently refer to an object.

You can check it:

```java
if (name == null) {

    System.out.println("Name is not available");
}
```

Output:

```text
Name is not available
```

Primitive variables cannot contain `null`.

This is invalid:

```java
int age = null;
```

---

# 22. Variable Naming Rules

Java has specific rules for variable names.

A variable name:

- Can contain letters
- Can contain digits
- Can contain `_`
- Can contain `$`
- Cannot start with a digit
- Cannot be a Java keyword
- Is case-sensitive

### Valid Names

```java
int age;
int customerAge;
int customer_age;
int age2;
int $value;
int _value;
```

### Invalid Names

```java
int 2age;
int customer-age;
int customer age;
int class;
```

---

# 23. Java Is Case-Sensitive

Java treats uppercase and lowercase letters as different.

These are three different variables:

```java
int age = 20;
int Age = 30;
int AGE = 40;
```

Example:

```java
System.out.println(age);
System.out.println(Age);
System.out.println(AGE);
```

Output:

```text
20
30
40
```

However, creating names that differ only by capitalization is usually a bad practice because it makes code harder to read.

---

# 24. Java Variable Naming Convention

Java normally uses **camelCase** for variables.

Recommended:

```java
int customerAge;
String customerName;
double accountBalance;
boolean accountActive;
```

Avoid:

```java
int CustomerAge;
String CUSTOMER_NAME;
double account_balance;
```

The Java naming convention is:

```text
variableName
customerName
accountBalance
transactionAmount
```

For constants, uppercase with underscores is commonly used:

```java
MAX_RETRY
DEFAULT_CURRENCY
MAX_CONNECTIONS
```

---

# 25. Local Variables

A local variable is declared inside:

- A method
- A constructor
- A block

Example:

```java
public class Main {

    public static void main(String[] args) {

        int age = 25;

        System.out.println(age);
    }
}
```

`age` is a local variable.

Its scope is limited to the method/block where it is declared.

---

# 26. Local Variables Must Be Initialized

Local variables do not automatically receive a default value.

This code is invalid:

```java
public class Main {

    public static void main(String[] args) {

        int age;

        System.out.println(age);
    }
}
```

Java reports a compilation error because `age` might not have been initialized.

Correct:

```java
int age = 25;

System.out.println(age);
```

Or:

```java
int age;

age = 25;

System.out.println(age);
```

---

# 27. Instance Variables

An instance variable is declared inside a class but outside methods, constructors, and blocks.

Example:

```java
class Customer {

    String name;
    int age;
}
```

Here:

```java
String name;
int age;
```

are instance variables.

Each object has its own instance variables.

Example:

```java
class Customer {

    String name;
    int age;
}

public class Main {

    public static void main(String[] args) {

        Customer customer1 = new Customer();

        customer1.name = "John";
        customer1.age = 30;

        Customer customer2 = new Customer();

        customer2.name = "David";
        customer2.age = 25;

        System.out.println(customer1.name);
        System.out.println(customer2.name);
    }
}
```

Output:

```text
John
David
```

Each object has its own `name` and `age`.

---

# 28. Instance Variable Default Values

Unlike local variables, instance variables receive default values.

For example:

```java
class Customer {

    String name;
    int age;
    boolean active;
    double balance;
}
```

If a new object is created:

```java
Customer customer = new Customer();
```

The fields initially have default values.

Conceptually:

```text
name    → null
age     → 0
active  → false
balance → 0.0
```

This is different from local variables.

---

# 29. Static Variables

A `static` variable belongs to the class rather than to an individual object.

Example:

```java
class Customer {

    static String bankName = "ABC Bank";

    String name;
}
```

You can access it using the class:

```java
System.out.println(Customer.bankName);
```

Example:

```java
class Customer {

    static String bankName = "ABC Bank";

    String name;
}

public class Main {

    public static void main(String[] args) {

        Customer customer1 = new Customer();
        customer1.name = "John";

        Customer customer2 = new Customer();
        customer2.name = "David";

        System.out.println(Customer.bankName);
    }
}
```

Output:

```text
ABC Bank
```

The `bankName` field is shared by instances of the class.

---

# 30. Local vs Instance vs Static Variables

| Variable | Declared                      | Belongs To             | Example             |
| -------- | ----------------------------- | ---------------------- | ------------------- |
| Local    | Inside method/block           | Method/block execution | `int age = 25;`     |
| Instance | Inside class, outside methods | Object                 | `String name;`      |
| Static   | Inside class with `static`    | Class                  | `static int count;` |

Example:

```java
class Customer {

    static String bankName = "ABC Bank";

    String name;

    void printCustomer() {

        int age = 30;

        System.out.println(bankName);
        System.out.println(name);
        System.out.println(age);
    }
}
```

Here:

```java
bankName
```

is a static variable.

```java
name
```

is an instance variable.

```java
age
```

is a local variable.

---

# 31. Constants

A constant is a variable whose reference/value cannot be reassigned after initialization.

Java uses the `final` keyword.

Example:

```java
final int MAX_RETRY = 3;
```

This is not allowed:

```java
MAX_RETRY = 5;
```

because `MAX_RETRY` is `final`.

Example:

```java
public class Main {

    public static void main(String[] args) {

        final int MAX_RETRY = 3;

        System.out.println(MAX_RETRY);
    }
}
```

---

# 32. Class Constants

A common pattern is:

```java
public static final
```

Example:

```java
public class BankConfig {

    public static final int MAX_RETRY = 3;

    public static final String DEFAULT_CURRENCY = "USD";
}
```

Usage:

```java
System.out.println(BankConfig.MAX_RETRY);
System.out.println(BankConfig.DEFAULT_CURRENCY);
```

Output:

```text
3
USD
```

---

# 33. Important Point About final and Objects

For primitive variables:

```java
final int age = 25;
```

The value cannot be reassigned.

For reference variables:

```java
final Customer customer = new Customer();
```

The reference cannot be reassigned:

```java
customer = new Customer();
```

This is not allowed.

However, if the object itself is mutable, its internal state may still change.

Example:

```java
final Customer customer = new Customer();

customer.name = "John";
```

This can be valid.

So:

```text
final reference
     ↓
cannot point to another object

but

object state
     ↓
may still be mutable
```

`final` does not automatically make an object immutable.

---

# 34. var in Java

Java supports local variable type inference using `var`.

Example:

```java
var age = 25;
var name = "John";
var balance = 1000.50;
```

The compiler determines the types.

For example:

```java
var age = 25;
```

is inferred as:

```java
int
```

And:

```java
var name = "John";
```

is inferred as:

```java
String
```

`var` was introduced in Java 10 and is available in Java 21.

---

# 35. var Is Still Statically Typed

`var` does not make Java dynamically typed.

Example:

```java
var age = 25;
```

Java knows that `age` is an `int`.

Therefore:

```java
age = "John";
```

is invalid.

The compiler knows the type of `age`.

Conceptually:

```text
var age = 25;

        ↓

int age = 25;
```

The compiler infers the type.

---

# 36. var Must Have an Initializer

This is invalid:

```java
var age;
```

Java cannot determine the type.

Correct:

```java
var age = 25;
```

Another example:

```java
var customer = new Customer();
```

The compiler knows that:

```text
customer → Customer
```

---

# 37. Where Can var Be Used?

`var` is intended for local variable declarations.

Valid:

```java
public void process() {

    var amount = 100;

}
```

Valid in loops:

```java
for (var i = 0; i < 10; i++) {

    System.out.println(i);
}
```

Valid in try-with-resources:

```java
try (var input = new java.io.FileInputStream("data.txt")) {

    // use input
}
```

But you cannot use `var` as a field type:

```java
class Customer {

    var name = "John";
}
```

This is invalid.

You also cannot use it as a method parameter:

```java
public void process(var amount) {
}
```

Or as a return type:

```java
public var getName() {
    return "John";
}
```

---

# 38. var vs Explicit Type

Both are valid:

```java
int age = 25;
```

and:

```java
var age = 25;
```

The first explicitly tells the reader the type.

The second allows the compiler to infer it.

A good use of `var` is when the type is obvious:

```java
var customer = new Customer();
```

It is obvious that `customer` is a `Customer`.

Another example:

```java
var customers = new ArrayList<Customer>();
```

The type is clear from the initializer.

However, if the type provides important information, explicit typing can sometimes improve readability:

```java
BigDecimal accountBalance = calculateBalance();
```

---

# 39. Assignment Operator

The basic assignment operator is:

```java
=
```

Example:

```java
int age = 25;
```

The expression:

```java
age = 30;
```

assigns `30` to `age`.

Assignment is different from equality comparison.

Assignment:

```java
age = 30;
```

Comparison:

```java
age == 30
```

---

# 40. Compound Assignment Operators

Java provides several compound assignment operators.

| Operator | Example  | Equivalent  |
| -------- | -------- | ----------- |
| `=`      | `x = 10` | `x = 10`    |
| `+=`     | `x += 5` | `x = x + 5` |
| `-=`     | `x -= 5` | `x = x - 5` |
| `*=`     | `x *= 5` | `x = x * 5` |
| `/=`     | `x /= 5` | `x = x / 5` |
| `%=`     | `x %= 5` | `x = x % 5` |

Example:

```java
int balance = 100;

balance += 50;

System.out.println(balance);
```

Output:

```text
150
```

---

# 41. Increment Operator

Java provides:

```java
++
```

Example:

```java
int count = 10;

count++;

System.out.println(count);
```

Output:

```text
11
```

This is equivalent to:

```java
count = count + 1;
```

---

# 42. Decrement Operator

Java provides:

```java
--
```

Example:

```java
int count = 10;

count--;

System.out.println(count);
```

Output:

```text
9
```

This is equivalent to:

```java
count = count - 1;
```

---

# 43. Pre-Increment

Pre-increment:

```java
++count
```

The variable is incremented before its value is used.

Example:

```java
int count = 10;

int result = ++count;

System.out.println(count);
System.out.println(result);
```

Output:

```text
11
11
```

---

# 44. Post-Increment

Post-increment:

```java
count++
```

The original value is used first, and then the variable is incremented.

Example:

```java
int count = 10;

int result = count++;

System.out.println(count);
System.out.println(result);
```

Output:

```text
11
10
```

---

# 45. Pre-Decrement

Example:

```java
int count = 10;

int result = --count;

System.out.println(count);
System.out.println(result);
```

Output:

```text
9
9
```

---

# 46. Post-Decrement

Example:

```java
int count = 10;

int result = count--;

System.out.println(count);
System.out.println(result);
```

Output:

```text
9
10
```

---

# 47. Variable Scope

Variable scope defines where a variable can be accessed.

Example:

```java
public class Main {

    public static void main(String[] args) {

        int age = 25;

        if (age >= 18) {

            String message = "Adult";

            System.out.println(message);
        }

        // message cannot be accessed here
    }
}
```

`message` exists only inside the `if` block.

---

# 48. Block Scope

A block is defined by:

```java
{
    // block
}
```

Example:

```java
public class Main {

    public static void main(String[] args) {

        int age = 25;

        {
            int number = 100;

            System.out.println(number);
        }

        // number is not accessible here
    }
}
```

The variable `number` has block scope.

---

# 49. Variable Lifetime

Variable scope and variable lifetime are related but not identical.

### Local variable

A local variable exists during execution of the relevant method/block.

### Instance variable

An instance variable is part of an object and exists while that object is reachable and eventually until it becomes eligible for garbage collection.

### Static variable

A static variable belongs to the class and is associated with the class's lifetime within the JVM.

Understanding scope and lifetime becomes important when working with:

- Object-oriented programming
- Memory management
- Threads
- Collections
- Application architecture

---

# 50. Primitive vs Reference Variables

Consider:

```java
int age = 25;
```

`age` is a primitive variable.

Now:

```java
String name = "John";
```

`name` is a reference variable.

A simplified conceptual model is:

```text
Primitive:

age
 ↓
25
```

Reference:

```text
name
 ↓
String object
 ↓
"John"
```

This distinction is important when learning:

- Classes
- Objects
- Arrays
- Collections
- `null`
- Method parameters
- Object identity
- Memory management

---

# 51. Type Conversion

Java supports conversion between compatible numeric types.

There are two major categories:

```text
Widening conversion
Narrowing conversion
```

---

# 52. Widening Conversion

Widening conversion occurs when a smaller numeric type is converted to a larger compatible type.

Example:

```java
int age = 25;

long value = age;
```

Java automatically performs the conversion.

Another example:

```java
int number = 10;

double value = number;

System.out.println(value);
```

Output:

```text
10.0
```

A simplified widening path is:

```text
byte
  ↓
short
  ↓
int
  ↓
long
  ↓
float
  ↓
double
```

Note that this diagram is conceptual; not every conversion has identical precision characteristics.

---

# 53. Narrowing Conversion

Narrowing conversion converts a larger type to a smaller type.

An explicit cast is usually required.

Example:

```java
double amount = 100.75;

int value = (int) amount;

System.out.println(value);
```

Output:

```text
100
```

The fractional part is discarded.

Another example:

```java
long number = 1000L;

int value = (int) number;
```

Be careful because narrowing conversion can result in data loss or overflow.

---

# 54. Variable in Expressions

Variables can be used in mathematical expressions.

Example:

```java
int quantity = 5;
double price = 10.50;

double total = quantity * price;

System.out.println(total);
```

Output:

```text
52.5
```

Another example:

```java
int a = 10;
int b = 20;

int sum = a + b;

System.out.println(sum);
```

Output:

```text
30
```

---

# 55. Variables and Conditions

Variables can be used with `if` statements.

Example:

```java
int age = 25;

if (age >= 18) {

    System.out.println("Adult");
}
```

Another example:

```java
boolean active = true;

if (active) {

    System.out.println("Account is active");
}
```

---

# 56. Variables and Loops

Variables are commonly used in loops.

Example:

```java
for (int i = 0; i < 5; i++) {

    System.out.println(i);
}
```

Output:

```text
0
1
2
3
4
```

Here:

```java
int i = 0;
```

declares and initializes a loop variable.

---

# 57. Variables and Methods

Variables can be passed to methods.

Example:

```java
public class Main {

    static void printCustomer(String name) {

        System.out.println("Customer: " + name);
    }

    public static void main(String[] args) {

        String customerName = "John";

        printCustomer(customerName);
    }
}
```

Output:

```text
Customer: John
```

The value stored in:

```java
customerName
```

is passed to the method parameter:

```java
name
```

---

# 58. Method Parameters Are Variables

Consider:

```java
public static void transfer(double amount) {

    System.out.println(amount);
}
```

Here:

```java
amount
```

is a method parameter.

You can call:

```java
transfer(1000.00);
```

For financial applications:

```java
public static void transfer(BigDecimal amount) {

    System.out.println("Transfer amount: " + amount);
}
```

---

# 59. Variable Return Values

Methods can calculate values and return them.

Example:

```java
public static int add(int a, int b) {

    int result = a + b;

    return result;
}
```

Usage:

```java
int total = add(10, 20);

System.out.println(total);
```

Output:

```text
30
```

Here:

```text
a
b
result
total
```

are all variables or parameters.

---

# 60. Effectively Final Variables

A local variable is **effectively final** when it is assigned once and never reassigned after initialization.

Example:

```java
String name = "John";

Runnable task = () -> {

    System.out.println(name);
};
```

`name` can be used inside the lambda because it is effectively final.

If you reassign it:

```java
String name = "John";

name = "David";
```

then it is no longer effectively final and cannot be captured by a lambda in the same way.

Example:

```java
String name = "John";

name = "David";

Runnable task = () -> {

    System.out.println(name);
};
```

This results in a compilation error.

---

# 61. final vs Effectively Final

### Explicitly final

```java
final String name = "John";
```

### Effectively final

```java
String name = "John";
```

If `name` is never reassigned, it is effectively final.

Both can be captured by lambdas.

---

# 62. Variable Shadowing

Variable shadowing occurs when a variable in an inner scope has the same name as a variable in an outer scope.

Example:

```java
class Customer {

    String name;

    void print() {

        String name = "Local John";

        System.out.println(name);
    }
}
```

The local variable:

```java
name
```

shadows the instance variable.

To access the instance variable, use:

```java
this.name
```

Example:

```java
class Customer {

    String name = "Customer Name";

    void print() {

        String name = "Local Name";

        System.out.println(name);
        System.out.println(this.name);
    }
}
```

Output:

```text
Local Name
Customer Name
```

---

# 63. Variables and this

Inside an instance method, `this` refers to the current object.

Example:

```java
class Customer {

    private String name;

    public Customer(String name) {

        this.name = name;
    }

    public void printName() {

        System.out.println(this.name);
    }
}
```

Here:

```java
this.name
```

refers to the instance variable.

While:

```java
name
```

in the constructor refers to the parameter.

---

# 64. Variables and Objects

Example:

```java
Customer customer = new Customer();
```

This statement contains:

```text
Customer
   ↓
type

customer
   ↓
reference variable

new Customer()
   ↓
object creation
```

This concept is fundamental to Java object-oriented programming.

---

# 65. Example: Banking Customer

```java
class Customer {

    String customerId;
    String customerName;
    boolean active;
}
```

Create an object:

```java
Customer customer = new Customer();

customer.customerId = "C001";
customer.customerName = "John Smith";
customer.active = true;
```

Print:

```java
System.out.println(customer.customerId);
System.out.println(customer.customerName);
System.out.println(customer.active);
```

Output:

```text
C001
John Smith
true
```

---

# 66. Example: Banking Transaction

For a banking system, a transaction may contain variables such as:

```java
String transactionId;
String accountNumber;
BigDecimal amount;
String currency;
boolean successful;
```

Example:

```java
import java.math.BigDecimal;

public class Main {

    public static void main(String[] args) {

        String transactionId = "FT000123";
        String accountNumber = "00123456789";
        BigDecimal amount = new BigDecimal("750.00");
        String currency = "USD";
        boolean successful = true;

        System.out.println("Transaction: " + transactionId);
        System.out.println("Account: " + accountNumber);
        System.out.println("Amount: " + amount);
        System.out.println("Currency: " + currency);
        System.out.println("Successful: " + successful);
    }
}
```

Output:

```text
Transaction: FT000123
Account: 00123456789
Amount: 750.00
Currency: USD
Successful: true
```

---

# 67. Example: Banking Balance Calculation

For exact monetary calculations, use `BigDecimal`.

```java
import java.math.BigDecimal;

public class Main {

    public static void main(String[] args) {

        BigDecimal openingBalance =
                new BigDecimal("5000.00");

        BigDecimal deposit =
                new BigDecimal("1000.00");

        BigDecimal withdrawal =
                new BigDecimal("750.00");

        BigDecimal balance =
                openingBalance
                        .add(deposit)
                        .subtract(withdrawal);

        System.out.println(
                "Final Balance: " + balance
        );
    }
}
```

Output:

```text
Final Balance: 5250.00
```

---

# 68. Example: Banking Account

```java
import java.math.BigDecimal;

public class BankAccount {

    private final String accountNumber;

    private String customerName;

    private BigDecimal balance;

    private boolean active;

    public BankAccount(
            String accountNumber,
            String customerName,
            BigDecimal balance) {

        this.accountNumber = accountNumber;
        this.customerName = customerName;
        this.balance = balance;
        this.active = true;
    }

    public void deposit(BigDecimal amount) {

        balance = balance.add(amount);
    }

    public BigDecimal getBalance() {

        return balance;
    }
}
```

Here we have several different variables:

```java
accountNumber
customerName
balance
active
amount
```

Their purposes are different:

| Variable        | Type         | Purpose            |
| --------------- | ------------ | ------------------ |
| `accountNumber` | `String`     | Account identifier |
| `customerName`  | `String`     | Customer name      |
| `balance`       | `BigDecimal` | Monetary balance   |
| `active`        | `boolean`    | Account status     |
| `amount`        | `BigDecimal` | Transaction amount |

---

# 69. Common Mistake: Uninitialized Local Variable

Incorrect:

```java
public static void main(String[] args) {

    int age;

    System.out.println(age);
}
```

Correct:

```java
public static void main(String[] args) {

    int age = 25;

    System.out.println(age);
}
```

Remember:

```text
Local variables
      ↓
must be definitely assigned before use
```

---

# 70. Common Mistake: Wrong Data Type

Incorrect:

```java
int age = "25";
```

The value `"25"` is a `String`.

Correct:

```java
int age = 25;
```

Or:

```java
String age = "25";
```

depending on the requirement.

---

# 71. Common Mistake: String vs char

Incorrect:

```java
char grade = "A";
```

Correct:

```java
char grade = 'A';
```

For a string:

```java
String grade = "A";
```

Remember:

```text
char   → single quotes
String → double quotes
```

---

# 72. Common Mistake: Changing final Variables

Incorrect:

```java
final int MAX_RETRY = 3;

MAX_RETRY = 5;
```

Correct:

```java
final int MAX_RETRY = 3;

System.out.println(MAX_RETRY);
```

A `final` variable cannot be reassigned.

---

# 73. Common Mistake: Using double for Money

Avoid:

```java
double balance = 1000.10;
```

when exact monetary arithmetic is required.

Prefer:

```java
BigDecimal balance =
        new BigDecimal("1000.10");
```

Also avoid constructing `BigDecimal` from a binary floating-point value when exact decimal input is intended:

```java
new BigDecimal(0.1);
```

Prefer:

```java
new BigDecimal("0.1");
```

or:

```java
BigDecimal.valueOf(0.1);
```

---

# 74. Common Mistake: Bad Variable Names

Bad:

```java
int x = 25;
String s = "John";
double b = 1000;
```

Better:

```java
int customerAge = 25;
String customerName = "John";
BigDecimal accountBalance =
        new BigDecimal("1000.00");
```

Meaningful names make code easier to understand and maintain.

---

# 75. Best Practice: Use Meaningful Names

Bad:

```java
int x;
```

Better:

```java
int customerAge;
```

Bad:

```java
String s;
```

Better:

```java
String customerName;
```

Bad:

```java
BigDecimal a;
```

Better:

```java
BigDecimal transactionAmount;
```

---

# 76. Best Practice: Follow camelCase

Recommended:

```java
String customerName;
String accountNumber;
BigDecimal accountBalance;
BigDecimal transactionAmount;
boolean accountActive;
```

Avoid:

```java
String CustomerName;
String CUSTOMERNAME;
String customer_name;
```

The normal Java convention for variables is **camelCase**.

---

# 77. Best Practice: Use final Where Appropriate

If a local variable should not be reassigned:

```java
final String currency = "USD";
```

If a class-level constant should be shared:

```java
public static final String DEFAULT_CURRENCY = "USD";
```

Using `final` can make the intended behavior clearer and prevent accidental reassignment.

---

# 78. Best Practice: Keep Scope Small

Prefer declaring a variable close to where it is used.

Instead of:

```java
public void process() {

    String customerName;
    BigDecimal amount;
    boolean active;

    // many lines...

    customerName = getCustomerName();

    // many more lines...

    amount = getAmount();

    // ...
}
```

Prefer:

```java
public void process() {

    String customerName = getCustomerName();

    System.out.println(customerName);

    BigDecimal amount = getAmount();

    System.out.println(amount);
}
```

Keeping variables close to their usage improves readability.

---

# 79. Best Practice: Choose the Correct Type

Choose a type based on the meaning of the data.

Example:

```java
int quantity;
```

For a large identifier:

```java
long transactionId;
```

For text:

```java
String customerName;
```

For true/false:

```java
boolean active;
```

For exact decimal money:

```java
BigDecimal amount;
```

Good type selection improves correctness and communicates intent.

---

# 80. Java Variable Cheat Sheet

```java
// Integer
int age = 25;

// Large integer
long transactionId = 9876543210L;

// Small integer
byte value = 100;

// Short integer
short year = 2026;

// Decimal
double temperature = 36.5;

// Float
float rate = 5.5F;

// Character
char grade = 'A';

// Boolean
boolean active = true;

// String
String name = "John";

// Reference object
Customer customer = new Customer();

// Type inference
var count = 100;

// Constant
final int MAX_RETRY = 3;

// Financial value
BigDecimal balance =
        new BigDecimal("1000.50");
```

---

# 81. Complete Java Variables Example

```java
import java.math.BigDecimal;

public class Main {

    public static void main(String[] args) {

        // Customer information
        String customerName = "John Smith";
        String accountNumber = "00123456789";

        // Account information
        BigDecimal openingBalance =
                new BigDecimal("5000.00");

        BigDecimal deposit =
                new BigDecimal("1000.00");

        BigDecimal withdrawal =
                new BigDecimal("750.00");

        // Account status
        boolean accountActive = true;

        // Constant
        final String CURRENCY = "USD";

        // Calculate balance
        BigDecimal balance =
                openingBalance
                        .add(deposit)
                        .subtract(withdrawal);

        if (accountActive) {

            System.out.println(
                    "Customer: " + customerName
            );

            System.out.println(
                    "Account: " + accountNumber
            );

            System.out.println(
                    "Currency: " + CURRENCY
            );

            System.out.println(
                    "Opening Balance: " + openingBalance
            );

            System.out.println(
                    "Deposit: " + deposit
            );

            System.out.println(
                    "Withdrawal: " + withdrawal
            );

            System.out.println(
                    "Final Balance: " + balance
            );
        }
    }
}
```

Output:

```text
Customer: John Smith
Account: 00123456789
Currency: USD
Opening Balance: 5000.00
Deposit: 1000.00
Withdrawal: 750.00
Final Balance: 5250.00
```

---

# 82. Variable Declaration Summary

The following are all valid examples:

```java
int age = 25;

long transactionId = 123456789L;

double percentage = 95.5;

float rate = 5.25F;

char grade = 'A';

boolean active = true;

String customerName = "John";

BigDecimal amount =
        new BigDecimal("1000.50");
```

---

# 83. Variable Categories Summary

Java variables can be understood as:

```text
Variables
│
├── Local Variables
│
├── Instance Variables
│
└── Static Variables
```

And by type:

```text
Variables
│
├── Primitive
│   ├── byte
│   ├── short
│   ├── int
│   ├── long
│   ├── float
│   ├── double
│   ├── char
│   └── boolean
│
└── Reference
    ├── String
    ├── Array
    ├── Class
    ├── Interface
    ├── Enum
    └── Record
```

---

# 84. Key Points to Remember

A Java variable:

1. Has a name.
2. Has a type.
3. Can hold or refer to a value.
4. Has a scope.
5. Has a lifetime.
6. Can normally be reassigned unless declared `final`.
7. Can be primitive or reference-based.
8. Must follow Java naming rules.
9. Should normally use camelCase.
10. Should use an appropriate data type.

---

# 85. Important Differences

## Local Variable

```java
void process() {

    int age = 25;
}
```

- Exists inside a method/block
- Must be initialized before use
- Has local scope

## Instance Variable

```java
class Customer {

    String name;
}
```

- Belongs to an object
- Receives a default value
- Each object normally has its own copy

## Static Variable

```java
class Customer {

    static int count;
}
```

- Belongs to the class
- Shared among instances of that class

## Constant

```java
static final int MAX_RETRY = 3;
```

- Cannot be reassigned
- Commonly used for fixed configuration values

---

# 86. Practice Exercises

## Exercise 1: Customer Variables

Create variables for:

- Customer ID
- Customer name
- Customer age
- Account number
- Account balance
- Account status

Example:

```java
String customerId = "C001";
String customerName = "John Smith";
int customerAge = 30;
String accountNumber = "00123456789";
BigDecimal accountBalance =
        new BigDecimal("5000.00");
boolean accountActive = true;
```

Print all values.

---

## Exercise 2: Product Calculation

Create:

```java
int quantity = 10;
double price = 25.50;
```

Calculate:

```text
total = quantity × price
```

Expected output:

```text
Total: 255.0
```

---

## Exercise 3: Balance Calculation

Create:

```java
int balance = 1000;
```

Then:

1. Add `500`
2. Subtract `200`
3. Print the final balance

Expected result:

```text
Final balance: 1300
```

---

## Exercise 4: Constants

Create:

```java
final double TAX_RATE = 0.10;
```

Then:

```java
double amount = 1000;
```

Calculate the tax.

Expected:

```text
Tax: 100.0
```

---

## Exercise 5: BigDecimal Banking Calculation

Create:

```text
Opening balance = 5000.00
Deposit = 1000.00
Withdrawal = 750.00
```

Calculate:

```text
Final balance = 5250.00
```

Use:

```java
BigDecimal
```

instead of:

```java
double
```

---

## Exercise 6: var

Create the following using `var`:

```java
var name = "John";
var age = 30;
var active = true;
var balance = 1000.50;
```

Determine the inferred type of each variable.

Expected:

```text
name    → String
age     → int
active  → boolean
balance → double
```

---

# 87. Interview Questions

## Question 1

### What is a variable in Java?

A variable is a named storage location or reference that allows a Java program to work with data.

Example:

```java
int age = 25;
```

---

## Question 2

### What are the eight primitive data types in Java?

```text
byte
short
int
long
float
double
char
boolean
```

---

## Question 3

### What is the difference between int and long?

`int` is a 32-bit signed integer.

`long` is a 64-bit signed integer.

Example:

```java
int count = 100;

long transactionId = 9876543210L;
```

---

## Question 4

### What is the difference between float and double?

Both represent floating-point values, but `double` provides greater precision and is the usual floating-point type.

Example:

```java
float rate = 5.5F;

double amount = 1000.50;
```

---

## Question 5

### Can a local variable be used without initialization?

No.

Example:

```java
int age;

System.out.println(age);
```

This causes a compilation error because the local variable has not been definitely assigned.

---

## Question 6

### Do instance variables need to be initialized?

They do not need explicit initialization before an object is created because Java assigns default values to instance fields.

For example:

```java
class Customer {

    int age;
    String name;
    boolean active;
}
```

Default values are approximately:

```text
age    → 0
name   → null
active → false
```

---

## Question 7

### What does final mean?

`final` prevents a variable from being reassigned after it has been initialized.

Example:

```java
final int MAX_RETRY = 3;
```

This is invalid:

```java
MAX_RETRY = 5;
```

---

## Question 8

### What is var?

`var` provides local variable type inference.

Example:

```java
var age = 25;
```

The compiler infers:

```java
int
```

`var` does not make Java dynamically typed.

---

## Question 9

### Can var be used for a class field?

No.

Invalid:

```java
class Customer {

    var name = "John";
}
```

`var` is used for local variable declarations.

---

## Question 10

### Can var be used without an initializer?

No.

Invalid:

```java
var age;
```

Correct:

```java
var age = 25;
```

---

## Question 11

### What is the difference between primitive and reference variables?

Primitive variables represent primitive values such as:

```java
int age = 25;
```

Reference variables refer to objects:

```java
String name = "John";
```

---

## Question 12

### Can primitive variables contain null?

No.

Invalid:

```java
int age = null;
```

Reference variables can contain `null`:

```java
String name = null;
```

---

## Question 13

### What is variable scope?

Variable scope defines the part of the program where a variable can be accessed.

Example:

```java
if (true) {

    int value = 100;

    System.out.println(value);
}
```

`value` is accessible inside that block.

---

## Question 14

### What is variable shadowing?

Variable shadowing occurs when a variable in an inner scope has the same name as a variable in an outer scope.

Example:

```java
class Customer {

    String name;

    void print() {

        String name = "John";

        System.out.println(name);
        System.out.println(this.name);
    }
}
```

---

## Question 15

### What type should generally be used for monetary calculations?

When exact decimal arithmetic is required, use:

```java
BigDecimal
```

Example:

```java
BigDecimal amount =
        new BigDecimal("1000.50");
```

Avoid relying on `float` or `double` for exact monetary calculations.

---

# 88. Learning Roadmap

Variables are one of the foundations of Java programming.

A recommended learning sequence is:

```text
Java Variables
       ↓
Java Data Types
       ↓
Java Operators
       ↓
Java Type Casting
       ↓
Java Input / Output
       ↓
Java if / else
       ↓
Java switch
       ↓
Java Loops
       ↓
Java Methods
       ↓
Java Arrays
       ↓
Java Strings
       ↓
Java Classes & Objects
       ↓
Constructors
       ↓
Encapsulation
       ↓
Inheritance
       ↓
Polymorphism
       ↓
Abstraction
       ↓
Interfaces
       ↓
Collections
       ↓
Generics
       ↓
Exceptions
       ↓
Streams
       ↓
Concurrency
       ↓
Modern Java / Java 21
```

---

# 89. Final Summary

The most important concept is:

```java
int age = 25;
```

This statement tells Java:

```text
int
 ↓
The type is integer

age
 ↓
The variable name

=
 ↓
Assign a value

25
 ↓
The value
```

Java variables can represent many kinds of data:

```java
int age = 30;

long transactionId = 123456789L;

double percentage = 95.5;

float rate = 5.5F;

char grade = 'A';

boolean active = true;

String customerName = "John";

BigDecimal balance =
        new BigDecimal("5000.00");
```

For professional Java development, especially enterprise and banking applications, focus on these principles:

```text
Choose the correct data type
          ↓
Use meaningful names
          ↓
Follow camelCase
          ↓
Keep variable scope small
          ↓
Use final when appropriate
          ↓
Use BigDecimal for exact monetary calculations
          ↓
Understand primitive vs reference types
          ↓
Understand local vs instance vs static variables
```

Once you understand Java variables, you have the foundation needed to learn **Java data types, operators, conditions, loops, methods, classes, and object-oriented programming**.
