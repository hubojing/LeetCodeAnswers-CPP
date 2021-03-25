难度：Medium
```cpp
class Solution {
public:
    int kthSmallest(vector<vector<int>>& matrix, int k) {
        int row = matrix.size();
        int col = matrix[0].size();
        vector<int> vec;
        for(int i = row - 1; i >= 0; --i)
        {
            for(int j = 0; j < col; ++j)
            {
                vec.push_back(matrix[i][j]);
            }
        }
        sort(vec.begin(), vec.end());
        return vec[k - 1];
    }
};
```
```
执行用时: 40 ms，超过了58%的cpp提交记录
内存消耗: 14.3 MB，超过了8%的cpp提交记录
```
