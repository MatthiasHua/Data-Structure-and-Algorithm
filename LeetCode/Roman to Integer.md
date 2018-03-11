# 13. Roman to Integer

---


Given a roman numeral, convert it to an integer.

Input is guaranteed to be within the range from 1 to 3999.

**Solution(cpp):**
```cpp
class Solution {
public:
    int romanToInt(string s) {
        char c[7] = {'I', 'V', 'X', 'L', 'C', 'D', 'M'};
        int v[7] = {1, 5, 10, 50, 100, 500, 1000}; 
        int i = 6, ps = 0, sum = 0;
        while (i >= 0 && ps < s.length()) {
            while (s[ps] == c[i]) {
                ps++;
                sum += v[i];
            }
            if (s[ps] != c[i] && ps < s.length() - 1 && s[ps + 1] == c[i]) {
                if (s[ps] == c[i-1])
                    sum += v[i]  - v[i-1];
                else
                    sum += v[i]  - v[i-2];
                ps += 2;
            }
            i--;
        }
        return sum;
    }
};
```