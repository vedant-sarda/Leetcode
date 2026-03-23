# 🧩 1431. Kids With the Greatest Number of Candies

🔗 **LeetCode Link:** https://leetcode.com/problems/kids-with-the-greatest-number-of-candies/

---

## 📝 Problem Statement

There are `n` kids with candies.

You are given:

* An array `candies[]`
* An integer `extraCandies`

👉 For each kid, check if giving them all extra candies makes them have the **greatest number of candies among all kids**.

Return a boolean array.

---

## 📌 Examples

### Example 1:

```
Input: candies = [2,3,5,1,3], extraCandies = 3
Output: [true,true,true,false,true]
```

### Example 2:

```
Input: candies = [4,2,1,1,2], extraCandies = 1
Output: [true,false,false,false,false]
```

### Example 3:

```
Input: candies = [12,1,12], extraCandies = 10
Output: [true,false,true]
```

---

## ⚙️ Constraints

* 2 <= n <= 100
* 1 <= candies[i] <= 100
* 1 <= extraCandies <= 50

---

## 💡 Approach (Brute Force)

* For each kid:

  * Add extraCandies
  * Compare with all other kids
* If no one has more → True

---

## 🚀 Python Solution

```python
from typing import List

class Solution:
    def kidsWithCandies(self, candies: List[int], extraCandies: int) -> List[bool]:
        ans = []
        
        for i in candies:
            res = True
            for j in candies:
                if i + extraCandies < j:
                    res = False
            ans.append(res)
        
        return ans
```

---

## ⚡ Optimized Approach (Better)

👉 Instead of comparing every time:

* Find max(candies)
* Check: `candies[i] + extraCandies >= max`

---

## 🚀 Optimized Python Solution

```python
from typing import List

class Solution:
    def kidsWithCandies(self, candies: List[int], extraCandies: int) -> List[bool]:
        max_candies = max(candies)
        return [(c + extraCandies) >= max_candies for c in candies]
```

---

## ⏱ Complexity

### Brute Force:

* Time: **O(n²)**

### Optimized:

* Time: **O(n)**
* Space: **O(n)**

---

## 🧠 Key Insight

You only need to compare with the **maximum value**, not every element.
