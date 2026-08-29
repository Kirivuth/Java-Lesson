# 📘 Java I/O Streams

---

## 1. What Is Java I/O?

**I/O** stands for:

> Input / Output

Java I/O is used to communicate with external resources such as:

- Files
- Network connections
- Keyboard input
- Console output
- Memory
- Databases
- Other applications

The basic idea is:

````text
Input
  |
  v
Java Application
  |
  v
Output


For example:

```text
File
 |
 | Read
 v
Java Application
 |
 | Write
 v
File
````

---

# 2. What Is an I/O Stream?

A **Stream** is a sequence of data flowing between a source and a destination.

Think of a stream like a pipe:

```text
Source
  |
  | Data
  v
====================
      Stream
====================
  |
  | Data
  v
Destination
```

For example:

```text
File
 |
 | Input Stream
 v
Java Application
```

And:

```text
Java Application
 |
 | Output Stream
 v
File
```

---

# 3. Input vs Output

There are two main directions.

### Input

Data comes **into** the Java application.

```text
File
  |
  v
InputStream
  |
  v
Java Application
```

### Output

Data goes **out of** the Java application.

```text
Java Application
  |
  v
OutputStream
  |
  v
File
```

---

# 4. Java I/O Stream Hierarchy

Java has two major categories of streams:

```text
Java I/O Streams
       |
       +-------------------+
       |                   |
       v                   v
   Byte Streams       Character Streams
       |                   |
       v                   v
 InputStream            Reader
 OutputStream           Writer
```

---

# 5. Byte Streams

**Byte Streams** are used to process raw binary data.

They work with:

```text
byte
```

The main classes are:

```java
InputStream
OutputStream
```

Byte streams are commonly used for:

- Images
- PDF files
- ZIP files
- Audio
- Video
- Binary files

---

# 6. Character Streams

**Character Streams** are designed to process text data.

The main classes are:

```java
Reader
Writer
```

They are commonly used for:

- Text files
- CSV
- XML
- JSON
- Configuration files
- Log files

---

# 7. Byte Stream vs Character Stream

| Feature      | Byte Stream     | Character Stream |
| ------------ | --------------- | ---------------- |
| Base class   | `InputStream`   | `Reader`         |
| Output class | `OutputStream`  | `Writer`         |
| Data         | Bytes           | Characters       |
| Common use   | Binary files    | Text files       |
| Examples     | Image, PDF, ZIP | TXT, CSV, XML    |

---

# 8. InputStream

`InputStream` is the base class for reading byte data.

Example:

```java
InputStream input =
        Files.newInputStream(
                Path.of("data.txt")
        );
```

You can read data from the stream:

```java
int data = input.read();
```

The `read()` method returns:

```text
0 - 255
```

for a byte value, or:

```text
-1
```

when the end of the stream is reached.

---

# 9. Reading One Byte at a Time

Example:

```java
import java.io.IOException;
import java.io.InputStream;
import java.nio.file.Files;
import java.nio.file.Path;

public class Main {

    public static void main(String[] args)
            throws IOException {

        Path path =
                Path.of("data.txt");

        try (InputStream input =
                Files.newInputStream(path)) {

            int data;

            while ((data = input.read()) != -1) {

                System.out.print(
                        (char) data
                );
            }
        }
    }
}
```

If the file contains:

```text
Hello
```

Output:

```text
Hello
```

---

# 10. Why Does read() Return int?

You might wonder:

> Why does `InputStream.read()` return `int` instead of `byte`?

Because Java needs a special value to indicate the end of the stream.

The possible result is:

```text
0 - 255
```

or:

```text
-1 = End of Stream
```

Therefore, `int` is used.

---

# 11. Reading Using a Buffer

Reading one byte at a time may be inefficient.

Instead, use a buffer.

```java
byte[] buffer =
        new byte[1024];
```

Example:

```java
try (InputStream input =
        Files.newInputStream(
                Path.of("data.txt")
        )) {

    byte[] buffer =
            new byte[1024];

    int bytesRead;

    while ((bytesRead =
            input.read(buffer)) != -1) {

        System.out.println(
                "Read: "
                        + bytesRead
                        + " bytes"
        );
    }
}
```

---

# 12. Why Use a Buffer?

Without a buffer:

```text
Read byte
Read byte
Read byte
Read byte
Read byte
...
```

With a buffer:

```text
Read 1024 bytes
       |
       v
Process data
       |
       v
Read next 1024 bytes
```

This can significantly reduce the number of I/O operations.

---

# 13. OutputStream

`OutputStream` is the base class for writing byte data.

Example:

```java
OutputStream output =
        Files.newOutputStream(
                Path.of("data.bin")
        );
```

Write a byte:

```java
output.write(65);
```

ASCII value `65` represents:

```text
A
```

---

# 14. Writing Bytes

Example:

```java
import java.io.IOException;
import java.io.OutputStream;
import java.nio.file.Files;
import java.nio.file.Path;

public class Main {

    public static void main(String[] args)
            throws IOException {

        Path path =
                Path.of("data.bin");

        try (OutputStream output =
                Files.newOutputStream(path)) {

            output.write(65);
            output.write(66);
            output.write(67);
        }
    }
}
```

The file contains:

```text
ABC
```

---

# 15. Writing a Byte Array

Instead of writing one byte at a time:

```java
byte[] data =
        {65, 66, 67};

try (OutputStream output =
        Files.newOutputStream(
                Path.of("data.bin")
        )) {

    output.write(data);
}
```

---

# 16. InputStream + OutputStream

A very common operation is copying data from one stream to another.

```text
Source
  |
  v
InputStream
  |
  v
Buffer
  |
  v
OutputStream
  |
  v
Destination
```

Example:

```java
Path source =
        Path.of("source.dat");

Path target =
        Path.of("target.dat");

try (
    InputStream input =
            Files.newInputStream(source);

    OutputStream output =
            Files.newOutputStream(target)
) {

    byte[] buffer =
            new byte[8192];

    int bytesRead;

    while ((bytesRead =
            input.read(buffer)) != -1) {

        output.write(
                buffer,
                0,
                bytesRead
        );
    }
}
```

---

# 17. BufferedInputStream

Java provides:

```java
BufferedInputStream
```

It adds buffering to an input stream.

Example:

```java
try (
    InputStream input =
            new BufferedInputStream(
                    Files.newInputStream(
                            Path.of("data.bin")
                    )
            )
) {

    int data;

    while ((data = input.read()) != -1) {

        // Process byte
    }
}
```

---

# 18. BufferedOutputStream

Similarly:

```java
BufferedOutputStream
```

can buffer output.

Example:

```java
try (
    OutputStream output =
            new BufferedOutputStream(
                    Files.newOutputStream(
                            Path.of("data.bin")
                    )
            )
) {

    output.write(65);
    output.write(66);
    output.write(67);
}
```

The buffered stream collects data and writes it more efficiently.

---

# 19. Reader

`Reader` is the base class for character input.

Example:

```java
Reader reader =
        Files.newBufferedReader(
                Path.of("data.txt")
        );
```

A reader works with characters rather than raw bytes.

---

# 20. Reading Characters

Example:

```java
try (
    Reader reader =
            Files.newBufferedReader(
                    Path.of("data.txt")
            )
) {

    int character;

    while ((character =
            reader.read()) != -1) {

        System.out.print(
                (char) character
        );
    }
}
```

---

# 21. Writer

`Writer` is the base class for character output.

Example:

```java
try (
    Writer writer =
            Files.newBufferedWriter(
                    Path.of("message.txt")
            )
) {

    writer.write("Hello Java!");
}
```

---

# 22. Reader vs InputStream

The main difference is the type of data.

```text
InputStream
     |
     v
   Bytes
```

while:

```text
Reader
     |
     v
 Characters
```

For example:

```text
Image
 |
 v
InputStream
```

For:

```text
Text File
 |
 v
Reader
```

---

# 23. Writer vs OutputStream

Similarly:

```text
OutputStream
     |
     v
   Bytes
```

while:

```text
Writer
     |
     v
 Characters
```

Use:

```text
OutputStream
```

for binary data.

Use:

```text
Writer
```

for text.

---

# 24. BufferedReader

`BufferedReader` is commonly used for reading text efficiently.

Example:

```java
try (
    BufferedReader reader =
            Files.newBufferedReader(
                    Path.of("users.txt")
            )
) {

    String line;

    while ((line =
            reader.readLine()) != null) {

        System.out.println(line);
    }
}
```

If the file contains:

```text
John
David
Michael
```

Output:

```text
John
David
Michael
```

---

# 25. BufferedWriter

`BufferedWriter` can efficiently write text.

Example:

```java
try (
    BufferedWriter writer =
            Files.newBufferedWriter(
                    Path.of("users.txt")
            )
) {

    writer.write("John");
    writer.newLine();

    writer.write("David");
    writer.newLine();

    writer.write("Michael");
}
```

File content:

```text
John
David
Michael
```

---

# 26. PrintWriter

`PrintWriter` is convenient for writing formatted text.

Example:

```java
try (
    PrintWriter writer =
            new PrintWriter(
                    "users.txt"
            )
) {

    writer.println("John");
    writer.println("David");
    writer.println("Michael");
}
```

You can also use formatted output:

```java
writer.printf(
        "Name: %s, Age: %d%n",
        "John",
        30
);
```

Output:

```text
Name: John, Age: 30
```

---

# 27. DataInputStream

`DataInputStream` allows Java primitive values to be read from a stream.

For example:

```java
int
long
double
boolean
UTF String
```

Example:

```java
try (
    DataInputStream input =
            new DataInputStream(
                    Files.newInputStream(
                            Path.of("data.bin")
                    )
            )
) {

    int id =
            input.readInt();

    double amount =
            input.readDouble();

    System.out.println(id);
    System.out.println(amount);
}
```

---

# 28. DataOutputStream

`DataOutputStream` allows primitive values to be written.

Example:

```java
try (
    DataOutputStream output =
            new DataOutputStream(
                    Files.newOutputStream(
                            Path.of("data.bin")
                    )
            )
) {

    output.writeInt(1001);
    output.writeDouble(2500.50);
    output.writeBoolean(true);
}
```

---

# 29. DataInputStream and DataOutputStream

These classes are useful when you control both the writer and reader.

Example flow:

```text
Java Application
       |
       v
DataOutputStream
       |
       v
Binary File
       |
       v
DataInputStream
       |
       v
Java Application
```

The order and data types must match.

For example:

```java
output.writeInt(100);
output.writeDouble(10.5);
```

must be read in the same order:

```java
int id =
        input.readInt();

double amount =
        input.readDouble();
```

---

# 30. ObjectOutputStream

Java can serialize objects using:

```java
ObjectOutputStream
```

Example class:

```java
import java.io.Serializable;

public class User
        implements Serializable {

    private Long id;
    private String name;

    public User(
            Long id,
            String name
    ) {
        this.id = id;
        this.name = name;
    }
}
```

Write the object:

```java
User user =
        new User(1L, "John");

try (
    ObjectOutputStream output =
            new ObjectOutputStream(
                    Files.newOutputStream(
                            Path.of("user.dat")
                    )
            )
) {

    output.writeObject(user);
}
```

---

# 31. ObjectInputStream

You can read the serialized object using:

```java
ObjectInputStream
```

Example:

```java
try (
    ObjectInputStream input =
            new ObjectInputStream(
                    Files.newInputStream(
                            Path.of("user.dat")
                    )
            )
) {

    User user =
            (User) input.readObject();
}
```

---

# 32. Serialization

Serialization converts an object into a byte representation.

```text
Java Object
     |
     v
Serialization
     |
     v
Bytes
     |
     v
File / Network
```

Deserialization reverses the process:

```text
File / Network
     |
     v
Bytes
     |
     v
Deserialization
     |
     v
Java Object
```

---

# 33. Important Serialization Warning

Java native serialization should not be used blindly with untrusted input.

For modern applications, especially APIs and distributed systems, formats such as:

```text
JSON
XML
Protocol Buffers
Avro
```

are often more appropriate.

For example, Spring Boot REST APIs commonly use JSON rather than Java native serialization.

---

# 34. Standard Input

Java provides:

```java
System.in
```

for reading input from the console.

Example:

```java
int value =
        System.in.read();
```

However, for normal console applications, `Scanner` or `BufferedReader` is usually easier to use.

---

# 35. Scanner

Example:

```java
Scanner scanner =
        new Scanner(System.in);

System.out.print(
        "Enter your name: "
);

String name =
        scanner.nextLine();

System.out.println(
        "Hello " + name
);
```

Example:

```text
Enter your name: John
Hello John
```

---

# 36. Standard Output

Java provides:

```java
System.out
```

for normal console output.

Example:

```java
System.out.println(
        "Hello Java"
);
```

---

# 37. Standard Error

Java also provides:

```java
System.err
```

for error messages.

Example:

```java
System.err.println(
        "Something went wrong"
);
```

This is commonly used for error output and diagnostics.

---

# 38. System.in, System.out, System.err

Java provides three standard streams:

```text
System.in
    |
    v
Standard Input


System.out
    |
    v
Standard Output


System.err
    |
    v
Standard Error
```

Conceptually:

```text
Keyboard
   |
   v
System.in
   |
   v
Java Application
   |
   +------> System.out ------> Console
   |
   +------> System.err ------> Error Console
```

---

# 39. Byte Streams and Character Streams Diagram

```text
                    Java I/O
                       |
          +------------+------------+
          |                         |
          v                         v
    Byte Streams              Character Streams
          |                         |
     +----+----+               +----+----+
     |         |               |         |
     v         v               v         v
InputStream OutputStream     Reader    Writer
     |         |               |         |
     v         v               v         v
 Binary      Binary          Text      Text
  Data        Data            Data      Data
```

---

# 40. Buffered Streams Diagram

```text
Without Buffer

File
 |
 v
InputStream
 |
 v
Java Application

Many small I/O operations
```

With buffering:

```text
File
 |
 v
InputStream
 |
 v
BufferedInputStream
 |
 v
Buffer
 |
 v
Java Application
```

For output:

```text
Java Application
 |
 v
BufferedOutputStream
 |
 v
Buffer
 |
 v
OutputStream
 |
 v
File
```

---

# 41. File Copy Example

One of the most common I/O operations is copying a file.

```java
import java.io.InputStream;
import java.io.OutputStream;
import java.nio.file.Files;
import java.nio.file.Path;

public class FileCopy {

    public static void main(String[] args)
            throws Exception {

        Path source =
                Path.of("source.pdf");

        Path target =
                Path.of("backup.pdf");

        try (
            InputStream input =
                    Files.newInputStream(source);

            OutputStream output =
                    Files.newOutputStream(target)
        ) {

            byte[] buffer =
                    new byte[8192];

            int bytesRead;

            while ((bytesRead =
                    input.read(buffer)) != -1) {

                output.write(
                        buffer,
                        0,
                        bytesRead
                );
            }
        }

        System.out.println(
                "File copied successfully."
        );
    }
}
```

---

# 42. Better Way to Copy Files

For normal file copying, you don't always need to manually create streams.

Java provides:

```java
Files.copy()
```

Example:

```java
Files.copy(
        Path.of("source.pdf"),
        Path.of("backup.pdf"),
        StandardCopyOption.REPLACE_EXISTING
);
```

This is simpler and usually the preferred approach when you simply need to copy a file.

---

# 43. I/O Streams with Stream API

Do not confuse:

```text
I/O Stream
```

with:

```text
Java Stream API
```

They are different concepts.

### I/O Stream

Used to transfer data:

```text
InputStream
OutputStream
Reader
Writer
```

### Stream API

Used to process data:

```text
stream()
filter()
map()
sorted()
collect()
```

---

# 44. I/O Stream vs Stream API

| I/O Stream       | Stream API            |
| ---------------- | --------------------- |
| Transfers data   | Processes data        |
| `InputStream`    | `Stream<T>`           |
| `OutputStream`   | `Stream<T>`           |
| `Reader`         | `Stream<T>`           |
| `Writer`         | `Stream<T>`           |
| File/network I/O | Collection processing |

Example:

```text
File
 |
 v
I/O Stream
 |
 v
Java Application
 |
 v
Stream API
 |
 +--> filter()
 +--> map()
 +--> sorted()
 |
 v
Result
```

---

# 45. Example Combining I/O Stream and Stream API

Read a transaction file:

```text
FT001 SUCCESS 1000
FT002 FAILED 500
FT003 SUCCESS 2500
```

Java:

```java
Path path =
        Path.of("transactions.txt");

try (Stream<String> lines =
        Files.lines(path)) {

    lines.filter(
            line ->
                    line.contains("SUCCESS")
    )
    .forEach(
            System.out::println
    );
}
```

Output:

```text
FT001 SUCCESS 1000
FT003 SUCCESS 2500
```

Here:

```text
Files.lines()
      |
      v
Java Stream API
      |
      +--> filter()
      |
      +--> forEach()
```

---

# 46. Character Encoding

When working with text, encoding is important.

Common encoding:

```text
UTF-8
```

Example:

```java
import java.nio.charset.StandardCharsets;

String content =
        Files.readString(
                Path.of("data.txt"),
                StandardCharsets.UTF_8
        );
```

Writing:

```java
Files.writeString(
        Path.of("data.txt"),
        "Hello Java",
        StandardCharsets.UTF_8
);
```

---

# 47. Why UTF-8 Matters

Suppose a file contains:

```text
Hello
សួស្តី
你好
こんにちは
```

The application must use the correct character encoding to read the characters correctly.

UTF-8 supports a very wide range of characters.

Conceptually:

```text
Text
 |
 v
UTF-8 Encoding
 |
 v
Bytes
 |
 v
File
```

Reading reverses the process:

```text
File
 |
 v
Bytes
 |
 v
UTF-8 Decoding
 |
 v
Text
```

---

# 48. IOException

Most I/O operations can fail.

Examples:

```text
File does not exist
Permission denied
Disk failure
Network failure
Invalid path
Connection closed
```

Java commonly represents these problems with:

```java
IOException
```

Example:

```java
try {

    String content =
            Files.readString(
                    Path.of("data.txt")
            );

} catch (IOException e) {

    System.err.println(
            "I/O Error: "
                    + e.getMessage()
    );
}
```

---

# 49. try-with-resources

I/O resources should normally be closed.

Instead of:

```java
InputStream input =
        Files.newInputStream(path);

try {

    // Work

} finally {

    input.close();
}
```

use:

```java
try (
    InputStream input =
            Files.newInputStream(path)
) {

    // Work

}
```

Java automatically closes the resource.

---

# 50. Multiple Resources

You can manage multiple resources.

```java
try (
    InputStream input =
            Files.newInputStream(source);

    OutputStream output =
            Files.newOutputStream(target)
) {

    // Copy data

}
```

When the block finishes:

```text
OutputStream -> closed
InputStream  -> closed
```

---

# 51. Common I/O Classes

| Class                  | Purpose                   |
| ---------------------- | ------------------------- |
| `InputStream`          | Read bytes                |
| `OutputStream`         | Write bytes               |
| `Reader`               | Read characters           |
| `Writer`               | Write characters          |
| `FileInputStream`      | Read bytes from file      |
| `FileOutputStream`     | Write bytes to file       |
| `FileReader`           | Read text from file       |
| `FileWriter`           | Write text to file        |
| `BufferedInputStream`  | Buffered byte input       |
| `BufferedOutputStream` | Buffered byte output      |
| `BufferedReader`       | Buffered character input  |
| `BufferedWriter`       | Buffered character output |
| `PrintWriter`          | Convenient text output    |
| `DataInputStream`      | Read primitive values     |
| `DataOutputStream`     | Write primitive values    |
| `ObjectInputStream`    | Deserialize objects       |
| `ObjectOutputStream`   | Serialize objects         |

---

# 52. java.io vs java.nio

Java has two major I/O APIs.

### Traditional I/O

```text
java.io
```

Contains:

```text
InputStream
OutputStream
Reader
Writer
File
```

### NIO

```text
java.nio
java.nio.file
```

Contains:

```text
Path
Files
ByteBuffer
Channel
```

For modern Java development, especially when working with files, `java.nio.file` is generally preferred.

---

# 53. Channels

Java NIO also provides **Channels**.

Examples:

```java
FileChannel
SocketChannel
ServerSocketChannel
```

A channel provides another way to perform I/O operations.

Conceptually:

```text
Application
     |
     v
Channel
     |
     v
External Resource
```

---

# 54. FileChannel

Example:

```java
try (
    FileChannel channel =
            FileChannel.open(
                    Path.of("data.txt"),
                    StandardOpenOption.READ
            )
) {

    ByteBuffer buffer =
            ByteBuffer.allocate(1024);

    int bytesRead =
            channel.read(buffer);

    System.out.println(
            "Bytes read: "
                    + bytesRead
    );
}
```

`FileChannel` is useful for more advanced file operations.

---

# 55. ByteBuffer

NIO uses `ByteBuffer` to work with byte data.

Example:

```java
ByteBuffer buffer =
        ByteBuffer.allocate(1024);
```

Conceptually:

```text
File
 |
 v
FileChannel
 |
 v
ByteBuffer
 |
 v
Java Application
```

---

# 56. Blocking vs Non-Blocking I/O

Traditional I/O is generally blocking.

Example:

```text
Application
    |
    v
Read
    |
    | Waiting...
    |
    v
Data arrives
    |
    v
Continue
```

NIO also provides APIs for non-blocking network I/O.

Conceptually:

```text
Application
    |
    v
Request I/O
    |
    v
Continue doing other work
    |
    v
Check/process I/O event
```

Non-blocking I/O is especially important for high-performance network applications.

---

# 57. I/O Streams in Web Applications

I/O streams are very important in Spring Boot applications.

For example:

```text
HTTP Request
      |
      v
Spring Boot
      |
      v
InputStream
      |
      v
Process File
```

For file download:

```text
Database / File
      |
      v
InputStream
      |
      v
HTTP Response
      |
      v
Client
```

---

# 58. File Upload Example Concept

A web application may receive:

```text
User
 |
 | Upload PDF
 v
Spring Boot
 |
 v
InputStream
 |
 v
File Storage
```

Conceptually:

```java
InputStream input =
        uploadedFile.getInputStream();
```

The application can then copy the stream to storage.

---

# 59. File Download Example Concept

The opposite direction:

```text
File Storage
      |
      v
InputStream
      |
      v
HTTP Response
      |
      v
Browser
```

In Spring Boot, this can be used to return a file to a client.

---

# 60. Banking Application Example

In a banking application, I/O streams can be used for:

```text
Transaction Logs
Reports
CSV Imports
CSV Exports
PDF Statements
File Uploads
File Downloads
Backup Files
Integration Files
```

Example:

```text
Banking Application
        |
        +--> Transaction Log
        |
        +--> CSV Import
        |
        +--> PDF Statement
        |
        +--> External File
        |
        +--> Backup
```

---

# 61. Example: Reading Transaction File

Suppose:

```text
transactions.txt
```

contains:

```text
FT001|ACC001|ACC002|1000|SUCCESS
FT002|ACC003|ACC004|500|FAILED
FT003|ACC005|ACC006|2500|SUCCESS
```

Read it:

```java
Path path =
        Path.of("transactions.txt");

try (BufferedReader reader =
        Files.newBufferedReader(path)) {

    String line;

    while ((line =
            reader.readLine()) != null) {

        String[] parts =
                line.split("\\|");

        String ftNumber =
                parts[0];

        String status =
                parts[4];

        System.out.println(
                ftNumber
                        + " -> "
                        + status
        );
    }
}
```

Output:

```text
FT001 -> SUCCESS
FT002 -> FAILED
FT003 -> SUCCESS
```

---

# 62. Example: Writing Transaction Log

```java
Path path =
        Path.of("transactions.log");

try (
    BufferedWriter writer =
            Files.newBufferedWriter(
                    path,
                    StandardOpenOption.CREATE,
                    StandardOpenOption.APPEND
            )
) {

    writer.write(
            "FT004|ACC007|ACC008|750|SUCCESS"
    );

    writer.newLine();
}
```

---

# 63. I/O Processing Flow

A typical file-processing application looks like:

```text
                 Start
                   |
                   v
              Open File
                   |
                   v
              Create Stream
                   |
                   v
             Read Buffer
                   |
                   v
             Process Data
                   |
                   v
             More Data?
              /       \
            Yes        No
             |          |
             +----------+
                   |
                   v
             Close Stream
                   |
                   v
                  End
```

---

# 64. Complete Example: Copy File Using Streams

```java
import java.io.InputStream;
import java.io.OutputStream;
import java.io.IOException;
import java.nio.file.Files;
import java.nio.file.Path;

public class StreamCopyExample {

    public static void main(String[] args) {

        Path source =
                Path.of("source.txt");

        Path target =
                Path.of("copy.txt");

        try (
            InputStream input =
                    Files.newInputStream(source);

            OutputStream output =
                    Files.newOutputStream(target)
        ) {

            byte[] buffer =
                    new byte[8192];

            int bytesRead;

            while ((bytesRead =
                    input.read(buffer)) != -1) {

                output.write(
                        buffer,
                        0,
                        bytesRead
                );
            }

            System.out.println(
                    "Copy completed."
            );

        } catch (IOException e) {

            System.err.println(
                    "I/O error: "
                            + e.getMessage()
            );
        }
    }
}
```

---

# 65. Complete Example: Text Processing

```java
import java.io.BufferedReader;
import java.io.BufferedWriter;
import java.io.IOException;
import java.nio.file.Files;
import java.nio.file.Path;

public class TextProcessing {

    public static void main(String[] args) {

        Path input =
                Path.of("input.txt");

        Path output =
                Path.of("output.txt");

        try (
            BufferedReader reader =
                    Files.newBufferedReader(input);

            BufferedWriter writer =
                    Files.newBufferedWriter(output)
        ) {

            String line;

            while ((line =
                    reader.readLine()) != null) {

                String result =
                        line.toUpperCase();

                writer.write(result);
                writer.newLine();
            }

        } catch (IOException e) {

            System.err.println(
                    "I/O error: "
                            + e.getMessage()
            );
        }
    }
}
```

Input:

```text
hello java
java io
spring boot
```

Output:

```text
HELLO JAVA
JAVA IO
SPRING BOOT
```

---

# 66. I/O Streams Best Practices

### 1. Prefer try-with-resources

Use:

```java
try (InputStream input = ...) {

}
```

instead of manually closing resources.

---

### 2. Use Buffering for Repeated I/O

For large files:

```java
BufferedInputStream
BufferedOutputStream
BufferedReader
BufferedWriter
```

can improve efficiency.

---

### 3. Use NIO for Modern File Operations

Prefer:

```java
Path
Files
```

for most modern file handling.

---

### 4. Specify Character Encoding

For text files, explicitly use:

```java
StandardCharsets.UTF_8
```

when predictable encoding is important.

---

### 5. Handle IOException

Don't silently ignore I/O failures.

```java
catch (IOException e) {

    // Log or handle error
}
```

---

### 6. Don't Load Huge Files into Memory

Avoid:

```java
Files.readAllBytes()
```

or:

```java
Files.readAllLines()
```

for extremely large files unless you know the memory requirements are acceptable.

Prefer streaming approaches:

```java
Files.lines()
```

or:

```java
BufferedReader
```

---

# 67. Important Difference to Remember

The word **Stream** is used in two different Java concepts.

### I/O Stream

Moves data:

```text
File
 |
 v
InputStream
 |
 v
Application
```

### Stream API

Processes data:

```text
Collection
 |
 v
Stream<T>
 |
 +--> filter()
 +--> map()
 +--> sorted()
 |
 v
Result
```

Remember:

```text
I/O Stream = Move Data

Stream API = Process Data
```

---

# 68. Java I/O Streams Cheat Sheet

| Requirement            | Recommended API             |
| ---------------------- | --------------------------- |
| Read binary data       | `InputStream`               |
| Write binary data      | `OutputStream`              |
| Read text              | `Reader` / `BufferedReader` |
| Write text             | `Writer` / `BufferedWriter` |
| Buffered binary input  | `BufferedInputStream`       |
| Buffered binary output | `BufferedOutputStream`      |
| Read primitive values  | `DataInputStream`           |
| Write primitive values | `DataOutputStream`          |
| Serialize object       | `ObjectOutputStream`        |
| Deserialize object     | `ObjectInputStream`         |
| Console input          | `System.in` / `Scanner`     |
| Console output         | `System.out`                |
| Error output           | `System.err`                |
| File path              | `Path`                      |
| File operations        | `Files`                     |
| Advanced file I/O      | `FileChannel`               |
| Byte buffer            | `ByteBuffer`                |

---

# 69. Final Concept Diagram

```text
                         Java I/O
                            |
          +-----------------+-----------------+
          |                                   |
          v                                   v
     Byte Streams                       Character Streams
          |                                   |
     +----+----+                         +----+----+
     |         |                         |         |
     v         v                         v         v
InputStream OutputStream              Reader    Writer
     |         |                         |         |
     v         v                         v         v
 Binary      Binary                    Text      Text
     |         |                         |         |
     +---------+-------------+-----------+---------+
                           |
                           v
                      java.io / NIO
                           |
                           v
                     Java Application
                           |
                           v
                  Stream API Processing
                           |
              +------------+------------+
              |            |            |
              v            v            v
           filter()      map()       sorted()
              |
              v
            Result
```

---

# 70. Summary

Java I/O Streams provide a mechanism for transferring data between Java applications and external resources.

The most important concepts are:

```text
InputStream
OutputStream
Reader
Writer
BufferedReader
BufferedWriter
```

For modern file operations, also remember:

```text
Path
Files
```

The fundamental difference is:

```text
Input
  |
  v
Java Application
  |
  v
Output
```

For binary data:

```text
InputStream
OutputStream
```

For text:

```text
Reader
Writer
```

For efficient processing:

```text
BufferedInputStream
BufferedOutputStream
BufferedReader
BufferedWriter
```

And for modern file handling:

```text
java.nio.file.Path
java.nio.file.Files
```

Finally, don't confuse I/O Streams with the Java Stream API:

```text
I/O Streams
     |
     v
Transfer Data


Stream API
     |
     v
Process Data
```

Together, these APIs provide the foundation for handling files, reports, logs, uploads, downloads, binary data, and many other forms of I/O in Java applications.
