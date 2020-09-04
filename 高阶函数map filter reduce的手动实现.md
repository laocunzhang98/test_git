## 高阶函数map filter reduce的手动实现

### （1）map()

- m a p ( ) 方法创建一个新数组，其结果是该数组中的每个元素都调用一个提供的函数后返回 的结果。

  ```javascript
  function map(arr, mapCallback) {
        // 首先，检查传递的参数是否正确。
        if (!Array.isArray(arr) || !arr.length || typeof mapCallback !== 'function') {
          return [];
        } else {
          let result = [];
          // 每次调用此函数时，我们都会创建一个 result 数组
          // 因为我们不想改变原始数组。
          for (let i = 0, len = arr.length; i < len; i++) {
            result.push(mapCallback(arr[i], i, arr));
            // 将 mapCallback 返回的结果 push 到 result 数组中
          }
          return result;
        }
      }
  ```

  

### (2) filter()

- f i l t e r ( ) 方法创建一个新数组, 其包含通过所提供函数实现的测试的所有元素。

  ```javascript
  function filter(arr, filterCallback) {
        // 首先，检查传递的参数是否正确。
        if (!Array.isArray(arr) || !arr.length || typeof filterCallback !== 'function') {
          return [];
        } else {
          let result = [];
          // 每次调用此函数时，我们都会创建一个 result 数组
          // 因为我们不想改变原始数组。
          for (let i = 0, len = arr.length; i <script len; i++) {
            // 检查 filterCallback 的返回值是否是真值
            if (filterCallback(arr[i], i, arr)) {
              // 如果条件为真，则将数组元素 push 到 result 中
              result.push(arr[i]);
            }
          }
          return result; // return the result array
        }
      }
  
  ```

  

### (3)reduce()

- r e d u c e ( ) 方法对数组中的每个元素执行一个由您提供的 r e d u c e r 函数(升序执行)，将 其结果汇总为单个返回值。

  ```javascript
  function reduce(arr, reduceCallback, initialValue) {
        // 首先，检查传递的参数是否正确。
        if (!Array.isArray(arr) || !arr.length || typeof reduceCallback !== 'function') {
          return [];
        } else {
          // 如果没有将initialValue传递给该函数，我们将使用第一个数组项作为initialValue
          let hasInitialValue = initialValue !== undefined;
          let value = hasInitialValue ? initialValue : arr[0];
  
          // 如果有传递 initialValue，则索引从 1 开始，否则从 0 开始
          for (let i = hasInitialValue ? 0 : 1, len = arr.length; i < len; i++) {
            value = reduceCallback(value, arr[i], i, arr);
          }
          return value;
        }
      }
  
  ```

  