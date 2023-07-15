### 1. 日期对象  
#### 1.1 实例化
```js
// new关键字 实例化
const date = new Date()
const date1 = new Date('2023-5-6')
const date2 = new Date('2023-5-6 08:30:00')
console.log(date1)
```
#### 1.2 日期对象方法
```js
getFullYear()
getMonth()
getDate()
getDay()
getHours()
getMinutes()
getSeconds()
```
#### 1.3 时间戳
```js
// 1970-1-1 0时0分0s
console.log(+new Date)
// 方法一
const date = new Date()
console.log(date.getTime())
// 方法二
console.log(+new Date) //数字型
console.log(+new Date('2023-7-14 18:30:0'))
// 方法三 只能返回当前时间的时间戳
console.log(Date.now())
```
### 2. 节点操作
#### 2.1 DOM节点
元素节点（主要）  
属性节点  
文本节点   
其他  
#### 2.2 查找节点  
根据关系  
父节点  
子节点  
兄弟节点  
```js
子元素.parentNode()
父元素.children() //仅获取元素节点
父元素.childNodes() //获取所有节点，包含元素节点、文本节点等
元素.nextElementSibling // 属性
元素.previousElementSibling // 属性
```
#### 2.3 增加节点  
```js
// 创建新节点
document.createElement('标签名')
// 放入指定元素内部
父元素.appendChild(元素) // 放入父元素的最后一个子元素
元素.insertBefor(传入的元素,定位元素)
元素.cloneNode(boolean) // true 克隆子孙后代 false仅克隆本元素节点
```
#### 2.4 删除节点  
删除元素必须通过父元素  
```js
父元素.removeChild(子元素)
```
### 3. M端事件  
touchstart  
touchmove  
touchend 

### 4. 插件  
别人写好的插件  
swiper示例  
- 熟悉官网，了解插件功能  
- 看在线演示  
- 看基本使用流程  
- 看API文档  
- 多个swiper使用，注意区分  

