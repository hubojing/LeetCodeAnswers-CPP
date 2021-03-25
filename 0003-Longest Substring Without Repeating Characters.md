```cpp
class Solution {
public:
    int lengthOfLongestSubstring(string s) {
        int len = s.size();
        int res = 0;
        
        for(int i = 0; i < len; ++i)
        {
            int tmp = 1;
            map<char, int> hashmap;
            hashmap[s[i]] = 1;
            for(int j = i + 1; j < len; ++j)
            {
                if(hashmap[s[j]])
                {
                    break;
                }
                else
                {
                    hashmap[s[j]] = 1;
                    tmp++;
                }
            }
            if(tmp > res)
            {
                res = tmp;
            }
        }
        return res;
    }
};
```
```
执行用时: 1404 ms
内存消耗: 257.9 MB
```
