## 基本类型

```javascript
let [String, Boolean, Number] = ['javascript', true, 2020];


// result：String = javascript, Boolean = true, Number = 2020

//如果数组本身带有嵌套，可以通过下面的形式进行解构赋值，注意嵌套层次和位置要和数据保持一致：
let [String, Boolean, Number] = ['javascript', [true, 2020]];
// result：String = javascript, Boolean = true,2020, Number = undefined
// 正确做法
let [String, [Boolean, Number]] = ['javascript', [true, 2020]];
// result：String = ES6, Boolean = true, lNumber = 2020
/*
 * 注意，对数组元素进行解构赋值时，多个变量要用[...]括起来。
 */
let [String, ...a] = ['javascript', true, 2020];
// result：a = [true,2020]

// 解构赋值还可以忽略某些元素：
let [, , Number] = ['ES6', [true, 2020]];
// result：Number = undefined

```

##  数组类型



```javascript
let [wstars, mstars] = [
    ['zhoudongyu', 'masichun'], 
    ['xiaolizi', 'huge', 'pengyuyan']
];
// result：wstars = [ 'zhoudongyu', 'masichun' ]
// result：mstars = [ 'xiaolizi', 'huge', 'pengyuyan']

```

##  对象类型

```javascript

let star = {
    name: '周冬雨',
    age: 20,
    gender: 'female',
    address: {
        city: '石家庄市',
        street: '天街',
        tel:10086
    }
};
let { name, address: { city, ...zip } } = person;
//注意: address不是变量，而是为了让city和zip获得嵌套的address对象的属性:address;
//     #ReferenceError: address is not defined
/**
 * name = '周冬雨'
 * city = '石家庄市'
 * zip  = {street: "天街", tel: 10086}
 */
 
/**
 *  当我们在使用解构赋值对对象属性进行赋值时，如果对应的属性不存在，变量将被赋值为undefined，
 *  这和引用一个不存在的属性获得undefined是一致的。
 */
// 当我们要使用的变量名和属性名不一致，可以用通过下面的语法赋值后获取：
let { name, address: { city, phone:tel } } = star;
// tel = '10086'

// 解构赋值还可以使用默认值，这样就避免了不存在的属性返回undefined的问题：
let { name, address: { city, zipcode:code }, club='kings' } = star;
// sign = 'kings'

```

##  使用场景

```javascript

// 快速获取当前页面的域名和路径：
let {hostname:domain, pathname:path} = location;

/**
 * 如果一个函数接收一个对象作为参数，那么，可以使用解构直接把对象的属性绑定到变量中。
 * 例如，下面的函数可以快速创建一个Date对象：
 */
function buildDate({year, month, day, hour=0, minute=0, second=0}) {
    return new Date(year + '-' + month + '-' + day + ' ' + hour + ':' + minute + ':' + second);
}
buildDate({ year: 2020, month: 12, day: 27 });
// Thu Dec 27 2020 00:00:00 GMT+0800 (中国标准时间)
// 传入hour、minute和second属性：
buildDate({ year: getFullYear, month: 12, day: 27, hour: 20, minute: 15 });
// Thu Dec 27 2020 20:15:00 GMT+0800 (中国标准时间)
```

## 补充

```java
var myDate = new Date(); //获取当前时间及日期
var year=myDate.getYear(); // 获取当前年份(当前年份-1900)
var fyear=myDate.getFullYear(); // 获取完整的年份(4位,1970-????)
var mon=myDate.getMonth(); // 获取当前月份(0-11,0代表1月)
var date=myDate.getDate(); // 获取当前日(1-31)
var day=myDate.getDay(); // 获取当前星期X(0-6,0代表星期天)
var time=myDate.getTime(); // 获取当前时间(从1970.1.1开始的毫秒数)
var hos=myDate.getHours(); // 获取当前小时数(0-23)
var min=myDate.getMinutes(); // 获取当前分钟数(0-59)
var sec=myDate.getSeconds(); // 获取当前秒数(0-59)
var secs=myDate.getMilliseconds(); // 获取当前毫秒数(0-999)
var dd=myDate.toLocaleDateString(); // 获取当前日期
var mytime=myDate.toLocaleTimeString(); // 获取当前时间
var str=myDate.toLocaleString( ); // 获取日期与时间
```

# 路漫漫求修远兮，吾将上下而求索！