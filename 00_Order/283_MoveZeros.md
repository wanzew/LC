# 移动零

###  代码

```C++
class Solution {
public:
    void moveZeroes(vector<int>& nums) {
        int indexFirstZero(0);
        while(indexFirstZero < nums.size() && nums[indexFirstZero]){
                indexFirstZero++;
        }
        
        int indexIter = indexFirstZero;
        
        for(int i = indexIter+1; i < nums.size(); i++){
            if(0 != nums[i]){
                nums[indexIter++] = nums[i];
            }
        }
        for(int i = indexIter; i<nums.size(); i++){
            nums[i] = 0;
        }
    }
};
```

### 解题思路

##### 先找到第一个0元素

##### 从第一个0元素后面的元素开始，把非0元素放到0元素的位置

##### 所有非0元素前移之后，剩余的元素置为0

![283_MoveZeros](283_MoveZeros.assets/283_MoveZeros.gif)