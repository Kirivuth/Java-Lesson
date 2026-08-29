# 📘 Java Data Types

## 1. What Are Java Data Types?

A **data type** tells Java what kind of data a variable can store or refer to.

For example:

```java
int age = 25;
```

Here:

```text
int
 ↓
Data type

age
 ↓
Variable name

25
 ↓
Value
```

The `int` data type tells Java that `age` is an integer variable.

Another example:

```java
String customerName = "John";
```

Here:

```text
String
 ↓
Data type

customerName
 ↓
Variable name

"John"
 ↓
Value
```

Data types are fundamental to Java because Java is a **statically typed language**.

This means that the type of a variable is known at compile time.

---

# 2. Why Are Data Types Important?

Data types help Java determine:

- What kind of value a variable can contain
- How the value should be interpreted
- What operations can be performed
- How much memory is required
- What conversions are allowed
- What methods are available for an object

For example:

```java
int quantity = 10;
```

You can perform:

```java
int total = quantity * 5;
```

But this is invalid:

```java
int quantity = "ten";
```

because `"ten"` is a `String`, not an `int`.

---

# 3. Java Data Type Categories

Java data types can broadly be divided into two categories:

```text
Java Data Types
│
├── Primitive Data Types
│
└── Reference Data Types
```

Primitive types:

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

# 4. Primitive Data Types

Java has exactly **8 primitive data types**.

They are:

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

They can be grouped as follows:

```text
Primitive Types
│
├── Integer Types
│   ├── byte
│   ├── short
│   ├── int
│   └── long
│
├── Floating-Point Types
│   ├── float
│   └── double
│
├── Character Type
│   └── char
│
└── Boolean Type
    └── boolean
```

---

# 5. Primitive Data Type Summary

| Type      |          Size | Approximate Range / Values   | Example             |
| --------- | ------------: | ---------------------------- | ------------------- |
| `byte`    |         8-bit | -128 to 127                  | `byte x = 10;`      |
| `short`   |        16-bit | -32,768 to 32,767            | `short x = 1000;`   |
| `int`     |        32-bit | -2³¹ to 2³¹-1                | `int x = 100000;`   |
| `long`    |        64-bit | -2⁶³ to 2⁶³-1                | `long x = 100000L;` |
| `float`   |        32-bit | Approx. 6-7 decimal digits   | `float x = 10.5F;`  |
| `double`  |        64-bit | Approx. 15-16 decimal digits | `double x = 10.5;`  |
| `char`    |        16-bit | `\u0000` to `\uFFFF`         | `char x = 'A';`     |
| `boolean` | JVM-dependent | `true` or `false`            | `boolean x = true;` |

---

# 6. byte Data Type

The `byte` data type is an 8-bit signed integer.

Its range is:

```text
-128 to 127
```

Example:

```java
byte age = 25;
byte temperature = -10;
byte value = 100;
```

Example program:

```java
public class Main {

    public static void main(String[] args) {

        byte value = 100;

        System.out.println(value);
    }
}
```

Output:

```text
100
```

---

# 7. byte Overflow

A `byte` cannot store a value greater than `127`.

This is invalid:

```java
byte value = 128;
```

You can see overflow behavior when calculations are performed.

Example:

```java
byte value = 127;

value++;

System.out.println(value);
```

Output:

```text
-128
```

The value wraps around because `byte` uses signed two's-complement representation.

---

# 8. When Should You Use byte?

`byte` is commonly useful when working with:

- Binary data
- Network protocols
- File data
- Byte arrays
- Low-level APIs
- Memory-sensitive data structures

Example:

```java
byte[] data = {10, 20, 30, 40};
```

A byte array is very common when processing binary data.

---

# 9. short Data Type

The `short` data type is a 16-bit signed integer.

Its range is:

```text
-32,768 to 32,767
```

Example:

```java
short year = 2026;
short temperature = -100;
```

Example:

```java
public class Main {

    public static void main(String[] args) {

        short year = 2026;

        System.out.println(year);
    }
}
```

Output:

```text
2026
```

In most business applications, `int` is generally preferred over `short` unless there is a specific reason to use `short`.

---

# 10. int Data Type

The `int` data type is a 32-bit signed integer.

Its range is:

```text
-2,147,483,648
```

to:

```text
2,147,483,647
```

Example:

```java
int age = 30;
int quantity = 100;
int accountNumber = 123456;
```

Example:

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

---

# 11. Why int Is Commonly Used

`int` is the default integer type for most ordinary integer calculations.

For example:

```java
int customerCount = 100;
int quantity = 5;
int retryCount = 3;
int month = 8;
```

For most application-level integer values, `int` is a good default.

---

# 12. int Arithmetic

Example:

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

Another example:

```java
int balance = 1000;

balance = balance + 500;

System.out.println(balance);
```

Output:

```text
1500
```

---

# 13. Integer Division

One important characteristic of integer arithmetic is that integer division produces an integer result.

Example:

```java
int a = 10;
int b = 3;

int result = a / b;

System.out.println(result);
```

Output:

```text
3
```

The decimal portion is discarded.

If you need a decimal result:

```java
double result = 10.0 / 3.0;

System.out.println(result);
```

Output:

```text
3.3333333333333335
```

---

# 14. long Data Type

The `long` data type is a 64-bit signed integer.

Its range is:

```text
-9,223,372,036,854,775,808
```

to:

```text
9,223,372,036,854,775,807
```

Example:

```java
long transactionId = 9876543210L;
```

Notice the `L`.

```java
long value = 10000000000L;
```

The `L` tells Java that the literal is a `long`.

---

# 15. Why Use long?

Use `long` when an integer value may exceed the range of `int`.

Examples include:

```java
long transactionId;
long customerId;
long fileSize;
long timestamp;
long recordCount;
```

Example:

```java
long transactionId = 9876543210L;

System.out.println(transactionId);
```

Output:

```text
9876543210
```

---

# 16. Integer Literal Types

Consider:

```java
int number = 100;
```

The integer literal:

```text
100
```

is normally an `int`.

For a long literal:

```java
long number = 100L;
```

The `L` suffix identifies it as a `long`.

You can use lowercase `l`, but uppercase `L` is recommended because it is easier to distinguish from the number `1`.

Recommended:

```java
long id = 100L;
```

Avoid:

```java
long id = 100l;
```

---

# 17. Numeric Literals With Underscores

Java allows underscores in numeric literals to improve readability.

Example:

```java
int population = 1_000_000;
```

Another example:

```java
long transactionId = 9_876_543_210L;
```

The underscores do not change the value.

For example:

```java
int amount = 1_000_000;
```

is equivalent to:

```java
int amount = 1000000;
```

---

# 18. Binary Literals

Java allows binary integer literals using the prefix:

```text
0b
```

Example:

```java
int value = 0b1010;

System.out.println(value);
```

Output:

```text
10
```

Another example:

```java
int value = 0b1111;

System.out.println(value);
```

Output:

```text
15
```

---

# 19. Octal Literals

Java supports octal literals using a leading `0`.

Example:

```java
int value = 012;
```

This represents octal `12`, which equals decimal `10`.

```java
System.out.println(value);
```

Output:

```text
10
```

Be careful with leading zeros because they can make numbers less obvious to readers.

---

# 20. Hexadecimal Literals

Java supports hexadecimal literals using:

```text
0x
```

Example:

```java
int value = 0xFF;

System.out.println(value);
```

Output:

```text
255
```

Hexadecimal notation is commonly used when working with:

- Colors
- Binary data
- Bit operations
- Low-level programming

---

# 21. float Data Type

The `float` type represents a 32-bit floating-point number.

Example:

```java
float price = 10.5F;
```

The `F` suffix is important.

This is valid:

```java
float price = 10.5F;
```

This is not normally valid:

```java
float price = 10.5;
```

because decimal literals are `double` by default.

---

# 22. double Data Type

The `double` type represents a 64-bit floating-point number.

Example:

```java
double price = 10.50;
double temperature = 36.5;
double percentage = 95.75;
```

Example:

```java
public class Main {

    public static void main(String[] args) {

        double temperature = 36.5;

        System.out.println(temperature);
    }
}
```

Output:

```text
36.5
```

`double` is normally preferred over `float` when floating-point arithmetic is required.

---

# 23. float vs double

| Feature        | `float`                  | `double`                            |
| -------------- | ------------------------ | ----------------------------------- |
| Size           | 32-bit                   | 64-bit                              |
| Precision      | Lower                    | Higher                              |
| Literal suffix | `F`                      | Usually none                        |
| Typical usage  | Specialized numeric work | General floating-point calculations |

Example:

```java
float rate = 5.5F;

double amount = 1000.50;
```

---

# 24. Floating-Point Precision

Floating-point numbers cannot represent every decimal value exactly.

Example:

```java
double result = 0.1 + 0.2;

System.out.println(result);
```

Possible output:

```text
0.30000000000000004
```

This is normal floating-point behavior.

It is not a Java bug.

The issue comes from representing decimal fractions using binary floating-point arithmetic.

---

# 25. Do Not Use float or double for Exact Money

For financial calculations, avoid:

```java
double balance = 1000.10;
```

when exact decimal arithmetic is required.

Prefer:

```java
BigDecimal balance =
        new BigDecimal("1000.10");
```

Import:

```java
import java.math.BigDecimal;
```

Example:

```java
import java.math.BigDecimal;

public class Main {

    public static void main(String[] args) {

        BigDecimal balance =
                new BigDecimal("1000.10");

        System.out.println(balance);
    }
}
```

Output:

```text
1000.10
```

---

# 26. BigDecimal for Banking Applications

For banking and financial systems, `BigDecimal` is generally preferred for exact decimal arithmetic.

Example:

```java
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
```

Output:

```text
5250.00
```

This is much more appropriate for monetary calculations than:

```java
double
```

---

# 27. char Data Type

The `char` type represents a single UTF-16 code unit.

Example:

```java
char grade = 'A';
```

Characters use single quotes:

```java
'A'
```

Strings use double quotes:

```java
"A"
```

Example:

```java
char firstLetter = 'J';

System.out.println(firstLetter);
```

Output:

```text
J
```

---

# 28. char and Unicode

Java `char` values use UTF-16 code units.

Example:

```java
char letter = 'A';

System.out.println(letter);
```

You can also use Unicode escape notation:

```java
char letter = '\u0041';

System.out.println(letter);
```

Output:

```text
A
```

The Unicode code point `U+0041` represents `A`.

---

# 29. Important char Limitation

A Java `char` is 16 bits and represents one UTF-16 code unit.

Most common characters fit in one `char`.

However, some Unicode characters require a **surrogate pair**, meaning they require two UTF-16 code units.

Therefore:

```java
char
```

does not necessarily represent every Unicode code point by itself.

For full Unicode code-point processing, Java provides APIs such as:

```java
String
Character
codePointAt()
codePoints()
```

---

# 30. boolean Data Type

The `boolean` type represents a logical value.

It has two values:

```text
true
false
```

Example:

```java
boolean active = true;
boolean completed = false;
```

Example:

```java
boolean accountActive = true;

System.out.println(accountActive);
```

Output:

```text
true
```

---

# 31. boolean in Conditions

Boolean values are commonly used in `if` statements.

Example:

```java
boolean accountActive = true;

if (accountActive) {

    System.out.println("Account is active");
}
```

Output:

```text
Account is active
```

Another example:

```java
boolean authenticated = false;

if (!authenticated) {

    System.out.println("Access denied");
}
```

Output:

```text
Access denied
```

---

# 32. Java Does Not Treat Numbers as boolean

Unlike some programming languages, Java does not allow:

```java
if (1) {
}
```

This is invalid.

Java requires a boolean expression:

```java
if (true) {
}
```

or:

```java
if (age >= 18) {
}
```

---

# 33. Primitive Data Type Default Values

Instance variables and static fields receive default values.

| Data Type       | Default Value |
| --------------- | ------------- |
| `byte`          | `0`           |
| `short`         | `0`           |
| `int`           | `0`           |
| `long`          | `0L`          |
| `float`         | `0.0F`        |
| `double`        | `0.0D`        |
| `char`          | `'\u0000'`    |
| `boolean`       | `false`       |
| Reference types | `null`        |

Example:

```java
class Customer {

    int age;
    boolean active;
    double balance;
    String name;
}
```

New objects receive the default values for these fields.

---

# 34. Local Variables Do Not Have Default Values

This is important.

The following is invalid:

```java
public static void main(String[] args) {

    int age;

    System.out.println(age);
}
```

Java reports a compilation error because `age` has not been definitely assigned.

Correct:

```java
int age = 25;

System.out.println(age);
```

---

# 35. Primitive vs Reference Types

Java data types can be divided into:

```text
Primitive
Reference
```

Primitive example:

```java
int age = 25;
```

Reference example:

```java
String name = "John";
```

The primitive variable directly represents a primitive value.

A reference variable refers to an object.

---

# 36. What Is a Reference Type?

A reference type represents an object or an array.

Examples:

```java
String name = "John";

Customer customer = new Customer();

int[] numbers = {1, 2, 3};
```

Here:

```text
String
Customer
int[]
```

are reference types.

---

# 37. String Data Type

`String` is a reference type, not a primitive type.

Example:

```java
String name = "John";
```

A `String` represents a sequence of characters.

Example:

```java
String message = "Hello Java";

System.out.println(message);
```

Output:

```text
Hello Java
```

---

# 38. String Concatenation

You can combine strings using `+`.

Example:

```java
String firstName = "John";
String lastName = "Smith";

String fullName =
        firstName + " " + lastName;

System.out.println(fullName);
```

Output:

```text
John Smith
```

You can also combine strings with numbers:

```java
int age = 30;

System.out.println(
        "Age: " + age
);
```

Output:

```text
Age: 30
```

---

# 39. String Is Immutable

Java `String` objects are immutable.

For example:

```java
String name = "John";

name = name + " Smith";
```

The original `String` object is not modified.

A new `String` object is created for the new value.

Conceptually:

```text
"John"
   ↓
original String

"John Smith"
   ↓
new String
```

The variable `name` is then updated to refer to the new object.

---

# 40. String Methods

`String` provides many useful methods.

Example:

```java
String name = "John Smith";

System.out.println(name.length());

System.out.println(name.toUpperCase());

System.out.println(name.toLowerCase());

System.out.println(name.contains("John"));
```

Output:

```text
10
JOHN SMITH
john smith
true
```

---

# 41. Array Data Type

An array is an object that stores multiple values of the same type.

Example:

```java
int[] numbers = {10, 20, 30, 40};
```

Access an element:

```java
System.out.println(numbers[0]);
```

Output:

```text
10
```

The index starts at:

```text
0
```

---

# 42. Array Example

```java
public class Main {

    public static void main(String[] args) {

        int[] numbers = {
                10,
                20,
                30,
                40
        };

        for (int number : numbers) {

            System.out.println(number);
        }
    }
}
```

Output:

```text
10
20
30
40
```

---

# 43. Array Length

Arrays have a `length` field.

Example:

```java
int[] numbers = {10, 20, 30, 40};

System.out.println(numbers.length);
```

Output:

```text
4
```

Notice that array length uses:

```java
numbers.length
```

not:

```java
numbers.length()
```

because `length` is a field, not a method.

---

# 44. Class Types

A class can define a reference type.

Example:

```java
class Customer {

    String name;
    int age;
}
```

You can create an object:

```java
Customer customer = new Customer();
```

Here:

```text
Customer
   ↓
Reference type

customer
   ↓
Reference variable

new Customer()
   ↓
Object
```

---

# 45. Interface Types

An interface can also be used as a reference type.

Example:

```java
interface PaymentService {

    void pay();
}
```

Implementation:

```java
class CardPaymentService
        implements PaymentService {

    @Override
    public void pay() {

        System.out.println("Card payment");
    }
}
```

You can declare:

```java
PaymentService service =
        new CardPaymentService();
```

The variable type is:

```text
PaymentService
```

while the actual object type is:

```text
CardPaymentService
```

This is an important concept in polymorphism.

---

# 46. Enum Types

An enum defines a fixed set of constants.

Example:

```java
enum AccountStatus {

    ACTIVE,
    BLOCKED,
    CLOSED
}
```

Usage:

```java
AccountStatus status =
        AccountStatus.ACTIVE;
```

Example:

```java
if (status == AccountStatus.ACTIVE) {

    System.out.println(
            "Account is active"
    );
}
```

---

# 47. Record Types

Java records provide a concise way to model data.

Example:

```java
record Customer(
        String id,
        String name,
        int age
) {
}
```

Create an object:

```java
Customer customer =
        new Customer(
                "C001",
                "John",
                30
        );
```

Access values:

```java
System.out.println(customer.id());
System.out.println(customer.name());
System.out.println(customer.age());
```

Output:

```text
C001
John
30
```

---

# 48. Wrapper Classes

Each primitive type has a corresponding wrapper class.

| Primitive | Wrapper     |
| --------- | ----------- |
| `byte`    | `Byte`      |
| `short`   | `Short`     |
| `int`     | `Integer`   |
| `long`    | `Long`      |
| `float`   | `Float`     |
| `double`  | `Double`    |
| `char`    | `Character` |
| `boolean` | `Boolean`   |

Example:

```java
int age = 30;

Integer boxedAge = age;
```

Java automatically performs boxing.

---

# 49. Why Do We Need Wrapper Classes?

Wrapper classes are useful because Java collections work with objects.

For example:

```java
List<Integer> numbers =
        new ArrayList<>();
```

You cannot write:

```java
List<int> numbers;
```

because generic type arguments must be reference types.

Instead:

```java
List<Integer> numbers;
```

Example:

```java
List<Integer> numbers =
        new ArrayList<>();

numbers.add(10);
numbers.add(20);
numbers.add(30);
```

---

# 50. Autoboxing

Autoboxing automatically converts a primitive into its wrapper type.

Example:

```java
int value = 100;

Integer boxed = value;
```

Conceptually:

```text
int
 ↓
Integer
```

Java performs the conversion automatically.

---

# 51. Unboxing

Unboxing converts a wrapper object back into a primitive.

Example:

```java
Integer boxed = 100;

int value = boxed;
```

Conceptually:

```text
Integer
   ↓
int
```

---

# 52. Be Careful With null and Unboxing

This can cause a `NullPointerException`:

```java
Integer value = null;

int number = value;
```

Java attempts to unbox `null` into an `int`.

There is no primitive integer value represented by `null`.

Be careful when working with wrapper classes.

---

# 53. Primitive Type Conversion

Java supports numeric type conversions.

There are two major categories:

```text
Widening Conversion
Narrowing Conversion
```

---

# 54. Widening Conversion

Widening conversion converts a smaller compatible numeric type into a larger type.

Example:

```java
int number = 100;

long value = number;
```

No explicit cast is required.

Another example:

```java
int number = 100;

double value = number;

System.out.println(value);
```

Output:

```text
100.0
```

---

# 55. Typical Widening Conversion Path

A simplified numeric widening path is:

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

For example:

```java
byte a = 10;

int b = a;

long c = b;

double d = c;
```

---

# 56. Narrowing Conversion

Narrowing conversion converts a larger type into a smaller type.

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

The fractional portion is discarded.

---

# 57. Casting

The syntax for explicit casting is:

```java
(targetType) value
```

Example:

```java
double amount = 100.75;

int result = (int) amount;
```

Another example:

```java
long number = 1000L;

int value = (int) number;
```

---

# 58. Narrowing Can Cause Data Loss

Example:

```java
long number = 3_000_000_000L;

int value = (int) number;

System.out.println(value);
```

The result does not equal the original value because the `long` value is outside the range of `int`.

Therefore, narrowing conversions should be performed carefully.

---

# 59. char and Numeric Conversion

A `char` can participate in numeric operations.

Example:

```java
char letter = 'A';

int value = letter;

System.out.println(value);
```

Output:

```text
65
```

The character `A` has Unicode value `U+0041`, which is decimal `65`.

You can also convert a number to a character:

```java
int value = 66;

char letter = (char) value;

System.out.println(letter);
```

Output:

```text
B
```

---

# 60. String to int

A `String` cannot automatically become an `int`.

Example:

```java
String value = "100";
```

Use:

```java
int number =
        Integer.parseInt(value);
```

Example:

```java
String value = "100";

int number =
        Integer.parseInt(value);

System.out.println(number);
```

Output:

```text
100
```

---

# 61. int to String

You can convert an integer to a string.

Example:

```java
int number = 100;

String value =
        String.valueOf(number);
```

Another common approach is:

```java
String value =
        Integer.toString(number);
```

You can also use:

```java
String value = "" + number;
```

but `String.valueOf()` is usually clearer when the intention is explicit conversion.

---

# 62. String to double

Example:

```java
String value = "100.50";

double amount =
        Double.parseDouble(value);

System.out.println(amount);
```

Output:

```text
100.5
```

---

# 63. String to BigDecimal

For financial values, use:

```java
BigDecimal amount =
        new BigDecimal("100.50");
```

Example:

```java
String value = "100.50";

BigDecimal amount =
        new BigDecimal(value);
```

This preserves the decimal representation appropriately for exact decimal arithmetic.

---

# 64. Important BigDecimal Mistake

Avoid:

```java
BigDecimal amount =
        new BigDecimal(0.1);
```

because `0.1` is already represented as a binary floating-point value before it reaches `BigDecimal`.

Prefer:

```java
BigDecimal amount =
        new BigDecimal("0.1");
```

or:

```java
BigDecimal amount =
        BigDecimal.valueOf(0.1);
```

For data received as text:

```java
BigDecimal amount =
        new BigDecimal(input);
```

is commonly appropriate.

---

# 65. Type Inference with var

Java supports local variable type inference using `var`.

Example:

```java
var age = 30;
```

The compiler infers:

```text
int
```

Another example:

```java
var name = "John";
```

The compiler infers:

```text
String
```

Another example:

```java
var amount =
        new BigDecimal("100.00");
```

The inferred type is:

```text
BigDecimal
```

---

# 66. var Does Not Mean Dynamic Typing

Consider:

```java
var age = 30;
```

The compiler knows:

```text
age → int
```

Therefore this is invalid:

```java
age = "John";
```

`var` is still statically typed.

It only allows the compiler to infer the type from the initializer.

---

# 67. var Requires an Initializer

Invalid:

```java
var age;
```

Java cannot determine the type.

Correct:

```java
var age = 30;
```

Another valid example:

```java
var customer =
        new Customer();
```

---

# 68. var Is Only for Local Variables

Valid:

```java
public void process() {

    var amount = 100;
}
```

Invalid as a field:

```java
class Customer {

    var name = "John";
}
```

Invalid as a method parameter:

```java
void process(var amount) {
}
```

Invalid as a return type:

```java
var getName() {
    return "John";
}
```

---

# 69. Choosing the Correct Data Type

A good developer chooses a type based on the meaning of the data.

Examples:

```java
int quantity;
```

For a normal count.

```java
long transactionId;
```

For a large numeric identifier.

```java
String customerName;
```

For text.

```java
boolean accountActive;
```

For true/false state.

```java
BigDecimal transactionAmount;
```

For exact monetary values.

```java
LocalDate transactionDate;
```

For a date.

```java
Instant createdAt;
```

For a timestamp representing an instant in time.

---

# 70. Date and Time Are Not Primitive Types

Java does not have a primitive `date` data type.

Modern Java applications should generally use the `java.time` API.

Examples:

```java
LocalDate
LocalTime
LocalDateTime
Instant
ZonedDateTime
OffsetDateTime
Duration
Period
```

Example:

```java
LocalDate transactionDate =
        LocalDate.now();
```

Example:

```java
Instant createdAt =
        Instant.now();
```

These are reference types.

---

# 71. Example: Banking Data Types

A banking transaction may contain:

```java
String transactionId;

String accountNumber;

BigDecimal amount;

String currency;

LocalDate valueDate;

Instant createdAt;

boolean successful;
```

Each data type has a specific purpose.

| Variable        | Type         | Purpose                |
| --------------- | ------------ | ---------------------- |
| `transactionId` | `String`     | Transaction identifier |
| `accountNumber` | `String`     | Account identifier     |
| `amount`        | `BigDecimal` | Exact monetary amount  |
| `currency`      | `String`     | Currency code          |
| `valueDate`     | `LocalDate`  | Business/value date    |
| `createdAt`     | `Instant`    | Creation timestamp     |
| `successful`    | `boolean`    | Transaction status     |

---

# 72. Why Account Numbers Should Often Be String

Consider:

```java
int accountNumber = 123456789;
```

This may appear reasonable, but an account number is generally an **identifier**, not a number used for arithmetic.

For example, an account number may contain leading zeros:

```text
00123456789
```

If you store it as an integer:

```java
int accountNumber = 00123456789;
```

you cannot preserve the leading zeros in the numeric value.

Prefer:

```java
String accountNumber =
        "00123456789";
```

This preserves the identifier exactly.

---

# 73. Why Transaction IDs Can Be String

Transaction IDs often contain letters and special formatting.

Example:

```text
FT000123
PAY202608290001
TXN-2026-000001
```

Therefore:

```java
String transactionId =
        "FT000123";
```

is usually more appropriate than:

```java
int transactionId = 123;
```

An identifier is not necessarily a mathematical number.

---

# 74. Data Type Selection for Banking

A simplified example:

```java
String customerId;

String accountNumber;

String transactionId;

BigDecimal amount;

String currency;

LocalDate bookingDate;

LocalDate valueDate;

Instant processingTimestamp;

boolean successful;
```

This design communicates the meaning of each field.

---

# 75. Primitive Type Memory Concept

Primitive types have well-defined value representations.

For example:

```java
byte
```

uses 8 bits.

```java
short
```

uses 16 bits.

```java
int
```

uses 32 bits.

```java
long
```

uses 64 bits.

Floating-point types have their own IEEE 754-based representations.

However, you should not assume that the exact JVM memory footprint of every Java variable in a running application is simply equal to the primitive bit width.

Object layout, references, alignment, and JVM implementation details affect actual memory usage for objects.

---

# 76. Data Type and Memory

A simplified conceptual model:

```text
byte
8 bits

short
16 bits

int
32 bits

long
64 bits

float
32 bits

double
64 bits

char
16 bits
```

For `boolean`, Java specifies the type's values but does not define a universal JVM object/field memory size that developers should rely on.

---

# 77. Data Type and Operations

Different types support different operations.

Example:

```java
int a = 10;
int b = 20;

int result = a + b;
```

For strings:

```java
String first = "Hello";
String second = "Java";

String result =
        first + " " + second;
```

For `BigDecimal`:

```java
BigDecimal a =
        new BigDecimal("10.50");

BigDecimal b =
        new BigDecimal("20.25");

BigDecimal result =
        a.add(b);
```

The operation depends on the type.

---

# 78. BigDecimal Does Not Use + for Addition

This is invalid:

```java
BigDecimal a =
        new BigDecimal("10.50");

BigDecimal b =
        new BigDecimal("20.25");

BigDecimal result = a + b;
```

Use:

```java
BigDecimal result =
        a.add(b);
```

Similarly:

```text
add()
subtract()
multiply()
divide()
compareTo()
```

are commonly used.

---

# 79. Comparing BigDecimal

Avoid relying on `equals()` when you want numeric equality regardless of scale.

Example:

```java
BigDecimal a =
        new BigDecimal("10.00");

BigDecimal b =
        new BigDecimal("10.0");
```

These have the same numeric value but different scales.

Using:

```java
a.equals(b)
```

returns:

```text
false
```

For numeric comparison:

```java
a.compareTo(b) == 0
```

is generally the appropriate approach.

---

# 80. Example: BigDecimal Comparison

```java
BigDecimal balance =
        new BigDecimal("100.00");

BigDecimal required =
        new BigDecimal("100.0");

if (balance.compareTo(required) >= 0) {

    System.out.println(
            "Sufficient balance"
    );
}
```

Output:

```text
Sufficient balance
```

This is particularly important in financial applications.

---

# 81. Primitive Type Limits

Java provides constants for many primitive numeric limits.

Example:

```java
System.out.println(Integer.MIN_VALUE);
System.out.println(Integer.MAX_VALUE);
```

Output:

```text
-2147483648
2147483647
```

For long:

```java
System.out.println(Long.MIN_VALUE);
System.out.println(Long.MAX_VALUE);
```

---

# 82. Wrapper Classes Provide Useful Constants

Example:

```java
System.out.println(Integer.MAX_VALUE);

System.out.println(Long.MAX_VALUE);

System.out.println(Double.MAX_VALUE);
```

You can also access:

```java
Byte.MIN_VALUE
Byte.MAX_VALUE

Short.MIN_VALUE
Short.MAX_VALUE

Integer.MIN_VALUE
Integer.MAX_VALUE

Long.MIN_VALUE
Long.MAX_VALUE
```

---

# 83. Numeric Literals and Overflow

Consider:

```java
int value = 2_147_483_647;

value++;

System.out.println(value);
```

Output:

```text
-2147483648
```

The integer overflows because the value exceeds the maximum `int` value.

For values that may exceed `int`, consider:

```java
long
```

or another appropriate representation.

---

# 84. Division by Zero

Integer division by zero causes an exception.

Example:

```java
int a = 10;
int b = 0;

int result = a / b;
```

This results in:

```text
ArithmeticException
```

Floating-point division behaves differently:

```java
double result = 10.0 / 0.0;

System.out.println(result);
```

The result is:

```text
Infinity
```

This difference is important when working with numeric types.

---

# 85. Type Promotion in Arithmetic

Java performs numeric promotion during arithmetic operations.

Example:

```java
byte a = 10;
byte b = 20;

int result = a + b;
```

The result of:

```java
a + b
```

is an `int`, not a `byte`.

Therefore this is invalid:

```java
byte result = a + b;
```

unless an explicit conversion is performed.

---

# 86. Example of byte Arithmetic

```java
byte a = 10;
byte b = 20;

int result = a + b;

System.out.println(result);
```

Output:

```text
30
```

This is an important detail for developers working with smaller integer types.

---

# 87. Type Promotion Example

```java
int a = 10;
long b = 20L;

long result = a + b;
```

The `int` value is promoted to `long`.

Another example:

```java
int a = 10;
double b = 20.5;

double result = a + b;
```

The result is a `double`.

---

# 88. Common Data Type Mistakes

## Mistake 1: Assigning String to int

Incorrect:

```java
int age = "25";
```

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

# 89. Common Mistake: Missing L

Incorrect:

```java
long id = 9876543210;
```

The integer literal is too large for `int`.

Correct:

```java
long id = 9876543210L;
```

---

# 90. Common Mistake: Missing F

Incorrect:

```java
float rate = 5.5;
```

Correct:

```java
float rate = 5.5F;
```

Or use `double`:

```java
double rate = 5.5;
```

---

# 91. Common Mistake: Using Double for Money

Avoid:

```java
double amount = 0.1 + 0.2;
```

for exact monetary calculations.

Prefer:

```java
BigDecimal amount =
        new BigDecimal("0.30");
```

or calculate using `BigDecimal` operations.

---

# 92. Common Mistake: Treating Account Number as int

Avoid:

```java
int accountNumber = 123456789;
```

when the account identifier can contain leading zeros.

Prefer:

```java
String accountNumber =
        "00123456789";
```

---

# 93. Common Mistake: Using == for String Content

Incorrect:

```java
String name = "John";

if (name == "John") {

    System.out.println("Match");
}
```

Use:

```java
if ("John".equals(name)) {

    System.out.println("Match");
}
```

or:

```java
if (name.equals("John")) {

    System.out.println("Match");
}
```

`==` compares references for objects, while `equals()` is generally used for content equality.

Using the literal on the left:

```java
"John".equals(name)
```

also avoids a `NullPointerException` if `name` is `null`.

---

# 94. Common Mistake: Confusing char and String

Incorrect:

```java
char grade = "A";
```

Correct:

```java
char grade = 'A';
```

String:

```java
String grade = "A";
```

Remember:

```text
char
 ↓
'A'

String
 ↓
"A"
```

---

# 95. Common Mistake: Assuming var Is Dynamic

Incorrect understanding:

```java
var value = 100;

value = "Hello";
```

This is invalid.

`var` infers a fixed compile-time type.

In this example:

```java
var value = 100;
```

the type is:

```text
int
```

---

# 96. Common Mistake: Assuming null Works With Primitives

Invalid:

```java
int age = null;
```

Correct for a reference type:

```java
Integer age = null;
```

or:

```java
String name = null;
```

Primitive values cannot be `null`.

---

# 97. Primitive vs Wrapper

Example:

```java
int age = 30;
```

Primitive.

Example:

```java
Integer age = 30;
```

Wrapper/reference type.

Wrapper classes are useful when:

- Using collections
- Using generics
- Working with nullable values
- Calling wrapper utility methods

---

# 98. Complete Data Type Example

```java
import java.math.BigDecimal;
import java.time.Instant;
import java.time.LocalDate;

public class Main {

    public static void main(String[] args) {

        // Primitive types

        byte retryCount = 3;

        short year = 2026;

        int customerCount = 1000;

        long transactionId =
                9876543210L;

        float interestRate = 5.5F;

        double temperature = 36.5;

        char statusCode = 'A';

        boolean active = true;

        // Reference types

        String customerName =
                "John Smith";

        BigDecimal balance =
                new BigDecimal("5000.00");

        LocalDate valueDate =
                LocalDate.now();

        Instant createdAt =
                Instant.now();

        System.out.println(
                "Retry Count: " + retryCount
        );

        System.out.println(
                "Year: " + year
        );

        System.out.println(
                "Customer Count: " + customerCount
        );

        System.out.println(
                "Transaction ID: " + transactionId
        );

        System.out.println(
                "Interest Rate: " + interestRate
        );

        System.out.println(
                "Temperature: " + temperature
        );

        System.out.println(
                "Status Code: " + statusCode
        );

        System.out.println(
                "Active: " + active
        );

        System.out.println(
                "Customer Name: " + customerName
        );

        System.out.println(
                "Balance: " + balance
        );

        System.out.println(
                "Value Date: " + valueDate
        );

        System.out.println(
                "Created At: " + createdAt
        );
    }
}
```

---

# 99. Output

Example output:

```text
Retry Count: 3
Year: 2026
Customer Count: 1000
Transaction ID: 9876543210
Interest Rate: 5.5
Temperature: 36.5
Status Code: A
Active: true
Customer Name: John Smith
Balance: 5000.00
Value Date: 2026-08-29
Created At: 2026-08-29T...
```

The exact `createdAt` output depends on the current time.

---

# 100. Data Type Selection Cheat Sheet

| Requirement                         | Recommended Type   |
| ----------------------------------- | ------------------ |
| Small integer                       | `byte`             |
| Small integer with specific range   | `short`            |
| Normal integer                      | `int`              |
| Large integer                       | `long`             |
| Approximate decimal                 | `double`           |
| Specialized lower-precision decimal | `float`            |
| Single UTF-16 code unit             | `char`             |
| True/false                          | `boolean`          |
| Text                                | `String`           |
| Exact decimal money                 | `BigDecimal`       |
| Date without time                   | `LocalDate`        |
| Time without date                   | `LocalTime`        |
| Date and time without zone          | `LocalDateTime`    |
| Point in time                       | `Instant`          |
| Fixed set of values                 | `enum`             |
| Multiple values                     | Array / Collection |
| Structured data                     | Class / Record     |

---

# 101. Primitive vs Reference Type Comparison

| Feature               | Primitive                  | Reference                     |
| --------------------- | -------------------------- | ----------------------------- |
| Examples              | `int`, `double`, `boolean` | `String`, `Customer`, `int[]` |
| Represents            | Primitive value            | Object/array reference        |
| Can be `null`         | No                         | Yes                           |
| Has methods           | No                         | Objects provide methods       |
| Generic type argument | No                         | Yes                           |
| Wrapper available     | Yes                        | Already reference type        |

---

# 102. Java Data Type Hierarchy

A useful conceptual model is:

```text
Java Data Types
│
├── Primitive
│   │
│   ├── Integral
│   │   ├── byte
│   │   ├── short
│   │   ├── int
│   │   └── long
│   │
│   ├── Floating Point
│   │   ├── float
│   │   └── double
│   │
│   ├── Character
│   │   └── char
│   │
│   └── Boolean
│       └── boolean
│
└── Reference
    │
    ├── Class
    ├── Interface
    ├── Array
    ├── Enum
    ├── Record
    └── String
```

---

# 103. Important Java Data Type Rules

Remember these rules:

```text
1. Java has 8 primitive data types.

2. String is NOT primitive.

3. Arrays are reference types.

4. Classes are reference types.

5. Interfaces are reference types.

6. Primitive variables cannot contain null.

7. Reference variables can contain null.

8. int is the normal default integer type.

9. double is the normal default floating-point type.

10. long literals commonly use L.

11. float literals commonly use F.

12. Local variables must be definitely assigned before use.

13. Instance fields receive default values.

14. var uses compile-time type inference.

15. var does not make Java dynamically typed.

16. BigDecimal is generally preferred for exact monetary calculations.
```

---

# 104. Banking Application Example

Consider a banking transaction:

```java
import java.math.BigDecimal;
import java.time.Instant;
import java.time.LocalDate;

public class Transaction {

    private String transactionId;

    private String accountNumber;

    private BigDecimal amount;

    private String currency;

    private LocalDate valueDate;

    private Instant createdAt;

    private boolean successful;
}
```

This is a good example of selecting data types based on **business meaning**.

```text
transactionId
      ↓
String

accountNumber
      ↓
String

amount
      ↓
BigDecimal

currency
      ↓
String

valueDate
      ↓
LocalDate

createdAt
      ↓
Instant

successful
      ↓
boolean
```

---

# 105. Why Data Type Design Matters in Banking

Choosing the wrong data type can cause real business problems.

For example:

```java
double amount = 100.10;
```

may cause floating-point precision issues.

Using:

```java
BigDecimal
```

provides exact decimal arithmetic appropriate for monetary calculations.

Similarly:

```java
int accountNumber
```

can lose leading zeros.

Using:

```java
String accountNumber
```

preserves the identifier exactly.

Therefore:

```text
Correct data type
       ↓
Correct representation
       ↓
Correct calculation
       ↓
More reliable application
```

---

# 106. Practical Example: Transfer

```java
import java.math.BigDecimal;

public class TransferService {

    public static void transfer(
            String fromAccount,
            String toAccount,
            BigDecimal amount) {

        System.out.println(
                "From: " + fromAccount
        );

        System.out.println(
                "To: " + toAccount
        );

        System.out.println(
                "Amount: " + amount
        );
    }
}
```

Call:

```java
TransferService.transfer(
        "00123456789",
        "00987654321",
        new BigDecimal("750.00")
);
```

Output:

```text
From: 00123456789
To: 00987654321
Amount: 750.00
```

Notice how the data types communicate the business meaning.

---

# 107. Practice Exercise 1

Create variables for a customer:

```text
Customer ID
Customer Name
Age
Active Status
Account Balance
```

Use appropriate data types.

Expected solution:

```java
String customerId = "C001";

String customerName =
        "John Smith";

int age = 30;

boolean active = true;

BigDecimal balance =
        new BigDecimal("5000.00");
```

---

# 108. Practice Exercise 2

Create a transaction with:

```text
Transaction ID = FT000123
Account Number = 00123456789
Amount = 1250.50
Currency = USD
Successful = true
```

Choose appropriate Java data types.

Expected:

```java
String transactionId =
        "FT000123";

String accountNumber =
        "00123456789";

BigDecimal amount =
        new BigDecimal("1250.50");

String currency =
        "USD";

boolean successful = true;
```

---

# 109. Practice Exercise 3

What is the output?

```java
int a = 10;
int b = 3;

System.out.println(a / b);
```

Expected answer:

```text
3
```

Why?

Because both operands are integers, so integer division is performed.

---

# 110. Practice Exercise 4

What is the output?

```java
double a = 10;
double b = 3;

System.out.println(a / b);
```

Expected answer is approximately:

```text
3.3333333333333335
```

Because floating-point division is used.

---

# 111. Practice Exercise 5

Identify the data type:

```java
var age = 30;
var name = "John";
var active = true;
var amount = 100.50;
```

Expected:

```text
age    → int
name   → String
active → boolean
amount → double
```

---

# 112. Practice Exercise 6

Find the problem:

```java
float rate = 5.5;
```

Correct it.

Solution:

```java
float rate = 5.5F;
```

Or:

```java
double rate = 5.5;
```

---

# 113. Practice Exercise 7

Find the problem:

```java
long transactionId =
        9876543210;
```

Correct:

```java
long transactionId =
        9876543210L;
```

---

# 114. Practice Exercise 8

Which is better for an account number?

```java
int accountNumber = 123456;
```

or:

```java
String accountNumber =
        "00123456";
```

The second is generally better when the value is an identifier because it preserves leading zeros and does not imply arithmetic meaning.

---

# 115. Practice Exercise 9

Which is better for money?

```java
double amount = 1000.50;
```

or:

```java
BigDecimal amount =
        new BigDecimal("1000.50");
```

For exact monetary calculations, the second approach is generally preferred.

---

# 116. Interview Questions

## Question 1

### How many primitive data types does Java have?

Java has 8 primitive data types:

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

## Question 2

### Is String a primitive type?

No.

`String` is a reference type.

Example:

```java
String name = "John";
```

---

## Question 3

### What is the difference between primitive and reference types?

Primitive types represent primitive values.

Examples:

```java
int
double
boolean
```

Reference types refer to objects or arrays.

Examples:

```java
String
Customer
int[]
```

---

## Question 4

### What is the default integer type in Java?

The default integer type for integer literals is:

```text
int
```

---

## Question 5

### What is the default floating-point type?

The default floating-point type for decimal literals is:

```text
double
```

---

## Question 6

### Why do we use L after a long literal?

Example:

```java
long id = 9876543210L;
```

The `L` identifies the literal as a `long`.

---

## Question 7

### Why do we use F after a float literal?

Example:

```java
float rate = 5.5F;
```

The `F` identifies the literal as a `float`.

Without the suffix, `5.5` is a `double` literal.

---

## Question 8

### Can a primitive variable contain null?

No.

Invalid:

```java
int age = null;
```

Reference types can contain `null`.

Example:

```java
String name = null;
```

---

## Question 9

### What is the difference between float and double?

Both are floating-point types.

`double` provides greater precision and is generally preferred when floating-point arithmetic is needed.

---

## Question 10

### Why should BigDecimal be used for money?

Because `float` and `double` use binary floating-point representation and cannot represent every decimal fraction exactly.

`BigDecimal` provides decimal arithmetic suitable for exact monetary calculations.

---

## Question 11

### What is autoboxing?

Autoboxing automatically converts a primitive into its corresponding wrapper type.

Example:

```java
int value = 10;

Integer boxed = value;
```

---

## Question 12

### What is unboxing?

Unboxing converts a wrapper object into its corresponding primitive.

Example:

```java
Integer value = 10;

int number = value;
```

---

## Question 13

### What is var?

`var` provides local variable type inference.

Example:

```java
var name = "John";
```

The compiler infers:

```text
String
```

---

## Question 14

### Is var dynamically typed?

No.

Java remains statically typed.

Example:

```java
var value = 100;
```

The compiler determines that `value` is an `int`.

---

## Question 15

### Can var be used for class fields?

No.

`var` is intended for local variable declarations.

---

## Question 16

### What is widening conversion?

Widening conversion converts a smaller compatible numeric type into a larger type.

Example:

```java
int value = 100;

long result = value;
```

---

## Question 17

### What is narrowing conversion?

Narrowing conversion converts a larger numeric type into a smaller type.

Example:

```java
double value = 100.50;

int result = (int) value;
```

The fractional part is lost.

---

## Question 18

### What is the difference between char and String?

`char` represents one UTF-16 code unit:

```java
char letter = 'A';
```

`String` represents a sequence of characters:

```java
String name = "John";
```

---

## Question 19

### Why should account numbers usually be String?

Because account numbers are identifiers rather than quantities.

Using `String` preserves:

- Leading zeros
- Formatting
- Non-numeric characters if permitted

Example:

```java
String accountNumber =
        "00123456789";
```

---

## Question 20

### Why should transaction IDs often be String?

Transaction IDs may contain letters, prefixes, separators, and leading zeros.

Example:

```java
String transactionId =
        "FT000123";
```

---

# 117. Final Data Type Cheat Sheet

```java
// Integer
int age = 30;

// Large integer
long transactionId = 9876543210L;

// Small integer
byte retryCount = 3;

// Short integer
short year = 2026;

// Floating point
float rate = 5.5F;

// Double precision floating point
double temperature = 36.5;

// Character
char status = 'A';

// Boolean
boolean active = true;

// String
String customerName = "John Smith";

// Exact monetary value
BigDecimal amount =
        new BigDecimal("1000.50");

// Date
LocalDate valueDate =
        LocalDate.now();

// Timestamp
Instant createdAt =
        Instant.now();

// Array
int[] numbers = {
        10, 20, 30
};

// Enum
AccountStatus status =
        AccountStatus.ACTIVE;

// Type inference
var count = 100;
```

---

# 118. Final Summary

Java data types tell the compiler what kind of data a variable represents.

The two major categories are:

```text
Java Data Types
│
├── Primitive
│
└── Reference
```

Primitive types:

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
```

For professional Java development, especially enterprise and banking applications, choose types based on **business meaning**, not just the appearance of the value.

For example:

```text
Customer ID
    ↓
String

Account Number
    ↓
String

Transaction ID
    ↓
String

Quantity
    ↓
int

Large numeric value
    ↓
long

Money
    ↓
BigDecimal

Business Date
    ↓
LocalDate

Timestamp
    ↓
Instant

Status
    ↓
boolean / enum
```

The most important principle is:

```text
Correct Data Type
       ↓
Correct Data Representation
       ↓
Correct Operations
       ↓
Fewer Bugs
       ↓
More Reliable Application
```

Once you understand Java data types, the next important topic is:

```text
Java Data Types
       ↓
Java Operators
       ↓
Arithmetic Operators
       ↓
Comparison Operators
       ↓
Logical Operators
       ↓
Assignment Operators
       ↓
Bitwise Operators
       ↓
Ternary Operator
```
