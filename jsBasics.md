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
