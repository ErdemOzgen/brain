[49. Group Anagrams](https://leetcode.com/problems/group-anagrams/)

Medium

Topics

Companies

Given an array of strings `strs`, group the 

anagrams

 together. You can return the answer in **any order**.

**Example 1:**

**Input:** strs = ["eat","tea","tan","ate","nat","bat"]

**Output:**  [["bat"],["nat","tan"],["ate","eat","tea"]]

**Explanation:**

- There is no string in strs that can be rearranged to form `"bat"`.
- The strings `"nat"` and `"tan"` are anagrams as they can be rearranged to form each other.
- The strings `"ate"`, `"eat"`, and `"tea"` are anagrams as they can be rearranged to form each other.

**Example 2:**

**Input:** strs = [""]

**Output:** [[""]]

**Example 3:**

**Input:** strs = ["a"]

**Output:** [["a"]]

**Constraints:**

- `1 <= strs.length <= 104`
- `0 <= strs[i].length <= 100`
- `strs[i]` consists of lowercase English letters.

To solve the "Group Anagrams" problem, we need to group strings that are anagrams of each other. Two strings are anagrams if they contain the same characters in the same frequencies, but possibly in a different order.

### Approach:

1. **Key Idea:**
   - We can use sorting to identify anagrams. If two strings are anagrams, their sorted versions will be identical.
   - Alternatively, we can use a frequency count of characters as a signature for each string.
   
2. **Optimal Approach:**
   - Create a dictionary where the key is a signature of the string (sorted characters or character counts), and the value is a list of strings that share that signature.
   - Iterate through the list of strings, compute the signature for each, and group them into the dictionary.
   - Finally, return the values of the dictionary as the grouped anagrams.

### Solution using Sorted Strings:

We can use sorted strings as the key for each group of anagrams. By sorting the characters in each string, we can group anagrams together.

### Algorithm:

1. Create an empty dictionary to store the groups of anagrams.
2. For each string in `strs`, sort its characters and use the sorted string as a key in the dictionary.
3. Append the original string to the list corresponding to that key.
4. After processing all strings, return the values of the dictionary, which are the grouped anagrams.

### Code Implementation:

```python
def groupAnagrams(strs):
    # Dictionary to store groups of anagrams
    anagram_map = {}
    
    # Iterate through each string in the input list
    for s in strs:
        # Sort the string to use as the key
        sorted_str = ''.join(sorted(s))
        
        # Add the string to the corresponding anagram group
        if sorted_str not in anagram_map:
            anagram_map[sorted_str] = []
        anagram_map[sorted_str].append(s)
    
    # Return all grouped anagrams
    return list(anagram_map.values())

# Test cases
print(groupAnagrams(["eat", "tea", "tan", "ate", "nat", "bat"]))
# Output: [["bat"], ["nat","tan"], ["ate","eat","tea"]]

print(groupAnagrams([""]))
# Output: [[""]]

print(groupAnagrams(["a"]))
# Output: [["a"]]
```

### Explanation:

- **strs = ["eat", "tea", "tan", "ate", "nat", "bat"]**:
  - For each string, we sort its characters:
    - "eat" → "aet"
    - "tea" → "aet"
    - "tan" → "ant"
    - "ate" → "aet"
    - "nat" → "ant"
    - "bat" → "abt"
  - The dictionary after processing all strings:
    ```python
    {
      "aet": ["eat", "tea", "ate"],
      "ant": ["tan", "nat"],
      "abt": ["bat"]
    }
    ```
  - The final result is `[['eat', 'tea', 'ate'], ['tan', 'nat'], ['bat']]`.

- **strs = [""]**:
  - The sorted version of the empty string is also an empty string, so the output is `[['']]`.

- **strs = ["a"]**:
  - The sorted version of "a" is "a", so the output is `[['a']]`.

### Time Complexity:

- **Time Complexity**: \(O(n \cdot k \log k)\), where \(n\) is the number of strings, and \(k\) is the maximum length of a string. Sorting each string takes \(O(k \log k)\), and we do this for all \(n\) strings.
- **Space Complexity**: \(O(n \cdot k)\), where \(n\) is the number of strings and \(k\) is the maximum length of a string, as we store the strings in a dictionary.

This solution is efficient and works well within the problem constraints.