# LeetCode(1) - 两数之和

#### 给定一个整数数组 nums 和一个目标值 target，请你在该数组中找出和为目标值的那 两个 整数，并返回他们的数组下标。

#### 你可以假设每种输入只会对应一个答案。但是，数组中同一个元素不能使用两遍。

### 示例

```javascript
给定 nums = [2, 7, 11, 15], target = 9

因为 nums[0] + nums[1] = 2 + 7 = 9

所以返回 [0, 1]
```

### 解题思路

- 通过差值寻找到正确的两个数
- indexof判断差值是否存在于nums数组中
- 通过find 或者some 函数 筛选出正确的差值
- 注意数组中同一个元素不能使用两遍

### 代码

```javascript
var twoSum = function (nums, target) {
      var _result
      nums.find(function (item, index) {
        // 判断是否包含
        var _index = nums.indexOf(target - item)
        if (_index !== -1 && index !== _index) {
          _result = [index, _index]
          return true
        }
      })
      return _result
    };
    
console.log(twoSum([2,7,11,15],target=18));// [1, 2]
console.log(twoSum([2,7,11,15],target=18));//undefined
```



