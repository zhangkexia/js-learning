### 1. 介绍
#### 1.1 是什么
#### 功能
- 运行在客户端（浏览器或者nodejs环境？）    
  编程语言，不是标记语言  
- 表单验证 
- 网页特效  
- 数据交互
- 服务端编程 node.js  
##### 组成
- ECMAScript  
核心语法知识
- WEB APIs
  - DOM  
  文档对象模型  
  操作文档，比如对页面元素进行移动、大小、添加删除等操作
  - BOM  
  浏览器对象模型  
  操作浏览器，比如页面弹窗，检测窗口宽度、存储数据到浏览器等。  
#### 1.2 书写位置  
##### 1. 内部javascript  
写在html页面，body内部。  </body>上面，考虑页面加载顺序。
##### 2. 外部js
通过script标签，引入（注意路径），与第一种方式区别就是js语句编成src路径引入。  
```html
<script src='path/to/your.js'> </script>
```
##### 3. 内联js
写在标签内部
```html
<button onclick=''></button>
```
#### 1.3 js注释及其他  
单行 // ctrl+/  
多行 /* */ shift + alt + a  
结束符 ; 写不写分号都行，推荐不加  
#### 1.4 输入输出语法  
- 输出语法1   
```javascript
document.write('kexia')
// 输入到body
```  
- 输出语法2  
```javascript
console.log('keixa')
// 输出到控制台
```
- 输入语法3  
```javascript
alert('kexia')
```
- 输入语法  
```javascript
prompt('please input')
```
- 执行顺序
alert prompt 优先于页面渲染执行  
其余顺序执行 
#### 1.5 字面量 
数字字面量  
字符串字面量  
数组字面量  

### 2. 变量  
#### 2.1 变量是什么  
存储数据 
不是数据本身，而是存储数据的容器  

#### 2.2 变量使用  
- 声明（或者定义）  
```javascript
let {var_name}
// 关键字let
```
忘记var, var是以前版本的关键字  
- 赋值  
```javascript
let age
age = 18
// 18是字面量，数字字面量
```
- 声明的同时直接赋值  
```js
let age = 18 
// 变量的初始化
```
- 更新变量  
```js
let age = 18
age = 19
// 更新变量
let age = 19
// 不能重新声明
```
- 同时声明多个变量  
```js
let age = 18, uname = 'kexia'
console.log(age, uname)
// 不提倡同时声明多个变量
```
#### 2.4 变量的本质 
内存，计算机中存储数据的地方  
变量本质：是程序在内存中申请的一块用来存放数据的小空间  
内存地址跟变量名  
#### 2.5 变量命名规则和规范  
- 规则，必须要遵守的  
数字、字母、$、下划线，开头不能是数字；  
不能使用关键字  
严格区分大小写
- 规范，建议  
起名要有意义  
小驼峰写法，第一个单词首字母小写，后面的单词首字母大写。
#### 2.6 let var区别  
- 旧版本使用var关键字声明变量  
- 可以先使用再声明（不合理）  
- 可以重复声明（不合理）  
- 其他问题：变量提升 全局变量 没有块级作用域
#### 2.7 数组  
一组数据存储在单个变量名下  
```js
let arr = []
arr = [1, 2, 3]
// 数组字面量
let arr2 = [3, 4, 5]
// 使用整个数组
console.log(arr2)
// 使用单个元素
console.log(arr2[0])
// 数组是顺序保存
// 使用索引使用
// 元素可以任意类型
```

### 3. 常量  
本质也是一个变量（这个变量需要具备不变性）  
用const 声明  
```js
// 一般使用大写  
// 常量声明的时候必须赋值
const PI = 3.14
console.log(PI)
PI = 3.1415 
// 这个赋值是不行的
```

### 4. 数据类型
两大类
- 基本数据类型
  - number
  - string
  - boolean
  - undefined
  - null
- 引用数据类型/复杂数据类型
  - object
- number  
  松散语言  
  整数 小数 负数等等不作区分  
  弱数据类型的语言  
  - 只有赋值了，才知道数据类型  

  强数据类型的语言   
  - int float等等严格区分  
  ```js
  console.log(1 + 1)
  console.log(1 - 1)
  console.log(1 * 1)
  console.log(1 / 1)
  console.log(1 % 1) // 求余
  // 搞清楚算术运算符优先级
  ```
  NaN
    - not a number  
    - 计算错误的输入  
    - 粘性的：任何对NaN的操作都返回NaN  
  
- string  
  单引号、双引号包裹的数据都是字符串  
  单引号、双引号本质上没有区别，推荐使用单引号  
  还有反引号 
  ```js
  let str = 'kexia'
  let str = "kexia"
  let str = `kexia`
  ```
  单引号里可以用双引号，要是单引号，需要转义（双引号同理）  
  字符串拼接  
  使用 + 
  ```js
  let str1 = 'kexia'
  let str2 = 'yue'
  let str3 = str1 + str2
  console.log(str3)
  let age = 18
  // 字符串和数字拼接，是字符串，强制类型转换
  document.write('i am' + age + 'years old')
  ```
  模板字符串  
  ```js
  // 反引号
  // ${}引用变量  
  let age = 18
  document.write(`i am ${age} years old`)
  ```



