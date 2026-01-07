**How Strings are Stored**

* When a Java program runs, the **JVM loads the program into memory**.
* The JVM creates an instance of **`java.lang.String`** for each **string literal** used.
* **Strings are immutable**, meaning once created, they cannot be changed.
* **String concatenation** results in the creation of a **new String object**.
* **`StringBuilder`** is used for **more efficient string modification**.
* Strings are stored in a **contiguous area of memory**, allowing **fast access**.
* Due to contiguous storage, strings **consume more memory** compared to some other data types.


![Code 1](pics/Code1.jpg)
![Visualization 1](pics/Visualization1.jpg)
![Code 2](pics/Code2.jpg)
![Visualization 2](pics/Visualization2.jpg)
