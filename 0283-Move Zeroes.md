思路：遍历数组，记录0的个数，并删除。最后统一在数组后面添加0。
```cpp
class Solution
{
public:
    void moveZeroes(vector<int> &nums)
    {
        int cnt = 0;
        for (auto iter = nums.begin(); iter != nums.end();)
        {
            if (*iter == 0)
            {
                cnt++;
                iter = nums.erase(iter);
            }
            else
            {
                ++iter;
            }
        }

        for (int j = 0; j < cnt; ++j)
        {
            nums.push_back(0);
        }
    }
};
```
```
执行用时：12 ms, 在所有 C++ 提交中击败了45.81%的用户
内存消耗：8.9 MB, 在所有 C++ 提交中击败了95.47%的用户
```
