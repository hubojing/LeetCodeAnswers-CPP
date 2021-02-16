难度：Medium  
思路：常规链表操作，注意删除最后一个节点和第一个节点的特殊情况即可。  
更好的解法是快慢指针，可在一趟遍历中完成。  
```cpp
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode() : val(0), next(nullptr) {}
 *     ListNode(int x) : val(x), next(nullptr) {}
 *     ListNode(int x, ListNode *next) : val(x), next(next) {}
 * };
 */
class Solution
{
public:
    ListNode *removeNthFromEnd(ListNode *head, int n)
    {
        int len = 1;
        ListNode *p = head;
        while (p->next != nullptr)
        {
            len++;
            p = p->next;
        }
        if (len == 1)
        {
            head = head->next;
            return head;
        }
        if (n == len)
        {
            head = head->next;
            return head;
        }
        ListNode *q = head;
        for (int i = 0; i < len; ++i)
        {

            if (i == len - n - 1)
            {
                q->next = q->next->next;
                break;
            }
            q = q->next;
        }
        return head;
    }
};
```
```
执行用时：4 ms, 在所有 C++ 提交中击败了88.90%的用户
内存消耗：10.4 MB, 在所有 C++ 提交中击败了80.81%的用户
```
