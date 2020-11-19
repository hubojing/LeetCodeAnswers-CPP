最开始的想法是两个for循环暴力遍历，但是最后有用例超出时间限制。
所以考虑改为一次遍历。
注意特殊用例，比如[]。
```cpp
class Solution
{
public:
    int maxProfit(vector<int> &prices)
    {
        int len = prices.size();
        if (len == 0)
        {
            return 0;
        }
        int minPrice = prices[0];
        int maxProfit = 0;

        for (int i = 0; i < len; ++i)
        {
            maxProfit = max(maxProfit, prices[i] - minPrice);
            minPrice = min(minPrice, prices[i]);
        }
        return maxProfit;
    }
};
```
```
执行用时：8 ms, 在所有 C++ 提交中击败了94.73%的用户
内存消耗：13 MB, 在所有 C++ 提交中击败了20.88%的用户
```

官方题解基本和上述思路一样，写法略有差别。
```
class Solution {
public:
    int maxProfit(vector<int>& prices) {
        int inf = 1e9;
        int minprice = inf, maxprofit = 0;
        for (int price: prices) {
            maxprofit = max(maxprofit, price - minprice);
            minprice = min(price, minprice);
        }
        return maxprofit;
    }
};
```
```
执行用时：16 ms, 在所有 C++ 提交中击败了38.08%的用户
内存消耗：12.9 MB, 在所有 C++ 提交中击败了28.37%的用户
```
但是效率还是有些差别。
