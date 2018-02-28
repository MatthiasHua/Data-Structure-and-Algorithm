# 5. Longest Palindromic Substring

---

Given a string s, find the longest palindromic substring in **s**. You may assume that the maximum length of **s** is 1000.

**Example:**
```
Input: "babad"

Output: "bab"

Note: "aba" is also a valid answer.
```

**Example:**
```
Input: "cbbd"

Output: "bb"
```

最容易想到的就是枚举中心点然后向两边找最大回文串，要注意分为奇数长度和偶数长度。
**Solution(cpp):**
```
class Solution {
public:
    string longestPalindrome(string s) {
        int i, j, maxLen = 0, maxIndex;
        string rs = "";
        for (i = 0; i < s.length(); i++) {
            int j = 0;
            while ( i > j && i + j + 1 < s.length() && s[i - j - 1] == s[i + j + 1]) {
                j ++;
            }
            if (2 * j + 1 > maxLen) {
                maxLen = 2 * j + 1;
                maxIndex = i - j;
            }
            
            if (i < s.length() - 1 && s[i] == s[i + 1]) {
                int j = 0;             
                while ( i > j && i + j + 2 < s.length() && s[i - j - 1] == s[i + j + 2]) {
                    j ++;
                }
                if (2 * j + 2 > maxLen) {
                    maxLen = 2 * j + 2;
                    maxIndex = i - j;
                }               
            }
        }
        for (i = maxIndex; i < maxIndex + maxLen; i++)
            rs += s[i];
        return rs;
    }
};
```

专门有一个Manacher算法来计算最长回文子串，大概看了一下，还没实现，先贴一段java的范例。
ps:貌似没快多少，这个java版的比c++暴力解法还慢，有空写成c++再试吧。
**Solution(java):**
```java
public class Solution {
    public String longestPalindrome(String s) {
        if(s.length()<=1){
            return s;
        }
        // 预处理字符串，避免奇偶问题
        String str = preProcess(s);
        // idx是当前能够向右延伸的最远的回文串中心点，随着迭代而更新
        // max是当前最长回文串在总字符串中所能延伸到的最右端的位置
        // maxIdx是当前已知的最长回文串中心点
        // maxSpan是当前已知的最长回文串向左或向右能延伸的长度
        int idx = 0, max = 0;
        int maxIdx = 0;
        int maxSpan = 0;
        int[] p = new int[str.length()];
        for(int curr = 1; curr < str.length(); curr++){
            // 找出当前下标相对于idx的对称点
            int symmetryOfCurr = 2 * idx - curr;
            // 如果当前已知延伸的最右端大于当前下标，我们可以用对称点的P值，否则记为1等待检查
            p[curr] = max > curr? Math.min(p[symmetryOfCurr], max - curr):1;
            // 检查并更新当前下标为中心的回文串最远延伸的长度
            while((curr+p[curr])<str.length() && str.charAt(curr+p[curr])==str.charAt(curr-p[curr])){
                p[curr]++;
            }
            // 检查并更新当前已知能够延伸最远的回文串信息
            if(curr+p[curr]>max){
                max = p[curr] + curr;
                idx = curr;
            }
            // 检查并更新当前已知的最长回文串信息
            if(p[curr]>maxSpan){
                maxSpan = p[curr];
                maxIdx = curr;
            }
        }
        //去除占位符
        return s.substring((maxIdx-maxSpan)/2,(maxSpan+maxIdx)/2-1);
    }
    
    private String preProcess(String s){
        // 如ABC,变为$#A#B#C#
        StringBuilder sb = new StringBuilder();
        sb.append("$");
        for(int i = 0; i < s.length(); i++){
            sb.append("#");
            sb.append(s.charAt(i));
        }
        sb.append("#");
        return sb.toString();
    }
}
```