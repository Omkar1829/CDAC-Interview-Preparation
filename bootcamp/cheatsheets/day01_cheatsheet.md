# ⚡ Day 01 High-Yield Cheatsheet — Java Architecture & Memory

## ☕ 1. Core Architecture Formulas
- **JDK Formula:** `JDK = JRE + Development Tools (javac, jdb, jar, javadoc)`
- **JRE Formula:** `JRE = JVM + Core Class Libraries (java.base, rt.jar)`
- **JVM Role:** Converts platform-neutral bytecode (`.class`) to OS-native machine code.

## 🧠 2. JVM Memory Allocation Trace: `Student s = new Student();`
1. **Metaspace:** `Student.class` bytecode & static fields loaded.
2. **JVM Stack:** Reference variable `s` created on active thread stack frame.
3. **Heap:** `new Student()` allocates memory for instance fields in Eden space.
4. **Link:** Memory reference address stored inside `s`.

## 🔤 3. String Pool & Memory Rules
- **Rule:** `String s = "CDAC";` $\rightarrow$ 1 object in String Constant Pool (SCP).
- **Rule:** `String s = new String("CDAC");` $\rightarrow$ 2 objects if `"CDAC"` not in SCP (1 SCP, 1 Heap). `s` points to **Heap**.
- **Equality:** `==` checks **memory reference address**; `.equals()` checks **character content**.

## 📊 4. Basic SQL Clause Order
`SELECT` $\rightarrow$ `FROM` $\rightarrow$ `WHERE` (filters rows before aggregation) $\rightarrow$ `GROUP BY` $\rightarrow$ `HAVING` (filters groups after aggregation) $\rightarrow$ `ORDER BY`
