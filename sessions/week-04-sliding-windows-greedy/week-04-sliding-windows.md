
# 🪟 Sliding Window: Mastering Efficient Range-Based Algorithms

## 🔍 What is Sliding Window?

The **sliding window** is a powerful technique used for problems involving **contiguous subarrays** or substrings. It helps **reduce the time complexity** of brute-force solutions by avoiding redundant calculations.

> 🧠 **Key Idea**: Instead of re-processing the entire window on every iteration, we **slide** the window and update relevant data incrementally.

---

## 🧩 When to Use It?

Use sliding window when the problem:
- Involves a **subarray or substring** in a linear data structure (array/string).
- Asks for:
    - Maximum/minimum sum/length
    - Longest/shortest subarray with some property
    - Count of substrings with constraints
- Has a **fixed-size window** or **variable-size** based on some condition.

---

## 🛠 Types of Sliding Window

### 1. **Fixed-size window**
Used when the window size is given explicitly (e.g. size `k`).

**Template:**
```python
for i in range(len(nums)):
    window_sum += nums[i]

    if i >= k - 1:
        result.append(window_sum)
        window_sum -= nums[i - k + 1]
```

---

### 2. **Variable-size window**
Used when you grow/shrink the window to meet a condition.

**Template:**
```python
start = 0
for end in range(len(nums)):
    # Expand the window by moving `end`

    while <window violates condition>:
        # Shrink the window by moving `start`

    # Check or update result
```

---

## 📉 Visual Concept

```
Initial     Expand               Slide
[ . . . ]   [ l . . . r ]        [ . l . . r ]
              ↑     ↑               ↑     ↑
            Expand               Slide
```

```python
# Expand example:
right += 1

# Slide example:
if <condition>:
    left += 1
else:
    right += 1
```

---

## 🧪 Examples with Patterns

### ✅ Example 1: Maximum Sum of Subarray of Size K

```python
def max_sum_subarray(nums, k):
    max_sum = window_sum = sum(nums[:k])
    for i in range(k, len(nums)):
        window_sum += nums[i] - nums[i - k]
        max_sum = max(max_sum, window_sum)
    return max_sum
```

🧠 *Pattern: Fixed-size window*

---

### ✅ Example 2: Longest Substring Without Repeating Characters

```python
def length_of_longest_substring(s):
    seen = set()
    left = max_len = 0
    for right in range(len(s)):
        while s[right] in seen:
            seen.remove(s[left])
            left += 1
        seen.add(s[right])
        max_len = max(max_len, right - left + 1)
    return max_len
```

🧠 *Pattern: Variable-size window + Set*

---

### ✅ Example 3: Minimum Size Subarray Sum ≥ Target

```python
def min_subarray_len(target, nums):
    total = left = 0
    min_len = float('inf')

    for right in range(len(nums)):
        total += nums[right]
        while total >= target:
            min_len = min(min_len, right - left + 1)
            total -= nums[left]
            left += 1

    return 0 if min_len == float('inf') else min_len
```

🧠 *Pattern: Shrink-to-fit variable-size window*

---

### ✅ Example 4: Permutation in String

Check if one string is a permutation of a substring of another string.

```python
from collections import Counter

def check_inclusion(s1, s2):
    if len(s1) > len(s2):
        return False

    s1_count = Counter(s1)
    window = Counter()

    for i in range(len(s2)):
        window[s2[i]] += 1
        if i >= len(s1):
            if window[s2[i - len(s1)]] == 1:
                del window[s2[i - len(s1)]]
            else:
                window[s2[i - len(s1)]] -= 1
        if window == s1_count:
            return True
    return False
```

🧠 *Pattern: Fixed-size + Frequency Matching*

---

## 📊 Time Complexity

Sliding window typically brings **O(n)** time complexity instead of O(n²).

---

## 🔁 Practice Problems

| Problem | Type | LeetCode |
|--------|------|----------|
| Maximum Sum of Subarray of Size K | Fixed-size | [Link](https://leetcode.com/problems/max-consecutive-ones-iii/) |
| Longest Substring Without Repeating Characters | Variable-size | [Link](https://leetcode.com/problems/longest-substring-without-repeating-characters/) |
| Minimum Size Subarray Sum | Variable-size | [Link](https://leetcode.com/problems/minimum-size-subarray-sum/) |
| Permutation in String | Fixed-size + Count Map | [Link](https://leetcode.com/problems/permutation-in-string/) |
| Longest Substring with At Most K Distinct Characters | Variable-size + Hash Map | [Link](https://leetcode.com/problems/longest-substring-with-at-most-k-distinct-characters/) |

---

## 🧠 Summary

| Feature | Fixed Window | Dynamic Window |
|--------|---------------|----------------|
| Size | Constant `k` | Varies based on condition |
| Adjust | Move both pointers | Expand/shrink dynamically |
| Use for | Known size problems | Conditional subarrays |

---
