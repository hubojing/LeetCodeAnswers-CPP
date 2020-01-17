我的思路：受之前刷题的影响，看到array就想用双指针法。  
仔细观察序列可发现，无非就几种情况：target比最左边数小，target比最左边数大，相等则直接输出。由于原序列最初是升序，target比最左边数小的话，就判断和最右边数的关系。如果小于最右边数，就从最右边开始遍历。如果大于最右边数，则无解。target比最左边数大，则从左边开始遍历。（这里我认为可改进，若加上考虑和最右边数的比较，比如所求数离右边更近，可能更好。）  
但是我的解法有个问题：时间复杂度O(n)并没有达标O(logn)......  
看了官方解法，以后注意：看到时间复杂度要求O(logn)，首先就应该想到二分查找法。  
以下是我的解法：
```cpp
class Solution
{
public:
    int search(vector<int> &nums, int target)
    {
        int i = 0;
        int j = nums.size() - 1;
        if (nums.size() == 0)
        {
            return -1;
        }
        if (nums.size() == 1)
        {
            if (nums[0] == target)
            {
                return 0;
            }
            else
            {
                return -1;
            }
        }
        while (i != j)
        {
            if (target == nums[i])
            {
                return i;
            }
            if (target == nums[j])
            {
                return j;
            }
            if (target < nums[i] && target > nums[j])
            {
                return -1;
            }
            else if (target < nums[i] && target < nums[j])
            {
                --j;
            }
            else
            {
                i++;
            }
        }
        return -1;
    }
};
```
```
Runtime: 4 ms, faster than 81.22% of C++ online submissions for Search in Rotated Sorted Array.
Memory Usage: 8.8 MB, less than 66.27% of C++ online submissions for Search in Rotated Sorted Array.
```
