# 9. Palindrome Number

---

Determine whether an integer is a palindrome. Do this without extra space.

**Some hints:**
Could negative integers be palindromes? (ie, -1)

If you are thinking of converting the integer to string, note the restriction of using extra space.

You could also try reversing an integer. However, if you have solved the problem "Reverse Integer", you know that the reversed integer might overflow. How would you handle such case?

There is a more generic way of solving this problem.

转换成数组/字符串处理:
**Solution(cpp):**
```
class Solution {
public:
    bool isPalindrome(int x) {
        vector<int> s;
        if (x < 0)
            return false;
        while (x) {
            s.push_back(x % 10);
            x = x / 10;
        }
        for (int i = 0; i < s.size() / 2; i ++) 
            if (s[i] != s[s.size() - i - 1])
                return false;
        return true;
    }
};
```

反转数字后判断是否相等，要注意负数:
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
    bool isPalindrome(int x) {
        int y = reverse(x);
        if (x == y && x >= 0)
            return true;
        return false;
    }
};
```