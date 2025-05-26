=# 🚀 Two Pointers Technique Lecture

## 🧠 1. Introduction
The Two Pointers technique is a powerful method used in algorithm design to solve problems involving linear data structures such as arrays or linked lists. It uses two indices (or pointers) that move through the data structure in a coordinated way to accomplish a task efficiently.

---

## 🎓 2. Lecture

### 🧭 Two Pointers Strategy Types

#### 🔁 A. Inward (Opposite Ends)
Two pointers start at both ends of the array and move toward the center.
- 📌 **Use Case:** Finding a pair with a given sum in a sorted array.

#### 🪝 B. Staged (Fixed + Moving)
One pointer is fixed, and the other scans or moves based on conditions.
- 📌 **Use Case:** Triple sum problems (3Sum), comparing elements after fixing one.

#### 🔂 C. Unidirectional (Same Direction)
Both pointers start from the beginning and move forward.
- 📌 **Use Case:** Moving non-zero elements forward in-place (e.g., Move Zeroes).

---

## 🧩 3. Pattern Examples

### 🔁 D. Inward: Valid Palindrome (🧼 Clean & Check)
```python
s = "A man, a plan, a canal: Panama"
filtered = [c.lower() for c in s if c.isalnum()]
left, right = 0, len(filtered) - 1
while left < right:
    if filtered[left] != filtered[right]:
        print(False)
        break
    left += 1
    right -= 1
else:
    print(True)
```
**🧼 Explanation:**
- Normalize the string: remove non-alphanumerics and convert to lowercase.
- Use two pointers from both ends to compare characters.
- If mismatch occurs, it's not a palindrome.
- Stops early on failure and returns True only if all characters match.

### 🔁 A. Inward: Two Sum II
```python
arr = [2, 7, 11, 15]
target = 9
left, right = 0, len(arr) - 1
while left < right:
    curr_sum = arr[left] + arr[right]
    if curr_sum == target:
        print(left, right)
        break
    elif curr_sum < target:
        left += 1
    else:
        right -= 1
```

### 🔂 B. Unidirectional: Move Zeroes (📚 Homework)
```python
nums = [0, 1, 0, 3, 12]
lastNonZeroFoundAt = 0
for current in range(len(nums)):
    if nums[current] != 0:
        nums[lastNonZeroFoundAt], nums[current] = nums[current], nums[lastNonZeroFoundAt]
        lastNonZeroFoundAt += 1
```

### 🪝 C. Staged: Triple Sum (🏫 In-Class Work)
```python
nums = [-1, 0, 1, 2, -1, -4]
nums.sort()
res = []
for i in range(len(nums) - 2):
    if i > 0 and nums[i] == nums[i - 1]:
        continue
    left, right = i + 1, len(nums) - 1
    while left < right:
        total = nums[i] + nums[left] + nums[right]
        if total < 0:
            left += 1
        elif total > 0:
            right -= 1
        else:
            res.append([nums[i], nums[left], nums[right]])
            while left < right and nums[left] == nums[left + 1]:
                left += 1
            while left < right and nums[right] == nums[right - 1]:
                right -= 1
            left += 1
            right -= 1
print(res)
```
**🔍 Explanation:**
- ✅ Sort the array.
- ✅ Fix one element, then use two pointers to find remaining two elements.
- ✅ Skip duplicates to ensure unique triplets.

---

## 🌟 4. Benefits
- ⚡ Reduces time complexity (often from O(n^2) to O(n))
- 🧩 Intuitive once practiced
- 🏆 Common in interviews and competitive programming

---

## 💡 5. Tips
- 🔍 Sort the array if order helps.
- ⚠️ Watch for duplicate elements and edge cases.
- ✏️ Simulate with pen & paper to understand pointer dynamics.

---

## 🏋️‍♂️ 6. Top Practice Problems
- ✅ LeetCode 167: Two Sum II - Input array is sorted
- ✅ LeetCode 15: 3Sum
- ✅ LeetCode 283: Move Zeroes
- ✅ LeetCode 125: Valid Palindrome
- ✅ LeetCode 344: Reverse String
- ✅ LeetCode 11: Container With Most Water
- ✅ LeetCode 26: Remove Duplicates from Sorted Array
- ✅ LeetCode 42: Trapping Rain Water (advanced two pointers)
- ✅ LeetCode 80: Remove Duplicates from Sorted Array II
- ✅ LeetCode 392: Is Subsequence
- ✅ LeetCode 524: Longest Word in Dictionary through Deleting

---

## 📝 7. Exercises

### 🏫 In-Class Work: Triple Sum (3Sum)
Dive deep into 3Sum to practice the staged two pointer strategy.

### 📚 Homework: Move Zeroes
Reinforce the unidirectional pointer technique with in-place modification.

---

## 🎯 Conclusion
The Two Pointers technique is a fundamental approach in algorithmic problem-solving. Mastering it will significantly improve your ability to write efficient and elegant code for array and linked list problems.

🔥 Keep solving, stay sharp, and have fun with pointers!
