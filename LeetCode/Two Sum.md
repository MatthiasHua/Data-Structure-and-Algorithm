# 1. Two Sum

---

Given an array of integers, return **indices** of the two numbers such that they add up to a specific target.

You may assume that each input would have **exactly** one solution, and you may not use the same element twice.

**Example:**
```
Given nums = [2, 7, 11, 15], target = 9,

Because nums[0] + nums[1] = 2 + 7 = 9,
return [0, 1].

```

**Solution(cpp):**
```cpp
class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        vector<int> rv;
        int min = 0;
        for (int i = 0; i < nums.size(); i++)
            if (nums[i] < min)
                min = nums[i];
        vector<int> record(target - 2 * min + 1, -1);
        for (int i = 0; i < nums.size(); i++)
            if (nums[i] <= target - min) {
                if (record[target-nums[i]-min] != -1){
                    rv.push_back(record[target-nums[i]-min]);
                    rv.push_back(i);
                    return rv;
                }
                else
                    record[nums[i]-min] = i;
            }
        
    }
};
```
