难度：Medium  
思路：逆序排序后找到第K个值即可。
```
class Solution {
public:
    int findKthLargest(vector<int>& nums, int k) {
        int len = nums.size();
        int res = nums[0];
        sort(nums.rbegin(), nums.rend());
        for(int i = 0; i < len; ++i)
        {
            if(i == k - 1)
            {
                res = nums[i];
            }
        }
        return res;
    }
};
```
```
执行用时：16 ms, 在所有 C++ 提交中击败了51.60%的用户
内存消耗：9.8 MB, 在所有 C++ 提交中击败了53.88%的用户
```
不过本题考查的重点应该是如何写排序代码。
