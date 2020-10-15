# 个人解法
这个字符串匹配的问题，主要就是用到栈。  
我的想法是，先把si-1入栈，如果si匹配，则si-1出栈，否则si入栈。
```cpp
class Solution
{
public:
    bool isValid(string s)
    {
        stack<char> st;
        char ch = s[0];
        st.push(ch);

        for (int i = 1; i < s.length(); ++i)
        {
            char ch1 = s[i];
            if (st.size() == 0)
            {
                st.push(ch1);
                continue;
            }
            char ch2 = st.top();
            if ((ch2 == '(' && ch1 == ')') || (ch2 == '[' && ch1 == ']') || (ch2 == '{' && ch1 == '}'))
            {
                st.pop();
            }
            else
            {
                st.push(ch1);
            }
        }
        if (st.size() == 0)
        {
            return true;
        }
        else
        {
            return false;
        }
    }
};
```
```
执行用时：4 ms, 在所有 C++ 提交中击败了 49.39% 的用户
内存消耗：6.5 MB, 在所有 C++ 提交中击败了 14.62% 的用户
```

# 官方解法
思路类似，不过用到了哈希映射存储符号。并且注意到有效字符串的长度一定为偶数，因此如果字符串的长度为奇数，可以直接返回False，省去后续的遍历判断过程。
```cpp
class Solution {
public:
    bool isValid(string s) {
        int n = s.size();
        if (n % 2 == 1) {
            return false;
        }

        unordered_map<char, char> pairs = {
            {')', '('},
            {']', '['},
            {'}', '{'}
        };
        stack<char> stk;
        for (char ch: s) {
            if (pairs.count(ch)) {
                if (stk.empty() || stk.top() != pairs[ch]) {
                    return false;
                }
                stk.pop();
            }
            else {
                stk.push(ch);
            }
        }
        return stk.empty();
    }
};
```
```cpp
执行用时：4 ms, 在所有 C++ 提交中击败了 49.39% 的用户
内存消耗：6.4 MB, 在所有 C++ 提交中击败了 28.76% 的用户
```
时间复杂度：O(n)  
空间复杂度：O(n+∣Σ∣)
