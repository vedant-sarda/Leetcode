# 🧩 605. Can Place Flowers

🔗 **LeetCode Link:** https://leetcode.com/problems/can-place-flowers/

---

## 📝 Problem Statement

You have a flowerbed where:

* `0` → empty plot
* `1` → already planted

👉 Rule: **No two flowers can be adjacent**

Given:

* `flowerbed[]`
* integer `n`

👉 Return `true` if you can plant `n` flowers without violating the rule.

---

## 📌 Examples

### Example 1:

```
Input: flowerbed = [1,0,0,0,1], n = 1
Output: true
```

### Example 2:

```
Input: flowerbed = [1,0,0,0,1], n = 2
Output: false
```

---

## ⚙️ Constraints

* 1 <= flowerbed.length <= 2 * 10⁴
* flowerbed[i] ∈ {0,1}
* No adjacent flowers initially
* 0 <= n <= flowerbed.length

---

## 💡 Approach (Greedy Counting)

* Traverse the array
* Count consecutive empty plots
* If you find space for planting → reduce `n`
* Continue until `n == 0`

---

## 🚀 Python Solution

```python
from typing import List

class Solution:
    def canPlaceFlowers(self, flowerbed: List[int], n: int) -> bool:
        count = 1
        for i in range(len(flowerbed)):
            if flowerbed[i] == 0:
                count += 1
            else:
                count = 0

            if count == 3:
                n -= 1
                count = 1

                if n == 0:
                    return True

        if count == 2:
            n -= 1

        return n <= 0
```

---

## ⚡ Alternative Approach (Cleaner)

👉 Check each position:

* If left & right are empty → plant flower

---

## 🚀 Optimized Python Solution

```python
from typing import List

class Solution:
    def canPlaceFlowers(self, flowerbed: List[int], n: int) -> bool:
        for i in range(len(flowerbed)):
            if flowerbed[i] == 0:
                left = (i == 0) or (flowerbed[i - 1] == 0)
                right = (i == len(flowerbed) - 1) or (flowerbed[i + 1] == 0)

                if left and right:
                    flowerbed[i] = 1
                    n -= 1
                    if n == 0:
                        return True

        return n <= 0
```

---

## ⏱ Complexity

* Time Complexity: **O(n)**
* Space Complexity: **O(1)**

---

## 🧠 Key Insight

Greedy placement works because:

* You only need **local validation (left & right)**
* No need to check entire array each time
