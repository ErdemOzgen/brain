https://leetcode.com/problems/contains-duplicate/description/

#leetcode
#interview 

Given an integer array `nums`, return `true` if any value appears **at least twice** in the array, and return `false` if every element is distinct.

**Example 1:**

**Input:** nums = [1,2,3,1]

**Output:** true

**Explanation:**

The element 1 occurs at the indices 0 and 3.

**Example 2:**

**Input:** nums = [1,2,3,4]

**Output:** false

**Explanation:**

All elements are distinct.

**Example 3:**

**Input:** nums = [1,1,1,3,3,4,3,2,4,2]

**Output:** true

**Constraints:**

- `1 <= nums.length <= 105`
- `-109 <= nums[i] <= 109`
  

Here's how you can solve the problem using Python. You can leverage the properties of sets to check for duplicates efficiently:

```python
class Solution:
    def containsDuplicate(self, nums: List[int]) -> bool:
        # Create an empty set to store unique elements
        seen = set()
        
        # Iterate through each number in the input list
        for num in nums:
            # If the number is already in the set, it means it's a duplicate
            if num in seen:
                return True
            # Otherwise, add the number to the set
            seen.add(num)
        
        # If no duplicates were found, return False
        return False
```

### Explanation:
1. **Initialize a set**: `seen = set()`. Sets in Python do not allow duplicate values, which makes them useful for checking whether an element has already been seen.
2. **Iterate through `nums`**: For each number in the input list `nums`, check if it already exists in the `seen` set.
3. **Check for duplicates**:
   - If `num` is already in `seen`, it means we've encountered a duplicate, so return `True`.
   - If not, add `num` to the `seen` set.
4. If we iterate through the entire list without finding a duplicate, return `False`.

### Time Complexity:
- The time complexity is O(n), where n is the number of elements in the list. Checking and inserting into a set both have an average time complexity of O(1).

### Space Complexity:
- The space complexity is O(n) because, in the worst case, we might need to store all elements of the input list in the set.

This solution efficiently checks for duplicates using sets and is well-suited for the given constraints.