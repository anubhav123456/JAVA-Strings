
---

## 📌 String Equality

### 1. How to Compare Strings in Java

In Java, **strings should be compared using methods, not operators**.

### ✅ `equals()` Method

* Compares **content (value)** of two strings.
* Returns `true` if both strings have the same sequence of characters.

```java
name1.equals(name2);
```

### ✅ `equalsIgnoreCase()` Method

* Compares string values **ignoring case differences**.

```java
name1.equalsIgnoreCase("jamila"); // true
```

---

### ❌ `==` Operator (Not Recommended for Strings)

* Compares **references (memory addresses)**, not values.
* Returns `true` only if both variables point to the **same object in memory**.

```java
name1 == name2;
```

---

## 2. String Pool vs Heap Memory

### 🔹 String Literals

```java
String name1 = "Jamila";
String name2 = "Jamila";
```

* Stored in the **String Pool**
* Both variables reference the **same memory location**

### 🔹 Using `new` Keyword

```java
String name3 = new String("Jamila");
```

* Stored in **heap memory**
* Creates a **new object**, even if the value already exists in the String Pool

---

## 3. Example Explanation

```java
String name1 = "Jamila";
String name2 = "Jamila";
name2 = "Alex";
String name3 = new String("Jamila");
```

### Reference Comparison (`==`)

```java
name1 == name2   // false → "Jamila" vs "Alex"
name1 == name3   // false → String Pool vs Heap memory
```

### Value Comparison (`equals`)

```java
name1.equals(name2) // false → values differ
name1.equals(name3) // true → values are same
```

---

## 4. Key Takeaways ⭐

* ✅ Always use **`equals()`** for string comparison
* ❌ Never rely on **`==`** for string value comparison
* 📦 String literals are stored in the **String Pool**
* 🧠 `new String()` always creates a **new object in heap memory**
* 🧪 `==` → compares **memory**
* 🧪 `equals()` → compares **content**

---
