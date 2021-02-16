难度：Medium  
思路：朴实无华的思路，遍历全部子串，并判断每个子串是不是回文串，同时计数。
```cpp
class Solution
{
public:
    bool isPalin(string str)
    {
        int len = str.size();
        for (int i = 0; i < len; ++i)
        {
            if (str[i] != str[len - i - 1])
            {
                return false;
            }
        }
        return true;
    }
    int countSubstrings(string s)
    {
        int len = s.size();
        int cnt = 0;
        for (int i = 0; i < len; ++i)
        {
            for (int j = 1; j < len - i + 1; ++j)
            {
                string subs = s.substr(i, j);
                if (isPalin(subs))
                {
                    cnt++;
                }
            }
        }
        return cnt;
    }
};
```
```
执行用时：1504 ms, 在所有 C++ 提交中击败了5.01%的用户
内存消耗：473 MB, 在所有 C++ 提交中击败了5.00%的用户
```
