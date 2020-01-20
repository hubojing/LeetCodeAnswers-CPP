本题提到时间复杂度为O(logn)，根据第33题的经验，采用二分查找法。  
找到其中一个与target值相同的数，然后以此数为中心遍历前后，找出起始点和终止点。
```cpp
class Solution
{
public:
    void binarySearch(int &existPos, vector<int> &nums, int target, int left, int right)
    {
        if (left > right)
        {
            return;
        }
        int midIndex = left + (right - left) / 2;
        if (target > nums[midIndex])
        {
            left = midIndex + 1;
            if (left >= nums.size())
            {
                return;
            }
            binarySearch(existPos, nums, target, left, right);
        }
        else if (target < nums[midIndex])
        {
            right = midIndex - 1;
            if (right < 0)
            {
                return;
            }
            binarySearch(existPos, nums, target, left, right);
        }
        else
        {
            existPos = midIndex;
        }
    }

    int findStartpos(vector<int> &nums, int existPos)
    {
        for (int i = existPos - 1; i >= 0; --i)
        {
            if (nums[i] == nums[existPos])
            {
                continue;
            }
            else
            {
                return i + 1;
            }
        }
        return 0;
    }

    int findEndpos(vector<int> &nums, int startPos)
    {
        for (int i = startPos + 1; i < nums.size(); ++i)
        {
            if (nums[i] == nums[startPos])
            {
                continue;
            }
            else
            {
                return i - 1;
            }
        }
        return nums.size() - 1;
    }
    vector<int> searchRange(vector<int> &nums, int target)
    {
        if (nums.size() == 0)
        {
            return {-1, -1};
        }
        if (nums.size() == 1)
        {
            if (nums[0] == target)
            {
                return {0, 0};
            }
            else
            {
                return {-1, -1};
            }
        }
        int existPos = -1;
        binarySearch(existPos, nums, target, 0, nums.size() - 1);
        if (existPos == -1)
        {
            return {-1, -1};
        }
        int startPos = findStartpos(nums, existPos);
        int endPos = findEndpos(nums, startPos);
        vector<int> result;
        result.push_back(startPos);
        result.push_back(endPos);
        return result;
    }
};
```
```
Runtime: 8 ms, faster than 85.23% of C++ online submissions for Find First and Last Position of Element in Sorted Array.
Memory Usage: 10.4 MB, less than 59.34% of C++ online submissions for Find First and Last Position of Element in Sorted Array.
```
