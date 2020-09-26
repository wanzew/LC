# 装水最多的容器

### 问题描述

**给你 n 个非负整数 a1，a2，...，an，每个数代表坐标中的一个点 (i, ai) 。在坐标内画 n 条垂直线，垂直线 i 的两个端点分别为 (i, ai) 和 (i, 0)。找出其中的两条线，使得它们与 x 轴共同构成的容器可以容纳最多的水。**

##### **说明：你不能倾斜容器，且 n 的值至少为 2。**



![011_ContainerWithMostWater](https://github.com/wanzew/Leetcode/blob/master/00_Order/011_ContainerWithMostWater.jpg)

### 解题思路



![011_ContainerWithMostWater2](F:\Code\Tutorial\05_leetcode\00_Order\011_ContainerWithMostWater2.jpg)

![011_ContainerWithMostWater3](F:\Code\Tutorial\05_leetcode\00_Order\011_ContainerWithMostWater3.jpg)

![011_ContainerWithMostWater4](F:\Code\Tutorial\05_leetcode\00_Order\011_ContainerWithMostWater4.jpg)

![011_ContainerWithMostWater5](F:\Code\Tutorial\05_leetcode\00_Order\011_ContainerWithMostWater5.jpg)

![011_ContainerWithMostWater6](F:\Code\Tutorial\05_leetcode\00_Order\011_ContainerWithMostWater6.jpg)

![011_ContainerWithMostWater7](F:\Code\Tutorial\05_leetcode\00_Order\011_ContainerWithMostWater7.jpg)

### 代码

```C++
class Solution {
public:
    int maxArea(vector<int>& height) {
        // 方法一： 暴力解法，但会超时
        /*int maxarea = 0;
        for(int i = 0; i < height.size() - 1; i++){
            for(int j = i+1; j < height.size(); j++){
                int area = (j-i) * min(height[i], height[j]);
                if (area > maxarea) maxarea = area;
            }
        }
        return maxarea;*/

        // 方法二：
        int i = 0, j = height.size() - 1;
        int area = 0;
        int maxarea = min(height[i], height[j]) * (j - i);

        while(i < j) {
            if (height[i] < height[j]) {
                //++i;
                area = min(height[++i], height[j]) * (j - i);
            }
            else {
                //--j;
                area = min(height[i], height[--j]) * (j - i);
            }
            
            if (area > maxarea) maxarea = area;
        }
        return maxarea;
    }
};
```

