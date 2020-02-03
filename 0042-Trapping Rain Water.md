# 官方题解  
## 法一：Brute force暴力解法
思路：对于数组中的每个元素，找出下雨后水能达到的最高位置，等于两边最大高度的较小值减去当前高度的值。
```cpp
class Solution
{
public:
    int trap(vector<int> &height)
    {
        int ans = 0;
        int size = height.size();
        for (int i = 1; i < size - 1; i++)
        {
            int max_left = 0, max_right = 0;
            for (int j = i; j >= 0; j--)
            { //Search the left part for max bar size
                max_left = max(max_left, height[j]);
            }
            for (int j = i; j < size; j++)
            { //Search the right part for max bar size
                max_right = max(max_right, height[j]);
            }
            ans += min(max_left, max_right) - height[i];
        }
        return ans;
    }
};
```
```
Runtime: 344 ms, faster than 5.17% of C++ online submissions for Trapping Rain Water.
Memory Usage: 9.1 MB, less than 78.48% of C++ online submissions for Trapping Rain Water.
```
时间复杂度：O(n^2)  
空间复杂度：O(1)
## 法二：动态编程
在暴力方法中，仅仅为了找到最大值每次都要向左和向右扫描一次。但是可以提前存储这个值。因此可以通过动态编程解决。
```cpp
class Solution
{
public:
    int trap(vector<int> &height)
    {
        if (height.empty())
            return 0;
        int ans = 0;
        int size = height.size();
        vector<int> left_max(size), right_max(size);
        left_max[0] = height[0];
        for (int i = 1; i < size; i++)
        {
            left_max[i] = max(height[i], left_max[i - 1]);
        }
        right_max[size - 1] = height[size - 1];
        for (int i = size - 2; i >= 0; i--)
        {
            right_max[i] = max(height[i], right_max[i + 1]);
        }
        for (int i = 1; i < size - 1; i++)
        {
            ans += min(left_max[i], right_max[i]) - height[i];
        }
        return ans;
    }
};
```
```
Runtime: 8 ms, faster than 61.89% of C++ online submissions for Trapping Rain Water.
Memory Usage: 9.3 MB, less than 39.24% of C++ online submissions for Trapping Rain Water.
```
时间复杂度：O(n)  
空间复杂度：O(n)
