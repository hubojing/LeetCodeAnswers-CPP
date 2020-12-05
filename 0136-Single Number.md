最直接的想法就是先排序，然后检测当前值是否和前后两个值相同。若当前值和前后两值都不同，那该值即为所求。要注意边界的判断条件略有不同。
```cpp
class Solution
{
public:
    int singleNumber(vector<int> &nums)
    {
        int len = nums.size();
        if (len == 1)
        {
            return nums[0];
        }
        sort(nums.begin(), nums.end());

        for (int i = 0; i < len; ++i)
        {
            if (i == 0)
            {
                if (nums[i] != nums[i + 1])
                {
                    return nums[i];
                }
            }
            else if (i == len - 1)
            {
                if (nums[i] != nums[i - 1])
                {
                    return nums[i];
                }
            }
            else
            {
                if (nums[i - 1] != nums[i] && nums[i + 1] != nums[i])
                {
                    return nums[i];
                }
            }
        }
        return 0;
    }
};
```
```
执行用时：76 ms, 在所有 C++ 提交中击败了13.82%的用户
内存消耗：16.8 MB, 在所有 C++ 提交中击败了46.32%的用户
```
但是题目要求线性时间复杂度，且不使用额外空间。  
但排序了就不是线性时间复杂度了...虽然能通过，但是没达到要求。  
官方题解使用异或位运算也是另辟蹊径了。  
