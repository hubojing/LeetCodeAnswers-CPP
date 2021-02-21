难度：Easy  
注意nums1数组后面的0是用来占位的。
```cpp
class Solution
{
public:
    void merge(vector<int> &nums1, int m, vector<int> &nums2, int n)
    {
        int len1 = nums1.size();
        int len2 = nums2.size();
        for (int i = m; i < m + n; ++i)
        {
            nums1[i] = nums2[i - m];
        }
        sort(nums1.begin(), nums1.end());
    }
};
```
