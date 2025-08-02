### 3. Longest Substring Without Repeating Characters
Given a string s, find the length of the longest substring without duplicate characters.

```js
Example 1:

Input: s = "abcabcbb"
Output: 3
Explanation: The answer is "abc", with the length of 3.
Example 2:

Input: s = "bbbbb"
Output: 1
Explanation: The answer is "b", with the length of 1.
Example 3:

Input: s = "pwwkew"
Output: 3
Explanation: The answer is "wke", with the length of 3.
Notice that the answer must be a substring, "pwke" is a subsequence and not a substring.
```
```js
function lengthOfLongestSubstring(s: string): number {
    /**
     * @charIndex : 儲存已遍歷過且最新的不重複字元Index
     * @maxlength : 找出最左及最右的string index做相減算出長度
     * @left ：不重複字串中最左邊字元的index
     * @right ：不重複字串中最右邊字元的index
     */
    const charIndex = new Map();
    let maxLength = 0;
    let left = 0;

    // 遍歷傳入的字串, 時間複雜度：O(n)
    for (let right = 0;right < s.length; right++){
        // 目前遍歷的字元
        let char = s[right];

        // 檢查是否為出現過的字元並更新left值
        if (charIndex.has(char) && charIndex.get(char) >= left){
            // 發現重複字元代表連續長度被中斷，將left位置更新到最新字元的位置重新計算最大連續長度
            left = charIndex.get(char) + 1
        }

        // 更新Index紀錄, Map.set(key, value)
        charIndex.set(char, right)

        // 長度 = 頭 - 尾 + 1
        maxLength = Math.max(maxLength, right - left + 1);
    }

    return maxLength;
};
```
