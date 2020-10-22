# 官方题解
## 法一：迭代法
当 l1 和 l2 都不是空链表时，判断 l1 和 l2 哪一个链表的头节点的值更小，将较小值的节点添加到结果里，当一个节点被添加到结果里之后，将对应链表中的节点向后移一位。  
首先设定一个哨兵节点prehead，使得最后容易返回合并后的链表。维护一个prev指针，需要做的是调整它的next指针。然后重复以下过程，直到l1或者l2指向了null：如果l1当前节点的值小于等于l2，我们就把 l1当前的节点接在prev节点的后面，同时将l1指针往后移一位。否则，对l2做同样的操作。不管将哪一个元素接在了后面，都需要把prev向后移一位。  
在循环终止的时候，l1和l2至多有一个是非空的。由于输入的两个链表都是有序的，所以不管哪个链表是非空的，它包含的所有元素都比前面已经合并链表中的所有元素都要大。所以只需要简单地将非空链表接在合并链表的后面，并返回合并链表即可。  
```cpp
class Solution {
public:
    ListNode* mergeTwoLists(ListNode* l1, ListNode* l2) {
        ListNode* preHead = new ListNode(-1);

        ListNode* prev = preHead;
        while (l1 != nullptr && l2 != nullptr) {
            if (l1->val < l2->val) {
                prev->next = l1;
                l1 = l1->next;
            } else {
                prev->next = l2;
                l2 = l2->next;
            }
            prev = prev->next;
        }

        // 合并后 l1 和 l2 最多只有一个还未被合并完，我们直接将链表末尾指向未合并完的链表即可
        prev->next = l1 == nullptr ? l2 : l1;

        return preHead->next;
    }
};
```
```
执行用时：
20 ms, 在所有 C++ 提交中击败了 5.91% 的用户
内存消耗：14.7 MB, 在所有 C++ 提交中击败了 8.76% 的用户
```
时间复杂度：O(n+m) ，其中n和m分别为两个链表的长度。因为每次循环迭代中，l1和l2只有一个元素会被放进合并链表中， 因此while循环的次数不会超过两个链表的长度之和。所有其他操作的时间复杂度都是常数级别的，因此总的时间复杂度为O(n+m)。  
空间复杂度：O(1)。只需要常数的空间存放若干变量。


## 法二：递归法
如果l1或者l2是空链表 ，无需合并，只需返回非空链表。否则，要判断l1和l2哪一个链表的头节点的值更小，然后递归地决定下一个添加到结果里的节点。如果两个链表有一个为空，递归结束。
```cpp
class Solution {
public:
    ListNode* mergeTwoLists(ListNode* l1, ListNode* l2) {
        if (l1 == nullptr) {
            return l2;
        } else if (l2 == nullptr) {
            return l1;
        } else if (l1->val < l2->val) {
            l1->next = mergeTwoLists(l1->next, l2);
            return l1;
        } else {
            l2->next = mergeTwoLists(l1, l2->next);
            return l2;
        }
    }
};
```
```
执行用时：
12 ms, 在所有 C++ 提交中击败了 57.05% 的用户
内存消耗：14.7 MB, 在所有 C++ 提交中击败了 6.79% 的用户
```
时间复杂度：O(n+m)，其中n和m分别为两个链表的长度。因为每次调用递归都会去掉l1或者l2的头节点（直到至少有一个链表为空），函数mergeTwoList至多只会递归调用每个节点一次。因此，时间复杂度取决于合并后的链表长度，即O(n+m)。  
空间复杂度：O(n+m)，其中n和m分别为两个链表的长度。递归调用mergeTwoLists函数时需要消耗栈空间，栈空间的大小取决于递归调用的深度。结束递归调用时mergeTwoLists函数最多调用n+m次，因此空间复杂度为 O(n+m)。
