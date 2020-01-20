# Markdown

> 摘抄自[菜鸟教程](https://www.runoob.com/markdown/md-tutorial.html)

## 定义

***专业记录技术笔记的方式***

用简单的符号就可以创建：标题、段落、描述、列表、公式、表格、代码块、流程图等等样式。

后缀名: 		***.md***

## 工具

- 马克飞象（印象笔记专用）

- 有道云笔记
- VScode
- ......

## 语法

### 标题

```md
1.使用 = 和 - 标记一级和二级标题
我展示的是一级标题
=================

我展示的是二级标题
-----------------

2.使用 # 号标记
使用 # 号可表示 1-6 级标题，一级标题对应一个 # 号，二级标题对应两个 # 号，以此类推。
# 一级标题
## 二级标题
### 三级标题
#### 四级标题
##### 五级标题
###### 六级标题
```

### 创建目录

```
[TOC]
```

### 列表

#### 有序列表

有序列表使用数字并加上 . 号来表示，如：

```
1. 第一项
2. 第二项
3. 第三项
```

#### 无序列表

无序列表使用星号(*****)、加号(**+**)或是减号(**-**)作为列表标记：

```
* 第一项
* 第二项
* 第三项

+ 第一项
+ 第二项
+ 第三项


- 第一项
- 第二项
- 第三项
```

#### 列表嵌套

列表嵌套只需在子列表中的选项添加四个空格即可

```
1. 第一项：
    - 第一项嵌套的第一个元素
    - 第一项嵌套的第二个元素
2. 第二项：
    - 第二项嵌套的第一个元素
    - 第二项嵌套的第二个元素
```

### 区块

#### 基础语法

Markdown 区块引用是在段落开头使用 **>** 符号 ，然后后面紧跟一个**空格**符号：

```
> 区块引用
> 林凡code
> 学习很苦，坚持很酷
```

另外区块是可以嵌套的，一个 **>** 符号是最外层，两个 **>** 符号是第一层嵌套，以此类推：

```
> 最外层
> > 第一层嵌套
> > > 第二层嵌套
```

#### 区块中使用列表

区块中使用列表实例如下：

```
> 区块中使用列表
> 1. 第一项
> 2. 第二项
> + 第一项
> + 第二项
> + 第三项
```

#### 列表中使用区块

如果要在列表项目内放进区块，那么就需要在 **>** 前添加四个空格的缩进。

区块中使用列表实例如下：

```
* 第一项
    > 菜鸟教程
    > 学的不仅是技术更是梦想
* 第二项
```

### 代码

如果是段落上的一个函数或片段的代码可以用反引号把它包起来（**`**），例如：

```
`printf()` 函数
```

#### 代码区块

代码区块使用 **4 个空格**或者一个**制表符（Tab 键）**。

实例如下：

```
	<?php
		echo "林凡code欢迎你！"
	?>
```

也可以用 **```** 包裹一段代码，并指定一种语言（也可以不指定）：

```
​```javascript
$(document).ready(function () {
    alert('林凡code');
});
​```
```

### 链接

#### 基本方法

```
[链接名称](链接地址)

或者

<链接地址>
```

例如：

```
这是一个链接 [林凡code](https://www.linfanppt.cn)
```

直接使用链接地址：

```
<https://www.linfanppt.cn>
```

#### 高级链接

```
链接也可以用变量来代替，文档末尾附带变量地址：
这个链接用 1 作为网址变量 [Google][1]
这个链接用 code 作为网址变量 [Runoob][code]
然后在文档的结尾为变量赋值（网址）

  [1]: http://www.google.com/
  [code]: http://www.linfanppt.cn/
```

### 图片

#### 格式

```
![alt 属性文本](图片地址)

![alt 属性文本](图片地址 "可选标题")
```

- 开头一个感叹号 !
- 接着一个方括号，里面放上图片的替代文字
- 接着一个普通括号，里面放上图片的网址，最后还可以用引号包住并加上选择性的 'title' 属性的文字。

例子：

```
![RUNOOB 图标](http://static.runoob.com/images/runoob-logo.png)

![RUNOOB 图标](http://static.runoob.com/images/runoob-logo.png "RUNOOB")
```

当然，也可以像网址那样对图片网址使用变量:

```
这个链接用 1 作为网址变量 [RUNOOB][1].
然后在文档的结尾为变量赋值（网址）

[1]: http://static.runoob.com/images/runoob-logo.png
```

Markdown 还没有办法指定图片的高度与宽度，如果你需要的话，可以使用普通的 <img> 标签。

```
<img src="http://static.runoob.com/images/runoob-logo.png" width="50%">
```

### 表格

#### 语法

Markdown 制作表格使用 **|** 来分隔不同的单元格，使用 **-** 来分隔表头和其他行。

```
|  表头   | 表头  |
|  ----  | ----  |
| 单元格  | 单元格 |
| 单元格  | 单元格 |
```

| 表头   | 表头   |
| ------ | ------ |
| 单元格 | 单元格 |
| 单元格 | 单元格 |

#### 对齐方式

- **-:** 设置内容和标题栏居右对齐。
- **:-** 设置内容和标题栏居左对齐。
- **:-:** 设置内容和标题栏居中对齐。

```
| 左对齐 | 右对齐 | 居中对齐 |
| :-----| ----: | :----: |
| 单元格 | 单元格 | 单元格 |
| 单元格 | 单元格 | 单元格 |
```
| 左对齐 | 右对齐 | 居中对齐 |
| :-----| ----: | :----: |
| 单元格 | 单元格 | 单元格 |
| 单元格 | 单元格 | 单元格 |

### 转义字符

Markdown 使用了很多特殊符号来表示特定的意义，如果需要显示特定的符号则需要使用转义字符，Markdown 使用反斜杠转义特殊字符：

```
**文本加粗** 
\*\* 正常显示星号 \*\*
```

Markdown 支持以下这些符号前面加上反斜杠来帮助插入普通的符号：

```
\   反斜线
`   反引号
*   星号
_   下划线
{}  花括号
[]  方括号
()  小括号
#   井字号
+   加号
-   减号
.   英文句点
!   感叹号
```





























































