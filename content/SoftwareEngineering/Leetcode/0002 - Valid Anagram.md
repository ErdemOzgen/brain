
[242. Valid Anagram](https://leetcode.com/problems/valid-anagram/)

Solved

Easy

Topics

Companies

Given two strings `s` and `t`, return `true` if `t` is an 

anagram

 of `s`, and `false` otherwise.

**Example 1:**

**Input:** s = "anagram", t = "nagaram"

**Output:** true

**Example 2:**

**Input:** s = "rat", t = "car"

**Output:** false

**Constraints:**

- `1 <= s.length, t.length <= 5 * 104`
- `s` and `t` consist of lowercase English letters.

**Follow up:** What if the inputs contain Unicode characters? How would you adapt your solution to such a case?





Here's how you can solve the problem using Python by leveraging sorting or a frequency count approach:

### Approach 1: Sorting
If two strings are anagrams, they should contain the same characters with the same frequency. By sorting the strings and comparing them, we can check if they are anagrams.

```python
class Solution:
    def isAnagram(self, s: str, t: str) -> bool:
        # If the lengths of s and t are different, they can't be anagrams
        if len(s) != len(t):
            return False
        
        # Sort both strings and compare
        return sorted(s) == sorted(t)
```

### Explanation:
1. **Check length**: If the lengths of `s` and `t` are different, return `False` immediately because they can't be anagrams.
2. **Sort and compare**: Sort both strings and check if they are equal. If they are, then `t` is an anagram of `s`.

### Time Complexity:
- Sorting both strings takes O(n log n) time, where n is the length of the strings.

### Space Complexity:
- Sorting requires additional space, but it depends on the language implementation. In general, the space complexity is O(1) if the sort is done in place, or O(n) if it creates a new sorted array.

---

### Approach 2: Frequency Count
Instead of sorting, we can count the frequency of each character in both strings and compare the counts.

```python
from collections import Counter

class Solution:
    def isAnagram(self, s: str, t: str) -> bool:
        # If the lengths of s and t are different, they can't be anagrams
        if len(s) != len(t):
            return False
        
        # Count the frequency of characters in both strings and compare
        return Counter(s) == Counter(t)
```

### Explanation:
1. **Check length**: If the lengths of `s` and `t` are different, return `False` immediately because they can't be anagrams.
2. **Frequency count**: Use the `Counter` from the `collections` module to count the frequency of each character in `s` and `t`.
3. **Compare counts**: If the two `Counter` objects are equal, `t` is an anagram of `s`.

### Time Complexity:
- Counting the frequency of each character takes O(n) time.

### Space Complexity:
- The space complexity is O(1) if the character set is fixed (e.g., 26 lowercase English letters), or O(n) if the character set can grow.

### Follow-Up for Unicode Characters:
If the inputs contain Unicode characters, the same approach will work. The only change would be handling Unicode strings properly, which Python natively supports with its `str` and `Counter` functionalities. So, no modifications are required for the above code to work with Unicode characters.



 Here's the solution using a hashmap (dictionary) approach to check if two strings are anagrams:

```python
class Solution:
    def isAnagram(self, s: str, t: str) -> bool:
        # If the lengths of s and t are different, they can't be anagrams
        if len(s) != len(t):
            return False
        
        # Create a dictionary to count characters in s
        count_s = {}
        
        # Count the frequency of each character in s
        for char in s:
            if char in count_s:
                count_s[char] += 1
            else:
                count_s[char] = 1
                
        # Subtract the frequency of each character in t
        for char in t:
            if char in count_s:
                count_s[char] -= 1
            else:
                # If a character in t is not in s, return False
                return False
        
        # If all values in count_s are zero, it's an anagram
        for count in count_s.values():
            if count != 0:
                return False
                
        return True
```

### Explanation:
1. **Length check**: If `s` and `t` have different lengths, return `False` immediately.
2. **Count frequency for `s`**: Create a hashmap (`count_s`) where keys are characters in `s` and values are the frequency of each character.
3. **Adjust frequency for `t`**: For each character in `t`, decrease its count in `count_s`.
   - If a character in `t` is not in `count_s`, return `False` (since it means `t` has a character not present in `s`).
4. **Check if all counts are zero**: After processing both strings, all the values in `count_s` should be zero. If not, it means the strings are not anagrams.

### Time Complexity:
- O(n), where n is the length of the strings. Each character is processed twice (once for counting and once for adjusting).

### Space Complexity:
- O(1), assuming a fixed character set like lowercase English letters (26 characters). If we consider all Unicode characters, it would be O(n) due to the possible large number of keys in the hashmap.

### Why Use a Hashmap?
Using a hashmap (dictionary) is efficient for counting elements, as accessing and modifying dictionary entries is O(1). This approach avoids the overhead of sorting and works well even for larger inputs.

Let me know if you'd like to see further optimizations or variations!



Also good solution


```python

class Solution:
    def isAnagram(self, s: str, t: str) -> bool:
        if len(s) != len(t):
            return False

        countS, countT = {}, {}

        for i in range(len(s)):
            countS[s[i]] = 1 + countS.get(s[i], 0)
            countT[t[i]] = 1 + countT.get(t[i], 0)
        return countS == countT

    
    # easier solution
    #return True if sorted(s) == sorted(t) else False
```


