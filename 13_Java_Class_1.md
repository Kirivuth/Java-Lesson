# Java Objects

## 1. What Is an Object?

In Java, an **object** is an instance of a class.

A class is a blueprint, while an object is a real instance created from that blueprint.

For example:

```java
public class Student {

    String name;
    int age;

    void study() {

        System.out.println(
                name + " is studying."
        );
    }
}
```

The `Student` class is a blueprint.

We can create objects from it:

```java
Student student1 =
        new Student();

Student student2 =
        new Student();
```

The relationship is:

```text
                 Class
                Student
                   |
          +--------+--------+
          |                 |
          v                 v
       Object 1          Object 2
       student1          student2
```

---

# 2. Class vs Object

A class describes what an object should contain and do.

An object is the actual instance created from that class.

```text
Class
 |
 +-- Fields
 |
 +-- Methods
 |
 +-- Constructor
 |
 v
Object
 |
 +-- Actual field values
 |
 +-- Actual state
 |
 +-- Behavior
```

Example:

```java
public class Car {

    String brand;

    void drive() {

        System.out.println(
                "Car is driving"
        );
    }
}
```

Create an object:

```java
Car car =
        new Car();
```

Here:

```text
Car
 |
 +-- Class

car
 |
 +-- Object
```

---

# 3. Creating an Object

Objects are normally created using the `new` keyword.

Syntax:

```java
ClassName variableName =
        new ClassName();
```

Example:

```java
Student student =
        new Student();
```

Another example:

```java
Car car =
        new Car();
```

Another:

```java
BankAccount account =
        new BankAccount();
```

---

# 4. What Happens When We Use `new`?

Consider:

```java
Student student =
        new Student();
```

Conceptually:

```text
                 new
                  |
                  v
           Create Student
              Object
                  |
                  v
        Initialize Object
                  |
                  v
        Call Constructor
                  |
                  v
        Return Reference
                  |
                  v
              student
```

The variable `student` contains a reference to the created object.

---

# 5. Object Reference

Consider:

```java
Student student =
        new Student();
```

It is useful to think of this as:

```text
student
   |
   | reference
   v
+-------------------+
| Student Object    |
|                   |
| name              |
| age               |
+-------------------+
```

The variable does not contain the entire object in the conceptual model.

It contains a reference to the object.

---

# 6. Object State

The data stored inside an object represents its state.

Example:

```java
public class Customer {

    String name;

    int age;
}
```

Create:

```java
Customer customer =
        new Customer();

customer.name = "David";
customer.age = 30;
```

The object's state is:

```text
Customer Object
 |
 +-- name = "David"
 |
 +-- age  = 30
```

---

# 7. Object Behavior

Methods represent an object's behavior.

Example:

```java
public class BankAccount {

    double balance;

    void deposit(
            double amount
    ) {

        balance += amount;
    }
}
```

The object contains:

```text
State
 |
 +-- balance

Behavior
 |
 +-- deposit()
```

So:

```text
Object
 |
 +-- State
 |
 +-- Behavior
```

---

# 8. Object State and Behavior

A useful way to understand objects is:

```text
                 Object
                   |
          +--------+--------+
          |                 |
          v                 v
        State            Behavior
          |                 |
          v                 v
       Fields            Methods
          |                 |
          v                 v
       name              deposit()
       age               withdraw()
       balance            transfer()
```

---

# 9. Multiple Objects

One class can create many objects.

Example:

```java
Student student1 =
        new Student();

Student student2 =
        new Student();

Student student3 =
        new Student();
```

Each object has its own state.

```text
                  Student Class
                       |
       +---------------+---------------+
       |               |               |
       v               v               v
   student1        student2        student3
       |               |               |
       v               v               v
     David           John            Mary
      20              25              22
```

---

# 10. Objects Have Independent State

Example:

```java
Student student1 =
        new Student();

Student student2 =
        new Student();

student1.name = "David";
student2.name = "John";
```

Now:

```text
student1
 |
 +-- name = David

student2
 |
 +-- name = John
```

Changing `student1` does not change `student2`.

---

# 11. Calling Methods on Objects

Use the dot operator:

```java
.
```

Example:

```java
student.study();
```

The structure is:

```text
object
  |
  v
.
  |
  v
method()
```

Example:

```java
Car car =
        new Car();

car.drive();
```

---

# 12. Accessing Object Fields

You can access an accessible field using `.`.

Example:

```java
Student student =
        new Student();

student.name = "David";

System.out.println(
        student.name
);
```

Output:

```text
David
```

However, in good object-oriented design, fields are usually kept `private`.

---

# 13. Objects and Constructors

Constructors initialize objects.

Example:

```java
public class Customer {

    String name;

    Customer(String name) {

        this.name = name;
    }
}
```

Create:

```java
Customer customer =
        new Customer("David");
```

The object starts with:

```text
Customer
 |
 +-- name = David
```

---

# 14. Object Creation Flow

```text
              Class
                |
                v
             new
                |
                v
        Memory allocated
                |
                v
       Fields initialized
                |
                v
          Constructor
                |
                v
         Object created
                |
                v
          Reference returned
```

---

# 15. Objects and `null`

A reference can contain `null`.

Example:

```java
Customer customer =
        null;
```

This means:

```text
customer
   |
   v
 null
```

There is currently no Customer object referenced by the variable.

---

# 16. NullPointerException

Consider:

```java
Customer customer =
        null;

customer.getName();
```

This can produce:

```text
NullPointerException
```

because there is no object to call the method on.

Safe checking:

```java
if (customer != null) {

    System.out.println(
            customer.getName()
    );
}
```

---

# 17. Two References to One Object

Consider:

```java
Customer customer1 =
        new Customer();

Customer customer2 =
        customer1;
```

Now both variables refer to the same object.

```text
customer1 --------+
                  |
                  v
            +-----------+
            | Customer  |
            | Object    |
            +-----------+
                  ^
                  |
customer2 --------+
```

Therefore:

```java
customer1 == customer2
```

returns:

```text
true
```

---

# 18. Object Reference Example

```java
Customer customer1 =
        new Customer();

Customer customer2 =
        customer1;

customer1.setName(
        "David"
);

System.out.println(
        customer2.getName()
);
```

Output:

```text
David
```

Why?

Because both references point to the same object.

---

# 19. Creating Different Objects

Compare:

```java
Customer customer1 =
        new Customer();

Customer customer2 =
        new Customer();
```

Now there are two different objects.

```text
customer1
   |
   v
+-----------+
| Customer  |
| Object 1  |
+-----------+


customer2
   |
   v
+-----------+
| Customer  |
| Object 2  |
+-----------+
```

Therefore:

```java
customer1 == customer2
```

returns:

```text
false
```

---

# 20. `==` vs `equals()`

For object references:

```java
==
```

checks whether two references point to the same object.

Example:

```java
customer1 == customer2
```

`equals()` is used to compare logical equality according to the class's implementation.

Example:

```java
customer1.equals(
        customer2
);
```

---

# 21. Object Identity

Object identity means:

```text
Are these references pointing
to exactly the same object?
```

Usually checked with:

```java
==
```

Example:

```java
Customer c1 =
        new Customer();

Customer c2 =
        c1;

System.out.println(
        c1 == c2
);
```

Output:

```text
true
```

---

# 22. Object Equality

Logical equality asks:

```text
Do these two objects represent
the same logical value?
```

For example, two Customer objects might represent the same customer if they have the same customer ID.

This is commonly implemented with:

```java
equals()
```

and:

```java
hashCode()
```

---

# 23. Passing Objects to Methods

Objects can be passed as method parameters.

Example:

```java
public void printCustomer(
        Customer customer
) {

    System.out.println(
            customer.getName()
    );
}
```

Call:

```java
Customer customer =
        new Customer();

printCustomer(customer);
```

---

# 24. Returning Objects from Methods

A method can return an object.

Example:

```java
public Customer createCustomer() {

    return new Customer(
            "David"
    );
}
```

Usage:

```java
Customer customer =
        createCustomer();
```

Flow:

```text
createCustomer()
       |
       v
new Customer()
       |
       v
Customer Object
       |
       v
returned to caller
```

---

# 25. Objects Inside Objects

Objects can contain references to other objects.

Example:

```java
public class Address {

    private String city;
}
```

Customer:

```java
public class Customer {

    private String name;

    private Address address;
}
```

Diagram:

```text
Customer
 |
 +-- name
 |
 +-- address
       |
       v
    Address
       |
       +-- city
```

This is a common example of composition.

---

# 26. HAS-A Relationship

When one class contains another object, we often describe it as a:

```text
HAS-A
```

relationship.

Examples:

```text
Car HAS-A Engine

Customer HAS-A Address

Order HAS-A Customer

BankAccount HAS-A Customer
```

Example:

```java
public class Car {

    private Engine engine;
}
```

---

# 27. IS-A Relationship

Inheritance represents an:

```text
IS-A
```

relationship.

Example:

```text
Dog IS-A Animal

SavingsAccount IS-A BankAccount

CreditCardPayment IS-A Payment
```

Java:

```java
public class Dog
        extends Animal {
}
```

---

# 28. Object Lifecycle

A simplified object lifecycle is:

```text
Class Definition
       |
       v
Object Creation
       |
       v
Initialization
       |
       v
Object Used
       |
       v
Object Becomes Unreachable
       |
       v
Garbage Collection
```

---

# 29. Garbage Collection

Java automatically manages memory using garbage collection.

If an object is no longer reachable, it can eventually be reclaimed by the JVM.

Example:

```java
Customer customer =
        new Customer();

customer = null;
```

Conceptually:

```text
Before:

customer -----> Customer Object


After:

customer -----> null

Customer Object
       |
       v
No longer reachable
       |
       v
Eligible for garbage collection
```

Garbage collection timing is controlled by the JVM; you should not rely on a specific moment when it occurs.

---

# 30. Object Creation with `new`

The `new` keyword is commonly used to create objects.

Examples:

```java
new Customer();
```

```java
new BankAccount();
```

```java
new ArrayList<>();
```

```java
new HashMap<>();
```

---

# 31. Objects from Java Libraries

Java provides many classes that you can instantiate.

Example:

```java
String name =
        new String("David");
```

Although for `String`, the literal form is usually preferred:

```java
String name =
        "David";
```

Another example:

```java
ArrayList<String> names =
        new ArrayList<>();
```

---

# 32. Object-Oriented Thinking

Instead of thinking only about functions, object-oriented programming asks:

```text
What objects exist?
        |
        v
What data do they have?
        |
        v
What can they do?
        |
        v
How do they interact?
        |
        v
What relationships exist?
```

Example banking system:

```text
Customer
    |
    +---- owns ----> BankAccount
                         |
                         +---- performs ----> Transaction
```

---

# 33. Banking Example

Consider a bank account.

```java
public class BankAccount {

    private String accountNumber;

    private BigDecimal balance;

    public void deposit(
            BigDecimal amount
    ) {

        balance =
                balance.add(amount);
    }

    public void withdraw(
            BigDecimal amount
    ) {

        balance =
                balance.subtract(amount);
    }
}
```

Object:

```java
BankAccount account =
        new BankAccount();
```

The object contains:

```text
BankAccount Object
 |
 +-- accountNumber
 |
 +-- balance
 |
 +-- deposit()
 |
 +-- withdraw()
```

---

# 34. Objects Interacting

Real applications contain many objects that interact.

Example:

```text
Customer
    |
    | owns
    v
BankAccount
    |
    | creates
    v
Transaction
    |
    | processed by
    v
PaymentService
```

A real application can contain thousands or millions of objects during execution.

---

# 35. Object-Oriented Application Diagram

```text
                  Application
                       |
       +---------------+---------------+
       |               |               |
       v               v               v
   Customer        Account          Payment
       |               |               |
       +---------------+---------------+
                       |
                       v
                  Transaction
```

Each object has its own responsibilities.

---

# 36. Objects and Encapsulation

A good object controls access to its internal state.

Bad design:

```java
public class BankAccount {

    public BigDecimal balance;
}
```

External code can directly modify it:

```java
account.balance =
        new BigDecimal("999999999");
```

Better:

```java
public class BankAccount {

    private BigDecimal balance;

    public void deposit(
            BigDecimal amount
    ) {

        // validation
        // business rules
        // update balance
    }

    public BigDecimal getBalance() {

        return balance;
    }
}
```

---

# 37. Objects and Abstraction

Objects can hide implementation details.

For example:

```java
account.withdraw(
        amount
);
```

The caller does not necessarily need to know:

```text
How balance is stored
How validation works
How transaction rules work
How database persistence works
How audit logging works
```

The object exposes the required behavior.

---

# 38. Objects and Polymorphism

A reference can point to different implementations.

Example:

```java
Payment payment =
        new CreditCardPayment();
```

Another:

```java
Payment payment =
        new BankTransferPayment();
```

Both can be used through the same interface:

```java
payment.pay(amount);
```

Diagram:

```text
                 Payment
                Interface
                    |
          +---------+---------+
          |                   |
          v                   v
 CreditCardPayment    BankTransferPayment
          |                   |
          v                   v
        pay()               pay()
```

---

# 39. Object-Oriented Design Flow

When designing a system:

```text
Business Requirement
        |
        v
Identify Objects
        |
        v
Identify Data
        |
        v
Identify Behavior
        |
        v
Define Relationships
        |
        v
Create Classes
        |
        v
Create Objects
        |
        v
Objects Interact
```

---

# 40. Class to Object Summary

```text
                 CLASS
                   |
             Blueprint
                   |
                   v
                  new
                   |
       +-----------+-----------+
       |           |           |
       v           v           v
    Object 1    Object 2    Object 3
       |           |           |
       v           v           v
     State       State       State
       |           |           |
       v           v           v
    Behavior     Behavior    Behavior
```

---

# 41. Important Object Concepts

| Concept            | Meaning                         |
| ------------------ | ------------------------------- |
| Object             | Instance of a class             |
| State              | Data stored in an object        |
| Behavior           | Actions provided by methods     |
| Reference          | Variable referring to an object |
| `new`              | Creates an object               |
| Constructor        | Initializes an object           |
| `this`             | Current object                  |
| `null`             | No object reference             |
| `==`               | Reference identity comparison   |
| `equals()`         | Logical equality                |
| Garbage Collection | Automatic memory reclamation    |

---

# 42. Object vs Primitive

Java has both primitive values and object references.

Primitive:

```java
int age = 30;
```

Object:

```java
Customer customer =
        new Customer();
```

Conceptually:

```text
Primitive
   |
   v
30


Reference
   |
   v
Customer Object
```

---

# 43. Wrapper Objects

Primitive values can have corresponding wrapper classes.

```text
int       -> Integer
long      -> Long
double    -> Double
boolean   -> Boolean
char      -> Character
```

Example:

```java
Integer age =
        Integer.valueOf(30);
```

Modern Java also supports autoboxing:

```java
Integer age = 30;
```

---

# 44. Object-Oriented Programming Foundation

Objects are the foundation of Java's object-oriented programming model.

The overall concept is:

```text
                    Java OOP
                       |
                       v
                    Classes
                       |
                       v
                    Objects
                       |
        +--------------+--------------+
        |              |              |
        v              v              v
 Encapsulation    Inheritance    Polymorphism
        |              |              |
        +--------------+--------------+
                       |
                       v
                   Abstraction
```

---

# 45. From Objects to OOP

Now that we understand objects, we can move to:

```text
Java Objects
      |
      v
Object-Oriented Programming
      |
      +--> Encapsulation
      |
      +--> Inheritance
      |
      +--> Polymorphism
      |
      +--> Abstraction
```

These four concepts are commonly called the:

```text
Four Pillars of OOP
```

---

# 46. Final Example

```java
public class Customer {

    private final Long id;

    private String name;

    public Customer(
            Long id,
            String name
    ) {

        this.id = id;
        this.name = name;
    }

    public Long getId() {

        return id;
    }

    public String getName() {

        return name;
    }

    public void setName(
            String name
    ) {

        this.name = name;
    }

    public void display() {

        System.out.println(
                "ID: " + id
        );

        System.out.println(
                "Name: " + name
        );
    }
}
```

Create an object:

```java
public class Main {

    public static void main(
            String[] args
    ) {

        Customer customer =
                new Customer(
                        1001L,
                        "David"
                );

        customer.display();

        customer.setName(
                "David Smith"
        );

        customer.display();
    }
}
```

Output:

```text
ID: 1001
Name: David

ID: 1001
Name: David Smith
```

The important idea is:

```text
Customer Class
      |
      | new
      v
Customer Object
      |
      +-- id
      +-- name
      |
      +-- getId()
      +-- getName()
      +-- setName()
      +-- display()
```

---

# 47. Key Takeaways

Remember these concepts:

```text
Class
    =
Blueprint

Object
    =
Instance of a Class

Field
    =
Object State

Method
    =
Object Behavior

Constructor
    =
Object Initialization

Reference
    =
Variable pointing to an Object

new
    =
Creates an Object

this
    =
Current Object

null
    =
No Object Reference

==
    =
Reference Identity

equals()
    =
Logical Equality
```

The most important relationship is:

```text
Class
   |
   | new
   v
Object
   |
   +-- State
   |
   +-- Behavior
```

And this leads directly to:

```text
Objects
   |
   v
OOP
   |
   +--> Encapsulation
   |
   +--> Abstraction
   |
   +--> Inheritance
   |
   +--> Polymorphism
```

These concepts are the foundation for understanding professional Java applications, including Spring Boot applications.

### Next session start from Object-Oriented Programming (OOP)

```
Java Classes
     |
     v
Java Objects
     |
     v
Object-Oriented Programming
     |
     +------------------+
     |                  |
     v                  v
Encapsulation       Abstraction
     |                  |
     v                  v
Inheritance <------> Interfaces
     |
     v
Polymorphism
     |
     v
Composition
     |
     v
SOLID Principles
     |
     v
Design Patterns
     |
     v
Spring Boot
     |
     v
Real Banking Application
```
