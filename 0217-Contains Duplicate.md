难度：Easy  
思路：存入哈希表并计数，若哈希表中计数大于1，则有重复值。
```cpp
class Solution {
public:
    bool containsDuplicate(vector<int>& nums) {
        int len = nums.size();
        map<int, int> hashmap;
        for(int i = 0; i < len; ++i)
        {
            hashmap[nums[i]] += 1;
            if(hashmap[nums[i]] > 1)
            {
                return true;
            }
        }
        return false;
    }
};
```
```
执行用时：60 ms, 在所有 C++ 提交中击败了67.48%的用户
内存消耗：20.4 MB, 在所有 C++ 提交中击败了11.28%的用户
```
