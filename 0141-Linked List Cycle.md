# 官方题解
## 法一：哈希表
思路：遍历所有节点，每次判断该节点是否被访问过。
```cpp
class Solution {
public:
    bool hasCycle(ListNode *head) {
        unordered_set<ListNode*> seen;
        while (head != nullptr) {
            if (seen.count(head)) {
                return true;
            }
            seen.insert(head);
            head = head->next;
        }
        return false;
    }
};
```
```
执行用时：24 ms, 在所有 C++ 提交中击败了13.72%的用户
内存消耗：9.6 MB, 在所有 C++ 提交中击败了14.17%的用户
```
时间复杂度：O(N)
空间复杂度：O(N)

## 法二：快慢指针
思路：Floyd判圈算法，又称龟兔赛跑算法。  
假想「乌龟」和「兔子」在链表上移动，「兔子」跑得快，「乌龟」跑得慢。当「乌龟」和「兔子」从链表上的同一个节点开始移动时，如果该链表中没有环，那么「兔子」将一直处于「乌龟」的前方；如果该链表中有环，那么「兔子」会先于「乌龟」进入环，并且一直在环内移动。等到「乌龟」进入环时，由于「兔子」的速度快，它一定会在某个时刻与乌龟相遇，即套了「乌龟」若干圈。  
具体地，定义两个指针，一快一满。慢指针每次只移动一步，而快指针每次移动两步。初始时，慢指针在位置 head，而快指针在位置 head.next。这样一来，如果在移动的过程中，快指针反过来追上慢指针，就说明该链表为环形链表。否则快指针将到达链表尾部，该链表不为环形链表。
```cpp
class Solution {
public:
    bool hasCycle(ListNode* head) {
        if (head == nullptr || head->next == nullptr) {
            return false;
        }
        ListNode* slow = head;
        ListNode* fast = head->next;
        while (slow != fast) {
            if (fast == nullptr || fast->next == nullptr) {
                return false;
            }
            slow = slow->next;
            fast = fast->next->next;
        }
        return true;
    }
};
```
```
执行用时：8 ms, 在所有 C++ 提交中击败了94.45%的用户
内存消耗：7.9 MB, 在所有 C++ 提交中击败了26.25%的用户
```
时间复杂度：O(N)  
空间复杂度：O(1)
