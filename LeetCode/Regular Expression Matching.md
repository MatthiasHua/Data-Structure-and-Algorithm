# 10. Regular Expression Matching

---

Implement regular expression matching with support for `'.'` and `'*'`.

'.' Matches any single character.
'*' Matches zero or more of the preceding element.

The matching should cover the entire input string (not partial).

The function prototype should be:
bool isMatch(const char *s, const char *p)

Some examples:
isMatch("aa","a") → false
isMatch("aa","aa") → true
isMatch("aaa","aa") → false
isMatch("aa", "a*") → true
isMatch("aa", ".*") → true
isMatch("ab", ".*") → true
isMatch("aab", "c*a*b") → true


**Solution(cpp):**
```cpp
class Solution {
public:
    bool isMatch(string s, string p) {
        int i = 0;
        if (!p.length())
            return (!s.length());
        if (p.length() == 1 || p[1]  != '*')
            return s.length() && (p[0] == '.' || s[0] == p[0]) && isMatch(s.substr(1), p.substr(1));
        else while (s.length() > i && (p[0] == '.' || s[i] == p[0])) {
            if (isMatch(s.substr(i+1), p.substr(2)))
                return true;
            i++;
        }
        return isMatch(s, p.substr(2));
    }
};
```