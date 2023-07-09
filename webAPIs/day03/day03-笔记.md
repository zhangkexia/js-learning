### 1. 事件流
#### 1.1 说明及两个阶段  
捕获  
document->html->body-div
冒泡  
div->body->html->document

#### 1.2 事件捕获  
从DOM的根元素开始  
```js
DOM.addEventListener(事件类型，事件处理函数，是否使用捕获机制)
// 一个对象上有多个事件，先从根元素开始  
```

#### 1.3 事件冒泡  
从本级开始，逐渐向上级 
L2事件监听，第三个参数默认是false, 默认是事件冒泡

#### 1.4 阻止冒泡  
事件只限定在本级， 不向上等级触发  
事件对象.stopPropagation

#### 1.4 解绑事件  
```js
// 传统的
btn.onclick = function() {
    console.log('L0')
}
btn.onclick = null // 解绑

// L2的
btn.addEventListener(事件，事件函数) // 不能是匿名函数
btn.removeEventListener(事件，事件函数)) // 不能是匿名函数

mouseover mouseout // 有冒泡
mouseenter mouseleave // 没有冒泡（推荐使用）
```  

### 2. 事件委托  
同时给多个元素注册事件 可以for循环实现  
利用事件流的技巧（冒泡）
给父元素注册事件，触发子元素的时候，会冒泡的父元素，从而触发父元素的事件  
### 3. 阻止事件默认行为  
```js
const form = document.querySelector('form')
form.addEventListener('submit', function(e) {
    e.preventDefault()
})

const a = document.querySelector('a')
form.addEventListener('click', function(e) {
    e.preventDefault()
})
```  

### 4. 其他事件  
- 页面加载事件  
  一般写在</body>前，在元素具备之后  
  老的代码，script写在head中  
  事件名load  
  ```js
  // 等待页面加载完毕后，执行回调函数
  window.addEventListener('load', function() {

  })
  // 也可以针对指定资源加载完毕  
  img.addEventListener('load', function() {
  
  })
  // DOMContentLoaded无需等待样式 图片资源等
  document.addEventListener('DOMContentLoaded', funciton() {

  })
  ```
- 页面滚动事件  
- 页面尺寸事件  