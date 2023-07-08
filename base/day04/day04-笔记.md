### 1. 函数
#### 1.1 为什么需要函数  
抽取 封装   
一次定义，多次调用  
代码块，执行特定功能  
#### 1.2 函数使用  
先声明,再调用  
```js
function funName() {
    console.log('kexia')
}

funName()
// 函数命名，前缀尽量为动词  
```
#### 1.3 函数传参  
```js
function getSquare(num1) {
    document.write(num1 * num1)
}
getSquage(8)

// 形参
function getSum(num1, num2) {
    document.write(num1 + num2)
}
getSum(3, 4) //实参

// 参数具备默认值的函数声明
function getSum2(num1 = 0, num2 = 0) {
    document.write(num1 + num2)
}
getSum(3, 4) //实参
```
#### 1.4 函数返回值  
return 关键字  
结束函数  
没有return， 默认返回值为undefinded  
```js
function getSum(num1, num2) {
    return num1 + num2
}

sum = getSum(1, 2)
```
#### 1.5 作用域  
变量是有作用域的  
函数内部的变量，仅在函数内部有效  
for循环语句中的变量()循环定义里的变量  
局部作用域/局部变量  
- 函数内部let的变量  
- for语句块里let的变量  
- 函数内部的形参  

全局作用域  
- script内直属的变量  
- 如果函数内部没有声明，直接赋值的变量是全局变量，注意规避  

访问原则  
先找局部，局部没有，则找全局  
#### 1.6 匿名函数  
```js
function() {

}
// 无法直接使用
// 1. 函数表达式，赋值给变量
let fn = function() {

}
fn() 
// 匿名函数调用，与具名函数的区别
// 具名函数，调用可以在任何位置
// 匿名函数，只有在赋值给变量后，通过变量名调用
btn.onClick = function() {
    
}

// 2. 立即执行函数(要用分号结束)  
// 避免变量污染
(function(){
    console.log('kexia')
})();  
(function(x, y){
    console.log(x + y)
})(1, 2); 
// 最后一个小括号是函数调用。
// 另一种写法
(function() {} ())
```
#### 1.7 逻辑中断  
```js
function fn(x, y) {
    x = x || 0
    y = y || 0
    return (x + y)
}
fn()
```
逻辑与，执行到假，后面就不执行了，如果都是真值，返回最后一个真值  
逻辑或，执行到真，后面就不执行了，返回第一个真值  

#### 1.8 转换为boolean  
```js
Boolean('kexia') // true
Boolean('') // false
Boolean(undefined) // false
Boolean(null) // false
Boolean(0) // false
Boolean(NaN) // false
```