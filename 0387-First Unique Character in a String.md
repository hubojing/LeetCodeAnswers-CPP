难度：Easy  
思路：建立一张哈希表记录次数，返回次数为1的索引。
```cpp
class Solution
{
public:
    int firstUniqChar(string s)
    {
        map<char, int> hashmap;
        int len = s.size();
        for (int i = 0; i < len; ++i)
        {
            map<char, int>::iterator iter = hashmap.find(s[i]);
            if (iter == hashmap.end())
            {
                hashmap.insert(make_pair(s[i], 1));
            }
            else
            {
                hashmap[s[i]] += 1;
            }
        }
        int maplen = hashmap.size();
        for (int i = 0; i < len; ++i)
        {
            if (hashmap[s[i]] == 1)
            {
                return i;
            }
        }
        return -1;
    }
};
```
```
执行用时：108 ms, 在所有 C++ 提交中击败了31.75%的用户
内存消耗：10.7 MB, 在所有 C++ 提交中击败了79.17%的用户
```
