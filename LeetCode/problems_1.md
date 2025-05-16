# Link

https://leetcode.com/problems/two-sum/

# Problem 1: Two Sum

Given an array of integers `nums` and an integer `target`, return indices of the two numbers such that they add up to `target`.

You may assume that each input would have exactly one solution, and you may not use the same element twice.

You can return the answer in any order.

# Example

Example 1:

> Input: nums = [2,7,11,15], target = 9
> Output: [0,1]
> Explanation: Because nums[0] + nums[1] == 9, we return [0, 1].

Example 2:

> Input: nums = [3,2,4], target = 6
> Output: [1,2]

Example 3:

> Input: nums = [3,3], target = 6
> Output: [0,1]

# Constraints:

- 2 <= nums.length <= 104
- -$10^9$ <= nums[i] <= $10^9$
- $10^9$ <= target <= $10^9$
- Only one valid answer exists.

**Follow-up** : Can you come up with an algorithm that is less than O(n2) time complexity?

# Answer

## 方法一 : 暴力解 (複雜度 $n^2$)

```ts
function twoSum(nums: number[], target: number): number[] {
  for (let i = 0; i < nums.length; i++) {
    for (let j = i + 1; j < nums.length; j++) {
      if (nums[i] + nums[j] === target) {
        return [i, j];
      }
    }
  }
  return [];
}
```

## 方法二 : HashMap (複雜度 $n$)

將遍歷過的資料保存到 Map，並在 Map 中檢查是否有符合條件的資料。
就像是翻通訊錄找朋友的號碼一樣，會比暴力解快很多。

```ts
function twoSum(nums: number[], target: number): number[] {
  const map = new Map<number, number>(); // value -> index

  for (let i = 0; i < nums.length; i++) {
    const complement = target - nums[i];
    if (map.has(complement)) {
      return [map.get(complement)!, i];
    }
    map.set(nums[i], i);
  }

  return [];
}
```
