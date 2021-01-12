难度：Easy

思路：难点是原地移动，满足空间复杂度O(1)。也不能排序，要满足时间复杂度O(n)。  
一开始我想复杂了，在草稿纸上想的是把值和对应的索引值交换，不断交换后索引和值不相等的即为所求。  
但题解思路更简单，代码也更好写。  
即：  
把对应的索引值nums[nums[i]-1]置为负数即可，表明这个索引的数存在。  
注意只用变为负数一次。  
```cpp
class Solution
{
public:
    vector<int> findDisappearedNumbers(vector<int> &nums)
    {
        int len = nums.size();
        for (int i = 0; i < len; ++i)
        {
            int index = abs(nums[i]);
            if (nums[index - 1] > 0)
            {
                nums[index - 1] = -nums[index - 1];
            }
        }

        vector<int> vecRes;
        for (int i = 0; i < len; ++i)
        {
            if (nums[i] > 0)
            {
                vecRes.push_back(i + 1);
            }
        }

        return vecRes;
    }
};
```
```
执行用时：100 ms, 在所有 C++ 提交中击败了90.50%的用户
内存消耗：31.7 MB, 在所有 C++ 提交中击败了47.11%的用户
```

顺手记一个别人题解的优秀思路：  
1. 将数组元素对应为索引的位置加n  
2. 遍历加n后的数组，若数组元素值小于等于n，则说明数组下标值不存在，即消失的数字  
