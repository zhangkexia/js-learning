### 1. 事件监听  
事件？例如单击一个按钮  
检测事件是否发生，事件触发，则调用一个函数来响应  
事件绑定/事件注册  
- 语法  
  ```js
  元素对象.addEventListener('事件类型', 要执行的函数)
  ```
  - 事件源
  - 事件类型  
  - 事件调用的函数  
  ```js
  <button>click</button>
  const btn = document.querySelector('button')
  btn.addEventListener('click', function() {
    alert('hello')
  })
  ```
事件监听版本  
- L0  
  事件源.on时间 = 事件函数  
- L2  
  addEventListener
- 区别  
  on方式会被覆盖，addEventListener方式可绑定多次  
### 2. 事件类型  
- 鼠标事件  
  click  
  mouseover
  mouseleave
- 焦点事件  
  focus  
  blur  
- 键盘事件  
  Keydown  
  Keyup
- 文本事件
  input 用户输入事件  

### 3. 事件对象  
包含事件触发时的相关信息的对象  
事件绑定的回调函数的第一个参数就是事件对象  
- type 事件类型  
- clientX/clientY 相对于浏览器可见窗口左上角的位置
- offsetX/offsetY 相对于当前DOM元素左上角的位置
- key 当前用户按下的键盘的值  

### 4. 环境对象  
函数内部的特殊变量，代表当前函数运行时所处的环境  
普通函数调用的是window  
谁调用，this就指向谁  
事件函数的this指向的是事件源  

### 5. 回调函数  
函数A作为参数传递给函数B，函数A就是回调函数  
```js
function fn() {
    console.log('callback function')
}
setInterval(fn, 1000)

box.addEventListener('click', function() {
    console.log('callback function too.')
})
```