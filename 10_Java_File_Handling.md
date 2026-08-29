# 📘 Java File Handling

## 1. What Is File Handling?

**File Handling** in Java means creating, reading, writing, updating, and deleting files and directories.

File handling is useful when an application needs to work with data stored outside the application memory.

Common examples include:

- Reading configuration files
- Creating log files
- Reading CSV files
- Exporting reports
- Processing text files
- Uploading and downloading files
- Reading JSON or XML files
- Working with temporary files

Java provides several APIs for file handling.

The most important modern API is:

```text
java.nio.file
```

---

# 2. Java File Handling APIs

Java provides several classes for working with files.

| Class            | Purpose                             |
| ---------------- | ----------------------------------- |
| `Path`           | Represents a file or directory path |
| `Paths`          | Creates `Path` objects              |
| `Files`          | Provides file operations            |
| `File`           | Older file API                      |
| `InputStream`    | Reads binary data                   |
| `OutputStream`   | Writes binary data                  |
| `Reader`         | Reads character data                |
| `Writer`         | Writes character data               |
| `BufferedReader` | Efficiently reads text              |
| `BufferedWriter` | Efficiently writes text             |

For modern Java applications, prefer:

```java
java.nio.file.Path
java.nio.file.Files
```

---

# 3. Creating a Path

The `Path` class represents the location of a file or directory.

Example:

```java
import java.nio.file.Path;

Path path = Path.of("data.txt");

System.out.println(path);
```

Output:

```text
data.txt
```

You can also specify a directory:

```java
Path path = Path.of("data", "customers.txt");
```

This represents:

```text
data/
    customers.txt
```

---

# 4. Absolute Path

An absolute path contains the complete location of a file.

Example on Windows:

```java
Path path =
        Path.of("C:\\data\\customers.txt");
```

Example on Linux:

```java
Path path =
        Path.of("/opt/data/customers.txt");
```

---

# 5. Relative Path

A relative path is based on the application's current working directory.

Example:

```java
Path path =
        Path.of("data/customers.txt");
```

The application interprets the path relative to its current working directory.

---

# 6. Checking Whether a File Exists

Use:

```java
Files.exists()
```

Example:

```java
import java.nio.file.Files;
import java.nio.file.Path;

Path path = Path.of("data.txt");

if (Files.exists(path)) {
    System.out.println("File exists");
} else {
    System.out.println("File does not exist");
}
```

Output:

```text
File exists
```

---

# 7. Checking Whether a Path Is a File

```java
if (Files.isRegularFile(path)) {
    System.out.println("This is a file");
}
```

---

# 8. Checking Whether a Path Is a Directory

```java
if (Files.isDirectory(path)) {
    System.out.println("This is a directory");
}
```

---

# 9. Creating a Directory

Use:

```java
Files.createDirectory()
```

Example:

```java
Path directory =
        Path.of("data");

Files.createDirectory(directory);
```

This creates:

```text
data/
```

---

# 10. Creating Nested Directories

If multiple directories may need to be created, use:

```java
Files.createDirectories()
```

Example:

```java
Path directory =
        Path.of("data/customers/2026");

Files.createDirectories(directory);
```

Result:

```text
data/
    customers/
        2026/
```

`createDirectories()` creates missing parent directories automatically.

---

# 11. Creating a File

Use:

```java
Files.createFile()
```

Example:

```java
Path path =
        Path.of("data.txt");

Files.createFile(path);
```

This creates:

```text
data.txt
```

If the file already exists, Java throws an exception.

Therefore, you may want to check first:

```java
if (!Files.exists(path)) {
    Files.createFile(path);
}
```

---

# 12. Writing Text to a File

One of the easiest ways to write text is:

```java
Files.writeString()
```

Example:

```java
Path path =
        Path.of("message.txt");

Files.writeString(
        path,
        "Hello Java!"
);
```

The file will contain:

```text
Hello Java!
```

---

# 13. Writing Multiple Lines

You can write multiple lines:

```java
Path path =
        Path.of("users.txt");

Files.writeString(
        path,
        "John\nDavid\nMichael"
);
```

File content:

```text
John
David
Michael
```

A better platform-independent approach is:

```java
String content =
        String.join(
                System.lineSeparator(),
                "John",
                "David",
                "Michael"
        );

Files.writeString(path, content);
```

---

# 14. Reading Text from a File

Use:

```java
Files.readString()
```

Example:

```java
Path path =
        Path.of("message.txt");

String content =
        Files.readString(path);

System.out.println(content);
```

If the file contains:

```text
Hello Java!
```

Output:

```text
Hello Java!
```

---

# 15. Writing a List of Lines

Java also provides:

```java
Files.write()
```

Example:

```java
Path path =
        Path.of("users.txt");

List<String> users =
        List.of(
                "John",
                "David",
                "Michael"
        );

Files.write(path, users);
```

The file contains:

```text
John
David
Michael
```

---

# 16. Reading All Lines

Use:

```java
Files.readAllLines()
```

Example:

```java
Path path =
        Path.of("users.txt");

List<String> users =
        Files.readAllLines(path);

for (String user : users) {
    System.out.println(user);
}
```

Output:

```text
John
David
Michael
```

---

# 17. Reading a File Line by Line

For larger files, it is often better to process the file line by line.

Use:

```java
Files.lines()
```

Example:

```java
Path path =
        Path.of("users.txt");

try (Stream<String> lines =
        Files.lines(path)) {

    lines.forEach(
            System.out::println
    );
}
```

This is useful when working with large files because the whole file does not need to be loaded into memory at once.

---

# 18. BufferedReader

Another common approach is `BufferedReader`.

```java
Path path =
        Path.of("users.txt");

try (BufferedReader reader =
        Files.newBufferedReader(path)) {

    String line;

    while ((line = reader.readLine()) != null) {

        System.out.println(line);
    }
}
```

---

# 19. Why Use try-with-resources?

File resources should be closed after use.

Java provides **try-with-resources** to automatically close resources.

Example:

```java
try (BufferedReader reader =
        Files.newBufferedReader(path)) {

    // Read file

}
```

When the block finishes, Java automatically closes the reader.

This is safer than manually calling:

```java
reader.close();
```

---

# 20. Appending Data to a File

By default:

```java
Files.writeString(
        path,
        "Hello"
);
```

may replace the existing content.

To append content, use:

```java
import static java.nio.file.StandardOpenOption.APPEND;
```

Example:

```java
Files.writeString(
        path,
        "New line\n",
        APPEND
);
```

---

# 21. Create or Append

A common requirement is:

> Create the file if it doesn't exist, otherwise append to it.

Example:

```java
Files.writeString(
        path,
        "New transaction\n",
        StandardOpenOption.CREATE,
        StandardOpenOption.APPEND
);
```

This is useful for simple application logs.

---

# 22. Overwriting a File

If you want to replace the existing content:

```java
Files.writeString(
        path,
        "New Content"
);
```

Example:

Before:

```text
Old Content
```

After:

```text
New Content
```

---

# 23. Copying a File

Use:

```java
Files.copy()
```

Example:

```java
Path source =
        Path.of("source.txt");

Path target =
        Path.of("backup.txt");

Files.copy(source, target);
```

Result:

```text
source.txt
backup.txt
```

Both files contain the same data.

---

# 24. Replacing an Existing File

If the target already exists, use:

```java
Files.copy(
        source,
        target,
        StandardCopyOption.REPLACE_EXISTING
);
```

Example:

```java
Files.copy(
        source,
        target,
        StandardCopyOption.REPLACE_EXISTING
);
```

---

# 25. Moving a File

Use:

```java
Files.move()
```

Example:

```java
Path source =
        Path.of("old.txt");

Path target =
        Path.of("new.txt");

Files.move(source, target);
```

This changes:

```text
old.txt
```

into:

```text
new.txt
```

---

# 26. Moving a File to Another Directory

```java
Path source =
        Path.of("report.txt");

Path target =
        Path.of("archive/report.txt");

Files.createDirectories(
        target.getParent()
);

Files.move(
        source,
        target
);
```

Result:

```text
archive/
    report.txt
```

---

# 27. Deleting a File

Use:

```java
Files.delete()
```

Example:

```java
Path path =
        Path.of("old.txt");

Files.delete(path);
```

If the file does not exist, an exception may be thrown.

---

# 28. deleteIfExists()

If you don't want an exception when the file does not exist:

```java
Files.deleteIfExists(path);
```

Example:

```java
boolean deleted =
        Files.deleteIfExists(path);

System.out.println(deleted);
```

The result is:

```text
true
```

if the file was deleted.

---

# 29. Listing Files in a Directory

Use:

```java
Files.list()
```

Example:

```java
Path directory =
        Path.of("data");

try (Stream<Path> files =
        Files.list(directory)) {

    files.forEach(
            System.out::println
    );
}
```

Example output:

```text
data/customer.txt
data/account.txt
data/transaction.txt
```

---

# 30. Filtering Files

You can combine `Files.list()` with the Stream API.

Example:

```java
try (Stream<Path> files =
        Files.list(Path.of("data"))) {

    files.filter(
            Files::isRegularFile
    ).forEach(
            System.out::println
    );
}
```

---

# 31. Finding Files Recursively

Use:

```java
Files.walk()
```

Example:

```java
try (Stream<Path> paths =
        Files.walk(Path.of("data"))) {

    paths.filter(
            Files::isRegularFile
    ).forEach(
            System.out::println
    );
}
```

Unlike `Files.list()`, `Files.walk()` can navigate into subdirectories.

Example:

```text
data/
    customers/
        customer1.txt
        customer2.txt

    accounts/
        account1.txt
```

The flow is:

```text
data/
 |
 +-- customers/
 |      |
 |      +-- customer1.txt
 |      +-- customer2.txt
 |
 +-- accounts/
        |
        +-- account1.txt
```

`Files.walk()` can visit all of them.

---

# 32. Getting File Size

Use:

```java
Files.size()
```

Example:

```java
Path path =
        Path.of("data.txt");

long size =
        Files.size(path);

System.out.println(
        "Size: " + size + " bytes"
);
```

---

# 33. Getting File Information

You can retrieve useful metadata.

Example:

```java
System.out.println(
        Files.getLastModifiedTime(path)
);

System.out.println(
        Files.size(path)
);

System.out.println(
        Files.isReadable(path)
);

System.out.println(
        Files.isWritable(path)
);

System.out.println(
        Files.isExecutable(path)
);
```

---

# 34. Checking File Permissions

You can check whether a file can be read:

```java
boolean readable =
        Files.isReadable(path);
```

Writable:

```java
boolean writable =
        Files.isWritable(path);
```

Executable:

```java
boolean executable =
        Files.isExecutable(path);
```

---

# 35. Path Operations

`Path` provides useful methods.

Example:

```java
Path path =
        Path.of(
                "data",
                "customers",
                "customer.txt"
        );
```

Get the file name:

```java
System.out.println(
        path.getFileName()
);
```

Output:

```text
customer.txt
```

Get the parent:

```java
System.out.println(
        path.getParent()
);
```

Output:

```text
data/customers
```

---

# 36. File Extension

Java does not provide a direct `getExtension()` method.

You can process it manually.

Example:

```java
String fileName =
        path.getFileName().toString();

int index =
        fileName.lastIndexOf('.');

if (index > 0) {

    String extension =
            fileName.substring(index + 1);

    System.out.println(extension);
}
```

For:

```text
report.pdf
```

Output:

```text
pdf
```

---

# 37. Resolving Paths

You can combine paths using:

```java
resolve()
```

Example:

```java
Path directory =
        Path.of("data");

Path file =
        directory.resolve(
                "customers.txt"
        );

System.out.println(file);
```

Output:

```text
data/customers.txt
```

This is preferable to manually constructing paths such as:

```java
"data/" + "customers.txt"
```

because `Path` handles platform-specific path separators.

---

# 38. Normalize Path

Sometimes a path contains:

```text
.
..
```

Example:

```java
Path path =
        Path.of(
                "data/customers/../accounts"
        );

Path normalized =
        path.normalize();

System.out.println(normalized);
```

Output:

```text
data/accounts
```

---

# 39. Absolute and Real Paths

Convert to an absolute path:

```java
Path absolute =
        path.toAbsolutePath();
```

Example:

```java
System.out.println(
        absolute
);
```

If the file exists, you can also use:

```java
Path real =
        path.toRealPath();
```

`toRealPath()` resolves the actual path and can resolve symbolic links.

---

# 40. Reading Binary Files

Not every file contains text.

Examples:

```text
Images
PDF
ZIP
Excel
Audio
Video
```

For binary files, you can use:

```java
Files.readAllBytes()
```

Example:

```java
Path path =
        Path.of("image.jpg");

byte[] data =
        Files.readAllBytes(path);

System.out.println(
        "Bytes: " + data.length
);
```

---

# 41. Writing Binary Files

Use:

```java
Files.write()
```

Example:

```java
byte[] data =
        {10, 20, 30, 40};

Path path =
        Path.of("data.bin");

Files.write(
        path,
        data
);
```

---

# 42. InputStream

For larger binary files, use an `InputStream`.

Example:

```java
Path path =
        Path.of("image.jpg");

try (InputStream input =
        Files.newInputStream(path)) {

    byte[] buffer =
            new byte[1024];

    int bytesRead;

    while ((bytesRead =
            input.read(buffer)) != -1) {

        System.out.println(
                "Read: " + bytesRead
        );
    }
}
```

---

# 43. OutputStream

You can write binary data using `OutputStream`.

```java
Path path =
        Path.of("data.bin");

try (OutputStream output =
        Files.newOutputStream(path)) {

    output.write(10);
    output.write(20);
    output.write(30);
}
```

---

# 44. Copying Large Files

For large files, `InputStream` and `OutputStream` can be used.

```java
Path source =
        Path.of("large-file.dat");

Path target =
        Path.of("backup.dat");

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

# 45. BufferedReader vs Files.readString()

For a small text file:

```java
String content =
        Files.readString(path);
```

is simple and convenient.

For processing a large file:

```java
try (Stream<String> lines =
        Files.lines(path)) {

    lines.forEach(
            System.out::println
    );
}
```

or:

```java
try (BufferedReader reader =
        Files.newBufferedReader(path)) {

    String line;

    while ((line =
            reader.readLine()) != null) {

        // Process line
    }
}
```

---

# 46. File Handling Exception

File operations can fail.

For example:

```java
Files.readString(path);
```

may fail because:

- File does not exist
- Permission denied
- Invalid path
- Disk problem
- File is inaccessible

Many file operations throw:

```java
IOException
```

Example:

```java
try {

    String content =
            Files.readString(path);

    System.out.println(content);

} catch (IOException e) {

    System.out.println(
            "Unable to read file: "
                    + e.getMessage()
    );
}
```

---

# 47. throws IOException

Instead of handling the exception immediately, a method can declare:

```java
public static String readFile(
        Path path
) throws IOException {

    return Files.readString(path);
}
```

Then the caller must handle the exception.

---

# 48. Complete Text File Example

```java
import java.io.IOException;
import java.nio.file.Files;
import java.nio.file.Path;
import java.util.List;

public class FileExample {

    public static void main(String[] args) {

        Path path =
                Path.of("users.txt");

        try {

            // Write data
            List<String> users =
                    List.of(
                            "John",
                            "David",
                            "Michael"
                    );

            Files.write(
                    path,
                    users
            );

            // Read data
            List<String> result =
                    Files.readAllLines(path);

            for (String user : result) {

                System.out.println(user);
            }

        } catch (IOException e) {

            System.out.println(
                    "File error: "
                            + e.getMessage()
            );
        }
    }
}
```

Output:

```text
John
David
Michael
```

---

# 49. Complete File Lifecycle

A typical file-processing application can follow this flow:

```text
                Start
                  |
                  v
            Create Path
                  |
                  v
          Does File Exist?
             /        \
           Yes         No
            |           |
            v           v
       Read File    Create File
            |           |
            +-----+-----+
                  |
                  v
             Process Data
                  |
                  v
             Update File
                  |
                  v
           Need Backup?
             /      \
           Yes       No
            |         |
            v         |
        Copy File     |
            |         |
            +----+----+
                 |
                 v
                End
```

---

# 50. Example: Transaction Log

File handling is common in banking and enterprise applications.

For example:

```text
transactions.log
```

Content:

```text
2026-08-29 | FT001 | ACC001 | ACC002 | 1000.00 | SUCCESS
2026-08-29 | FT002 | ACC003 | ACC004 | 2500.00 | SUCCESS
2026-08-29 | FT003 | ACC005 | ACC006 | 500.00  | FAILED
```

Java can read the file:

```java
Path path =
        Path.of("transactions.log");

try (Stream<String> lines =
        Files.lines(path)) {

    lines.filter(
            line -> line.contains("SUCCESS")
    ).forEach(
            System.out::println
    );
}
```

Output:

```text
2026-08-29 | FT001 | ACC001 | ACC002 | 1000.00 | SUCCESS
2026-08-29 | FT002 | ACC003 | ACC004 | 2500.00 | SUCCESS
```

This example combines:

```text
File Handling
      +
Stream API
      +
Lambda Expression
```

---

# 51. Example: Count Successful Transactions

```java
Path path =
        Path.of("transactions.log");

long successCount;

try (Stream<String> lines =
        Files.lines(path)) {

    successCount =
            lines.filter(
                    line ->
                            line.contains(
                                    "SUCCESS"
                            )
            )
            .count();
}

System.out.println(
        "Successful transactions: "
                + successCount
);
```

---

# 52. Example: Find Error Transactions

```java
Path path =
        Path.of("transactions.log");

try (Stream<String> lines =
        Files.lines(path)) {

    lines.filter(
            line ->
                    line.contains("FAILED")
    )
    .forEach(
            System.out::println
    );
}
```

This is a practical example of how Java File Handling can work together with the Stream API.

---

# 53. Java File Handling with Regex

File handling can also be combined with Regex.

Suppose a file contains:

```text
FT001 SUCCESS
FT002 FAILED
FT003 SUCCESS
```

We can search for transaction IDs:

```java
Pattern pattern =
        Pattern.compile("FT\\d+");

try (Stream<String> lines =
        Files.lines(
                Path.of("transactions.log")
        )) {

    lines.forEach(line -> {

        Matcher matcher =
                pattern.matcher(line);

        if (matcher.find()) {

            System.out.println(
                    "Transaction: "
                            + matcher.group()
            );
        }
    });
}
```

Output:

```text
Transaction: FT001
Transaction: FT002
Transaction: FT003
```

This combines:

```text
File Handling
      +
Regex
      +
Stream API
      +
Lambda Expressions
```

---

# 54. Modern Java File Handling

For modern Java applications, prefer the `java.nio.file` API.

Recommended:

```java
Path
Files
```

Example:

```java
Path path =
        Path.of("data.txt");

String content =
        Files.readString(path);
```

Instead of relying heavily on the older:

```java
File
FileReader
FileWriter
```

The older APIs are still available and useful for compatibility, but `java.nio.file` provides a more modern and powerful API.

---

# 55. File Handling Best Practices

### 1. Prefer Path and Files

Use:

```java
Path
Files
```

for modern applications.

---

### 2. Use try-with-resources

For resources such as:

```java
BufferedReader
InputStream
OutputStream
```

use:

```java
try (Resource resource = ...) {

}
```

---

### 3. Handle IOException

Don't ignore file exceptions.

```java
try {

    // File operation

} catch (IOException e) {

    // Handle error
}
```

---

### 4. Validate File Paths

Avoid blindly accepting file paths from users.

For example, an application should be careful about paths such as:

```text
../../sensitive-file
```

Path validation is especially important for web applications that allow users to upload or download files.

---

### 5. Avoid Loading Huge Files into Memory

For small files:

```java
Files.readString()
```

is convenient.

For large files:

```java
Files.lines()
```

or:

```java
BufferedReader
```

is usually more appropriate.

---

### 6. Use Appropriate Buffer Sizes

When processing large binary files:

```java
byte[] buffer =
        new byte[8192];
```

can reduce the number of read/write operations.

---

### 7. Use UTF-8 Explicitly When Appropriate

For predictable text encoding:

```java
String content =
        Files.readString(
                path,
                StandardCharsets.UTF_8
        );
```

Likewise:

```java
Files.writeString(
        path,
        content,
        StandardCharsets.UTF_8
);
```

---

# 56. Java File Handling Cheat Sheet

| Requirement        | Java API                    |
| ------------------ | --------------------------- |
| Create Path        | `Path.of()`                 |
| Check exists       | `Files.exists()`            |
| Check file         | `Files.isRegularFile()`     |
| Check directory    | `Files.isDirectory()`       |
| Create directory   | `Files.createDirectory()`   |
| Create directories | `Files.createDirectories()` |
| Create file        | `Files.createFile()`        |
| Read text          | `Files.readString()`        |
| Read lines         | `Files.readAllLines()`      |
| Stream lines       | `Files.lines()`             |
| Write text         | `Files.writeString()`       |
| Write lines        | `Files.write()`             |
| Append             | `StandardOpenOption.APPEND` |
| Copy               | `Files.copy()`              |
| Move               | `Files.move()`              |
| Delete             | `Files.delete()`            |
| Delete safely      | `Files.deleteIfExists()`    |
| List directory     | `Files.list()`              |
| Recursive search   | `Files.walk()`              |
| File size          | `Files.size()`              |
| Read binary        | `Files.readAllBytes()`      |
| Write binary       | `Files.write()`             |
| Input stream       | `Files.newInputStream()`    |
| Output stream      | `Files.newOutputStream()`   |

---

# 57. Key Concepts to Remember

The most important classes are:

```text
Path
  |
  +--> Represents file/directory location
  |
  v
Files
  |
  +--> Create
  +--> Read
  +--> Write
  +--> Copy
  +--> Move
  +--> Delete
  +--> List
  +--> Walk
```

Modern Java file handling is mainly based on:

```java
java.nio.file.Path
java.nio.file.Files
```

---

# 58. Final Example

The following example demonstrates a complete file workflow:

```java
import java.io.IOException;
import java.nio.file.Files;
import java.nio.file.Path;
import java.nio.file.StandardOpenOption;
import java.util.List;

public class FileHandlingDemo {

    public static void main(String[] args) {

        Path directory =
                Path.of("data");

        Path file =
                directory.resolve(
                        "transactions.txt"
                );

        try {

            // 1. Create directory
            Files.createDirectories(
                    directory
            );

            // 2. Create initial file content
            List<String> transactions =
                    List.of(
                            "FT001 SUCCESS 1000",
                            "FT002 SUCCESS 2500",
                            "FT003 FAILED 500"
                    );

            Files.write(
                    file,
                    transactions
            );

            // 3. Append another transaction
            Files.writeString(
                    file,
                    "FT004 SUCCESS 750"
                            + System.lineSeparator(),
                    StandardOpenOption.APPEND
            );

            // 4. Read the file
            System.out.println(
                    "Transactions:"
            );

            try (var lines =
                    Files.lines(file)) {

                lines.forEach(
                        System.out::println
                );
            }

            // 5. Show file size
            System.out.println(
                    "File size: "
                            + Files.size(file)
                            + " bytes"
            );

        } catch (IOException e) {

            System.err.println(
                    "File operation failed: "
                            + e.getMessage()
            );
        }
    }
}
```

Output:

```text
Transactions:
FT001 SUCCESS 1000
FT002 SUCCESS 2500
FT003 FAILED 500
FT004 SUCCESS 750

File size: 90 bytes
```

---

# Summary

Java File Handling allows applications to work with files and directories.

The most important modern API is:

```java
java.nio.file
```

The two classes you should remember first are:

```java
Path
Files
```

A typical modern Java file operation looks like:

```text
Path
 |
 v
Files
 |
 +--> Create
 |
 +--> Read
 |
 +--> Write
 |
 +--> Append
 |
 +--> Copy
 |
 +--> Move
 |
 +--> Delete
 |
 +--> List
 |
 +--> Walk
```

And when combined with modern Java features:

```text
                    Java File Handling
                           |
          +----------------+----------------+
          |                |                |
          v                v                v
        Path             Files           IOException
                           |
                           v
                     Stream API
                           |
             +-------------+-------------+
             |             |             |
             v             v             v
          filter()       map()        sorted()
             |
             v
       Lambda Expression
             |
             v
          Result
```

For Java 21 development, a good foundation is:

```text
Path
Files
try-with-resources
IOException
Stream API
Lambda Expressions
Regex
```

These concepts are especially useful when building Spring Boot applications that process logs, reports, CSV files, uploaded documents, configuration files, or banking transaction files.
