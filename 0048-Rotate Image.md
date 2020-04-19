思路：n*n数组旋转问题，观察数组形式，可发现先沿对角线对折，再沿y轴对折，即可。  
注意循环中i和j的边界问题。
```cpp
class Solution
{
public:
    void rotate(vector<vector<int>> &matrix)
    {
        int n = matrix.size();
        for (int i = 0; i < n; ++i)
        {
            for (int j = 0; j < i; ++j)
            {
                int tmp = matrix[i][j];
                matrix[i][j] = matrix[j][i];
                matrix[j][i] = tmp;
            }
        }

        for (int i = 0; i < n; ++i)
        {
            for (int j = 0; j < n / 2; ++j)
            {
                int tmp = matrix[i][j];
                matrix[i][j] = matrix[i][n - j - 1];
                matrix[i][n - j - 1] = tmp;
            }
        }
    }
};
```
```
Runtime: 4 ms, faster than 75.26% of C++ online submissions for Rotate Image.
Memory Usage: 6.7 MB, less than 100.00% of C++ online submissions for Rotate Image.
```
