# Find Duplicates in an Array of Integers

## Problem Statement

Given an array of integers, find all the duplicate elements present in the array. The solution should return a list of duplicates.

## Example

```plaintext
Input: [4, 3, 2, 7, 8, 2, 3, 1]
Output: [2, 3]
```

## Constraints

- The array can contain both positive and negative integers.
- The array is not necessarily sorted.
- The solution should have a time complexity of O(n) and a space complexity of O(1) if possible.

## Approach

1. **Using a HashMap**: 
    - Traverse the array and use a hashmap to count the occurrences of each element.
    - Collect elements that have a count greater than 1.

2. **In-place Marking**:
    - Traverse the array and for each element, mark the index corresponding to the value as visited by negating the value at that index.
    - If an index is already marked, it means the element is a duplicate.

## Solution

### Using a HashMap

```python
def find_duplicates(nums):
     counts = {}
     duplicates = []
     for num in nums:
          if num in counts:
                counts[num] += 1
          else:
                counts[num] = 1
     for num, count in counts.items():
          if count > 1:
                duplicates.append(num)
     return duplicates
```

### In-place Marking

```python
def find_duplicates(nums):
     duplicates = []
     for i in range(len(nums)):
          index = abs(nums[i]) - 1
          if nums[index] < 0:
                duplicates.append(abs(nums[i]))
          else:
                nums[index] = -nums[index]
     return duplicates
```

## Testing

To test the solution, you can use the following test cases:

```python
assert find_duplicates([4, 3, 2, 7, 8, 2, 3, 1]) == [2, 3]
assert find_duplicates([1, 1, 2]) == [1]
assert find_duplicates([1]) == []
```

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.