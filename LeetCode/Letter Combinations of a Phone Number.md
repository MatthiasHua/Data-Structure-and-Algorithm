# 17. Letter Combinations of a Phone Number

---

Given a digit string, return all possible letter combinations that the number could represent.

A mapping of digit to letters (just like on the telephone buttons) is given below.

![p](http://upload.wikimedia.org/wikipedia/commons/thumb/7/73/Telephone-keypad2.svg/200px-Telephone-keypad2.svg.png)

```
Input:Digit string "23"
Output: ["ad", "ae", "af", "bd", "be", "bf", "cd", "ce", "cf"].
```

**Note**:
Although the above answer is in lexicographical order, your answer could be in any order you want.

**Solution(cpp):**
```cpp
class Solution {
public:
    vector<string> letterCombinations(string digits) {
        vector<string> v;
        if (digits == "")
            return v;
        string s[10] = {"", "", "abc", "def" , "ghi", "jkl", "mno", "pqrs", "tuv", "wxyz"};
        vector<string> tmp;
        v.push_back("");
        for (int i = 0; i < digits.length(); i++) {
            vector<string> tmp;
            for (int j = 0; j < v.size(); j++) 
                for (int k = 0; k < s[digits[i] - '0'].length(); k++)
                    tmp.push_back(v[j] + s[digits[i] - '0'][k]);
            v = tmp;
        }
        return v;
    }
};
```