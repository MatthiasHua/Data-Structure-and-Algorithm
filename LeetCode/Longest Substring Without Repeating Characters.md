# 3. Longest Substring Without Repeating Characters

---

Given a string, find the length of the **longest substring** without repeating characters.

**Examples:**

Given `"abcabcbb"`, the answer is `"abc"`, which the length is 3.

Given `"bbbbb"`, the answer is `"b"`, with the length of 1.

Given `"pwwkew"`, the answer is `"wke"`, with the length of 3. Note that the answer must be a **substring**, `"pwke"` is a subsequence and not a substring.

**Solution(cpp):**
```
class Solution {
public:
    int lengthOfLongestSubstring(string s) {
        int maxLen = 0, i = 0, j = 0;
        int contained[256] = {0};
            for (j = 0; j < s.length(); j++) {
                while (contained[s[j]]) {
                    contained[s[i]] = 0;
                    i++;
                }
                if (j - i + 1 > maxLen)
                    maxLen = j - i + 1;
                contained[s[j]] = 1;
            }
        return maxLen;
    }
};
```