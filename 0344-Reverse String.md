难度：Easy  
思路：对半换位即可。
```cpp
class Solution
{
public:
    void reverseString(vector<char> &s)
    {
        int len = s.size();
        for (int i = 0; i < len / 2; ++i)
        {
            char tmp = s[i];
            s[i] = s[len - i - 1];
            s[len - i - 1] = tmp;
        }
    }
};
```
```
执行用时：20 ms, 在所有 C++ 提交中击败了92.85%的用户
内存消耗：22.5 MB, 在所有 C++ 提交中击败了86.24%的用户
```
