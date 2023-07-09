### 1. web API 基本认知  
变量声明，建议const优先，而不是用let  
引用数据类型，是可以用const声明的（即使会变化，元素变化，而不是整体变化），例如数组、对象  
基本数据类型，用const声明，则不能修改  
#### 1.1 作用和分类  
js操作html和浏览器  
DOM 文档对象模型  
BOM 浏览器对象模型  
#### 1.2 什么是DOM  
与HMTL或XML文档交互的API  
操作网页  
#### 1.3 DOM树  
HTML文档，树状结构  
- 元素节点  
  例如 p h1
- 属性节点 
  例如 src href 
- 文本节点  
  例如<p></p>之间的内容  
#### 1.4 DOM对象 
具有属性和方法  
把网页内容当作对象来处理  
网页所有内容都在document里  
```js
// DOM对象
document.write()
const div = document.querySelector('div')
console.log(div)
``` 

### 2. 获取DOM对象 
- CSS选择器（推荐使用过的）  
  最好有一些CSS的基础  
  利用JS选择页面中的标签元素  
  ```js
  // 选择匹配的第一个元素  
  document.querySeclector('CSS选择器')
  // CSS选择器
  // 1. 直接标签名
  document.querySeclector('div')
  // 2. .classname
  document.querySeclector('.header')
  // 3. #id
  document.querySeclector('#nav')
  // 4. 组合选择器 ul标签下的第一个子标签li
  const li = document.querySelector('ul li:first-child')
  // 第三个子标签li
  const li = document.querySelector('ul li:nth-child(3)')

  // 选择匹配的所有元素，返回对象集合，得到的是伪数组，有长度和索引号，没有pop() push()方法，可以使用for遍历
  document.querySeclectorAll('ul li')
  ``` 
- 其他方法（过时的）  
  ```js
  document.getElementById()
  docuemnt.getElementsByTagName()
  document.getElementsByClassName()
  ```
### 3. 操作元素内容  
.innerText属性  
.innerHTML属性  
```js
const box01 = document.querySeclector('.box')
console.log(box01.innerText) // 获取对象属性
box01.innerText = 'new content here.'
box01.innerText = '<strong>new content here.</strong>' //不解析标签
box01.innerHTML = '<strong>new content here.</strong>' //解析标签
```  
### 4. 操作元素属性  
- 元素常用属性 
  href title src(更换图片)  
  ```js
  const pic = document.querySelector('img')
  pic.src = '../images/xx.png'
  pic.title = 'kexia'
  pic.alt = 'alt here'
  ```
- 元素样式属性  
  - style  
    ```js
    const box1 = document.querySelector('.box')
    box1.style.width = '200px'
    box1.style.backgroundColor = 'pink' // 小驼峰
    box1.style.border = '2px solic blue'
    ```
  - className  
    直接修改类名，不同的类名，不同的样式  
    ```js
    const box1 = document.querySelector('.box')
    box1.className = 'newclassname' // 新类的样式被应用
    // CSS和JS的配合  
    // 要增加类，需要保留之前的类名  
    ```
  - classList  
    追加和删除类名  
    ```js
    const box1 = document.querySelector('.box')
    box1.classList.add('addclassname')
    box1.classList.remove('popclassname')
    // 没有就加上，有就删掉
    box1.classList.toggle('toggleclassname')
    ```
- 表单元素属性  
  ```js
  <input type='text' value='kexia'>
  const uname = document.querySelector('input')
  console.log(uname.value)
  表单.value = 'kexia'
  表单.type = 'password'
  表单.disabled // button
  表单.checked // 复选框 checkbox, 只接受布尔值
  表单.selected
  ```
- 自定义属性  
  html5推出的  
  data-自定义属性  
  data- 开头  
  ```js
  <div data-id='1' data-spm='kexia'></div>
  const div1 = document.querySelector('div')
  console.log(div.dataset.id)
  console.log(div.dataset.spm)
  ```
### 5. 定时器-间歇函数  
- 间歇函数（定时器的一种）  
  开启定时器  
  ```js
  setInterval(函数, 间隔时间)
  // 函数名，不是函数（）, 定时器自动去调用    
  // 每隔一段时间调用函数  
  // 间隔时间单位是ms
  setInterval(function(){console.log('ex')}, 1000)
  ```
  关闭定时器  
  ```js
  // 定时器返回的是id号
  let n = setInterval(function(){console.log('ex')}, 1000)
  // 使用定时器id号进行关闭操作
  clearInterval(n)
  ```
  