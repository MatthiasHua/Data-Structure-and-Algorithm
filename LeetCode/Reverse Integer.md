# 7. Reverse Integer

---

Given a 32-bit signed integer, reverse digits of an integer.

**Example 1:**
```
Input: 123
Output:  321
```

**Example 2:**
```
Input: -123
Output: -321
```

**Example 3:**
```
Input: 120
Output: 21
```

**Note:**
Assume we are dealing with an environment which could only hold integers within the 32-bit signed integer range. For the purpose of this problem, assume that your function returns 0 when the reversed integer overflows.

**Solution(cpp):**
```
class Solution {
public:
    int reverse(int x) {
        int y = 0;
        while (x) {
            y = y * 10 + x % 10;
            if (y % 10 == x % 10)
                x = x / 10;
            else
                return 0;
        }
        return y;
    }
};
```