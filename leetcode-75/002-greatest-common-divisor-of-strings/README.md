# 🧩 002. Greatest Common Divisor of Strings

🔗 **LeetCode Link:** https://leetcode.com/problems/greatest-common-divisor-of-strings/

---

## 📝 Problem Statement

For two strings `s` and `t`, we say **"t divides s"** if and only if
`s = t + t + t + ... + t`

👉 Given two strings `str1` and `str2`, return the **largest string x** such that
x divides both `str1` and `str2`.

---

## 📌 Examples

### Example 1:

```
Input: str1 = "ABCABC", str2 = "ABC"
Output: "ABC"
```

### Example 2:

```
Input: str1 = "ABABAB", str2 = "ABAB"
Output: "AB"
```

### Example 3:

```
Input: str1 = "LEET", str2 = "CODE"
Output: ""
```

---

## ⚙️ Constraints

* 1 <= str1.length, str2.length <= 1000
* Strings consist of uppercase English letters

---

## 💡 Approach (Math + GCD Concept)

👉 Key Observation:

* If a valid string exists →
  `str1 + str2 == str2 + str1`

👉 Then answer = substring of length:

```
gcd(len(str1), len(str2))
```

---

## 🚀 Python Solution

```python
import math

class Solution:
    def gcdOfStrings(self, str1: str, str2: str) -> str:
        if str1 + str2 != str2 + str1:
            return ""
        
        gcd_len = math.gcd(len(str1), len(str2))
        
        return str1[:gcd_len]
```

---

## ⏱ Complexity

* Time Complexity: **O(n + m)**
* Space Complexity: **O(1)**

---

## 🧠 Key Insight

String pattern must repeat consistently →
Then GCD of lengths gives the answer.
