```cpp
class Solution {
public:
	int maxArea(vector<int>& height) {
		int result = 0;
		for (int i = 0; i < height.size() - 1; ++i)
		{
			int begin = height[i];
			int cnt = 1;
			for (int j = i + cnt; j < height.size(); ++j)
			{
				int end = height[j];
				int smaller = 0;
				if (begin <= end)
				{
					smaller = begin;
				}
				else
				{
					smaller = end;
				}
				int temp = cnt*smaller;
				if (temp > result)
				{
					result = temp;
				}
				cnt++;
			}
		}
		return result;
	}
};
```

Runtime: 728 ms, faster than 16.45% of C++ online submissions for Container With Most Water.
Memory Usage: 9.8 MB, less than 68.04% of C++ online submissions for Container With Most Water.

思路：从第一个数开始，遍历每个容器的大小，取最大值。
