
# Two Sum Problem

## Problem Description
Given an array of integers `nums` and an integer `target`, return **indices** of the two numbers such that they add up to the `target`.

You may assume that each input would have **exactly one solution**, and you may not use the same element twice.

The output can be returned in any order.

## Example 1
```
Input: nums = [2, 7, 11, 15], target = 9  
Output: [0, 1]  
Explanation: nums[0] + nums[1] == 9, so we return [0, 1].
```

## Example 2
```
Input: nums = [3, 2, 4], target = 6  
Output: [1, 2]
```

## Example 3
```
Input: nums = [3, 3], target = 6  
Output: [0, 1]
```

## Constraints
- 2 <= nums.length <= 10^4
- -10^9 <= nums[i] <= 10^9
- -10^9 <= target <= 10^9
- Only one valid solution exists for each input.

## Approach

The problem can be solved in less than O(n²) time complexity by using a hash map (or dictionary) to store the indices of the numbers we have seen so far. For each number, we check if the complement (i.e., `target - num`) exists in the hash map. If it does, we return the indices of the current number and the complement.

This approach has a time complexity of **O(n)**, where `n` is the number of elements in the array.

### Steps:
1. Initialize an empty hash map (`dict`).
2. Loop through the list of numbers:
   - For each number `num` at index `i`, calculate the complement: `complement = target - num`.
   - If the complement exists in the hash map, return the index of the complement and the current index `i`.
   - Otherwise, store the current number and its index in the hash map.
   
### Code Example

```python
def two_sum(nums, target):
    num_to_index = {}
    
    for i, num in enumerate(nums):
        complement = target - num
        if complement in num_to_index:
            return [num_to_index[complement], i]
        num_to_index[num] = i
```

## Follow-up
The above algorithm has a time complexity of **O(n)**, which is optimal for this problem as we need to check every element at least once. This solution uses **O(n)** space due to the hash map.
