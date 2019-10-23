这个题重点在于，题目没说需要删除重复的数字……而删除又是一件费时的事情，那么不删就好了。
```cpp
class Solution {
public:
	int removeDuplicates(vector<int>& nums)
	{
		int cnt = 0;
		for (int i = 1;i < nums.size();++i)
		{
			if (nums[i] == nums[i - 1])
			{
				cnt++;
			}
			else
			{
				nums[i - cnt] = nums[i];
			}
		}
		return nums.size() - cnt;
	}
};
```
```
Runtime: 20 ms, faster than 93.35% of C++ online submissions for Remove Duplicates from Sorted Array.
Memory Usage: 10.1 MB, less than 36.25% of C++ online submissions for Remove Duplicates from Sorted Array.
```
然后我在讨论区看到一个更简的答案：
```cpp
class Solution {
public:
	int removeDuplicates(vector<int>& nums)
	{
		nums.erase(unique(nums.begin(), nums.end()), nums.end());
		return nums.size();
	}
};
```
我试了试：
```
Runtime: 20 ms, faster than 93.35% of C++ online submissions for Remove Duplicates from Sorted Array.
Memory Usage: 10 MB, less than 82.50% of C++ online submissions for Remove Duplicates from Sorted Array.
```
