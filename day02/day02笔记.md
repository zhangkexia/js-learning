### 1. 运算符
#### 1.1 赋值运算符  
使用赋值运算符简化代码  
```js
let num = 1
num = num + 1
num += 1
// 简化的写法
```

#### 1.2 一元运算符  
正负号  
自增自减  
```js
let num = 0
num++
++num
let num2 = 10
num--
--num
// 前置自增和后置自增，单独使用没有区别
// 如果参与运算，则有区别
let i = 1
console.log(++i + 1)
// 3 先自增，然后参与运算
console.log(i++ + 1)
// 2 先参与运算，后自增
// 一般开发中，单独使用
```

#### 1.3 比较运算符  
< > >= <=  
== 判断两个值是不是相等  
=== 判断类型和值是不是都相等  
!== 不等于  
比较结果是boolean型，true or false  
字符串比较，是比较字符的ASCII码  
#### 1.4 逻辑运算符  
与或非 && || ！  
多重条件判断  
```js
3 < 4 && 3 > 5
// true && false
3 < 4 || 3 > 5
// true || false
!(3 < 5)
// !true
```
#### 1.5 运算符优先级  
按优先级排序 
1. ()  
2. 一元运算符
3. 算数运算符 先* / % 再+ -  
4. 关系运算符  
5. 相等运算符  
6. 逻辑运算符 先&& 后 || 
7. 赋值运算符  
8. 逗号运算符  
### 2. 语句  
#### 2.1 表达式和语句  
表达式是可以被求值的代码  
语句是一段可以被执行的代码， 语句不一定有值，例如alert() prompt() for break等  

#### 2.2 分支语句  
- 三大流程控制语句  
  顺序结构  
  分支结构  
  循环结构  
- 分支语句  
  if  
  ```js 
  // 单分支  
  // 除了0，其余数字都是真
  // 除了空字符串，其余字符串都是真
  if (条件(boolean值)) {

  }
  // 双分支  
  if () {

  } else {

  }
  // 多分支 多个else if
  if () {

  } else if {

  } else if {

  } else {

  }
  ```
  三元运算符  
  ```js
  // 条件 ? 满足条件执行的代码 ： 不满足条件执行的代码
  5 > 3 ? console.log('5 大于 3') : console.log('5 不大于 3')

  let num1 = +prompt('please input a number: ')
  let num2 = +prompt('please input a number: ')
  let max = (num1 > num2 ? num1 : num2)
  // 求取两个数中的最大值
  // 数字补0操作
  console.log(num < 10 ? '0' + num : num)
  ```
  switch  
  ```js
  switch (数据) {
    case 值1：
        代码1
        break
    case 值2：
        代码2
        break
    default:
        代码n
  }
  ```
#### 2.3 循环语句  
- 断点调试  
  浏览器 F12中  
- while 循环  
    ```js
    // 语法
    while (循环条件) {
        循环体
    }

    let i = 0
    while (i < 5) {
        console.log(i)
        i++
    }
    ```
- 循环退出  
  continue  
  退出本次循环  
  break  
  退出整个循环  
