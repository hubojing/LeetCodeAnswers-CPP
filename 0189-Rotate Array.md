难度：Medium  
思路：很朴素的想法，将原始数组往后开辟k个位置，将现有数组从后往前移动k个位置，将多出来的那部分转换到数组前面，最后弹出后面多余的部分。由于每次都是单循环，所以时间复杂度为O(n)。
```cpp
class Solution {
public:
	void rotate(vector<int>& nums, int k) {
		int len = nums.size();
		k %= len;
		if (len != 1 && k != 0)
		{
			for (int i = 0; i < k; ++i)
			{
				nums.push_back(1);
			}
			for (int j = len - 1; j >= 0; --j)
			{
				nums[j + k] = nums[j];
			}
			for (int m = 0; m < k; ++m)
			{
				nums[m] = nums[len + m];
			}
			for (int cnt = 0; cnt < k; ++cnt)
			{
				nums.pop_back();
			}
		}
	}
};
```
```
执行用时：4 ms, 在所有 C++ 提交中击败了95.61%的用户
内存消耗：9.6 MB, 在所有 C++ 提交中击败了89.99%的用户
```
