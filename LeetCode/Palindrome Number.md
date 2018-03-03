# 9. Palindrome Number

Determine whether an integer is a palindrome. Do this without extra space.

**Some hints:**
Could negative integers be palindromes? (ie, -1)

If you are thinking of converting the integer to string, note the restriction of using extra space.

You could also try reversing an integer. However, if you have solved the problem "Reverse Integer", you know that the reversed integer might overflow. How would you handle such case?

There is a more generic way of solving this problem.

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