此题是最大子列和问题。
最简单的想法就是双重for循环遍历每个子列，记录其最大值。但此法时间复杂度高。
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

# 官方题解
# 动态规划法
要求的连续子数组的最大和，其实就是
$$\sum_{0≤i≤n-1}{f(i)}$$
因此求出每个位置的f(i)，返回最大值即可。
动态规划转移方程：
$$f(i) = max{f(i-1}+a_i,a_i}$$

若前一个元素大于0，则将其加到当前元素上。
```cpp
class Solution {
public:
    int maxSubArray(vector<int>& nums) {
        int pre = 0, maxAns = nums[0];
        for (const auto &x: nums) {
            pre = max(pre + x, x);
            maxAns = max(maxAns, pre);
        }
        return maxAns;
    }
};
```
```
Runtime: 12 ms, faster than 17.10% of C++ online submissions for Maximum Subarray.
Memory Usage: 13.2 MB, less than 5.88% of C++ online submissions for Maximum Subarray.
```
时间复杂度：O(n)  
空间复杂度：O(1)

# 分治法
对于一个区间 [l, r][l,r]，维护四个量：  
lSum 表示 [l, r][l,r] 内以 ll 为左端点的最大子段和  
rSum 表示 [l, r][l,r] 内以 rr 为右端点的最大子段和  
mSum 表示 [l, r][l,r] 内的最大子段和  
iSum 表示 [l, r][l,r] 的区间和  
以下简称 [l,m] 为 [l,r] 的「左子区间」，[m+1,r] 为 [l,r] 的「右子区间」。如何维护这些量呢（如何通过左右子区间的信息合并得到 [l,r] 的信息）？对于长度为 11 的区间 [i,i]，四个量的值都和 ai 相等。对于长度大于 1 的区间：  

首先最好维护的是 iSum，区间 [l,r] 的 iSum 就等于「左子区间」的 iSum 加上「右子区间」的 iSum。  
对于 [l,r] 的 lSum，存在两种可能，它要么等于「左子区间」的 lSum，要么等于「左子区间」的 iSum 加上「右子区间」的 lSum，二者取大。  
对于 [l,r] 的 rSum，同理，它要么等于「右子区间」的 rSum，要么等于「右子区间」的 iSum 加上「左子区间」的 rSum，二者取大。  
当计算好上面的三个量之后，就很好计算 [l,r] 的 mSum 了。我们可以考虑 [l,r] 的 mSum 对应的区间是否跨越 mm——它可能不跨越 mm，也就是说 [l,r] 的 mSum 可能是「左子区间」的 mSum 和 「右子区间」的 mSum 中的一个；它也可能跨越 mm，可能是「左子区间」的 rSum 和 「右子区间」的 lSum 求和。三者取大。  
```cpp
class Solution {
public:
    struct Status {
        int lSum, rSum, mSum, iSum;
    };

    Status pushUp(Status l, Status r) {
        int iSum = l.iSum + r.iSum;
        int lSum = max(l.lSum, l.iSum + r.lSum);
        int rSum = max(r.rSum, r.iSum + l.rSum);
        int mSum = max(max(l.mSum, r.mSum), l.rSum + r.lSum);
        return (Status) {lSum, rSum, mSum, iSum};
    };

    Status get(vector<int> &a, int l, int r) {
        if (l == r) return (Status) {a[l], a[l], a[l], a[l]};
        int m = (l + r) >> 1;
        Status lSub = get(a, l, m);
        Status rSub = get(a, m + 1, r);
        return pushUp(lSub, rSub);
    }

    int maxSubArray(vector<int>& nums) {
        return get(nums, 0, nums.size() - 1).mSum;
    }
};
```
```
Runtime: 8 ms, faster than 49.72% of C++ online submissions for Maximum Subarray.
Memory Usage: 13.2 MB, less than 5.88% of C++ online submissions for Maximum Subarray.
```
时间复杂度：O(n)  
空间复杂度：O(logn)  
