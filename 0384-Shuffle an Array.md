难度：Medium  
思路：随机索引，然后和当前位置的数交换。
```cpp
class Solution {
private:
    vector<int> vec;
public:
    Solution(vector<int>& nums) {
        vec = nums;
    }
    
    /** Resets the array to its original configuration and return it. */
    vector<int> reset() {
        return vec;
    }
    
    /** Returns a random shuffling of the array. */
    vector<int> shuffle() {
        vector<int> svec = vec;
        int len = svec.size();
        for(int i = 0; i < len; ++i)
        {
            int tmp = (rand() % (len - 1 - 0 + 1)) + 0;
            swap(svec[i], svec[tmp]);
        }
        return svec;
    }
};

/**
 * Your Solution object will be instantiated and called as such:
 * Solution* obj = new Solution(nums);
 * vector<int> param_1 = obj->reset();
 * vector<int> param_2 = obj->shuffle();
 */
```
```
执行用时：144 ms, 在所有 C++ 提交中击败了55.60%的用户
内存消耗：88.2 MB, 在所有 C++ 提交中击败了61.12%的用户
```
