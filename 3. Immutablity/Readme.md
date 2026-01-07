
---

## Why Strings Are Immutable in Java 

---

## 1️⃣ String Pool & References

![Viz1](pics/Viz1.jpg)

### Memory Stack

* Variables like `name1`, `name2`, `name3`, `name4` are stored in the **stack**
* These variables do **not store the actual string**
* They store **references (addresses)** to String objects

### Heap → String Pool

* String literals like `"Alex"` and `"Jamila"` are stored in the **String Pool**
* The String Pool is a special part of the **Heap memory**
* Multiple references can point to the **same String object**

Example:

```java
String name1 = "Jamila";
String name2 = "Alex";
String name3 = "Jamila";
String name4 = "Jamila";
```

All `name1`, `name3` and `name4` point to **the same `"Jamila"` object** in the String Pool.
This is exactly what the first picture shows.

---

## 2️⃣ What If Strings Were Mutable? (The Core Problem)

![Viz2](pics/Viz2.jpg)

Assume **Strings were mutable**.

Now consider:



If `"Jamila"` were mutable, Java would modify the **same object** in memory.

### What would happen then?

* `"Jamila"` becomes `"Foo"`
* Since `name1`, `name3`, `name4` all reference the **same object**
* **All references would see the change**

That means:

```java
System.out.println(name1); // Foo ❌
System.out.println(name3); // Foo ❌
System.out.println(name4); // Foo ❌
```

### 🚨 This is dangerous

* One reference changing the value affects all others
* Leads to **unexpected behavior**
* Breaks reliability and safety of the program

---

## 3️⃣ Java’s Design Decision: Strings Are Immutable

To avoid this problem, Java makes **Strings immutable**.

👉 **Once a String object is created, its value can never be changed.**

---

## 4️⃣ What Actually Happens

Consider this code again:

```java
String name1 = "Jamila";
name1 = name1.concat("Foo");
```

### What Java really does:

❌ Java does **NOT** change `"Jamila"`
✅ Java creates a **new String object**

Steps:

1. `"Jamila"` remains unchanged in the String Pool
2. A new String object `"JamilaFoo"` is created
3. `name1` now points to `"JamilaFoo"`
4. Other references (`name3`, `name4`) still point to `"Jamila"`

📌 **Only the reference changes, not the original object**

This is exactly what your second picture demonstrates.

---

## 5️⃣ Key Rule (Very Important)

> **In Java, Strings never change their value. When you “modify” a String, Java actually creates a new String and changes the reference.**

---

## 6️⃣ Additional Benefits of String Immutability

### 🔐 Security

* Strings are used for passwords, file paths, URLs
* Immutability prevents accidental or malicious modification

### ⚡ Performance (String Pool)

* Same string values are reused
* Saves memory

### 🧵 Thread Safety

* Immutable objects are automatically thread-safe
* No synchronization needed

---

## 7️⃣ Final Summary (Interview-Ready)

> **Strings are immutable in Java to prevent shared references from causing unintended changes. Instead of modifying the object, Java creates a new String and updates the reference.**

This ensures **safety, predictability, and performance**.

---
