# 📘 Primitive Types vs Wrapper Classes

> **Lowercase types are usually Java primitive types. Capitalized types are wrapper/reference classes.**

## 1. Primitive Types vs Wrapper Classes

Java has **8 primitive data types**:

```text
Primitive Types
      |
      +-- byte
      +-- short
      +-- int
      +-- long
      +-- float
      +-- double
      +-- char
      +-- boolean
```

Java also provides corresponding **wrapper classes**:

```text
Primitive        Wrapper Class
---------        -------------
byte      --->   Byte
short     --->   Short
int       --->   Integer
long      --->   Long
float     --->   Float
double    --->   Double
char      --->   Character
boolean   --->   Boolean
```

So there are **8 primitive types + 8 main wrapper classes**.

---

# 2. `boolean` vs `Boolean`

This is probably the first one you noticed.

### Primitive

```java
boolean active = true;
```

### Wrapper

```java
Boolean active = true;
```

They look similar, but they are different types.

```text
boolean
   |
   +-- Primitive
   +-- Can be true or false
   +-- Cannot be null
   +-- Lower memory overhead
   +-- Faster for simple operations

Boolean
   |
   +-- Class / reference type
   +-- Can be true, false, or null
   +-- Has methods
   +-- Can be used in generic collections
```

For example:

```java
boolean a = true;

Boolean b = true;

Boolean c = null;
```

This is valid:

```java
Boolean c = null;
```

But this is not:

```java
boolean c = null;
```

because a primitive cannot hold `null`.

---

# 3. `int` vs `Integer`

This is one of the most common differences.

Primitive:

```java
int age = 30;
```

Wrapper:

```java
Integer age = 30;
```

Conceptually:

```text
int
 |
 +-- Primitive number


Integer
 |
 +-- Object representing an int
```

`Integer` can be `null`:

```java
Integer age = null;
```

But:

```java
int age = null;
```

is invalid.

---

# 4. Why Does Java Have Wrapper Classes?

One major reason is that **Java Collections and Generics work with objects/reference types, not primitive types**.

For example, this is invalid:

```java
List<int> numbers;
```

You must use:

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

Diagram:

```text
List
 |
 +-- Integer
      |
      +-- 10
      +-- 20
      +-- 30
```

This is one of the most important reasons you'll see `Integer` frequently in Java applications.

---

# 5. All 8 Primitive Types

## 5.1 `byte`

```java
byte age = 30;
```

Size:

```text
8 bits
```

Range:

```text
-128 to 127
```

Useful when working with small integer values or raw binary data.

---

## 5.2 `short`

```java
short age = 30000;
```

Size:

```text
16 bits
```

Range:

```text
-32,768 to 32,767
```

Not used very frequently in normal business applications.

---

## 5.3 `int`

```java
int age = 30;
```

Size:

```text
32 bits
```

Range:

```text
-2,147,483,648
to
2,147,483,647
```

This is the **default choice for normal integer calculations**.

Example:

```java
int customerCount = 1000;
```

---

## 5.4 `long`

```java
long accountNumber = 1234567890123L;
```

Size:

```text
64 bits
```

Range:

```text
-9,223,372,036,854,775,808
to
9,223,372,036,854,775,807
```

Notice the `L`:

```java
1234567890123L
```

The `L` tells Java that the number is a `long` literal.

---

## 5.5 `float`

```java
float rate = 3.14f;
```

Size:

```text
32 bits
```

Notice:

```java
3.14f
```

The `f` tells Java this is a `float` literal.

However, `float` is generally not recommended for financial calculations.

---

# 6. `double`

```java
double temperature = 25.5;
```

Size:

```text
64 bits
```

`double` is the default floating-point type.

Example:

```java
double salary = 1500.50;
```

But for banking/money calculations, don't normally use:

```java
double balance;
```

Instead, use:

```java
BigDecimal balance;
```

For example:

```java
BigDecimal balance =
        new BigDecimal("1000.50");
```

This is particularly important for your banking-related Java development.

---

# 7. `char`

`char` stores a single UTF-16 code unit.

Example:

```java
char grade = 'A';
```

Notice the **single quotes**:

```java
'A'
```

not:

```java
"A"
```

This is a `String`:

```java
String grade = "A";
```

---

# 8. `String`

This is another very important distinction.

`String` is **not a primitive type**.

It is a Java class.

```java
String name = "David";
```

Therefore:

```text
String
   |
   +-- Reference type
   +-- Class
   +-- Not primitive
```

Java provides special language support for String literals, which is why it can look simpler than other objects.

---

# 9. `char` vs `String`

Single character:

```java
char letter = 'A';
```

Multiple characters:

```java
String name = "David";
```

Difference:

```text
char
 |
 +-- 'A'
 +-- One UTF-16 code unit


String
 |
 +-- "David"
 +-- Sequence of characters
```

---

# 10. `Character` vs `char`

Wrapper:

```java
Character letter = 'A';
```

Primitive:

```java
char letter = 'A';
```

And:

```java
Character letter = null;
```

is valid.

But:

```java
char letter = null;
```

is invalid.

---

# 11. Complete Primitive vs Wrapper Table

| Primitive | Wrapper     | Typical Use              |
| --------- | ----------- | ------------------------ |
| `byte`    | `Byte`      | Small integer            |
| `short`   | `Short`     | Small/medium integer     |
| `int`     | `Integer`   | Normal integer           |
| `long`    | `Long`      | Large integer            |
| `float`   | `Float`     | Single-precision decimal |
| `double`  | `Double`    | Double-precision decimal |
| `char`    | `Character` | Single UTF-16 code unit  |
| `boolean` | `Boolean`   | True/false               |

Remember this table:

```text
byte       -> Byte
short      -> Short
int        -> Integer
long       -> Long
float      -> Float
double     -> Double
char       -> Character
boolean    -> Boolean
```

---

# 12. Primitive vs Wrapper Diagram

```text
                    Java Types
                        |
              +---------+---------+
              |                   |
              v                   v
          Primitive           Reference
             Types              Types
              |                   |
       +------+------+       +----+----+
       |      |      |       |         |
       v      v      v       v         v
      int   long   boolean Integer   Boolean
                            |
                            |
                       Wrapper Class
```

---

# 13. Autoboxing

Java can automatically convert a primitive into its wrapper class.

This is called **autoboxing**.

Example:

```java
int number = 10;

Integer value = number;
```

Java automatically converts:

```text
int
 |
 | autoboxing
 v
Integer
```

Conceptually:

```java
Integer value =
        Integer.valueOf(number);
```

---

# 14. Unboxing

The reverse conversion is called **unboxing**.

Example:

```java
Integer value = 10;

int number = value;
```

Java automatically converts:

```text
Integer
 |
 | unboxing
 v
int
```

Conceptually:

```java
int number =
        value.intValue();
```

---

# 15. Autoboxing Example with Collections

This is very common:

```java
List<Integer> numbers =
        new ArrayList<>();

numbers.add(10);
numbers.add(20);
numbers.add(30);
```

`add()` expects:

```java
Integer
```

but we give:

```java
10
```

which is an `int` literal.

Java automatically boxes it:

```text
10
 |
 | autoboxing
 v
Integer
 |
 v
List<Integer>
```

---

# 16. The `null` Problem with Unboxing

Be careful with:

```java
Integer number = null;

int value = number;
```

This causes:

```text
NullPointerException
```

because Java tries to unbox:

```text
null Integer
      |
      v
     int
```

but there is no actual integer value.

---

# 17. Why `Integer` Is Common in Spring Boot

You will frequently see:

```java
private Integer age;
```

instead of:

```java
private int age;
```

One reason is that `Integer` can represent:

```text
30
```

or:

```text
null
```

This can be useful when `null` means:

```text
Value not provided
Unknown
Not applicable
Database NULL
```

For example:

```java
public class Customer {

    private Integer age;
}
```

If the database column is nullable, `Integer` can represent that absence.

---

# 18. Primitive vs Wrapper in Database Applications

Suppose a database column contains:

```text
AGE
----
30
NULL
25
```

With:

```java
private Integer age;
```

Java can represent:

```text
30
null
25
```

But:

```java
private int age;
```

cannot represent database `NULL` directly.

This is one reason wrapper types are common in:

```text
JPA
Hibernate
Spring Data
DTOs
Entity Classes
```

---

# 19. Wrapper Classes Have Useful Methods

Because `Integer` is a class, it has methods.

Example:

```java
String value = "123";

int number =
        Integer.parseInt(value);
```

Output:

```text
123
```

Another:

```java
Integer number = 100;

System.out.println(
        number.compareTo(50)
);
```

---

# 20. Common Wrapper Methods

### Integer

```java
Integer.parseInt("100");
Integer.valueOf("100");
```

### Long

```java
Long.parseLong("100000");
Long.valueOf("100000");
```

### Double

```java
Double.parseDouble("10.50");
```

### Boolean

```java
Boolean.parseBoolean("true");
```

---

# 21. `Integer` Constants

Wrapper classes also provide constants.

Example:

```java
System.out.println(
        Integer.MAX_VALUE
);
```

Output:

```text
2147483647
```

And:

```java
System.out.println(
        Integer.MIN_VALUE
);
```

Output:

```text
-2147483648
```

Similarly:

```java
Long.MAX_VALUE
Long.MIN_VALUE
Double.MAX_VALUE
Float.MAX_VALUE
```

---

# 22. `String` Is Different

Remember:

```text
int
Integer
```

have a direct primitive/wrapper relationship.

But:

```text
String
```

does not have a corresponding primitive called:

```text
string
```

There is no Java primitive:

```java
string
```

This is invalid:

```java
string name = "David";
```

Correct:

```java
String name = "David";
```

---

# 23. Common Capitalization Mistakes

### Wrong

```java
Boolean
```

is not wrong.

It is the wrapper.

But:

```java
bolean
```

is wrong.

Correct:

```java
boolean
```

---

### Wrong

```java
integer age = 30;
```

Correct:

```java
Integer age = 30;
```

---

### Wrong

```java
string name = "David";
```

Correct:

```java
String name = "David";
```

---

### Correct

```java
int age = 30;

Integer age2 = 30;

boolean active = true;

Boolean active2 = true;

String name = "David";
```

---

# 24. Why Capital Letters?

Java naming conventions use:

```text
Primitive types
    |
    v
lowercase

Classes
    |
    v
PascalCase
```

Examples:

```text
int
boolean
double
char
```

versus:

```text
Integer
Boolean
Double
Character
String
```

The capitalized names are classes/reference types.

---

# 25. Are Wrapper Classes Objects?

Yes.

For example:

```java
Integer number = 100;
```

`number` is a reference to an `Integer` object/value representation.

Conceptually:

```text
number
   |
   v
+------------+
| Integer    |
| 100        |
+------------+
```

Whereas:

```java
int number = 100;
```

uses a primitive value directly.

---

# 26. Memory Concept

At a high level:

```text
Primitive:

int number = 100;

number
 |
 +-- primitive value: 100
```

Wrapper:

```text
Integer number = 100;

number
 |
 | reference
 v
+-------------+
| Integer     |
| value = 100 |
+-------------+
```

This is a simplified conceptual model. The JVM may optimize object allocation in various ways, so don't treat this diagram as a precise JVM memory-layout specification.

---

# 27. Which One Should I Use?

A practical rule:

### Use primitive when:

You need a simple value and `null` is not meaningful.

```java
int count = 10;

boolean active = true;

double rate = 5.5;
```

### Use wrapper when:

You need:

```text
null
Generics
Collections
Framework/API compatibility
Nullable database values
```

Example:

```java
Integer count = null;
```

or:

```java
List<Integer> numbers = new ArrayList<>();
```

---

# 28. Example: Simple Application

Primitive:

```java
public class Counter {

    private int count;

    public void increment() {

        count++;
    }

    public int getCount() {

        return count;
    }
}
```

This makes sense because `count` normally always has a numeric value.

---

# 29. Example: Database Entity

Wrapper:

```java
public class Customer {

    private Long id;

    private Integer age;

    private Boolean active;
}
```

This is common in application code because these fields may correspond to nullable database columns.

For example:

```text
CUSTOMER
---------------------------
ID        = 1001
AGE       = NULL
ACTIVE    = TRUE
```

Java:

```text
Long      -> 1001
Integer   -> null
Boolean   -> true
```

---

# 30. What About `BigInteger` and `BigDecimal`?

These are **not primitive types** and are not simple wrapper classes for primitives.

They are classes:

```java
BigInteger
BigDecimal
```

For example:

```java
BigDecimal amount =
        new BigDecimal("1000.50");
```

They are especially important in financial applications.

For banking systems, prefer:

```java
BigDecimal
```

for monetary amounts rather than:

```java
float
double
```

because floating-point arithmetic can introduce representation/rounding issues.

---

# 31. Complete Java Type Family

A useful mental model is:

```text
                         Java Types
                             |
              +--------------+--------------+
              |                             |
              v                             v
         Primitive Types              Reference Types
              |                             |
      +-------+-------+             +-------+-------+
      |       |       |             |       |       |
      v       v       v             v       v       v
     int    long   boolean       Integer Boolean String
      |
      v
  Wrapper Class
```

---

# 32. All Main Primitive/Wrapper Pairs

```text
+----------+--------------+
| Primitive | Wrapper      |
+----------+--------------+
| byte      | Byte         |
| short     | Short        |
| int       | Integer      |
| long      | Long         |
| float     | Float        |
| double    | Double       |
| char      | Character    |
| boolean   | Boolean      |
+----------+--------------+
```

There are:

```text
8 primitive types
8 corresponding wrapper classes
```

---

# 33. Important: `void`

You may also see:

```java
void
```

Example:

```java
public void printHello() {

    System.out.println(
            "Hello"
    );
}
```

`void` means:

```text
This method does not return a value.
```

There is also:

```java
Void
```

which is a reference type used in certain APIs/generic contexts.

But `void` is **not one of Java's 8 value-bearing primitive data types**.

---

# 34. Quick Comparison

| Type         | Primitive? | Wrapper/Class | Can be `null`? |
| ------------ | ---------: | ------------- | -------------: |
| `byte`       |         ✅ | `Byte`        |             ❌ |
| `short`      |         ✅ | `Short`       |             ❌ |
| `int`        |         ✅ | `Integer`     |             ❌ |
| `long`       |         ✅ | `Long`        |             ❌ |
| `float`      |         ✅ | `Float`       |             ❌ |
| `double`     |         ✅ | `Double`      |             ❌ |
| `char`       |         ✅ | `Character`   |             ❌ |
| `boolean`    |         ✅ | `Boolean`     |             ❌ |
| `String`     |         ❌ | `String`      |             ✅ |
| `BigInteger` |         ❌ | Class         |             ✅ |
| `BigDecimal` |         ❌ | Class         |             ✅ |

---

# 35. Most Important Things to Remember

If you see:

```java
int
long
double
boolean
char
```

think:

```text
Primitive
```

If you see:

```java
Integer
Long
Double
Boolean
Character
```

think:

```text
Wrapper Class
```

If you see:

```java
String
BigDecimal
BigInteger
```

think:

```text
Reference/Class Type
```

---

# 36. Simple Memory Trick

Remember:

```text
lowercase
    |
    v
primitive

Capital Letter
    |
    v
class/reference type
```

For example:

```text
int       -> primitive
Integer   -> class

boolean   -> primitive
Boolean   -> class

char      -> primitive
Character -> class
```

---

# 37. Java Developer Practical Rule

For everyday Java development:

```text
Simple calculations
        |
        v
Primitive
```

Example:

```java
int count = 10;
```

Collections:

```text
Collection
    |
    v
Wrapper
```

Example:

```java
List<Integer> numbers;
```

Nullable application/database values:

```text
Nullable
    |
    v
Wrapper
```

Example:

```java
Integer age;
Boolean active;
Long customerId;
```

Money:

```text
Financial amount
        |
        v
BigDecimal
```

Example:

```java
BigDecimal balance;
```

---

# 38. Final Diagram

```text
                         JAVA DATA TYPES
                                |
              +-----------------+-----------------+
              |                                   |
              v                                   v
        PRIMITIVE TYPES                     REFERENCE TYPES
              |                                   |
     +--------+--------+                 +--------+--------+
     |        |        |                 |        |        |
     v        v        v                 v        v        v
    int     long    boolean           Integer  Boolean  String
     |        |        |                 |
     +--------+--------+                 |
              |                           |
              v                           v
       8 Primitive Types           8 Wrapper Classes
              |                           |
              +------------+--------------+
                           |
                           v
                      Autoboxing
                           |
                           v
                     Collections
                           |
                           v
                    List<Integer>
```

---

# 39. Final Cheat Sheet

```text
Primitive                 Wrapper
---------                 -------
byte                      Byte
short                     Short
int                       Integer
long                      Long
float                     Float
double                    Double
char                      Character
boolean                   Boolean
```

Examples:

```java
// Primitive
int age = 30;

boolean active = true;

double salary = 1500.50;

char grade = 'A';
```

```java
// Wrapper
Integer age = 30;

Boolean active = true;

Double salary = 1500.50;

Character grade = 'A';
```

Nullable:

```java
Integer age = null;

Boolean active = null;

Long id = null;
```

Collections:

```java
List<Integer> numbers = new ArrayList<>();
```

Money:

```java
BigDecimal balance = new BigDecimal("1000.50");
```

---

# 40. Key Takeaway

The easiest rule to remember is:

```text
                     Java
                       |
             +---------+---------+
             |                   |
             v                   v
        Primitive             Object
             |                   |
             v                   v
           int               Integer
         boolean             Boolean
          double              Double
           char             Character
```

**Primitive types** are simple built-in value types.

**Wrapper classes** are object/reference types that represent primitive values and are especially useful when Java requires objects, such as collections and generics, or when `null` needs to be represented.

And one very important distinction for your future Spring Boot development:

```java
int age;
```

means the field always has a primitive `int` value (with Java's default initialization rules depending on where it is declared), while:

```java
Integer age;
```

allows the field to represent:

```text
30
25
0
null
```

That difference becomes particularly important when you work with **JPA/Hibernate entities, DTOs, JSON, database NULL values, and Java Generics**.

And the complete list is **8 primitive types**

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

This is a very good topic to clarify now because when we move into **Java OOP → Generics → Collections → Spring Boot/JPA**, you'll see `Integer`, `Long`, `Boolean`, `BigDecimal`, etc. everywhere.
