难度：Easy  
注意0P这个测试用例。
```cpp
class Solution
{
public:
    bool isPalindrome(string s)
    {
        string str;
        int lens = s.size();
        for (int i = 0; i < lens; ++i)
        {
            if ((s[i] >= 'a' && s[i] <= 'z') || (s[i] >= 'A' && s[i] <= 'Z') || (s[i] >= '0' && s[i] <= '9'))
            {
                s[i] = tolower(s[i]);
                str += s[i];
            }
        }

        int strlen = str.size();
        for (int j = 0; j < strlen; ++j)
        {
            if (str[j] != str[strlen - j - 1])
            {
                return false;
            }
        }
        return true;
    }
};
```
```
执行用时：0 ms, 在所有 C++ 提交中击败了100.00%的用户
内存消耗：7.5 MB, 在所有 C++ 提交中击败了68.14%的用户
```
