# Java Classes

## 1. What Is a Java Class?

A **class** is a blueprint or template used to create objects in Java.

A class defines:

- Data
- Properties
- Behavior
- Methods
- Constructors
- Rules for working with an object

For example, a `Car` class can describe:

```
Car
 |
 +-- Data
 |    |
 |    +-- brand
 |    +-- model
 |    +-- year
 |
 +-- Behavior
      |
      +-- start()
      +-- stop()
      +-- drive()
```

A simple Java class:

```java
public class Car {

    String brand;
    String model;
    int year;

    void start() {
        System.out.println("Car is starting...");
    }

    void stop() {
        System.out.println("Car is stopping...");
    }
}
```

The class itself is not a specific car.

It is a blueprint for creating car objects.

---

# 2. Class vs Object

A class is a blueprint.

An object is an actual instance created from that blueprint.

```text
                 Class
                  Car
                   |
          +--------+--------+
          |        |        |
          v        v        v
       Object   Object   Object
       Car #1   Car #2   Car #3
```

For example:

```java
Car car1 = new Car();
Car car2 = new Car();
Car car3 = new Car();
```

All three objects are created from the same `Car` class.

---

# 3. Creating a Class

The basic syntax is:

```java
class ClassName {

    // fields

    // methods

    // constructors
}
```

Example:

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

Here:

```text
Student
```

is the class name.

---

# 4. Class Naming Convention

Java class names normally use **PascalCase**.

Correct:

```java
Student
BankAccount
CustomerService
PaymentTransaction
LoanApplication
```

Avoid:

```java
student
bankaccount
customer_service
payment_transaction
```

Recommended:

```text
One class name
      |
      v
PascalCase
      |
      v
BankAccount
```

---

# 5. Fields

A field is a variable declared inside a class.

Example:

```java
public class Customer {

    String name;
    int age;
    String email;
}
```

The fields are:

```text
name
age
email
```

They represent the object's data or state.

---

# 6. Object State

The values stored inside an object's fields represent its **state**.

Example:

```java
Customer customer = new Customer();

customer.name = "John";
customer.age = 30;
customer.email = "john@example.com";
```

The object's state is:

```text
Customer
 |
 +-- name  = "John"
 +-- age   = 30
 +-- email = "john@example.com"
```

---

# 7. Methods

A method defines behavior.

Example:

```java
public class Customer {

    String name;

    void sayHello() {

        System.out.println(
                "Hello, my name is " + name
        );
    }
}
```

Calling the method:

```java
Customer customer = new Customer();

customer.name = "John";

customer.sayHello();
```

Output:

```text
Hello, my name is John
```

---

# 8. Class with Fields and Methods

Example:

```java
public class BankAccount {

    String accountNumber;
    String customerName;
    double balance;

    void deposit(double amount) {

        balance += amount;
    }

    void displayBalance() {

        System.out.println(
                "Balance: " + balance
        );
    }
}
```

The class contains:

```text
BankAccount
 |
 +-- Fields
 |    |
 |    +-- accountNumber
 |    +-- customerName
 |    +-- balance
 |
 +-- Methods
      |
      +-- deposit()
      +-- displayBalance()
```

---

# 9. Creating an Object

Use the `new` keyword.

```java
BankAccount account =
        new BankAccount();
```

The general syntax is:

```java
ClassName variable =
        new ClassName();
```

Example:

```java
Student student =
        new Student();
```

---

# 10. Accessing Object Fields

Use the dot `.` operator.

```java
Student student =
        new Student();

student.name = "David";
student.age = 20;
```

The dot operator means:

```text
object
  |
  v
.
  |
  v
field or method
```

Example:

```java
student.name
student.age
student.study()
```

---

# 11. Calling Object Methods

Example:

```java
public class Student {

    String name;

    void study() {

        System.out.println(
                name + " is studying."
        );
    }
}
```

Use:

```java
Student student =
        new Student();

student.name = "David";

student.study();
```

Output:

```text
David is studying.
```

---

# 12. Multiple Objects

One class can create many objects.

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
        +-----------+-----------+
        |           |           |
        v           v           v
    student1    student2    student3
       |           |           |
     David       John        Mary
      20          25          22
```

Changing one object does not automatically change the others.

---

# 13. Example of Multiple Objects

```java
public class Main {

    public static void main(String[] args) {

        Student student1 =
                new Student();

        Student student2 =
                new Student();

        student1.name = "David";
        student1.age = 20;

        student2.name = "John";
        student2.age = 25;

        System.out.println(
                student1.name
        );

        System.out.println(
                student2.name
        );
    }
}
```

Output:

```text
David
John
```

---

# 14. Constructors

A constructor is a special method used when an object is created.

Example:

```java
public class Student {

    String name;
    int age;

    Student() {

        System.out.println(
                "Student object created"
        );
    }
}
```

Create the object:

```java
Student student =
        new Student();
```

Output:

```text
Student object created
```

---

# 15. Constructor Rules

A constructor:

1. Has the same name as the class.
2. Does not have a return type.
3. Runs when an object is created.

Example:

```java
public class Customer {

    Customer() {

        System.out.println(
                "Customer created"
        );
    }
}
```

Notice there is no:

```java
void
```

or:

```java
int
```

before the constructor name.

---

# 16. Default Constructor

If you don't define any constructor, Java provides a default constructor automatically.

Example:

```java
public class Student {

    String name;
    int age;
}
```

Java effectively provides:

```java
Student() {
}
```

Therefore:

```java
Student student =
        new Student();
```

works.

---

# 17. User-Defined Constructor

You can create your own constructor.

```java
public class Student {

    String name;
    int age;

    Student(String name, int age) {

        this.name = name;
        this.age = age;
    }
}
```

Create an object:

```java
Student student =
        new Student("David", 20);
```

Now:

```text
student
 |
 +-- name = David
 +-- age  = 20
```

---

# 18. Constructor Parameters

A constructor can receive parameters.

```java
public class BankAccount {

    String accountNumber;
    double balance;

    BankAccount(
            String accountNumber,
            double balance
    ) {

        this.accountNumber =
                accountNumber;

        this.balance =
                balance;
    }
}
```

Create:

```java
BankAccount account =
        new BankAccount(
                "ACC1001",
                5000.00
        );
```

---

# 19. The `this` Keyword

`this` refers to the current object.

Example:

```java
public class Customer {

    String name;

    Customer(String name) {

        this.name = name;
    }
}
```

Here:

```java
this.name
```

means:

```text
Current object's name field
```

while:

```java
name
```

means:

```text
Constructor parameter
```

---

# 20. Understanding `this`

Consider:

```java
public class Customer {

    String name;

    Customer(String name) {

        this.name = name;
    }
}
```

The flow is:

```text
Constructor parameter
        |
        | name
        v
this.name = name
    |
    v
Object field
```

Without `this`, Java cannot clearly distinguish the field from the parameter when they have the same name.

---

# 21. Multiple Constructors

A class can have multiple constructors.

```java
public class Student {

    String name;
    int age;

    Student() {

        this.name = "Unknown";
        this.age = 0;
    }

    Student(String name) {

        this.name = name;
        this.age = 0;
    }

    Student(String name, int age) {

        this.name = name;
        this.age = age;
    }
}
```

This is called:

```text
Constructor Overloading
```

---

# 22. Constructor Overloading

Example:

```java
Student s1 =
        new Student();

Student s2 =
        new Student("David");

Student s3 =
        new Student(
                "John",
                25
        );
```

Java selects the appropriate constructor based on the arguments.

```text
new Student()
       |
       v
Constructor #1

new Student("David")
       |
       v
Constructor #2

new Student("John", 25)
       |
       v
Constructor #3
```

---

# 23. Methods with Return Values

A method can return a value.

Example:

```java
public class Calculator {

    int add(
            int a,
            int b
    ) {

        return a + b;
    }
}
```

Use it:

```java
Calculator calculator =
        new Calculator();

int result =
        calculator.add(
                10,
                20
        );

System.out.println(result);
```

Output:

```text
30
```

---

# 24. `void` Methods

A method with no return value uses:

```java
void
```

Example:

```java
void printHello() {

    System.out.println(
            "Hello"
    );
}
```

There is no returned value.

---

# 25. Method Parameters

Methods can receive parameters.

```java
public class Calculator {

    int multiply(
            int a,
            int b
    ) {

        return a * b;
    }
}
```

Call:

```java
Calculator calculator =
        new Calculator();

int result =
        calculator.multiply(
                5,
                10
        );
```

Result:

```text
50
```

---

# 26. Method Overloading

A class can have multiple methods with the same name if their parameter lists are different.

Example:

```java
public class Calculator {

    int add(
            int a,
            int b
    ) {

        return a + b;
    }

    double add(
            double a,
            double b
    ) {

        return a + b;
    }

    int add(
            int a,
            int b,
            int c
    ) {

        return a + b + c;
    }
}
```

This is called:

```text
Method Overloading
```

---

# 27. Method Overloading Rules

Methods can be overloaded by changing:

- Number of parameters
- Parameter types
- Parameter order

Example:

```java
add(int, int)

add(double, double)

add(int, int, int)

add(int, double)
```

Changing only the return type is not enough.

Invalid:

```java
int calculate() {
    return 10;
}

double calculate() {
    return 10.0;
}
```

This causes a compilation error.

---

# 28. Access Modifiers

Java classes, fields, constructors, and methods can have access modifiers.

The main access modifiers are:

```text
public
protected
default
private
```

Example:

```java
public class Customer {

    private String name;

    public void setName(
            String name
    ) {

        this.name = name;
    }
}
```

---

# 29. `public`

A `public` member can generally be accessed from other classes.

Example:

```java
public class Customer {

    public String name;
}
```

Use:

```java
Customer customer =
        new Customer();

customer.name = "David";
```

---

# 30. `private`

A `private` member can only be accessed inside its declaring class.

Example:

```java
public class BankAccount {

    private double balance;
}
```

This is not allowed from another class:

```java
BankAccount account =
        new BankAccount();

account.balance = 1000;
```

because `balance` is private.

---

# 31. Encapsulation

Encapsulation means keeping an object's internal data protected and controlling access through methods.

Instead of:

```java
public class BankAccount {

    public double balance;
}
```

prefer:

```java
public class BankAccount {

    private double balance;

    public double getBalance() {

        return balance;
    }

    public void deposit(
            double amount
    ) {

        if (amount > 0) {

            balance += amount;
        }
    }
}
```

This gives the class control over its data.

---

# 32. Encapsulation Diagram

```text
             BankAccount
                  |
        +---------+---------+
        |                   |
        v                   v
   private balance      public methods
                            |
                   +--------+--------+
                   |                 |
                   v                 v
                deposit()       getBalance()
```

The outside code does not directly modify:

```text
balance
```

Instead, it uses:

```text
deposit()
getBalance()
```

---

# 33. Getters and Setters

A getter reads a value.

A setter changes a value.

Example:

```java
public class Customer {

    private String name;

    public String getName() {

        return name;
    }

    public void setName(
            String name
    ) {

        this.name = name;
    }
}
```

Usage:

```java
Customer customer =
        new Customer();

customer.setName("David");

System.out.println(
        customer.getName()
);
```

---

# 34. Why Use Getters and Setters?

They allow validation and business rules.

Example:

```java
public void setAge(
        int age
) {

    if (age < 0) {

        throw new IllegalArgumentException(
                "Age cannot be negative"
        );
    }

    this.age = age;
}
```

Now invalid values can be rejected.

---

# 35. Static Fields

A `static` field belongs to the class rather than to individual objects.

Example:

```java
public class Counter {

    static int count = 0;

    Counter() {

        count++;
    }
}
```

Create objects:

```java
Counter c1 =
        new Counter();

Counter c2 =
        new Counter();

Counter c3 =
        new Counter();
```

The value of:

```java
Counter.count
```

is:

```text
3
```

---

# 36. Static vs Instance

Instance field:

```java
String name;
```

Each object has its own value.

Static field:

```java
static int count;
```

The class shares one value.

Diagram:

```text
                 Counter Class
                      |
                static count
                      |
                      v
                     3
                      ^
          +-----------+-----------+
          |           |           |
          v           v           v
         c1          c2          c3
```

---

# 37. Static Methods

A static method belongs to the class.

Example:

```java
public class Calculator {

    public static int add(
            int a,
            int b
    ) {

        return a + b;
    }
}
```

Call it without creating an object:

```java
int result =
        Calculator.add(
                10,
                20
        );
```

---

# 38. Instance Method vs Static Method

Instance method:

```java
Calculator calculator =
        new Calculator();

calculator.add(
        10,
        20
);
```

Static method:

```java
Calculator.add(
        10,
        20
);
```

Conceptually:

```text
Instance Method
      |
      v
Object-specific behavior


Static Method
      |
      v
Class-level behavior
```

---

# 39. Static Block

A static block runs when the class is initialized.

Example:

```java
public class Application {

    static {

        System.out.println(
                "Static block executed"
        );
    }

    public static void main(
            String[] args
    ) {

        System.out.println(
                "Main method"
        );
    }
}
```

Output:

```text
Static block executed
Main method
```

---

# 40. Instance Initializer Block

Java also supports instance initializer blocks.

Example:

```java
public class Student {

    {
        System.out.println(
                "Instance initializer"
        );
    }

    Student() {

        System.out.println(
                "Constructor"
        );
    }
}
```

When an object is created:

```java
Student student =
        new Student();
```

Output:

```text
Instance initializer
Constructor
```

---

# 41. Class Initialization Order

A simplified initialization flow is:

```text
Class Loading
      |
      v
Static Fields
      |
      v
Static Blocks
      |
      v
Object Creation
      |
      v
Instance Fields
      |
      v
Instance Initializers
      |
      v
Constructor
```

The exact details depend on the class structure and initialization process, but this is a useful learning model.

---

# 42. Nested Classes

A class can contain another class.

Example:

```java
public class Outer {

    class Inner {

        void show() {

            System.out.println(
                    "Inner class"
            );
        }
    }
}
```

This is called a:

```text
Nested Class
```

---

# 43. Static Nested Class

A nested class can be static.

```java
public class Outer {

    static class Inner {

        void show() {

            System.out.println(
                    "Static nested class"
            );
        }
    }
}
```

Create:

```java
Outer.Inner inner =
        new Outer.Inner();

inner.show();
```

---

# 44. Inner Class

A non-static nested class is commonly called an inner class.

```java
public class Outer {

    private String message =
            "Hello";

    class Inner {

        void print() {

            System.out.println(
                    message
            );
        }
    }
}
```

The inner class can access members of the outer object.

---

# 45. Local Class

A class can also be declared inside a method.

```java
public void process() {

    class Helper {

        void execute() {

            System.out.println(
                    "Processing..."
            );
        }
    }

    Helper helper =
            new Helper();

    helper.execute();
}
```

This is called a:

```text
Local Class
```

---

# 46. Anonymous Class

An anonymous class has no explicit class name.

Example:

```java
Runnable task =
        new Runnable() {

            @Override
            public void run() {

                System.out.println(
                        "Running..."
                );
            }
        };
```

Anonymous classes are useful when implementing something for a one-time purpose.

---

# 47. Abstract Classes

An abstract class is a class that cannot normally be instantiated directly.

Example:

```java
public abstract class Animal {

    public abstract void sound();

    public void sleep() {

        System.out.println(
                "Animal is sleeping"
        );
    }
}
```

You cannot do:

```java
Animal animal =
        new Animal();
```

Instead, another class extends it.

---

# 48. Extending an Abstract Class

```java
public class Dog
        extends Animal {

    @Override
    public void sound() {

        System.out.println(
                "Dog says: Woof"
        );
    }
}
```

Create:

```java
Dog dog =
        new Dog();

dog.sound();
dog.sleep();
```

---

# 49. Abstract Class Diagram

```text
                 Animal
             abstract class
                   |
          +--------+--------+
          |                 |
          v                 v
         Dog               Cat
          |                 |
       sound()            sound()
```

The abstract class provides common structure.

Subclasses provide specific behavior.

---

# 50. Final Classes

A `final` class cannot be extended.

Example:

```java
public final class SecurityToken {

    private String value;
}
```

This is not allowed:

```java
public class MyToken
        extends SecurityToken {
}
```

because `SecurityToken` is final.

---

# 51. Final Methods

A `final` method cannot be overridden by subclasses.

Example:

```java
public class Parent {

    public final void display() {

        System.out.println(
                "Parent display"
        );
    }
}
```

A child class cannot override:

```java
display()
```

---

# 52. Final Fields

A `final` field can normally be assigned only once.

Example:

```java
public class Customer {

    private final String customerId;

    public Customer(
            String customerId
    ) {

        this.customerId =
                customerId;
    }
}
```

After initialization:

```java
customerId
```

cannot be reassigned.

---

# 53. Object References

Consider:

```java
Customer customer =
        new Customer();
```

The variable:

```text
customer
```

holds a reference to an object.

Conceptually:

```text
Variable
customer
   |
   | reference
   v
+----------------+
| Customer Object|
|                |
| name           |
| age            |
+----------------+
```

---

# 54. Two References to One Object

Example:

```java
Customer customer1 =
        new Customer();

Customer customer2 =
        customer1;
```

Now both variables reference the same object.

```text
customer1 ----+
              |
              v
        +-------------+
        | Customer    |
        | Object      |
        +-------------+
              ^
              |
customer2 ----+
```

Changing the object through one reference can be visible through the other.

---

# 55. `null` References

A reference can contain:

```java
null
```

Example:

```java
Customer customer =
        null;
```

This means the variable does not currently refer to a Customer object.

Diagram:

```text
customer
    |
    v
  null
```

Calling:

```java
customer.getName();
```

can result in:

```text
NullPointerException
```

---

# 56. Object Equality

Two objects can be compared using:

```java
==
```

and:

```java
.equals()
```

For objects, `==` checks whether the references point to the same object.

Example:

```java
Customer c1 =
        new Customer();

Customer c2 =
        new Customer();

System.out.println(
        c1 == c2
);
```

Usually:

```text
false
```

because they are different objects.

---

# 57. `equals()`

`equals()` is intended to compare object content according to the class's equality definition.

Example:

```java
public class Customer {

    private String customerId;

    public Customer(
            String customerId
    ) {

        this.customerId =
                customerId;
    }

    @Override
    public boolean equals(
            Object obj
    ) {

        if (this == obj) {
            return true;
        }

        if (!(obj instanceof Customer other)) {
            return false;
        }

        return customerId.equals(
                other.customerId
        );
    }
}
```

---

# 58. `hashCode()`

When overriding `equals()`, you should also correctly override:

```java
hashCode()
```

Example:

```java
@Override
public int hashCode() {

    return Objects.hash(
            customerId
    );
}
```

This is important when objects are used in collections such as:

```java
HashSet
HashMap
```

---

# 59. `toString()`

Every Java object inherits a `toString()` method from `Object`.

You can override it to provide useful information.

Example:

```java
public class Customer {

    private String name;
    private int age;

    @Override
    public String toString() {

        return "Customer{" +
                "name='" + name + '\'' +
                ", age=" + age +
                '}';
    }
}
```

Then:

```java
Customer customer =
        new Customer();

System.out.println(
        customer
);
```

can produce:

```text
Customer{name='David', age=30}
```

---

# 60. Java `Object` Class

Every Java class ultimately inherits from:

```java
Object
```

For example:

```text
Object
  |
  v
Customer
  |
  v
MyCustomer
```

Common methods inherited from `Object` include:

```java
toString()
equals()
hashCode()
getClass()
```

---

# 61. Inheritance

Inheritance allows one class to reuse and extend another class.

Syntax:

```java
class Child
        extends Parent {

}
```

Example:

```java
public class Animal {

    void eat() {

        System.out.println(
                "Animal is eating"
        );
    }
}
```

Child:

```java
public class Dog
        extends Animal {

    void bark() {

        System.out.println(
                "Dog is barking"
        );
    }
}
```

---

# 62. Inheritance Diagram

```text
                 Animal
                    |
                    |
                  extends
                    |
                    v
                   Dog
                 /     \
                /       \
             eat()     bark()
```

The `Dog` class inherits:

```java
eat()
```

from `Animal`.

---

# 63. Method Overriding

A child class can provide its own implementation of a parent method.

Example:

```java
public class Animal {

    void sound() {

        System.out.println(
                "Animal sound"
        );
    }
}
```

Child:

```java
public class Dog
        extends Animal {

    @Override
    void sound() {

        System.out.println(
                "Woof"
        );
    }
}
```

This is called:

```text
Method Overriding
```

---

# 64. Polymorphism

Polymorphism allows a parent reference to point to a child object.

Example:

```java
Animal animal =
        new Dog();

animal.sound();
```

Although the reference type is:

```text
Animal
```

the actual object is:

```text
Dog
```

Therefore the overridden `Dog.sound()` method runs.

---

# 65. Polymorphism Diagram

```text
             Animal reference
                    |
                    v
             +-------------+
             | Dog object  |
             +-------------+
                    |
                    v
             Dog.sound()
                    |
                    v
                  "Woof"
```

---

# 66. `super` Keyword

The `super` keyword refers to the parent class.

Example:

```java
public class Dog
        extends Animal {

    void show() {

        super.eat();

        System.out.println(
                "Dog"
        );
    }
}
```

Here:

```java
super.eat();
```

calls the parent implementation.

---

# 67. Calling Parent Constructor

`super()` can also call the parent constructor.

```java
public class Animal {

    Animal(String name) {

        System.out.println(
                "Animal: " + name
        );
    }
}
```

Child:

```java
public class Dog
        extends Animal {

    Dog(String name) {

        super(name);
    }
}
```

The parent constructor runs before the child constructor body.

---

# 68. Composition

Composition means a class contains another object.

Example:

```java
public class Engine {

    void start() {

        System.out.println(
                "Engine started"
        );
    }
}
```

Car:

```java
public class Car {

    private Engine engine =
            new Engine();

    void start() {

        engine.start();
    }
}
```

Diagram:

```text
Car
 |
 +-- Engine
      |
      +-- start()
```

---

# 69. Inheritance vs Composition

Inheritance:

```text
Dog IS-A Animal
```

Composition:

```text
Car HAS-A Engine
```

A useful rule:

```text
IS-A
  |
  v
Inheritance

HAS-A
  |
  v
Composition
```

---

# 70. Interface

An interface defines a contract that classes can implement.

Example:

```java
public interface Payment {

    void pay(
            double amount
    );
}
```

Implementation:

```java
public class CreditCardPayment
        implements Payment {

    @Override
    public void pay(
            double amount
    ) {

        System.out.println(
                "Paid by credit card: "
                        + amount
        );
    }
}
```

---

# 71. Interface Diagram

```text
                 Payment
                interface
                    |
          +---------+---------+
          |                   |
          v                   v
 CreditCardPayment      BankTransferPayment
          |                   |
          v                   v
       pay()                pay()
```

---

# 72. Class Structure Example

A typical Java class can contain:

```text
Class
 |
 +-- Fields
 |
 +-- Constructors
 |
 +-- Methods
 |
 +-- Static Members
 |
 +-- Nested Classes
 |
 +-- Initialization Blocks
```

Example:

```java
public class Customer {

    // Field
    private String name;

    // Constructor
    public Customer(String name) {

        this.name = name;
    }

    // Method
    public String getName() {

        return name;
    }

    // Method
    public void display() {

        System.out.println(name);
    }
}
```

---

# 73. Complete Class Example

```java
public class BankAccount {

    private final String accountNumber;

    private String customerName;

    private double balance;

    public BankAccount(
            String accountNumber,
            String customerName,
            double initialBalance
    ) {

        if (initialBalance < 0) {

            throw new IllegalArgumentException(
                    "Initial balance cannot be negative"
            );
        }

        this.accountNumber =
                accountNumber;

        this.customerName =
                customerName;

        this.balance =
                initialBalance;
    }

    public void deposit(
            double amount
    ) {

        if (amount <= 0) {

            throw new IllegalArgumentException(
                    "Deposit amount must be positive"
            );
        }

        balance += amount;
    }

    public void withdraw(
            double amount
    ) {

        if (amount <= 0) {

            throw new IllegalArgumentException(
                    "Withdrawal amount must be positive"
            );
        }

        if (amount > balance) {

            throw new IllegalArgumentException(
                    "Insufficient balance"
            );
        }

        balance -= amount;
    }

    public double getBalance() {

        return balance;
    }

    public String getAccountNumber() {

        return accountNumber;
    }

    public String getCustomerName() {

        return customerName;
    }
}
```

---

# 74. Using the BankAccount Class

```java
public class Main {

    public static void main(
            String[] args
    ) {

        BankAccount account =
                new BankAccount(
                        "ACC10001",
                        "David",
                        1000.00
                );

        account.deposit(
                500.00
        );

        account.withdraw(
                200.00
        );

        System.out.println(
                "Account: "
                        + account.getAccountNumber()
        );

        System.out.println(
                "Customer: "
                        + account.getCustomerName()
        );

        System.out.println(
                "Balance: "
                        + account.getBalance()
        );
    }
}
```

Output:

```text
Account: ACC10001
Customer: David
Balance: 1300.0
```

---

# 75. Class Design Flow

When designing a class, think about:

```text
                  What is the object?
                         |
                         v
                    Class Name
                         |
                         v
                  What data does
                  it contain?
                         |
                         v
                       Fields
                         |
                         v
                  What can it do?
                         |
                         v
                      Methods
                         |
                         v
                How is it created?
                         |
                         v
                    Constructor
                         |
                         v
                What should be hidden?
                         |
                         v
                  Encapsulation
```

---

# 76. Class and Object Real-World Example

Consider a banking system.

A customer account can be modeled as:

```text
                  BankAccount
                       |
        +--------------+--------------+
        |              |              |
        v              v              v
 accountNumber    customerName     balance
        |
        +-----------------------------+
                                      |
                                      v
                                  Methods
                                      |
                         +------------+------------+
                         |            |            |
                         v            v            v
                      deposit()   withdraw()  getBalance()
```

Java:

```java
public class BankAccount {

    private String accountNumber;
    private String customerName;
    private BigDecimal balance;

    public void deposit(
            BigDecimal amount
    ) {
        // ...
    }

    public void withdraw(
            BigDecimal amount
    ) {
        // ...
    }

    public BigDecimal getBalance() {
        // ...
    }
}
```

---

# 77. Class Relationships

Java applications commonly contain relationships such as:

```text
Inheritance
    |
    v
IS-A

Composition
    |
    v
HAS-A

Association
    |
    v
USES / KNOWS

Implementation
    |
    v
IMPLEMENTS
```

Example:

```text
Dog
 |
 +-- IS-A --> Animal

Car
 |
 +-- HAS-A --> Engine

OrderService
 |
 +-- USES --> OrderRepository

CreditCardPayment
 |
 +-- IMPLEMENTS --> Payment
```

---

# 78. POJO

POJO means:

```text
Plain Old Java Object
```

A POJO is a normal Java class without requiring it to extend a special framework class.

Example:

```java
public class Customer {

    private Long id;

    private String name;

    private String email;

    public Customer() {
    }

    public Customer(
            Long id,
            String name,
            String email
    ) {

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

POJOs are widely used in Java applications.

---

# 79. JavaBean

A JavaBean traditionally follows conventions such as:

- Private fields
- Public getters
- Public setters
- No-argument constructor

Example:

```java
public class Customer {

    private String name;

    public Customer() {
    }

    public String getName() {

        return name;
    }

    public void setName(
            String name
    ) {

        this.name = name;
    }
}
```

---

# 80. Immutable Class

An immutable object cannot have its state changed after creation.

Example:

```java
public final class Customer {

    private final String id;

    private final String name;

    public Customer(
            String id,
            String name
    ) {

        this.id = id;
        this.name = name;
    }

    public String getId() {

        return id;
    }

    public String getName() {

        return name;
    }
}
```

There are:

```text
No setters
Final fields
Final class
State initialized in constructor
```

---

# 81. Mutable vs Immutable

Mutable:

```text
Object
  |
  v
State can change
```

Example:

```java
customer.setName("John");
```

Immutable:

```text
Object
  |
  v
State cannot change
```

Instead of modifying it, you create another object.

---

# 82. Why Immutability Is Useful

Immutable objects can make applications easier to reason about.

Benefits include:

```text
Predictable state
Thread-safety advantages
Easier debugging
Safer sharing
Reduced accidental modification
```

Java's `String` is a famous immutable class.

---

# 83. Records

Modern Java provides `record` for concise data-carrying classes.

Example:

```java
public record Customer(
        Long id,
        String name,
        String email
) {
}
```

This automatically provides methods such as:

```text
Constructor
Accessors
equals()
hashCode()
toString()
```

For example:

```java
Customer customer =
        new Customer(
                1L,
                "David",
                "david@example.com"
        );

System.out.println(
        customer.name()
);
```

Records are especially useful for immutable data models and DTO-style objects.

---

# 84. Class vs Record

Traditional class:

```java
public class Customer {

    private final Long id;

    private final String name;

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
}
```

Record:

```java
public record Customer(
        Long id,
        String name
) {
}
```

A record is much more concise.

---

# 85. Class Modifiers

A class can use modifiers such as:

```text
public
abstract
final
sealed
non-sealed
```

Examples:

```java
public class Customer {
}
```

```java
public abstract class Animal {
}
```

```java
public final class SecurityToken {
}
```

Java also supports sealed classes for controlling inheritance.

---

# 86. Sealed Classes

A sealed class restricts which classes can extend it.

Example:

```java
public sealed class Payment
        permits
        CreditCardPayment,
        BankTransferPayment {
}
```

Then:

```java
public final class CreditCardPayment
        extends Payment {
}
```

and:

```java
public final class BankTransferPayment
        extends Payment {
}
```

Only permitted classes can directly extend `Payment`.

---

# 87. Sealed Class Diagram

```text
                    Payment
                   sealed class
                        |
             +----------+----------+
             |                     |
             v                     v
    CreditCardPayment      BankTransferPayment
          final                   final
```

This is useful when the set of allowed subclasses should be controlled.

---

# 88. Class Loading Concept

Before Java can use a class, the JVM loads and initializes it as needed.

A simplified concept:

```text
Java Source
     |
     v
   javac
     |
     v
.class file
     |
     v
JVM Class Loader
     |
     v
Class Loaded
     |
     v
Class Initialized
     |
     v
Object Created
```

---

# 89. `.java` vs `.class`

Java source file:

```text
Customer.java
```

contains:

```java
public class Customer {
}
```

The Java compiler produces:

```text
Customer.class
```

The JVM executes the compiled bytecode.

```text
Customer.java
     |
     | javac
     v
Customer.class
     |
     | JVM
     v
Running Program
```

---

# 90. One Public Class per File

A public top-level class normally has the same name as the file.

Example:

```text
Customer.java
```

contains:

```java
public class Customer {
}
```

The names match:

```text
File Name
Customer.java

Class Name
Customer
```

---

# 91. Package and Class

Classes are normally organized into packages.

Example:

```java
package com.example.customer;

public class Customer {

}
```

Directory structure:

```text
src
 |
 +-- main
      |
      +-- java
           |
           +-- com
                |
                +-- example
                     |
                     +-- customer
                          |
                          +-- Customer.java
```

---

# 92. Importing Classes

A class from another package can be imported.

Example:

```java
import java.util.ArrayList;
```

Then:

```java
ArrayList<String> names =
        new ArrayList<>();
```

Without the import, you can use the fully qualified name:

```java
java.util.ArrayList<String> names =
        new java.util.ArrayList<>();
```

---

# 93. Class Design Best Practices

When creating Java classes:

### 1. Give the class one clear responsibility

Good:

```text
CustomerService
AccountService
PaymentService
```

Avoid a class that does everything:

```text
EverythingService
```

---

### 2. Keep fields private

Prefer:

```java
private String name;
```

instead of:

```java
public String name;
```

---

### 3. Protect object state

Use:

```text
Constructors
Getters
Setters when appropriate
Validation
Business methods
```

---

### 4. Prefer composition when appropriate

Instead of creating deep inheritance hierarchies, consider:

```text
HAS-A
```

relationships.

---

### 5. Keep methods focused

A method should have a clear purpose.

---

# 94. Common Mistakes

### Mistake 1: Public fields everywhere

Avoid:

```java
public double balance;
```

Prefer:

```java
private double balance;
```

---

### Mistake 2: Huge classes

Avoid classes containing hundreds or thousands of unrelated responsibilities.

---

### Mistake 3: Too much inheritance

Avoid deep inheritance hierarchies when composition would be clearer.

---

### Mistake 4: No validation

Don't allow invalid object state.

For example:

```java
balance = -999999;
```

may not make sense for a bank account.

---

### Mistake 5: Exposing internal collections

Avoid unnecessarily returning mutable internal collections directly.

---

# 95. Class Design Example for Banking

A banking application might contain:

```text
Banking Application
        |
        +-- Customer
        |
        +-- BankAccount
        |
        +-- Transaction
        |
        +-- Payment
        |
        +-- Loan
        |
        +-- Card
        |
        +-- Branch
```

Each class has its own responsibility.

Example:

```java
public class Customer {

    private Long id;

    private String name;

    private String email;
}
```

Account:

```java
public class BankAccount {

    private String accountNumber;

    private BigDecimal balance;

    public void deposit(
            BigDecimal amount
    ) {
        // ...
    }

    public void withdraw(
            BigDecimal amount
    ) {
        // ...
    }
}
```

Transaction:

```java
public class Transaction {

    private String transactionId;

    private BigDecimal amount;

    private String transactionType;
}
```

---

# 96. Object-Oriented Programming

Java classes are the foundation of Object-Oriented Programming.

The four major OOP concepts are:

```text
              OOP
               |
       +-------+-------+
       |       |       |
       v       v       v
 Encapsulation Inheritance Polymorphism
       |
       v
 Abstraction
```

More commonly represented as:

```text
Encapsulation
Inheritance
Polymorphism
Abstraction
```

Classes are used to implement these concepts.

---

# 97. Four Pillars of OOP

## Encapsulation

Protect object state.

```java
private BigDecimal balance;
```

---

## Inheritance

Reuse and extend another class.

```java
class Dog
        extends Animal {
}
```

---

## Polymorphism

One interface/reference can represent different implementations.

```java
Animal animal =
        new Dog();
```

---

## Abstraction

Expose important behavior while hiding implementation details.

```java
public interface Payment {

    void pay(
            BigDecimal amount
    );
}
```

---

# 98. Java Class Complete Concept Diagram

```text
                         Java Class
                             |
        +--------------------+--------------------+
        |                    |                    |
        v                    v                    v
      State              Behavior             Creation
        |                    |                    |
        v                    v                    v
     Fields               Methods            Constructor
        |                    |
        |                    |
        +----------+---------+
                   |
                   v
                 Object
                   |
        +----------+----------+
        |                     |
        v                     v
    Encapsulation        Business Logic
        |
        v
    private fields
    getters/setters
    validation
```

---

# 99. Class to Object Flow

```text
                    Java Class
                       |
                       |
                 Blueprint
                       |
                       v
                     new
                       |
          +------------+------------+
          |            |            |
          v            v            v
       Object 1     Object 2     Object 3
          |            |            |
          v            v            v
        State        State        State
          |            |            |
          v            v            v
       Behavior      Behavior     Behavior
```

---

# 100. Important Keywords Related to Classes

| Keyword      | Purpose                                                       |
| ------------ | ------------------------------------------------------------- |
| `class`      | Defines a class                                               |
| `new`        | Creates an object                                             |
| `this`       | Refers to current object                                      |
| `super`      | Refers to parent class                                        |
| `static`     | Class-level member                                            |
| `final`      | Prevents reassignment/extension/overriding depending on usage |
| `abstract`   | Defines incomplete/abstract class or method                   |
| `extends`    | Inherits from a class                                         |
| `implements` | Implements an interface                                       |
| `public`     | Public access                                                 |
| `private`    | Private access                                                |
| `protected`  | Protected access                                              |

---

# 101. Quick Reference

Create a class:

```java
public class Customer {
}
```

Create an object:

```java
Customer customer =
        new Customer();
```

Create a field:

```java
private String name;
```

Create a constructor:

```java
public Customer(
        String name
) {

    this.name = name;
}
```

Create a method:

```java
public void display() {

    System.out.println(name);
}
```

Get a value:

```java
public String getName() {

    return name;
}
```

Set a value:

```java
public void setName(
        String name
) {

    this.name = name;
}
```

Extend a class:

```java
class Dog
        extends Animal {
}
```

Implement an interface:

```java
class PaymentService
        implements Payment {
}
```

---

# 102. Final Example

Here is a complete example combining several concepts:

```java
public class Customer {

    private final Long id;

    private String name;

    private String email;

    public Customer(
            Long id,
            String name,
            String email
    ) {

        if (id == null) {

            throw new IllegalArgumentException(
                    "ID cannot be null"
            );
        }

        if (name == null ||
                name.isBlank()) {

            throw new IllegalArgumentException(
                    "Name cannot be empty"
            );
        }

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

    public void setName(
            String name
    ) {

        if (name == null ||
                name.isBlank()) {

            throw new IllegalArgumentException(
                    "Name cannot be empty"
            );
        }

        this.name = name;
    }

    public String getEmail() {

        return email;
    }

    public void setEmail(
            String email
    ) {

        this.email = email;
    }

    public void display() {

        System.out.println(
                "Customer ID: " + id
        );

        System.out.println(
                "Customer Name: " + name
        );

        System.out.println(
                "Email: " + email
        );
    }

    @Override
    public String toString() {

        return "Customer{" +
                "id=" + id +
                ", name='" + name + '\'' +
                ", email='" + email + '\'' +
                '}';
    }
}
```

Usage:

```java
public class Main {

    public static void main(
            String[] args
    ) {

        Customer customer =
                new Customer(
                        1001L,
                        "David",
                        "david@example.com"
                );

        customer.display();

        customer.setName(
                "David Smith"
        );

        System.out.println(
                customer
        );
    }
}
```

---

# 103. Final Summary

A Java class is a blueprint used to create objects.

The most important concepts are:

```text
Class
   |
   +-- Fields
   |
   +-- Methods
   |
   +-- Constructors
   |
   +-- Access Modifiers
   |
   +-- Static Members
   |
   +-- Nested Classes
   |
   +-- Inheritance
   |
   +-- Encapsulation
   |
   +-- Abstraction
   |
   +-- Polymorphism
```

The basic relationship is:

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

Remember:

```text
Class = Blueprint

Object = Instance of a Class

Field = Object Data

Method = Object Behavior

Constructor = Object Initialization

this = Current Object

super = Parent Class

static = Class-Level Member

private = Encapsulated Member

extends = Inheritance

implements = Interface Implementation
```

A good Java class should have:

```text
Clear responsibility
        |
        v
Encapsulated state
        |
        v
Meaningful methods
        |
        v
Valid object state
        |
        v
Clean relationships
```

This is the foundation for understanding the next major Java topics:

```text
Classes
   |
   +--> Objects
   |
   +--> OOP
   |
   +--> Inheritance
   |
   +--> Interfaces
   |
   +--> Abstract Classes
   |
   +--> Polymorphism
   |
   +--> Encapsulation
   |
   +--> Design Patterns
   |
   +--> Spring Boot
```
