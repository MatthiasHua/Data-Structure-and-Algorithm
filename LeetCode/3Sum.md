# 15. 3Sum

---

Given an array S of n integers, are there elements a, b, c in S such that a + b + c = 0? Find all unique triplets in the array which gives the sum of zero.

**Note:** The solution set must not contain duplicate triplets.

```
For example, given array S = [-1, 0, 1, 2, -1, -4],

A solution set is:
[
  [-1, 0, 1],
  [-1, -1, 2]
]
```

**Solution(cpp):**
```cpp
class Solution {
public:
    vector<vector<int>> threeSum(vector<int>& nums) {
        vector<vector<int>> rv;
        vector<int> tmp(3);
        if (!nums.size())
            return rv;
        sort(nums.begin(), nums.end());
        int maxNum = nums[nums.size() - 1], minNum = nums[0];
        vector<int> recode(maxNum - minNum + 1, 0);
        for (int i = 0; i < nums.size(); i++)
            recode[nums[i] - minNum] = i;
        for (int i = 0; i < nums.size(); i++)
            if (i > 0 && nums[i] == nums[i-1])
                continue;
            else
              for (int j = i + 1; j < nums.size(); j++)
                  if (nums[i] + nums[j] + minNum <= 0 && nums[i] + nums[j] >= - maxNum && recode[- nums[i] - nums[j] - minNum] > j)
                      if (!rv.size() || !(rv[rv.size() - 1][2] == nums[recode[- nums[i] - nums[j] - minNum]] && (rv[rv.size() - 1][1]) == nums[j] && (rv[rv.size() - 1][0]) == nums[i])) {
                          tmp[0] = nums[i];
                          tmp[1] = nums[j];
                          tmp[2] = nums[recode[- nums[i] - nums[j] - minNum]];
                          rv.push_back(tmp); 
                      }
        return rv;
    }
};
```

想先做预处理再搜索的，但是写起来感觉不太好，判断重复值比较麻烦，而且容易漏解，适合像第一题一样找到一个解的问题。这里又想了一个从两侧逼近的方法，就不会漏解了。
```cpp
class Solution {
public:
    vector<vector<int>> threeSum(vector<int>& nums) {
        vector<vector<int>> rv;
        vector<int> tmp(3);
        sort(nums.begin(), nums.end());
        int j, k;
        for (int i = 0; i < nums.size(); i++) {
            if (i && nums[i] == nums[i-1])
                continue;
            j = i + 1;
            k = nums.size() - 1;
            while(j < k) {
                if (nums[i] + nums[j] + nums[k] == 0) {
                    tmp[0] = nums[i];
                    tmp[1] = nums[j];
                    tmp[2] = nums[k];
                    rv.push_back(tmp);
                    while(nums[j + 1] == nums[j]) 
                        j++;
                    while(nums[k - 1] == nums[k]) 
                        k--;
                    j++;
                    k--;
                } else if (nums[i] + nums[j] + nums[k] < 0)
                    j++;
                else
                    k--;
            }
        }
        return rv;
    }
};
```