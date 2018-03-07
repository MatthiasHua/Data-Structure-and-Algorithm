# 12. Integer to Roman

---

Given an integer, convert it to a roman numeral.

Input is guaranteed to be within the range from 1 to 3999.

**Solution(cpp):**
```
class Solution {
public:
    string intToRoman(int num) {
        string c[4][10] = {
            {"", "I", "II", "III", "IV", "V", "VI", "VII", "VIII", "IX"},
            {"", "X", "XX", "XXX", "XL", "L", "LX", "LXX", "LXXX", "XC"},
            {"", "C", "CC", "CCC", "CD", "D", "DC", "DCC", "DCCC", "CM"},
            {"", "M", "MM","MMM"}};
        return c[3][num / 1000] + c[2][num / 100 % 10] + c[1][num / 10 % 10] + c[0][num % 10];
    }
};
```