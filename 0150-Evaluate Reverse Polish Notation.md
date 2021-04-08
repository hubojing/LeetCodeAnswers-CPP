难度：Medium  
思路：用栈保存中间计算值。  
```cpp
class Solution {
public:
    int evalRPN(vector<string>& tokens) {
        stack<string> st;
        int len = tokens.size();
        for(int i = 0; i < len; ++i)
        {
            string& token = tokens[i];
            if (tokens[i] != "+" && tokens[i] != "-" && tokens[i] != "*" && tokens[i] != "/")
            {
                st.push(tokens[i]);
            }
            else if(tokens[i] == "+")
            {
                string s1 = st.top();
                st.pop();
                string s2 = st.top();
                st.pop();
                int si1 = atoi(s1.c_str());
                int si2 = atoi(s2.c_str());
                int val = si1 + si2;
                st.push(to_string(val));
            }
            else if(tokens[i] == "-")
            {
                string s1 = st.top();
                st.pop();
                string s2 = st.top();
                st.pop();
                int si1 = atoi(s1.c_str());
                int si2 = atoi(s2.c_str());
                int val = si2 - si1;
                st.push(to_string(val));
            }
            else if(tokens[i] == "*")
            {
                string s1 = st.top();
                st.pop();
                string s2 = st.top();
                st.pop();
                int si1 = atoi(s1.c_str());
                int si2 = atoi(s2.c_str());
                int val = si2 * si1;
                st.push(to_string(val));
            }
            else
            {
                string s1 = st.top();
                st.pop();
                string s2 = st.top();
                st.pop();
                int si1 = atoi(s1.c_str());
                int si2 = atoi(s2.c_str());
                int val = si2/si1;
                st.push(to_string(val));
            }
        }
        string tmp = st.top();
        int res = atoi(tmp.c_str());
        return res;
    }
};
```
```
执行用时：16 ms, 在所有 C++ 提交中击败了35.27%的用户
内存消耗：12.5 MB, 在所有 C++ 提交中击败了5.00%的用户
```
