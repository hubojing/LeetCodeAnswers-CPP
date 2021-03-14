难度：Hard  
思路：和153题代码一样。
```cpp
class Solution {
public:
    int findMin(vector<int>& nums) {
        int res = nums[0];
        int len = nums.size();
        for(int i = 0; i < len - 1; ++i)
        {
            if(nums[i] > nums[i + 1])
            {
                res = nums[i + 1];
                break;
            }
        }
        return res;
    }
};
```
```
执行用时：4 ms, 在所有 C++ 提交中击败了94.85%的用户
内存消耗：12 MB, 在所有 C++ 提交中击败了38.29%的用户
```
