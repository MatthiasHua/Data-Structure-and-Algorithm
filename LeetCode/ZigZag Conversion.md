# 6. ZigZag Conversion

---

The string `"PAYPALISHIRING"` is written in a zigzag pattern on a given number of rows like this: (you may want to display this pattern in a fixed font for better legibility)

```
P   A   H   N
A P L S I I G
Y   I   R
```

And then read line by line: `"PAHNAPLSIIGYIR"`
Write the code that will take a string and make this conversion given a number of rows:

```
string convert(string text, int nRows);
```

`convert("PAYPALISHIRING", 3)` should return `"PAHNAPLSIIGYIR"`.

**Solution(cpp):**
```cpp
class Solution {
public:
    string convert(string s, int numRows) {
        if (numRows == 1)
            return s;
        string rs = "";
        for (int i = 0; i < numRows; i++)
            for ( int j = i; j < s.length(); j += numRows * 2 - 2) {
                rs += s[j];
                if ( i != 0 && i != numRows - 1 && j + 2 * (numRows - i - 1) < s.length())
                     rs += s[j + 2 * (numRows - i - 1)];
            }
        return rs;
    }
};
```