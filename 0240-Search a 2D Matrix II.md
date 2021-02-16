难度：Medium
思路：从左下角开始，大于目标值就上移一行，小于目标值就右移一列。
```cpp
class Solution
{
public:
    bool searchMatrix(vector<vector<int>> &matrix, int target)
    {
        int row = matrix.size() - 1, col = 0;
        if (matrix[row][col] == target)
        {
            return true;
        }
        while (row < matrix.size() && col < matrix[0].size())
        {
            if (matrix[row][col] > target)
            {
                row--;
            }
            else if (matrix[row][col] < target)
            {
                col++;
            }
            else
            {
                return true;
            }
        }
        return false;
    }
};
```
```
执行用时：136 ms, 在所有 C++ 提交中击败了74.57%的用户
内存消耗：14.3 MB, 在所有 C++ 提交中击败了76.24%的用户
```
