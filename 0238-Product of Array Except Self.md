难度：Medium  
思路：用总乘积除以当前项即可，注意有0的情况，0为1个和多个情况不同。
```cpp
class Solution {
public:
    vector<int> productExceptSelf(vector<int>& nums) {
        int len = nums.size();
        int pro = 1;
        int zcnt = 0;
        int zpro = 1;
        for(int i = 0; i < len; ++i)
        {
            if(nums[i] == 0)
            {
                zcnt++;
                zpro = pro;
            }
            else
            {
                if(zcnt < 2)
                {
                    zpro *= nums[i];
                }
                else
                {
                    zpro = pro;
                }
            }
            pro *= nums[i];
            
        }
        vector<int> res;
        for(int j = 0; j < len; ++j)
        {
            int tmp = pro;
            if(nums[j] != 0)
            {
                tmp = pro / nums[j];
            }
            else
            {
                tmp = zpro;
            }
            res.push_back(tmp);
        }
        return res;
    }
};
```
```
执行用时：24 ms, 在所有 C++ 提交中击败了87.06%的用户
内存消耗：24.3 MB, 在所有 C++ 提交中击败了32.09%的用户
```
