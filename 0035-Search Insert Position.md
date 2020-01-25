```cpp
class Solution
{
public:
    int searchInsert(vector<int> &nums, int target)
    {
        for (int i = 0; i < nums.size(); ++i)
        {
            if (nums[i] == target || nums[i] > target)
            {
                return i;
            }
        }
        return nums.size();
    }
};
```
```
Runtime: 8 ms, faster than 59.70% of C++ online submissions for Search Insert Position.
Memory Usage: 8.8 MB, less than 93.75% of C++ online submissions for Search Insert Position.
```
