# 39. Combination Sum

---

Given a **set** of candidate numbers (**C**) (**without duplicates**) and a target number (T), find all unique combinations in C where the candidate numbers sums to T.

The **same** repeated number may be chosen from C unlimited number of times.

**Note:**
All numbers (including target) will be positive integers.
The solution set must not contain duplicate combinations.
For example, given candidate set [2, 3, 6, 7] and target 7, 
A solution set is: 
```
[
  [7],
  [2, 2, 3]
]
```

**Solution(cpp):**
```cpp
class Solution {
public:
    void find(vector<int> v, vector<int> &candidates, int i, int target, vector<vector<int>> &r) {
        if (!target) {
            r.push_back(v);
            return;
        }
        if (i >= candidates.size())
            return;
        find(v, candidates, i + 1, target, r);
        while(target >= candidates[i]) {
            target -= candidates[i];
            v.push_back(candidates[i]);
            find(v, candidates, i + 1, target, r);
        }
    }
    vector<vector<int>> combinationSum(vector<int> &candidates, int target) {
        vector<vector<int>> r;
        vector<int> v;
        find(v, candidates, 0, target, r);
        return r;
    }
};
```