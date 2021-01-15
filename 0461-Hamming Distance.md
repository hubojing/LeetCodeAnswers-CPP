思路：首先进制转换，然后遍历数组。  
注意进制转换后的vector没有补上左侧的0。比如，1110和0010，后者只记录了10。  
所以需增加边界判断条件，即遍历索引到小size数组边界时，要判断大size多余的部分是否有1，有1则最终结果要加上1的个数。
```cpp
class Solution
{
public:
    int hammingDistance(int x, int y)
    {
        vector a = convert(x);
        vector b = convert(y);
        int i = 0;
        int cnt = 0;
        while (i < a.size() || i < b.size())
        {
            if (i == a.size())
            {
                for (int j = a.size(); j < b.size(); ++j)
                {
                    if (b[j] == 1)
                    {
                        cnt++;
                    }
                }
                return cnt;
            }
            if (i == b.size())
            {
                for (int j = b.size(); j < a.size(); ++j)
                {
                    if (a[j] == 1)
                    {
                        cnt++;
                    }
                }
                return cnt;
            }
            if (a[i] != b[i])
            {
                cnt++;
            }
            i++;
        }
        return cnt;
    }

    vector<int> convert(int a)
    {
        vector<int> vec;
        while (a != 0)
        {
            vec.push_back(a % 2);
            a = a / 2;
        }
        return vec;
    }
};
```
```
执行用时：0 ms, 在所有 C++ 提交中击败了100.00%的用户
内存消耗：6.1 MB, 在所有 C++ 提交中击败了75.93%的用户
```
