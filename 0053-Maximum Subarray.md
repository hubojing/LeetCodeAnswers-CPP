此题是最大子列和问题。
最简单的想法就是双重for循环遍历每个子列，记录其最大值。但此法时间复杂度高，应有更好的方法。
```cpp
class Solution
{
public:
    int maxSubArray(vector<int> &nums)
    {
        int maxSum = nums[0];
        for (int i = 0; i < nums.size(); ++i)
        {
            int sum = nums[i];
            for (int j = i; j < nums.size(); ++j)
            {
                if (j != i)
                {
                    sum += nums[j];
                }
                if (sum > maxSum)
                {
                    maxSum = sum;
                }
            }
        }
        return maxSum;
    }
};
```
```
Runtime: 816 ms, faster than 5.00% of C++ online submissions for Maximum Subarray.
Memory Usage: 7 MB, less than 100.00% of C++ online submissions for Maximum Subarray.
```
