# 个人解法
想法很简单，用vector实现就好了。
```cpp
class MinStack {
public:
    /** initialize your data structure here. */
    MinStack() {
        vector<int> vec;
    }
    
    void push(int x) {
        vec.push(x);
    }
    
    void pop() {
        vec.pop(x);
    }
    
    int top() {
        vec.top(x);
    }
    
    int getMin() {
        int min = vec[0];
        for(int i = 0; i < vec.size(); ++i)
        {
            if (min > vec[i])
            {
                min = vec[i];
            }
        }
        return min;
    }
};

/**
 * Your MinStack object will be instantiated and called as such:
 * MinStack* obj = new MinStack();
 * obj->push(x);
 * obj->pop();
 * int param_3 = obj->top();
 * int param_4 = obj->getMin();
 */
```
```
执行用时：352 ms, 在所有 C++ 提交中击败了5.03%的用户
内存消耗：14.7 MB, 在所有 C++ 提交中击败了24.81%的用户
```
虽然能通过，但题目要求getMin()的时间复杂度为O(1)。

# 官方题解
设计一个数据结构，使得每个元素 a 与其相应的最小值 m 时刻保持一一对应。因此可以使用一个辅助栈，与元素栈同步插入与删除，用于存储与每个元素对应的最小值。  
- 当一个元素要入栈时，取当前辅助栈的栈顶存储的最小值，与当前元素比较得出最小值，将这个最小值插入辅助栈中；
- 当一个元素要出栈时，我们把辅助栈的栈顶元素也一并弹出；
- 在任意一个时刻，栈内元素的最小值就存储在辅助栈的栈顶元素中。
```cpp
class MinStack {
    stack<int> x_stack;
    stack<int> min_stack;
public:
    MinStack() {
        min_stack.push(INT_MAX);
    }
    
    void push(int x) {
        x_stack.push(x);
        min_stack.push(min(min_stack.top(), x));
    }
    
    void pop() {
        x_stack.pop();
        min_stack.pop();
    }
    
    int top() {
        return x_stack.top();
    }
    
    int getMin() {
        return min_stack.top();
    }
};
```
```
执行用时：28 ms, 在所有 C++ 提交中击败了98.95%的用户
内存消耗：14.8 MB, 在所有 C++ 提交中击败了9.82%的用户
```
