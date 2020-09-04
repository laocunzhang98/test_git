## LeetCode(2)-有效的括号

### 给定一个只包括 '('，')'，'{'，'}'，'['，']' 的字符串，判断字符串是否有效。

#### 有效字符串需满足：

##### 左括号必须用相同类型的右括号闭合。

##### 左括号必须以正确的顺序闭合。

##### 注意空字符串可被认为是有效字符串。

##### 示例 1:

- 输入: "()"
- 输出: true

##### 示例 2:

- 输入: "()[]{}"
- 输出: true

##### 示例 3:

- 输入: "(]"
- 输出: false

##### 示例 4:

- 输入: "([)]"
- 输出: false

##### 示例 5:

- 输入: "{[]}"
- 输出: true

### 解题思路

- 1.使用栈结构，当为{,[,(,时压住栈内，当为},],),与栈顶元素进行匹配 匹配成功出栈

- 2.每种括号的左右数量分别相等，但不是有效的括号。这是因为结果还与括号的位置有关。

- 3.匹配时我们使用了哈希表来判断是否能够形成括号

- 4.栈内最后为空时说明匹配完成 全部出栈，返回true 反之返回false

  

### 代码

```javascript
var isValid = function (s) {
      let flag = true
      let sList = s.split('')
      let sListLength = sList.length
      let stack = []
      // 创建hash映射
      const map = {
        '{': '}',
        '(': ')',
        '[': ']'
      }
      if (!sListLength) return true
      if (sListLength % 2 !== 0) return false
      sList.forEach(item => {
        if (map.hasOwnProperty(item)) {
          stack.push(item)
        }
        else{
          const peak = stack.pop()
          if(map[peak] !== item){
            flag = false
          }
        }
      })
      if(stack.length>0) return false
      return flag
    };
    console.log(isValid('((())))'));//false
	console.log(isValid('([{}])'));//true
```



## 路漫漫其修远兮，吾将上下而求索