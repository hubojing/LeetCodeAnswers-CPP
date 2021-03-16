难度：Easy
```cpp
class Solution {
public:
    bool isPalindrome(int x) {
        stringstream s;
        s << x;
        string str = s.str();
        int len = str.size();
        for(int i = 0; i < len/2; ++i)
        {
            if(str[i] != str[len - i - 1])
            {
                return false;
            }
        }
        return true;
    }
};
```
```
执行用时：24 ms, 在所有 C++ 提交中击败了23.20%的用户
内存消耗：5.7 MB, 在所有 C++ 提交中击败了85.12%的用户
```
由于要求不用字符串，于是改为：
```cpp
class Solution {
public:
    bool isPalindrome(int x) {
        if(x < 0 || (x % 10 == 0 && x != 0))
        {
            return false;
        }

        int renum = 0;
        while(x > renum)
        {
            renum = renum * 10 + x % 10;
            x /= 10;
        }

        return x == renum || x == renum / 10;
    }
};
```
```
执行用时：16 ms, 在所有 C++ 提交中击败了55.55%的用户
内存消耗：5.9 MB, 在所有 C++ 提交中击败了43.16%的用户
```
