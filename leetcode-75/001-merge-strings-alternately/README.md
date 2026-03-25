# 🧩 1768. Merge Strings Alternately

🔗 **LeetCode Link:** https://leetcode.com/problems/merge-strings-alternately/

---

## 📝 Problem Statement

You are given two strings `word1` and `word2`.

Merge the strings by adding letters in alternating order, starting with `word1`.
If a string is longer than the other, append the additional letters onto the end of the merged string.

👉 Return the merged string.

---

## 📌 Examples

### Example 1:

```
Input: word1 = "abc", word2 = "pqr"
Output: "apbqcr"
```

### Example 2:

```
Input: word1 = "ab", word2 = "pqrs"
Output: "apbqrs"
```

### Example 3:

```
Input: word1 = "abcd", word2 = "pq"
Output: "apbqcd"
```

---

## ⚙️ Constraints

* 1 <= word1.length, word2.length <= 100
* word1 and word2 consist of lowercase English letters

---

## 💡 Approach (Two Pointer)

* Use two pointers for both strings
* Add characters alternately
* Append remaining characters

---

## 🚀 Python Solution

```python
class Solution:
    def mergeAlternately(self, word1: str, word2: str) -> str:
        result = []
        i = 0
        while i < len(word1) or i < len(word2):
            if i < len(word1):
                result.append(word1[i])
            if i < len(word2):
                result.append(word2[i])
            i += 1
        return ''.join(result)
```

---

## ⏱ Complexity

* Time Complexity: **O(n + m)**
* Space Complexity: **O(n + m)**

---

## 🧠 Key Insight

Alternate merging + handling leftover characters is the core idea.
