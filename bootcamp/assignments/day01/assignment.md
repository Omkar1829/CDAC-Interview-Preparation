# Day 01 Assignment

## 1. Today's Goal

Build a clean base for Java fundamentals, array/string coding, SQL basics, and project explanation.

## 2. Learning Objectives

- Explain JVM, JDK, and JRE with one practical example each.
- Describe Java stack vs heap memory.
- Write Java programs using arrays and strings without library shortcuts where asked.
- Write basic SQL queries confidently.
- Start a project explanation suitable for interviews.

## 3. Theory

Prepare short answers for:

1. What happens when `java Main` runs?
2. Difference between JDK, JRE, and JVM.
3. Stack memory vs heap memory.
4. How objects become eligible for garbage collection.
5. Why String is immutable in Java.

## 4. Reading Material

- Java official tutorial: classes, objects, arrays, strings.
- Any SQL notes covering SELECT, WHERE, GROUP BY, HAVING, ORDER BY.
- Your own resume/project files.

## 5. Coding Exercises

Easy:

1. Find the largest and second largest element in an array.
2. Reverse a string without using `StringBuilder.reverse()`.

Medium:

1. Move all zeroes to the end while maintaining order.
2. Check whether two strings are anagrams using frequency counting.

Hard:

1. Find the maximum subarray sum using Kadane's algorithm and explain why it works.

## 6. SQL Problems

Create an `employees` table mentally or in your SQL tool with columns:

`id`, `name`, `department`, `salary`, `joining_date`

Write queries for:

1. Employees with salary greater than 50000.
2. Highest salary per department.
3. Departments with average salary greater than 60000.
4. Employees who joined after 2024-01-01.
5. Count employees in each department, sorted by count descending.

## 7. Java Interview Questions

1. What is JVM and why is Java platform independent?
2. Difference between `==` and `.equals()` for strings.
3. Why is `String` immutable?
4. What is garbage collection?
5. Difference between primitive and reference variables.

## 8. DSA Problems

Use the 5 coding exercises above. For each, write:

- Approach
- Code
- Time complexity
- Space complexity
- Edge cases

## 9. Debugging Exercise

Find and explain the issue:

```java
public class Main {
    public static void main(String[] args) {
        String name = null;
        if (name.equals("CDAC")) {
            System.out.println("Match");
        }
    }
}
```

Required answer:

- Symptom
- Root cause
- Safe fix
- Prevention rule

## 10. Mini Project Task

Choose one project you will defend in interviews. Write:

- Project name
- Problem solved
- Users
- Tech stack
- Modules
- Database tables, if any
- Your exact contribution
- One technical challenge

## 11. Resume Question

Explain your strongest project in 90 seconds.

## 12. HR Question

Tell me about yourself as a software developer, not as a student.

## 13. Mock Interview Questions

Answer without checking notes first:

1. Explain JVM, JRE, JDK.
2. Walk me through memory allocation for `Student s = new Student();`.
3. Why are strings immutable?
4. Write a query to find the second highest salary.
5. Explain Kadane's algorithm.

## 14. Reflection

Write:

- What I completed
- What I skipped
- What I found difficult
- What I can explain confidently
- What I need revised tomorrow

## 15. Revision Checklist

- [x] JVM/JDK/JRE (Mastered JVM launcher vs `javac`)
- [x] Java memory (Mastered Stack vs Heap for `Student s = new Student()`)
- [ ] Object lifecycle & String Pool (Needs revision: Immutability reasons & `new String()` SCP count)
- [ ] Arrays (Carried over: Kadane's Algorithm)
- [ ] Strings (Carried over: Immutability benefits)
- [x] SQL basics (Mastered `WHERE`, `HAVING`, `GROUP BY`, and 2nd Highest Salary subquery)
- [x] Project intro (Mastered EduGuide-AI tech stack defense)
