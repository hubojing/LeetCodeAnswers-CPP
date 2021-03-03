难度：Easy  
思路：如果两个字符串排序后相同则为true，否则为false。
```cpp
class Solution
{
public:
    bool isAnagram(string s, string t)
    {
        sort(s.begin(), s.end());
        sort(t.begin(), t.end());
        if (s == t)
        {
            return true;
        }
        return false;
    }
};
```
```
执行用时：16 ms, 在所有 C++ 提交中击败了44.57%的用户
内存消耗：7.2 MB, 在所有 C++ 提交中击败了73.72%的用户
```
