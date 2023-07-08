### 1. 对象  
#### 1.1 什么是对象  
新的数据类型  
kv 类型  
无序的数据集合  
事物的抽象  
```js
let obj = {
    uname: 'kexia',
    age: 18,
    gender: 'male'
}
```
#### 1.2 对象使用  
声明对象  
对象有属性和方法  
- 属性，一般是名词  
- 方法，一般是动词  
```js
let obj = {}
let obj = new Object()
let 对象名 = {
    属性名: 属性值,
    方法名: 函数
}
// 通常情况，属性名、方法名的引号都是省略的。
// 查
let obj = {
    uname: 'kexia',
    age: 18,
    gender: 'male'
}
console.log(obj.uname) // 方式1
console.log(obj['uname']) // 方式2
// 改
obj.name = 'yue' // 赋值的方式
// 增
obj.addr = 'xianggang' // 赋值的方法
// 删
delete obj.uname
// 方法
let person = {
    uame: 'kexia',
    sing: function() {
        console.log('keixa')
    }
}
// 方法调用 
obj.sing()
document.write()
```
#### 1.3 遍历对象  
```js
let person = {
    uame: 'kexia',
    sing: function() {
        console.log('keixa')
    }
}
// 无序的键值对
// 按key遍历
// k是'uname',带引号的，不能直接obj.k
for (let k in obj) {
    console.log(obj[k])
}

// for in可以遍历数组，k是string型，一般不使用这种方式遍历数组。
arr = ['kexia', 'yue']
for (let k in arr) {
    console.log(arr[k])
}
```
#### 1.4 内置对象  
js内部提供的，不用自己开发  
```js
document.write()
console.log()
Math.PI
Math.abs()
Math.random() //返回0-1，包括0，不包括1
Math.ceil()
Math.floor()
Math.round() // 四舍五入
Math.max()
Math.min()
Math.pow()
// 等等
// 生成0-10的随机数，包含10
Math.foor((10 + 1) * Math.random())
// 生成5-10的随机数 0-5 + 5
Math.foor((5 + 1) * Math.random()) +5
// 生成N-M 
Math.foor((M - N + 1) * Math.random()) + N

// 随机显示数组元素
let arr = ['kexia', 'yue', 'zhang']
let index = Math.foor((arr.length) * Math.random())
console.log(arr[index])
// 随机显示，不重复显示
let arr = ['kexia', 'yue', 'zhang']
let index = Math.foor((arr.length) * Math.random())
console.log(arr[index])
arr.splice(index, 1) // 删除已经抽到的元素
```

###  2. 扩展  
#### 2.1 第一部分  
- 关键字  
- 保留字  
- 标识符
- 表达式  
- 语句
#### 2.2 基本数据类型和引用数据类型  
- 值类型  
存的值，直接在栈里    
栈    
- 引用类型  
存的地址 
地址放栈里，值放到堆里  
堆  
- 示例  
```js
let num1 = 10
let num2 = num1 // 值赋值
num1 = 20
console.log(num1) // 10
// num1的存储空间是独立的（新开辟的），存储的值在栈里
// num2的存储空间是独立的（新开辟的），存储的值在栈里，改变num2，num1不受影响

let obj1 = {
    age: 18
}

let obj2 = obj1 // 地址赋值
obj2.age = 20
console.log(obj1.age) // 20
// obj1 在栈里有个空间，这块空间的值是一个地址
// obj2 在栈里也有个空间，这块空间的值也是一个地址，跟obj1的地址的值是一样的（赋值语句）
// 改变obj2的age的值（age的值存在堆里的），堆里的值变了，obj1 obj2指向的地址都是一个

```

