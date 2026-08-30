# 📘 Introduction to Java 21

## 1. What is Java?

Java is a **popular and powerful programming language**, originally created in 1995.  
It is currently owned by **Oracle**, and more than **3 billion devices run Java** worldwide.

### Common Uses of Java

- Mobile applications (especially Android apps)
- Desktop applications
- Web applications
- Web servers and application servers
- Games
- Database connections
- And much more!

---

## 2. Why Use Java?

Java remains one of the most widely used programming languages because:

- Works across multiple platforms (Windows, Mac, Linux, Raspberry Pi, etc.)
- Large demand in the job market
- Easy to learn and simple to use
- Open-source and free
- Secure, fast, and powerful
- Huge community support (tens of millions of developers)
- Object-oriented structure → clear program design and reusable code
- Similar to C++ and C#, making it easier for developers to switch

---

# 🚀 Get Started With Java 21

## 2.1. Installing Java

To begin coding in Java, you need to install the **Java Development Kit (JDK)**.

- Download the latest JDK (Java 21) from [Oracle](https://www.oracle.com/java/technologies/downloads/).
- Install it on your system (Windows, Mac, or Linux).
- Verify installation by running:

```bash
  java -version
```

✅ Expected output:

```
java version "21" 2023-09-19
Java(TM) SE Runtime Environment (build 21+35)
Java HotSpot(TM) 64-Bit Server VM (build 21+35, mixed mode)
```

## 2.2. Setting Up Environment

- On Windows: Add the JDK bin folder to your PATH environment variable.
- On Mac/Linux: Update your shell profile (.bashrc, .zshrc) with:

```
export PATH=$PATH:/usr/lib/jvm/java-21/bin
```

## 2.3. Using an IDE

While you can use any text editor, most developers prefer an IDE (Integrated Development Environment):

- IntelliJ IDEA (recommended for Java 21)
- Eclipse
- VS Code with Java extensions

These tools provide syntax highlighting, debugging, and project management.

# ✍️ Java Syntax and Statements

## 2.4. Basic Syntax Rules

- Every Java application must have a `main` method:

```java
public static void main(String[] args) { }
```

- Statements end with a semicolon (;).
- Code blocks are enclosed in curly braces { }.
- Java is case-sensitive (Hello ≠ hello).

### Keywords

Java has reserved words that cannot be used as identifiers:

```
Examples: class, public, static, void, if, else, while, return.
```

# 🖨️ Java Output / Print

## 1. Java Output (Printing to Console)

In Java, output is typically displayed using the `System.out` stream.

- `System.out.println()` → prints text followed by a newline.
- `System.out.print()` → prints text without adding a newline.
- `System.out.printf()` → prints formatted text.

### Example:

```java
public class OutputDemo {
    public static void main(String[] args) {
        System.out.println("Hello, World!"); // prints with newline
        System.out.print("Hello ");          // prints without newline
        System.out.print("Java");            // continues on same line
        System.out.printf("\nNumber: %d", 42); // formatted output
    }
}
```

✅ Output:

- Hello, World!
- Hello Java
- Number: 42

# 💬 Java Comments

Comments are ignored by the compiler. They are used to explain code and improve readability.

There are three types of Comments:

- Single-line comment: //
- Multi-line comment: /_ ... _/
- Documentation comment: /\*_ ... _/ (used for Javadoc)

```java
public class CommentDemo {
    public static void main(String[] args) {
        // This is a single-line comment
        System.out.println("Single-line comment above");

        /* This is a
           multi-line comment */
        System.out.println("Multi-line comment above");

        /**
         * This is a documentation comment
         * It can be used to generate Javadoc
         */
        System.out.println("Documentation comment above");
    }
}

```

## 3. First Java Program (Java 21)

### 3.1. Let’s write the classic **Hello World** program in Java 21:

```java
// HelloWorld.java
public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Hello, Java 21!");
    }
}
```

### 3.2. How to Run Java

- Save the file as HelloWorld.java.
- Compile the program:

```
javac HelloWorld.java
```

- 3.2. Run the program

```java
java HelloWorld
```

✅ Output

```
Hello, Java 21!
```

## 4. Online Simulator

### 🥇 My first recommendation: myCompiler

[myCompiler — Online Java 21 Compiler](https://www.mycompiler.io/online-java-compiler?utm_source=chatgpt.com)

This is probably the **best fit for our course** because it currently runs **Java 21**, is free, requires no installation or sign-up, and supports syntax highlighting, autocomplete, multiple files, terminal/stdin, and sharing. ([myCompiler][1])

For example, you can paste:

```java
public class Main {

    public static void main(String[] args) {

        String name = "David";

        System.out.println(
                "Hello " + name
        );
    }
}
```

and immediately click **Run**.

---

### 🥈 OneCompiler

[OneCompiler Java](https://onecompiler.org/java?utm_source=chatgpt.com)

Very good alternative. It is free, supports Java, standard input/output, and even dependency management with Gradle. However, its current Java compiler runs **Java 25**, so for our **Java 21 course**, I would prefer myCompiler when we specifically want Java 21 behavior. ([OneCompiler][2])

---

### 🥉 Programiz

[Programiz Online Compilers](https://www.programiz.com/?utm_source=chatgpt.com)

Programiz is especially nice for **beginners** because it combines an online compiler with interactive programming lessons. ([Programiz][3])

I'd use it when you want to learn a concept and practice it immediately.

---

### Other good choices

| Tool            | Free | Java version              | Best for                  |
| --------------- | ---- | ------------------------- | ------------------------- |
| **myCompiler**  | ✅   | **Java 21**               | ⭐ Our course             |
| **OneCompiler** | ✅   | Java 25                   | More advanced experiments |
| **Programiz**   | ✅   | Java                      | Beginners + lessons       |
| **JDoodle**     | ✅   | Multiple versions/options | Quick code testing        |
| **Codiva**      | ✅   | Java                      | Simple Java learning      |

JDoodle provides online Java compilers/editors and supports a broad range of programming languages. ([JDoodle][4]) Codiva is also designed specifically as an online Java compiler/IDE and supports interactive input. ([Codiva][5])

### ⭐ What I recommend for _your_ Java course

Since we've been building your lesson around **Java 21**, I would use:

```text
                 Your Java Course
                       |
                       v
                  Java 21
                       |
                       v
              ┌────────────────┐
              │   myCompiler   │
              │    Java 21     │
              └────────────────┘
                       |
          +------------+------------+
          |            |            |
          v            v            v
       Write         Run         Output
        Code         Code         Result
```
