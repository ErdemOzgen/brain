
[1. Two Sum](https://leetcode.com/problems/two-sum/)

Easy

Topics

Companies

Hint

Given an array of integers `nums` and an integer `target`, return _indices of the two numbers such that they add up to `target`_.

You may assume that each input would have **_exactly_ one solution**, and you may not use the _same_ element twice.

You can return the answer in any order.

**Example 1:**

**Input:** nums = [2,7,11,15], target = 9
**Output:** [0,1]
**Explanation:** Because nums[0] + nums[1] == 9, we return [0, 1].

**Example 2:**

**Input:** nums = [3,2,4], target = 6
**Output:** [1,2]

**Example 3:**

**Input:** nums = [3,3], target = 6
**Output:** [0,1]

**Constraints:**

- `2 <= nums.length <= 104`
- `-109 <= nums[i] <= 109`
- `-109 <= target <= 109`
- **Only one valid answer exists.**

**Follow-up:** Can you come up with an algorithm that is less than `O(n2)` time complexity?


To solve the "Two Sum" problem, we need to find two distinct indices in the array where the sum of the numbers at those indices equals the target.

### Approach:

1. **Brute Force (O(n²)):**
   - Check every possible pair of numbers and see if their sum equals the target.
   - However, the brute force approach isn't efficient for large inputs, as it has a time complexity of \(O(n^2)\).

2. **Optimal Approach using HashMap (O(n)):**
   - We can solve this in linear time using a hash map (or dictionary in Python).
   - As we iterate through the array, we check if the complement (i.e., `target - current number`) exists in the hash map.
   - If it exists, we found our pair; otherwise, we store the current number along with its index in the hash map.
   - This approach works in \(O(n)\) time since we only pass through the array once.

### Algorithm:

1. Create an empty hash map (dictionary) to store numbers and their indices.
2. Iterate through the `nums` array.
3. For each element, compute its complement by subtracting the current element from the target (`complement = target - nums[i]`).
4. Check if the complement exists in the hash map.
   - If it does, return the indices of the current element and the complement.
   - If not, store the current element and its index in the hash map.
5. Continue this process until the solution is found.

### Code Implementation:

```python
def twoSum(nums, target):
    # Dictionary to store the value and its index
    hashmap = {}
    
    # Iterate through the array
    for i, num in enumerate(nums):
        # Calculate the complement
        complement = target - num
        
        # Check if complement is in the hashmap
        if complement in hashmap:
            # Return the indices if complement is found
            return [hashmap[complement], i]
        
        # Store the current number and its index in the hashmap
        hashmap[num] = i

# Test cases
print(twoSum([2, 7, 11, 15], 9))  # Output: [0, 1]
print(twoSum([3, 2, 4], 6))       # Output: [1, 2]
print(twoSum([3, 3], 6))          # Output: [0, 1]
```

### Explanation:

- **nums = [2, 7, 11, 15], target = 9**:
  - Iteration 1: `num = 2`, `complement = 7`. Hash map is `{}`. Store `2` with index `0` → `{2: 0}`.
  - Iteration 2: `num = 7`, `complement = 2`. Found `2` in the hash map! Return `[0, 1]`.

- **nums = [3, 2, 4], target = 6**:
  - Iteration 1: `num = 3`, `complement = 3`. Hash map is `{}`. Store `3` with index `0` → `{3: 0}`.
  - Iteration 2: `num = 2`, `complement = 4`. Store `2` with index `1` → `{3: 0, 2: 1}`.
  - Iteration 3: `num = 4`, `complement = 2`. Found `2` in the hash map! Return `[1, 2]`.

### Time Complexity:

- **Time Complexity**: \(O(n)\), where \(n\) is the length of the input array `nums`. We only iterate through the array once.
- **Space Complexity**: \(O(n)\), because in the worst case, we need to store all the elements in the hash map.

This solution is efficient and solves the problem in linear time.
```python
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        prevMap = {}  # val -> index

        for i, n in enumerate(nums):
            diff = target - n
            if diff in prevMap:
                return [prevMap[diff], i]
            prevMap[n] = i

```
