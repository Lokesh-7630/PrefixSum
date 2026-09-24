# 3. Longest Substring Without Repeating Characters

![LeetCode](https://img.shields.io/badge/LeetCode-3._Longest_Substring_Without_Repeating_Characters-FFA116?style=for-the-badge&logo=leetcode&logoColor=black)
![Difficulty](https://img.shields.io/badge/Difficulty-Medium-yellow?style=for-the-badge)
![Language](https://img.shields.io/badge/Language-C++-00599C?style=for-the-badge&logo=cplusplus)

---

## 📝 Problem Statement

Given a string `s`, find the length of the **longest substring** without duplicate characters.

---

## 💡 Examples

### Example 1
**Input:** `s = "abcabcbb"`  
**Output:** `3`  
**Explanation:** The answer is `"abc"`, with the length of `3`. Note that `"bca"` and `"cab"` are also valid substrings of length `3`.

### Example 2
**Input:** `s = "bbbbb"`  
**Output:** `1`  
**Explanation:** The answer is `"b"`, with the length of `1`.

### Example 3
**Input:** `s = "pwwkew"`  
**Output:** `3`  
**Explanation:** The answer is `"wke"`, with the length of `3`.  
*Note:* The answer must be a **substring**. `"pwke"` is a *subsequence* and not a substring.

---

## 🔒 Constraints

- `0 <= s.length <= 10^5`
- `s` consists of English letters, digits, symbols, and spaces.

---

## 🧠 Intuition & Approach

We use the **Sliding Window (Two Pointers)** technique optimized with an array/hash table to keep track of the last seen index of each character.

1. Maintain two pointers: `left` and `right`, defining the sliding window `s[left ... right]`.
2. As `right` iterates from `0` to `N - 1`:
   - If `s[right]` was seen before **within the current window** (i.e., its last seen position `>= left`), shift `left` directly to `last_seen[s[right]] + 1`.
   - Update the last seen position of `s[right]` to `right`.
   - Calculate the max length: `maxLength = max(maxLength, right - left + 1)`.
3. Because ASCII has 256 standard characters, we can replace a heavy hash map with a fixed-size `vector<int> lastSeen(256, -1)` for optimal O(1) lookup performance.

---

