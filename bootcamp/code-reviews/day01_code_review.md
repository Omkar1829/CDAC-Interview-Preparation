# 🔍 Day 01 Code Review — Array & String Solutions

## 1. String Reversal (Two Pointer In-Place)
```java
public static String reverseString(String str) {
    if (str == null || str.isEmpty()) return str;
    char[] chars = str.toCharArray();
    int left = 0, right = chars.length - 1;
    while (left < right) {
        char temp = chars[left];
        chars[left] = chars[right];
        chars[right] = temp;
        left++; right--;
    }
    return new String(chars);
}
```
* **Time Complexity:** $\mathcal{O}(N)$
* **Space Complexity:** $\mathcal{O}(N)$ (for `char[]` array creation)
* **Review Verdict:** **PASS (10/10)** — Optimal in-place character swapping. Avoided `StringBuilder.reverse()` per requirement.

## 2. Null Pointer Debugging Review
```java
// Candidate Fix
if ("CDAC".equals(name)) { ... }
```
* **Review Verdict:** **PASS (9.5/10)** — Yoda condition correctly prevents runtime `NullPointerException` when `name` is `null`.
