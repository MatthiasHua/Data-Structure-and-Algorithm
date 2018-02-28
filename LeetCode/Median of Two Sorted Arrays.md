# 4. Median of Two Sorted Arrays

---

There are two sorted arrays **nums1** and **nums2** of size m and n respectively.

Find the median of the two sorted arrays. The overall run time complexity should be O(log (m+n)).

**Example 1:**
```
nums1 = [1, 3]
nums2 = [2]

The median is 2.0
```
**Example 2:**
```
nums1 = [1, 2]
nums2 = [3, 4]

The median is (2 + 3)/2 = 2.5
```

**Solution(cpp):**
```cpp
class Solution {
public:
    double findMedianSortedArrays(vector<int>& nums1, vector<int>& nums2) {
        int i = nums1.size() + nums2.size(), j = 0, tmp, x = 0, y = 0;
        double k = 0;
        for (j = 0; j < i / 2 + 1; j++) {
            if (x == nums1.size() || (y != nums2.size() && nums1[x] > nums2[y])) {
                tmp = nums2[y];
                y++;
            } else {
                tmp = nums1[x];
                x++;
            }
            if (!(i % 2) && j == i / 2 - 1)
                k += tmp;
            if (j == i / 2)
                k += tmp;
        }
        if (!(i % 2))
            k = k / 2;
        return k;
    }
};
```