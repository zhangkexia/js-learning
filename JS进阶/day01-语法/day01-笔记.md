### 1. 作用域 
变量能够访问的范围 
#### 1.1 局部
1. 函数作用域  
函数内部声明，函数内部使用，外部无法访问  
2. 块作用域
{}包裹的代码块 
例如函数、循环体、分支等
var声明的话，是全局作用域
#### 1.2 全局
js文件内最外层  
script标签最外层  
函数内未使用声明关键字的变量  
#### 1.3 作用域链
本质是变量查找机制  
函数被执行时，优先查找当前函数作用域  
当前作用域没有，依次逐级查找父级作用域直到全局作用域  
嵌套关系的作用域串联起来形成了作用域链  
子作用域能访问父作用域，反之不可  
#### 1.4 闭包
- 垃圾回收机制  GC  
  内存分配和完成是自动完成的
  - 内存分配  
    声明变量、函数、对象时
  - 内存使用  
    读写内存，使用内存、函数  
  - 内存回收  
    使用完毕，由垃圾回收器自动回收  

  全局变量一般不会回收（关闭页面时回收）  
  一般，局部变量的值，不用了，会被自动回收掉  
  内存泄漏：无法释放、无法回收  
- 引用计数法  
  堆  
  栈  
  一个对象是否有指向它的引用，没有引用了，就回收  
  arr = null //回收数组  
  嵌套引用 相互引用，无法回收  
- 标记清除法  
  不再使用的对象，定义为无法达到的对象  
  从根部开始，无法到达，则清除  
- 闭包  
  一个函数对周围状态的引用捆绑在一起，内层函数中访问到其外层函数的作用域  
  简单理解：闭包 = 内存函数  + 外层函数的变量  
  ```js
  function outer() {
    const a = 1
    function f() {
        console.log(a) //内层函数用到了外层函数的变量  
    }
    f() // 这里直接调用，内层函数使用外部函数变量
  }
  outer()
  ```
  作用： 封闭数据，提供操作，外部也可以访问函数内部的变量  
  ```js
  function outer(){
    let i = 1
    function fn() {
        console.log(i)
    }
    return fn // return语句，返回的是一个函数，没有直接调用使用i
    // outer() 赋值给一个外部的函数，外部的函数就实现了使用i
  }
  const fun = outer()
  fun() // 外层函数使用内部函数的变量
  ```
  作用：实现数据的私有  
  ```js
  let i = 0
  function fn(){
    i++
    console.log(i)
  }
  fn()  // 调用一次，i增加一次
  fn()
  // 问题： i是全局变量，有被修改的风险  

  // 改成闭包的方式  
  function outer() {
    let i = 0
    function fn(){
        i++
        console.log(i)
    }
    return fn
  }
  const fun = outer()
  fun() // 实现了可以使用局部作用域的i
  fun() // i私有，外部无法修改  
  // 为什么没有被回收？
  // fun()可以达到 fn可以达到 outer的i可以达到，所以没有被回收  
  // 闭包可能会有内存泄漏的风险  
  ```

#### 1.5 变量提升
允许变量声明之前被访问（var声明的变量）  
所有var声明的变量，提升到当前作用域的最前面  
只提升声明，不提升赋值  
```js
console.log(num + 'pcs')
var num = 10
// undefinedpcs
// 相当于
var num
console.log(num + 'pcs')
num = 10
```

### 2. 函数进阶  
- 函数提升  
  函数声明之前被调用  
  ```js
  fn()
  function fn() {
    console.log('kexia')
  }
  ```
  把函数声明提升到到当前作用域的最前面  
  只提升函数声明，不提升函数调用  
  函数表达式必须先声明和赋值，后调用  
  ```js
  bar()

  var bar = function() {
    console.log('函数表达式')
  }
  ```
- 函数参数  
  - 动态参数  
    ```js
    getSum(2, 3)
    getSum(2, 3, 5)
    // arguments获取参数 
    // arguments是个伪数组
    function getSum() {
        // console.log(arguments)
        let sum = 0
        for (let i = 0; i < arguments.length; i++) {
            sum += arguments[i]
        }
    }
    ```
  - 剩余参数  
    ```js
    // 将一个不定量的参数，放入一个数组(真数组)  
    // 取最末尾的参数
    function getSum(...arr) {
        let sum = 0
        for (let i = 0; i < arr.length; i++) {
            sum += arr[i]
        }
    }
    getSum(2, 3)
    getSum(1, 2, 3)

    function getSum2(a, b, ...arr) {
        let sum = a + b
        for (let i = 0; i < arr.length; i++) {
            sum += arr[i]
        }
    }
    getSum2(2, 3)
    getSum2(1, 2, 3)
    ```
  - 展开运算符  
    ```js 
    const arr = [1, 3, 4, 5]
    console.log(...arr) // 1 3 4 5
    // 不修改原数组
    // 合并数组
    const arr1 = [2, 3]
    const newarr = [...arr, ...arr1]

    // 求数组最大值 最小值    
    console.log(Math.max(...arr))
    console.log(Math.min(...arr))
    ```
  
- 箭头函数  
  更简短的函数写法  
  不绑定this  
  简化函数表达式  
  更适用于需要匿名函数的地方  
  - 基本语法 
    ```js
    const fn = function () {
        console.log(123)
    }
    // 箭头函数  
    const fn = () => {
        console.log(123)
    }

    const fn = (x) => {
        console.log(x)
    }

    // 只有一个形参，省略小括号
    const fn = x => {
        console.log(x)
    }

    // 只有一行代码，省略大括号
    const fn = x => console.log(x)

    // 只有一行代码，省return 
    const fn = x => x + x

    // 直接返回对象  
    const fn = uname => ({uname: 'kexia'})

    ``` 
  - 参数  
    ```js
    箭头函数没有arguments, 有剩余参数  
    const getSum = (...arr) => {
        let sum = 0
        for (i = 0; i< arr.length; i++) {
            sum += arr[i]
        }
        return sum
    }

    getSum(2, 3)
    ```
  - 箭头函数的this  
    ```js
    console.log(this) // 指向window
    function fun() {
        console.log(this) // 指向window
    }
    window.fun() // 指向window，谁调用指向谁

    const obj = {
        name: 'kexia',
        sayHi: function() {
            console.log(this) // 指向obj，谁调用指向谁
        }
    }
    obj.sayHi() // 指向obj

    // 箭头函数不会创建自己的this,从自己的作用域链的上一层沿用this
    const fn = () => {
        console.log(this) //指向window，上一层的this是指向window的
    }
    fn()

    // 对象方法
    const obj = {
        name: 'keixa',
        sayHi: () => {
            console.log(this) // 上一层作用域是window, 指向window
        }
    }
    obj.sayHi()

    const obj = {
        name: 'keixa',
        sayHi: function() {
            console.log(this) // 传统函数有this
            let i = 10
            const count = () => {
                console.log(this) // 指向上一级，obj
            }
            count() // 这里调用了
        }
    }
    obj.sayHi()

    // DOM事件回调函数不推荐使用箭头函数  

    ```

### 3. 解构赋值
- 数组结构  
  使用解构简洁语法快速为变量赋值  
  将数组元素的单元值快速批量复制给一系列的变量  
  ```js
  const arr [100, 60, 80]
  const [a, b, c] = arr
  // 立即执行函数必须要加分号  
  (function () {})();
  (function () {})();
  // 使用数组的时候
  const str = 'pink'; // 这里要加分号，否则'pink'[1, 2, 3]
  [1, 2, 3,].map(function (item) {
    console.log(item)
  })
  // 变量多，单元值少
  const [a, b, c, d] = [1, 2, 3] // d undefinde
  // 变量少，单元值多
  const [a, b, c, ...arr] = [1, 2, 3, 4, 5, 6, 7]
  // 防止传递undefined 给默认值
  const [a, b, c, d=0] = [1, 2, 3] 
  // 按需导入赋值  
  const [a, b, , d] = [1, 2, 3, 4] // d 4
  // 支持多维数组解构
  const [a, b, c] = [1, 3, [3, 4]]
  const [a, b, [c,]] = [1, 3, [3, 4]]
  ```
- 对象结构  
  解构的属性和方法  
  ```js
  const obj = {
    unmae: 'kexia',
    age: 18
  }
  const {uname, age} = obj //必须声明的变量名和属性名一样  

  // 给结构的变量改名, 旧变量名：新变量名
  const {uname：username, age} = obj 

  // 数组对象结构
  const arrobj = [{
    unmae: 'kexia',
    age: 18
  }]
  const [{uname, age}] = arrobj

  // 多级对象结构
  const mobj = {
    unmae: 'kexia',
    age: 18，
    obj2: {
        ma: 'kexia',
        fa: 'sum'
    }
  }
  const {uname, age, obj2: {ma, fa}} = mobj // 标明内存对象的名字
  // 多级数组对象
  const arrmobj = {
    uname: 'kexia',
    age: 18，
    obj2: {
        ma: 'kexia',
        fa: 'sum'
    }
  }
  const [{uname, age, obj2: {ma, fa}}] = arrmobj
  // 传递参数可以顺便解构,利用结构只用对象的一部分属性值
  function render({uname}) {
    console.log(uname)
  }
  render(arrmobj)
  ```
- forEach()
  只遍历，不返回数组，map返回一个数组    
  适合遍历数组对象  
  ```js
  被遍历的数组.forEach(function(item, index) {
    console.log(item, index)
  })
  ```
- 筛选数组filter
  ```js
  const arr = [10, 20, 30, 40]
  const newarr = arr.filter(function(item, index) {
    return item >= 20
  })
  // 箭头函数写法  
  const newarr = arr.filter(item => item >= 20)
  // 类似map
  ```