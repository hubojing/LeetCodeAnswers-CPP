思路：和第15题3Sum差不多，只是target由0变成了离设定target最近的值。因此首先把第15题的代码给复制过来。设置了一个bias记录sum离target的距离。当bias最小时(需要一个min变量来保存bias最小值)，返回此时的sum记为result。
```cpp
class Solution {
public:
	int threeSumClosest(vector<int>& nums, int target) {
		sort(nums.begin(), nums.end());
		int result = nums[0] + nums[1] + nums[2];
		int min = nums[0] + nums[1] + nums[2] - target;
		for (int i = 0; i < nums.size() - 2; ++i)
		{
			if (i > 0 && nums[i] == nums[i - 1])
			{
				continue;
			}
			int j = i + 1;
			int k = nums.size() - 1;
			while (j < k)
			{
				int sum = nums[i] + nums[j] + nums[k];
				int bias = sum - target;
				if (abs(min)>abs(bias))
				{
					min = bias;
					result = sum;
				}
				if (bias > 0)
				{

					k--;
					while (nums[k] == nums[k + 1] && j < k)
					{
						k--;
					}
				}
				else if (bias < 0)
				{
					j++;
					while (nums[j] == nums[j - 1] && j < k)
					{
						j++;
					}
				}
				else
				{
					result = sum;
					j++;
					while (nums[j] == nums[j - 1] && j < k)
					{
						j++;
					}
					k--;
					while (nums[k] == nums[k + 1] && j < k)
					{
						k--;
					}
				}
			}
		}
		return result;
	}
};
```
```
Runtime: 12 ms, faster than 36.98% of C++ online submissions for 3Sum Closest.
Memory Usage: 8.7 MB, less than 77.36% of C++ online submissions for 3Sum Closest.
```
