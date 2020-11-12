# 官方题解
## 动态规划
f(x) = f(x-1) + f(x-2)  
滚动数组思想使空间复杂度化为O(1)。
```cpp
class Solution {
public:
    int climbStairs(int n) {
        int p = 0, q = 0, r = 1;
        for (int i = 1; i <= n; ++i) {
            p = q; 
            q = r; 
            r = p + q;
        }
        return r;
    }
};
```
```
执行用时：
4 ms, 在所有 C++ 提交中击败了15.36% 的用户
内存消耗：
6.1 MB, 在所有 C++ 提交中击败了34.58% 的用户
```
时间复杂度：O(n)
空间复杂度：O(1)
