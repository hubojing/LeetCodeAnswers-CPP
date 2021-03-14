难度：Medium  
思路：找到第一个后者大于前者的数即可。
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
执行用时：0 ms, 在所有 C++ 提交中击败了100.00%的用户
内存消耗：9.9 MB, 在所有 C++ 提交中击败了69.67%的用户
```
