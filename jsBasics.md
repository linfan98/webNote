# JS

## JS基本知识

### 推荐书籍

1. JavaScript高级程序设计（第三版）
2. ES6标准入门（电子书网址：[ECMAScript6入门](http://www.es6.ruanyifeng.com)）
3. 你不知道的JavaScript(上中下)
4. JavaScript权威指南（俗称犀牛书，不推荐学习看）

### js效果

+ **人机交互**
+ **动画效果**
+ **数据绑定**
+ **写后台**
+ **...**

### JS做客户端语言

> 按照相关的JS语法，去操作页面中的元素，有时还要操作浏览器里面的一些功能

- ECMAScript3/5/6...：JS的语法规范（变量、数据类型、操作语句等等）

- DOM（document object model）：文档对象模型，提供一些JS的属性和方法，用来操作页面中的DOM元素
- BOM（browser object model）：浏览器对象模型，提供一些JS的属性和方法，用来操作浏览器的



## js变量

### JS中的变量 variable

多种定义方式：***var / let / const / function / import / class***    

***严谨的命名规范：区分大小写 / 驼峰命名 / 关键字保留字***  
> 变量：可变的量，在编程语言中，变量其实就是一个名字，用来存储和代表不同值的东西

```javascript
//ES3
var a = 12;
a = 13;
console.log(a); //=>输出的是a代表的值13

//ES6
let b = 100;
b = 200;

const c = 1000;
c = 2000; //=>报错：CONST创建的变量，存储的值不能被修改（可以理解为叫做常量）

//创建函数也相当于在创建变量
function fn(){}
//创建类也相当于创建变量
class A{}
//ES6的模块导入也可以创建变量
import B from './B.js';

//Symbol创建唯一值
let n = Symbol(100);
let m = Symbol(100);
n == m //=>false
```

### JS中的命名规范
> 官方规范：必须按照这样来写，不这样就不行

> 约定熟成的规范：开发者共同认为的规范，为了提高开发效率，与团队共同开发。

- 严格区分大小写

```javascript
let Test=100;
console.log(test);//=>无法输出，因为第一个字母小写了
```

- 使用数字、字母、下划线、$，数字不能作为开头

```javascript
let $box; //=>一般用JQ获取的以$开头
let _box; //=>一般公共变量都是_开头
let 1box; //=>不可以，但是可以写box1
```

- 使用驼峰命名法：首字母小写，其余每一个有意义单词的首字母都要大写（命名尽可能语义化明显，使用英文单词）

```javascript
let studentInformation;
let studentInfo;
let stuInfo;
//常用的缩写：add/insert/create/new（新增）、update（修改）、delete/del/remove/rm（删除）、sel/select/query/get（查询）、info（信息）...

//不正确的写法
//=> 不会报错，但很恶心
let xueshengInfo;
let xueshengxinxi;//=> 比较low，但不会挨打
let xsxx;//=> 会被打
let a;//=> 不推荐无语意的变量
```

- 不能使用关键字和保留字

```javascript
// 当下有特殊含义的是关键字，未来可能会成为关键字的叫做保留字(？)
var let const function ...;
var var1 = 10;//=>可以，但不推荐
var var = 10; //=>肯定不行的
```

//=>代码强迫症（代码洁癖）：良好的编程习惯、极客精神
> 不加空格难受、不加分号难受、不对齐难受...

> 免测产品：不需要测试的项目。必备技能：从细节做起。

## JS中常用的数据类型

### 分类

- 基本数据类型
  - 数字number
    常规数字和NaN
  - 字符串string
    所有用单引号、双引号、反引号（撇）包起来的都是字符串
  - 布尔boolean
    true/false
  - 空对象指针null
  - 未定义undefined（js独有的）
- 引用数据类型
  - 对象数据类型object
    - {} 普通对象
    - [] 数组对象
    - /^[+-]?(\d|([1-9]\d+))(\.\d+)?$/ 正则对象
      
      > 检验是否是有效数字：/^[+-]?(\d|([1-9]\d+))(\.\d+)?$/
    - Math数学函数对象
    - 日期对象
    - ...
  - 函数数据类型function

### number数字类型

> 包含：常规数字、NaN
```javascript
  var a = 1;
  var b = 1.2;
```

#### NaN

> not a number：不是一个数，但它率属于数字类型
```javascript
  // console.log();//=>在控制台输出
  // ==：比较符
  console.log(1 == 2);//=>false
  console.log('AA' == NaN);//=>false
  console.log(1 == NaN);//=>false
  console.log(NaN == NaN);//=>false
```

NaN和任何值（包括自己）都不相等：NaN!=NaN，所以我们不能用相等的方式判断是否为有效数字

#### isNaN

> 检测一个值是否为非有效数字，如果**不是有效数字返回TRUE**，反之**是有效数字返回FALSE**
```javascript
  //isNaN([val])//([val]):参数描述占位符，经常在技术文档里面看到
  console.log(isNaN(10)); //=>false,是有效数字
  console.log(isNaN('AA')); //=>true,不是有效数字
  /*
   * Number('AA') => NaN
   * isNaN(NaN) => true
   */
  console.log(isNaN('10')); //=>false,是有效数字,JS自动转换了
  /*
   * Number('10') => 10
   * isNaN(10) => false
   */
  console.log(isNaN('123A')); //=>true
  console.log(isNaN('A123')); //=>true
```

在使用isNaN进行检测的时候，首先会验证检测的值是否为数字类型，如果不是，先基于Number()这个方法，把值转换为数字类型，然后再检测

#### 把其它类型值转换为数字类型

- Number([val])
  + 走的是V8内核的底层机渲染规则
- parseInt/parseFloat([val],[进制])：也是转换为数字的方法，对于字符串来说，它是从左到右依次查找有效数字字符，直到遇到非有效数字字符，停止查找（不管后面是否还有数字，都不在找了），把找到的当做数字返回
  + 走的是单独方法的规则，只能查找字符串
- ==进行比较的时候，可能要出现把其它类型值转换为数字
```javascript
  // 1. Number([val]) 
  // 把字符串转换为数字
  // 必须保证里面是有效数字，只要有一个不是，就是NaN。空字符串为数字0
  console.log(Number('12.5')); //=>12.5
  console.log(Number('12.5px')); //=>NaN
  console.log(Number('12.5.5')); //=>Nan
  console.log(Number('')); //=>0
  console.log(Number(' ')); //=>0
  // 布尔转换为数字
  console.log(Number(true)); //=>1
  console.log(Number(false)); //=>0
  console.log(isNaN(true)); //=>false,是
  console.log(isNaN(false)); //=>false,是
  // null转换为数字
  console.log(Number(null)); //=>0
  // undefined转换为数字
  console.log(Number(undefined)); //=>NaN
  // 引用数字类型
  // 先基于toString()方法转换为字符串，然后再转换为数字
  // {}/{xxx:'xxx'}.toString() => "[object Object]" => NaN
  console.log(Number({name:'xxx'})); //=>NaN
  console.log(Number({})); //=>NaN
  // [].toString() => '' => 0
  console.log(Number([])); //=>0
  // [12].toString() => '12' => 12
  console.log(Number([12])); //=>12
  // [12,13].toString() => '12,13' => NaN
  console.log(Number([12,13])); //=>NaN

  // 2. parseInt/parseFloat([val],[进制])
  let str = '12.5px';
  console.log(Number(str)); //=>NaN
  console.log(parseInt(str)); //=>12
  console.log(parseFloat(str)); //=>12.5
  console.log(parseFloat('width: 12.5px')); //=>NaN

  // 3. ==
  console.log('10' == 10); //=>true
```

##### Number与parseInt/parseFloat区别
```javascript
  console.log(Number(true)); //=>1
  console.log(parseInt(true)); //=>NaN
  /*
   * 额外提供方法实现，先转换为字符串，在进行转换
   * parseInt(true) => parseInt('true') => NaN
   */
```

### string字符串数据类型

> 所有用单引号、双引号、反引号（撇 ES6模板字符串）包起来的都是字符串
```javascript
  var str1 = 'hello';
  var str2 = "world";
  var str3 = `!!!`; //=>ES6模板字符串
```

#### 把其它类型值转换为字符串

- [val].toString()
- 字符串拼接
  + 四则运算中，除了加法可能存在字符串拼接，其他都是数学计算（加法一旦遇到字符串，则进行字符串拼接，而不是数学运算）
```javascript
  // 1. [val].toString()
  var a = 12;
  console.log(a.toString()); //=>'12'
  console.log((NaN).toString()); //=>'NaN'
  console.log((true).toString()); //=>'true'
  console.log((null).toString()); //=>报错，禁止直接调用（保护机制）
  console.log((undefined).toString()); //=>报错
  console.log(([]).toString()); //=>''
  console.log(([12]).toString()); //=>'12'
  console.log(([12,13]).toString()); //=>'12,13'
  console.log(/^$/.toString()); //=>'/^$/'
  // 特殊:普通对象.toString() => '[object Object]'
  console.log(({name: 'xxx'}).toString()); //=> '[object Object]' => Object.prototype.toString方法不是用来转换为字符串的，而是原来检测数据类型的

  // 2. 字符串拼接
  console.log('10' + 10); //=> '1010'
  console.log('10' - 10); //=> 0
  console.log('10px' - 10); //=> NaN

  // 面试题
  let a = 10 + null + true + [] + undefined + '林凡' + null + [] + 10 +false;
  /*
   * 10 + null -> 10 + 0 = 10
   * 10 + true -> 10 + 1 = 11
   * 11 + [] -> 11 + '' -> '11' + '' ='11'
   * '11' + undefined -> '11undefined'
   * 接下来一路拼接
   * '11undefined林凡null10false'
   */
  console.log(a); //=> '11undefined林凡null10false'
```

### boolean布尔数据类型
> 只有两个值 true/false
```javascript
  var b1 = true;
  var b2 = false;
```

#### 把其它类型值转换为布尔类型
> 只有 0、NaN、''、null、undefined 五个值转换为FALSE，其余都转换为TRUE（而且没有任何的特殊情况）

- Boolean([val])
- !/!!
- 条件判断
```javascript
  console.log(Boolean(0)); //=> false
  console.log(Boolean(NaN)); //=> false
  console.log(Boolean('')); //=> false
  console.log(Boolean(' ')); //=> ture
  console.log(Boolean(null)); //=> false
  console.log(Boolean(undefined)); //=> false
  console.log(Boolean([])); //=> ture
  console.log(Boolean([12])); //=> ture
  console.log(Boolean(-1)); //=> ture

  // 1个叹号——取反操作 => 先转为布尔类型，再取反
  // 2个叹号——转换为布尔 == boolean => 逼格较高
  console.log(!1); //=>false
  console.log(!!1); //=>true

  // 条件判断
  if (1) {
    /*
      如果条件只是一个值，先转换为布尔值
    */
    console.log("哈哈"); //=> 哈哈
  }
  if ('3px' + 3) {
    // => '3px3' => true
    console.log("哈哈"); //=> 哈哈
  }
  if ('3px' - 3) {
    // => '3px' => NaN, NaN - 3 = NaN => flase
    console.log("哈哈"); //=> 不输出
  }
  
```

### null / undefined

> null和undefined都代表的是没有

- null：意料之中（**一般都是开始不知道值，我们手动先设置为null，后期再给予赋值操作**）

```javascript
let num = null; //=>let num = 0;  
// 一般最好用null作为初始的空值，因为零不是空值，他在栈内存中有自己的存储空间（占了位置）
// 0会消耗一点点点点点点性能，null不消耗性能
...
num = 12;
```

- undefined：意料之外（**不是我能决定的**）

```javascript
let num; //=>创建一个变量没有赋值，默认值是undefined
...
num = 12;
```

### object对象数据类型-普通对象

> {[key]:[value],...} 任何一个对象都是由零到多组键值对（属性名：属性值）组成的（并且属性名不能重复）

```javascript
// 属性名都是字符串或者数字格式的
 let person = {
   name: '易烊千玺',
   // 'name': '易烊千玺'
   age: 40,
   height: '185cm',
   weight: '80kg',
   1:100 // 假设第一科成绩为100分
 };

//  设置&修改属性名，属性值
 person.gf = 'pander';
 person.name = '李易峰',
 person.gf['gf']; //=> pander
 person.name; //=> 李易峰

//  获取属性名对应的属性值
 person.name; //=> 易烊千玺
 person['age']; //=> 40
//  当前属性值不存在，输出undefined
 person.sex; //=> undefined
 person[1]; //=> 100
//  如果属性名是数字，则不能使用“.”的方式调用属性值
 person.1; //=> SyntaxError,语法错误

// 删除属性名，属性值
  // 真删除 => 把属性彻底删除
delete person[1]; //=> 1彻底消失
  // 假删除 => 属性值删除，属性还在
 person.weight = null; //=> null
 person.weight = undefined; //=> undefined，不推荐

```
> ### 数组是特殊的对象数据类型
```javascript
/*
 * 数组是特殊的对象数据类型
 *   1. 我们中括号中设置的是属性值，属性名默认为0~n，每一个数字代表每一项的位置，这个数字叫做“索引” => 从0开始，连续递增，代表每一项位置的数字属性名
 *   2. 默认属性length，存储数组的长度
 */
  let  ary = [12,'哈哈',true,13];
  console.log(ary); //=> (4)[12,'哈哈',true,13]
  ary.length; //=> 4
  ary['lenght']; //=> 4
  ary[1]; //=> 哈哈
  ary[ary.lenght-1]; //=> 获取数组最后一项，13
  ary[ary.lenght]; //=> 内容溢出，报错
  ary[ary.lenght] = 100; //=> 向数组末尾增加内容
```

## 面试题
```javascript
let a = 12;
let b = a;
b = 13;
console.log(a);

let n = {name:'林凡'};
let m = n;
m.name = 'code';
console.log(n.name);

```

## 数据类型之间的区别

> ## __JS的底层学习,没有一张图解决不了的__

### 浏览器执行JS代码
> 从电脑内存中分配出一块内存，用来执行代码（栈内存：Stack）

> 浏览器分配一个主线程，用来自上而下执行JS代码

### 栈内存
> 变量存储空间

> 值存储空间

> 代码执行空间：主线程

```javascript
let a = 2;
// 1.创建变量a，放到当前栈内存变量存储区域中
// 2.创建一个值12，把它存储到栈内存的值区域中（简单的基本类型值，复杂的引用类型不是）
// 3.等号为赋值，其实赋值是让变量和值相互关联的过程

let b = a;
// 和上面大致相同，步骤2省略

b = 13;
// 创建一个值13
// 让变量b与值13产生关联

console.log(a); //=> 12
```
#### 简单值赋值过程
> 创建变量a，放到当前栈内存变量存储区域中

> 创建一个值12，把它存储到栈内存的值区域中（简单的基本类型值，复杂的引用类型不是）

> 等号为赋值，其实赋值是让变量和值相互关联的过程

### 堆内存


#### 复杂值（变量和值不是一一对应的）

> 在内存中新分配出一块内存，用来存储引用类型的值（堆内存：heap ） 内存有16机制地址

> 把对象中的属性名：属性值（键值对）依次存储到对内存中

> 把堆内存地址和变量关联起来

```javascript
let n = {name:'林凡'};
// 1.分配堆内存
// 2.存储对象中的键值对
// 3.在栈内存中创建变量
// 4.在栈内存中创建堆内存的地址
// 5.将对象变量与堆地址关联

let m = n;
// 1.在栈内存中创建变量
// 2.寻找栈内存的值
// 关联与n相对应的堆地址

m.name = 'code';
// 修改堆内存中的值，但指向的堆地址不变

console.log(n.name); //=> code
```

#### 基本数据类型与引用数据类型区别

| 基本数据类型 | 引用数据类型 |
| ---- | ---- |
|按值操作|操作堆内存的地址|
|值类型|引用类型|

```javascript
let n = [10,20];
// 开辟堆内存，地址为AAAFFF000
// 在栈内存创建变量n
// 在栈内存创建堆地址
// 关联堆地址
// 在堆内存创建值（多个）

let m = n;
// 创建变量m
// 关联堆地址AAAFFF000

let x = m;
// 创建变量x
// 关联堆地址AAAFFF000

m[0] = 100;
// 修改堆内存AAAFFF000里面的x

x = [30,40];
// x已经指定堆内存，只能修改
// 创建新堆内存地址bbbfff000
// x重新关联新堆地址bbbfff000
// 新堆内存创建值

x[0] = 200;
// 修改堆地址bbbfff000的值

m = x;
// m指向堆地址bbbfff000

m[1] = 300;
// 修改堆地址bbbfff000的值

n[2] = 400;
// 在堆地址aaafff000添加新的键值对

consloe.olg(n,m,x);
// n => [100,20,400]
// m,x => [200,300]
```
## 名企面试题

```javascript
let a = {
  n: 1
};
// 在栈内存创建变量a
// 创建堆内存，地址为aaFF00，值为 n:1
// 堆内存创建键值对 n:1
// 在栈内存中关联变量a和堆地址aaFF00
let b = a;
// 在栈内存创建变量b
// 在栈内存中关联变量b与堆地址aaFF00
a.x = a = {
  n: 2
} ;
// 重新创建堆地址bbff00,值为 n:2
// a.x => 在堆地址aaff00创建新的键值对 x:bbff00
// a与bbff00关联

/* 
  此时 
  a = {n:2},
  b = {
    n:1,
    x:{
      n:2
    }
}
*/
console.log(a.x); //=> undefined
consloe.log(b); //=> b = { n:1, x:{ n:2 }}
```
```javascript
let a = {n:1};
let b = a;
a.x = b;
// 会造成内存无限溢
```

## JS的数据类型检测

> typeof [val] => 用来检测数据类型的运算符

> instanceof => 用来检测当前实例是否隶属于某个类

> constructor => 基于构造函数检测数据类型(样式基于类的方式)

> Object.prototype.toString.call() => 检测数据类型最好的办法

```javascript
// 基于typeof检测出来的是字符串,字符串中包含对应的类型
// 局限性:
  // typeof null => Object,但null不是对象
  // 基于typeof无法细分出当前值是普通对象还是数组对象,因为只要是对象类型,返回结果都是"Object"
  console.log(typeof 1); //=> number
  let a = NaN;
  console.log(typeof a); //=> number
  console.log(typeof function () {}); //=> function

  console.log(typeof typeof typeof []); //=>从右向左计算
// typeof [] => 'object'
// typeof 'object' => 'string'
// typeof 'string' => 'string'
// 综上，输出结果为'string'
```

> typeof只要两个及两个以上同时检测，最后结果必然是字符串类型

## JS的常见操作语句：判断、循环

### 判断

> 条件成立做什么？不成立做什么？

#### if/else if/else

> if/else

```javascript
// 语法
  if (条件) {
    // 条件成立执行语句
    // 条件可以多样性：等于、大于、小于的比较；一个值或者取反等 => 最后都是转换为布尔值（TRUE or FALSE）
  } else if (条件2) {
    // 条件成立执行语句
  }
  ...
  else {
    // 以上条件均不满足执行的语句
  }
```

```javascript
  let a = 10;
  if (a <= 0) {
    console.log("哈哈");
  } else if (a > 0 && a < 10) {
    // A && B:A和B都成立才为TRUE
    // A || B:A或B其中一个成立就为TRUE
    console.log("呵呵");
  } else if (a == 10) {
    // a = 10 => 赋值操作，恒成立
    console.log("嘿嘿");
  } else {
    consloe.log("嘻嘻");
  }
  //=> 输出 “嘿嘿”
```

#### 三元运算符

> 简单if/else的特殊处理方式

```javascript
  // 语法：
  // 条件?执行语句1(成立):执行语句2(不成立);
  // 应用场景：简单的if/else语句处理，在工作中尽可能不使用，增加代码可阅读性
  // 1. 如果处理的事情比较多，用括号括起来，每一件用逗号分隔
  // 2. 如果不处理事情，可以用null或者undefined占位
  let a = 10;
  if (a < 10 ) {
    console.log('a < 10');
  } else {
    console.log('a < 10');
  }
  // 上面的代码可以简化为下面的代码：
  a < 10 ? console.log('a < 10') : console.log('a < 10');
```

```javascript
  let a = 10;
  if (a > 0 && a < 20) {
    a++; //=> a += 1 a = a + 1 => 自身累加
    console.log(a);
  }
  a > 0 && a < 20 ? (a++, console.log(a)) : null;
```

```javascript
// 求下面if/else的三元运算符
let a = 10;
if (a > 0) {
  if (a < 10) {
    a++;
  } else {
    a--;
  }
  // 1. a < 10 ? a++ : a--;
} else {
  if (a > -10) {
    a += 2;
  }
  // 2. a > -10 ? a += 2 : null;
}
// 3. 三元表达式
a > 0 ? ( a < 10 ? a++ : a--) : (a > -10 ? a += 2 : null);

```

#### switch case

> 一个变量在不同值情况下的不同操作

> 1. 每一个CASE情况后面都最好加上BREAK

> 2. default等价于else，以上都不成立干的事情

> 3. 每一个case用的都是'===' => 绝对等号

```javascript
//  语法
switch (变量) {
  case 成立的值1:
    // 执行语句
    break;
  case 成立的值2:
    // 执行语句
    break;
  ...
  default:
   // 都不成立的执行语句
}
let a = 10;
if (a == 1) {
  console.log(1);
} else if (a == 5) {
  console.log(5);
} else if (a == 10) {
  console.log(10);
} else {
  console.log(null);
}
// switch语法
let a = 10;
switch (a) {
  case 1:
    console.log(1);
    break;
  case 5:
    console.log(5);
    break;
  case 10:
    console.log(10);
    break;
  default:
    console.log(null);
}
```

> case后面不加break

```javascript
  let a = 1;
  switch (a) {
    case 1:
      a++;
    case 5:
      a += 2;
      break;
    default:
      a--;
  }
  console.log(a); //=> 4
  // case 1 条件成立，但因为没有break，继续执行了case 5 部分的代码，无论条件是否成立，都执行，直到找到break为止。
```

> case不会主动将字符串转换为数字,但if/else会

```javascript
let a = '5';
  switch (a) {
      case 1:
        console.log("嘻嘻");
        break;
      case 5:
        console.log("哈哈");
        break;
      default:
        console.log("呵呵");
    } //=> "呵呵"

  if (a == 1) {
    console.log("嘻嘻");
  } else if (a == 5) {
    console.log("哈哈");
  } else {
    console.log("呵呵");
  } //=> 哈哈
```

> __编程开发人员应当具备探索尝试之心，试一试就不会怀疑了__

#### == VS ===

> ==： 相等 =》左右两边数据类型不同，默认先转换为相同的，再开始比较

> ===： 绝对相等 =》如果类型不一样，肯定不相等

```javascript
  console.log('5' == 5); //=> true
  console.log('5' === 5); //=> false
```

> 业务逻辑中，建议使用绝对相等，保证业务的严谨性

### 循环

> 重复做某件事情

```javascript
  // 1. for循环
  // 2. for in循环
  // 3. for of循环（ES6新增）
  // 4.while
  // 5.do while
```

#### for循环

```JavaScript
// 1.创建循环初始值
// 2.设置（验证）循环执行的条件
// 3.条件成立自行循环体中的内容
// 4.当前循环结束，执行步长累加操作
```

```JavaScript
for (var i = 0;i < 5;i++) {
  concole.log(i); //=> 1,2,3,4 
}
console.log(i); //=> 5

for (var n = 10; n > 4;i -= 2) {
  if (n < 7) {
    n++;
  } else {
    n--;
  }
}
console.log(n); //=> 4

```

#### 循环中的关键词

```javascript
  // continue:结束当前这轮循环 => continue后面的代码不再执行，继续执行下一步循环
  // break:强制结束整个循环 => break后面的代码不再执行，跳出循环体，整个循环直接结束
```
```javascript
  for (i = 0;i < 10;i++) {
    if (i >= 2) {
      i += 2;
      continue;
    }
    if(i >= 6) {
      i--;
      break;
    }
    i++;
    console.log(i); 
  }
  console.log(i); 
  // 1,11,共输出2次
```





## JS操作DOM

> 传统基于DOM实现业务需求

```javascript
// 1. 想操作谁就绑定谁
// 2. 给某元素绑定响应事件
// 3. 在事件触发的时候修改元素的样式

// 语法：
  // document.getELementById() => 在整个文档中，通过ID获取当前元素对象
  // 元素对象.onxxx=function(){} => 事件绑定，xxx时间类型（click、mouseover、mousedown、keydowm...）
    // 操作的是元素的行内样式
  // 元素.style.xxx => 获取某一个元素的样式
    // 如果我们没有在行内样式上面写样式，在JS中基于元素.style.xxx的方式是无法获取到样式的。
```

```javascript
        let box = document.getElementById('box');
        let detail = document.getElementById('detail');

        box.onclick=function(){
            // 获取原有的显示的样式
            console.log(detail.style.display);
            if (detail.style.display == 'none'){
                detail.style.display = 'block';
                box.style.borderBottomColor = '#fff';
            }else if (detail.style.display == 'block') {
                detail.style.display = 'none';
                box.style.borderBottomColor = 'lightcoral';
            }
            
        };
```

> 如果是点击实现显示，不需要JS也可以实现，可以基于:target实现手风琴效果
