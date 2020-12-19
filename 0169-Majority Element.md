# 官方题解
## 法一：哈希表
```cpp
class Solution {
public:
    int majorityElement(vector<int>& nums) {
        unordered_map<int, int> counts;
        int majority = 0, cnt = 0;
        for (int num: nums) {
            ++counts[num];
            if (counts[num] > cnt) {
                majority = num;
                cnt = counts[num];
            }
        }
        return majority;
    }
};
```
```
执行用时：36 ms, 在所有 C++ 提交中击败了41.13%的用户
内存消耗：9 MB, 在所有 C++ 提交中击败了23.40%的用户
```
时间复杂度：O(n)  
空间复杂度：O(n)

## 法二：排序
```cpp
class Solution {
public:
    int majorityElement(vector<int>& nums) {
        sort(nums.begin(), nums.end());
        return nums[nums.size() / 2];
    }
};
```
```
执行用时：56 ms, 在所有 C++ 提交中击败了22.87%的用户
内存消耗：8.8 MB, 在所有 C++ 提交中击败了62.96%的用户
```
时间复杂度：O(nlogn)  
空间复杂度：O(logn)

## 法三：随机化
```cpp
class Solution {
public:
    int majorityElement(vector<int>& nums) {
        while (true) {
            int candidate = nums[rand() % nums.size()];
            int count = 0;
            for (int num : nums)
                if (num == candidate)
                    ++count;
            if (count > nums.size() / 2)
                return candidate;
        }
        return -1;
    }
};
```
```
执行用时：8 ms, 在所有 C++ 提交中击败了99.86%的用户
内存消耗：9 MB, 在所有 C++ 提交中击败了17.02%的用户
```
时间复杂度：理论上最坏情况下的时间复杂度为O(∞)，期望的时间复杂度为 O(n)。  
空间复杂度：O(1)

## 法四：分治
```cpp
class Solution {
    int count_in_range(vector<int>& nums, int target, int lo, int hi) {
        int count = 0;
        for (int i = lo; i <= hi; ++i)
            if (nums[i] == target)
                ++count;
        return count;
    }
    int majority_element_rec(vector<int>& nums, int lo, int hi) {
        if (lo == hi)
            return nums[lo];
        int mid = (lo + hi) / 2;
        int left_majority = majority_element_rec(nums, lo, mid);
        int right_majority = majority_element_rec(nums, mid + 1, hi);
        if (count_in_range(nums, left_majority, lo, hi) > (hi - lo + 1) / 2)
            return left_majority;
        if (count_in_range(nums, right_majority, lo, hi) > (hi - lo + 1) / 2)
            return right_majority;
        return -1;
    }
public:
    int majorityElement(vector<int>& nums) {
        return majority_element_rec(nums, 0, nums.size() - 1);
    }
};
```
```
执行用时：20 ms, 在所有 C++ 提交中击败了72.77%的用户
内存消耗：9 MB, 在所有 C++ 提交中击败了19.61%的用户
```
时间复杂度：O(nlogn)  
空间复杂度：O(logn)

## 法五：Boyer-Moore 投票算法
如果候选人不是maj，则maj会和其他非候选人一起反对 会反对候选人，所以候选人一定会下台（maj==0时发生换届选举）。  
如果候选人是maj，则maj会支持自己，其他候选人会反对，同样因为maj票数超过一半，所以maj一定会成功当选。
```cpp
class Solution {
public:
    int majorityElement(vector<int>& nums) {
        int candidate = -1;
        int count = 0;
        for (int num : nums) {
            if (num == candidate)
                ++count;
            else if (--count < 0) {
                candidate = num;
                count = 1;
            }
        }
        return candidate;
    }
};
```
```
执行用时：8 ms, 在所有 C++ 提交中击败了99.86%的用户
内存消耗：9 MB, 在所有 C++ 提交中击败了24.30%的用户
```
时间复杂度：O(n)  
空间复杂度：O(1)
