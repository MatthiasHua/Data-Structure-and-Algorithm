# 14. Longest Common Prefix

---

Write a function to find the longest common prefix string amongst an array of strings.

**Solution(cpp):**
```cpp
class Solution {
public:
    string longestCommonPrefix(vector<string>& strs) {
        if (!strs.size())
            return "";
        string s = "";
        int i = 0;
        sort(strs.begin(), strs.end());
        while(i < strs[0].size() && strs[0][i] == strs[strs.size() - 1][i]) {
            s += strs[0][i];
            i++;
        }
        return s;
    }
};
```