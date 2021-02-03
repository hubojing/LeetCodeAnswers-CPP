难度：Easy  
思路：左边小于右边，减。左边不小于右边，加。  
```cpp
class Solution {
public:
    int romanToInt(string s) {
        int res = 0;
        map<char, int> transmap;
        transmap['I'] = 1;
        transmap['V'] = 5;
        transmap['X'] = 10;
        transmap['L'] = 50;
        transmap['C'] = 100;
        transmap['D'] = 500;
        transmap['M'] = 1000;
        
        int len = s.size();
        for(int i = 0; i < len; ++i)
        {
            if(transmap[s[i]] < transmap[s[i+1]])
            {
                res -= transmap[s[i]];
            }
            else
            {
                res += transmap[s[i]];
            }
        }
        return res;
    }
};
```
```
执行用时：24 ms, 在所有 C++ 提交中击败了45.52%的用户
内存消耗：8.2 MB, 在所有 C++ 提交中击败了41.55%的用户
```
