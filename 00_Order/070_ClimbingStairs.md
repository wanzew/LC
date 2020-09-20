# 爬楼梯

假设你正在爬楼梯。需要 n 阶你才能到达楼顶。

每次你可以爬 1 或 2 个台阶。你有多少种不同的方法可以爬到楼顶呢？

注意：给定 n 是一个正整数。

示例 1：

输入： 2
输出： 2
解释： 有两种方法可以爬到楼顶。
1.  1 阶 + 1 阶
2.  2 阶



### 1 滚动数组

```C++
class Solution {
public:
    int climbStairs(int n) {
        /*vector<int> steps(n+1, 0);

        steps[1] = 1;
        steps[2] = 2;

        for (int i = 3; i <=n; i++) {
            steps[i] = steps[i-1] + steps[i-2]; // overflow
        }
        return steps[n];*/
        
        //初始化
        int pre = 1;
        int cur = 1;  
        //开始迭代n-1次
        for (int i = 0; i<n-1;i++) {
            cur = cur + pre;
            pre = cur - pre;
        }
        return cur;
};
```

#### 时间复杂度

循环执行 n 次，每次花费常数的时间代价，故渐进时间复杂度为 O(n)。

#### 空间复杂度

这里只用了常数个变量作为辅助空间，故渐进空间复杂度为 O(1)。



### 动态规划



