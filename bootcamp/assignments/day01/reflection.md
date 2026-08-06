# Day 01 Reflection

Completed after Day 01 Mock Interview session.

## Completion

- Work completed: JVM architecture, Java Stack vs Heap memory, NullPointerException debugging & short-circuit `&&`, SQL queries (`WHERE`, `HAVING`, 2nd highest salary subquery), EduGuide-AI project pitch & system/DB architecture defense.
- Work skipped: DSA (Kadane's algorithm), String Pool deep dive.
- Time spent: ~3 hours interactive session.

## Weak Topics

- String Immutability design reasons (Security, Thread Safety, HashCode caching).
- String Constant Pool object allocation count (`new String("CDAC")`).
- Kadane's Algorithm ($O(N)$ maximum subarray sum accumulator).

## Strong Topics

- SQL Queries, Aggregates, Subqueries, and `WHERE` vs `HAVING`.
- Reference variable memory allocation on Stack holding Heap addresses.
- System Design & Database Schema Design for EduGuide-AI (ASP.NET Core, EF Core, React, PostgreSQL).

## Mistakes

| Topic | Mistake | Root Cause | Fix |
|---|---|---|---|
| JVM | Confused `java Main` with compilation | Thought `java` compiles code | `javac` compiles `.java` to `.class`; `java` launches JVM |
| Strings | Couldn't recall immutability reasons & SCP object count | Had not revised String pool internals | Memorize 4 reasons (Security, Thread safety, SCP, HashCode) and 2-object rule |
| DSA | Skipped Kadane's algorithm question | Not prepared for array algorithm | Practice 5 core DSA patterns on Day 02 |

## Tomorrow's Focus

- OOP 4 Pillars, Abstraction vs Encapsulation, Abstract Class vs Interface.
- Linked Lists (Reversing & Floyd's Cycle Detection) + Kadane's Algorithm carryover.
- SQL Joins (`INNER`, `LEFT`, `RIGHT`, `SELF JOIN`).

## Honesty Check

Can I explain today's topics without notes?

Answer: SQL, Stack/Heap memory, and Project defense: YES. String Pool & DSA: NO (carried over to Day 02).
