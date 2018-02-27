# 2. Add Two Numbers

---

You are given two `non-empty` linked lists representing two non-negative integers. The digits are stored in `reverse order` and each of their nodes contain a single digit. Add the two numbers and return it as a linked list.

You may assume the two numbers do not contain any leading zero, except the number 0 itself.

Example
```
Input: (2 -> 4 -> 3) + (5 -> 6 -> 4)
Output: 7 -> 0 -> 8
Explanation: 342 + 465 = 807.
```

数据结构已经定义好了，链表第一项不为空会导致第一项和之后的项的建立方式有所区别，平时习惯用第一项为空的来写，比较方便，浪费的一项的空间通常也可以接受。所以先定义了一个空项，返回的时候从第二项开始返回。

Solution(cpp):
```cpp
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode(int x) : val(x), next(NULL) {}
 * };
 */
class Solution {
public:
    ListNode* addTwoNumbers(ListNode* l1, ListNode* l2) {
        ListNode *l = new ListNode(0), *tmp = l;
        int of = 0;
        while (l1 != NULL || l2 != NULL) {
            ListNode* newNode = new ListNode((l1 ? l1 -> val : 0) + (l2 ? l2 -> val : 0) + of);
            of = newNode -> val / 10;
            newNode -> val = newNode -> val %10;
            tmp -> next = newNode; 
            tmp = tmp -> next;
            l1 = l1 ? l1 -> next : NULL;
            l2 = l2 ? l2 -> next : NULL;
        }
        if (of)
            tmp -> next = new ListNode(of);
        return l -> next;
    }
};
```