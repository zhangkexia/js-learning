### 1. 深入对象  
- 创建对象三种方式  
  ```js
  // method 1
  const obj = {

  }

  // method 2
  const obj = new Object()

  // method 3
  // 使用构造函数创建变量
  ``
- 构造函数  
特殊的函数，用来初始化对象  
约定：首字母大写、只能由new操作符来执行
  ```js
  // 不同对象的公共属性，抽取到一个对象上（构造函数）
  function Pig(name, age, gender) {
    this.name = name
    this.age = age
    this.gender = gener
  }
  // 创建对象(快速创建多个类似的对象) 实例化，例如new Date() 也是实例化函数
  const peiqi = new Pig('peiqi', 12, 'f')
  // 实例化执行过程
  // 1. 创建新的空对象
  // 2. 构造函数this指向新对象
  // 3. 执行构造函数代码，修改this,添加新的属性
  // 4. 返回新对象
  ```
- 实例成员和静态成员  
  ```js
  // 通过构造函数创建的对象是实例对象
  // 实例对象的属性和方法是实例成员
  // 创建的不同对象，彼此独立，互不影响
  peiqi.name = 'peiqi'
  peiqi.sayHi = () => {
    console.log('hi')
  }

  // 构造函数的属性和方法是静态成员
  Pig.height = 120
  ```
  
### 2. 内置构造函数  
```js
// 简单数据类型str number也有数据方法
const str = 'kexia'
// 内置封装为引用数据类型
const str = String('kexia')
```
- Object
- String
- Array
- Number
- RegExp
- Date
```js
// 3个常用静态方法,Object  
Object.keys(obj)  //获取所有的属性名,返回数组
Object.values(obj)  //获取所有的属性值,返回数组
Object.assign(dst, src) // 拷贝
Object.assign(dst, {name: 'kexia'}) // 追加属性
```
```js
// 数组核心方法
forEach()
filter()
map()
reduce() // 返回累计处理的结果  
arr.reduce(function(){}, 起始值)
arr.reduce(function(上一次值， 当前值){}, 初始值)

const arr = [1, 5, 8]
const total = arr.reduce(function (prev, current) {
    return prev + current
})

const total = arr.reduce(function (prev, current) {
    return prev + current
}, 10)

// 如果没有初始值，则第一个prev值以数组的第一个元素的值为准
// 每一次循环，把返回值作为下一次循环的prev值
// 如果有起始值，则起始值就是第一个prev值

// 数组的实例方法
// join
// find
// every
// some

const arr = [1, 2, 3]
arr.find((item) => item === 2) = 2 // 返回找到的第一个值,参数是回调函数

const arr = [
    {
    name: 'kexia',
    gener: 'm'
    }
]
const kexia = arr.find((item) => item.name === 'kexia') // 返回符合要求的数组元素（是一个对象）

// 静态方法,伪数组转为真数组
真数组 = Array.from(伪数组)
```
```js
// 字符串常见方法
// 实例方法
length
split()
substring()
startswith()
includes()
```
