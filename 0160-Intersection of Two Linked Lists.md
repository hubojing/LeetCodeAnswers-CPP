难度：Easy
思路：哈希表保存链表A的节点，再遍历链表B，一旦B中有节点在哈希表中，就是相交节点。  
注意：题意中相交是指节点本身相同，而非值相同。
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
    ListNode *getIntersectionNode(ListNode *headA, ListNode *headB) {
        ListNode* res = nullptr;
        map<ListNode*, int> hashmap;
        while(headA != nullptr)
        {
            hashmap[headA] = headA->val;
            headA = headA->next;
        }
        while(headB != nullptr)
        {
            if(hashmap[headB])
            {
                res = headB;
                break;
            }
            headB = headB->next;
        }
        return res;
    }
};
```
```
执行用时：80 ms, 在所有 C++ 提交中击败了11.71%的用户
内存消耗：20.8 MB, 在所有 C++ 提交中击败了5.04%的用户
```
