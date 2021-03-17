难度：Medium  
思路：三重循环暴力解。
```cpp
class Solution {
public:
    bool increasingTriplet(vector<int>& nums) {
        int len = nums.size();
        for(int i = 0; i < len; ++i)
        {
            for(int j = i + 1; j < len; ++j)
            {
                if(nums[i] < nums[j])
                {
                    for(int k = j + 1; k < len; ++k)
                    {
                        if(nums[j] < nums[k])
                        {
                            return true;
                        }
                    }
                }
            }
        }
        return false;
    }
};
```
```
执行用时：524 ms, 在所有 C++ 提交中击败了5.15%的用户
内存消耗：10 MB, 在所有 C++ 提交中击败了56.32%的用户
```
