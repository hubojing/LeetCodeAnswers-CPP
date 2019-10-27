本题思路简单，直接删掉一样的数就好了，不过可以预见这种方法不会是最佳的。
```cpp
class Solution
{
public:
	int removeElement(vector<int>& nums, int val)
	{
		vector<int>::iterator it;
		for (it = nums.begin();it != nums.end();)
		{
			if (*it == val)
			{
				it = nums.erase(it);
			}
			else
			{
				++it;
			}
		}
		return nums.size();
	}
};
```
```
Runtime: 4 ms, faster than 70.95% of C++ online submissions for Remove Element.
Memory Usage: 8.5 MB, less than 95.59% of C++ online submissions for Remove Element.
```
