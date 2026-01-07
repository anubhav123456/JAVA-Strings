# Strings in Java

### What is a String?

* In Java, **String is a class** (`java.lang.String`), not a primitive type.
* A String represents a **sequence of characters**.
* Strings are **immutable**, meaning once created, their value **cannot be changed**.

```java
String s = "Hello";
s = s + " World";  // creates a new String object
```

---

## String Immutability

* Any operation like `replace()`, `toLowerCase()`, etc. **returns a new String**.
* The original String remains unchanged.
* This improves **security, thread-safety, and performance (via String Pool)**.

---

## String Pool

* Java stores string literals in a **String Pool**.
* If two literals have the same value, they refer to the **same object**.

```java
String a = "Java";
String b = "Java";  // same reference
```

---

# Commonly Used String Methods

---

## 1. `isEmpty()`

* Checks if the string length is **0**.

```java
"".isEmpty();      // true
"Java".isEmpty();  // false
```

---

## 2. `length()`

* Returns the **number of characters** in the string.

```java
"Java".length(); // 4
```

---

## 3. `replace()`

* Replaces **all occurrences** of a character or substring.

```java
"banana".replace('a', 'o'); // "bonono"
"abcabc".replace("abc", "x"); // "xx"
```

---

## 4. `substring()`

* Extracts a part of the string.

```java
"JavaProgramming".substring(4);      // "Programming"
"JavaProgramming".substring(0, 4);   // "Java"
```

---

## 5. `indexOf()`

* Returns the **first index** of a character or substring.
* Returns `-1` if not found.

```java
"Java".indexOf('a');  // 1
"Java".indexOf("va"); // 2
```

---

## 6. `lastIndexOf()`

* Returns the **last occurrence index**.

```java
"banana".lastIndexOf('a'); // 5
```

---

## 7. `startsWith()`

* Checks whether a string **starts with a given prefix**.
* Case-sensitive.

```java
String str = "JavaProgramming";

str.startsWith("Java");   // true
str.startsWith("Program"); // false
```

### Using offset

```java
str.startsWith("Program", 4); // true
```

**Use case:** URL validation, file name checks, protocol checks (`http`, `https`).

---

## 8. `contains()`

* Checks whether a string **contains a sequence of characters** anywhere.
* Case-sensitive.
* Accepts `CharSequence`, not `char`.

```java
String str = "JavaProgramming";

str.contains("Program"); // true
str.contains("java");    // false
```

```java
str.contains("a"); // valid
// str.contains('a'); ❌ compile-time error
```

**Internally uses:** `indexOf()`

---

## 9. `toLowerCase()`

* Converts all characters to lowercase.

```java
"JAVA".toLowerCase(); // "java"
```

---

## 10. `toUpperCase()`

* Converts all characters to uppercase.

```java
"java".toUpperCase(); // "JAVA"
```

---

## 11. `trim()`

* Removes **leading and trailing whitespaces**.

```java
"  Java  ".trim(); // "Java"
```

---

## 12. `isBlank()` (Java 11+)

* Returns `true` if the string is empty or contains **only whitespace**.

```java
"   ".isBlank(); // true
"Java".isBlank(); // false
```

---

## 13. `charAt()`

* Returns the character at a specific index.

```java
"Java".charAt(1); // 'a'
```

---

## 14. `chars()`

* Returns an **IntStream** of character Unicode values.

```java
"ABC".chars().forEach(System.out::println);
// Output: 65, 66, 67
```

---

## 15. `equals()`

* Compares **content**, not reference.

```java
"Java".equals("Java"); // true
```

---

## 16. `replaceFirst("^0+", "")`

* Uses **regular expression**.
* Removes **leading zeros**.

```java
"000123".replaceFirst("^0+", ""); // "123"
```

---

# `String.valueOf()` Methods

Used to convert **primitive data types into String**.

---

## 17. `String.valueOf(boolean b)`

```java
String.valueOf(true); // "true"
```

---

## 18. `String.valueOf(char c)`

```java
String.valueOf('A'); // "A"
```

---

## 19. `String.valueOf(char[] data)`

```java
char[] arr = {'J', 'a', 'v', 'a'};
String.valueOf(arr); // "Java"
```

---

## 20. `String.valueOf(int i)`

```java
String.valueOf(10); // "10"
```

---

## 21. `String.valueOf(long l)`

```java
String.valueOf(100000L); // "100000"
```

---

## 22. `String.valueOf(float f)`

```java
String.valueOf(10.5f); // "10.5"
```

---

## 23. `String.valueOf(double d)`

```java
String.valueOf(99.99); // "99.99"
```

---

# Additional Important String Methods

---

## 24. `String.join()` (Java 8+)

* Used to **join multiple strings** using a delimiter.
* Internally uses `StringBuilder`.

```java
String result = String.join("-", "Java", "Spring", "React");
// Java-Spring-React
```

### Joining a collection

```java
List<String> skills = List.of("Java", "Spring Boot", "React");
String joined = String.join(", ", skills);
// Java, Spring Boot, React
```

**Use cases:** CSV generation, displaying tags, joining list data

---

## 25. `String.format()`

* Creates **formatted strings** using placeholders (similar to `printf`).

```java
String msg = String.format("My name is %s and I am %d years old", "Anubhav", 30);
```

### Common format specifiers

| Specifier | Meaning            |
| --------- | ------------------ |
| `%s`      | String             |
| `%d`      | Integer            |
| `%f`      | Floating-point     |
| `%.2f`    | Two decimal places |
| `%n`      | New line           |

### Example

```java
double price = 123.456;
String formatted = String.format("Price: %.2f", price);
// Price: 123.46
```

**Use cases:** logs, reports, user messages

---

# Key Interview Points

* Strings are **immutable**
* Use `equals()` instead of `==`
* `isEmpty()` ≠ `isBlank()`
* `startsWith()` checks prefix, `contains()` checks anywhere
* `replace()` replaces all matches, `replaceFirst()` replaces first match
* `String.join()` is best for joining collections
* `String.format()` improves readability over concatenation
* `String.valueOf()` is preferred for primitive to String conversion
---

