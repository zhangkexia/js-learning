### 1. window对象
#### 1.1 BOM  
浏览器对象模型  
全局对象、顶级对象  
包含document   
window下属性和方法的调用，可以省略  

#### 1.2 定时器-延时函数  
```js
setTimeout(function(){
    console.log('时间到了')
}, 等待的毫秒数)
// 返回id
// 仅执行一次  
clearTimeout(timer)
```

#### 1.3 JS执行机制  
js本身是单线程，需要前面一个任务执行完，再执行下一个任务，如果某个人物执行时间过长，则渲染不连贯  
解决：使用多核CPU，HTML5提出web worker机制   
- 同步任务  
都在主线程上，形成一个执行栈  
- 异步任务  
    通过回调实现  
  - 普通事件 
  - 资源加载
  - 定时器  
异步任务相关添加到任务队列中  
- 机制  
先执行执行栈中的同步任务  
异步任务给浏览器异步进程，处理后放入任务队列中  
所有同步任务执行完毕后，系统按次读取任务队列中的异步任务，被执行的任务等待结束进入执行栈  
浏览器可以多线程  

#### 1.4 location对象  
使用location.href 跳转页面  
location 就是页面地址  
```js
location.href = 'www.baidu.com'
location.search  // ？后
location.hash // #后
location.reload(boolean) // true强制刷新
```

#### 1.5 navigator对象  
浏览器相关信息  
根据设备类型，跳转  

#### 1.6 history对象
history.back()  
history.forward()  
history.go(参数)  


### 2. 本地存储  
#### 2.1 介绍  
数据存储在浏览器  
设置、读取方便，页面刷新不丢失  
容量 sessionStorae localStorage 5M左右

#### 2.2 localStorage
存储在浏览器  
多窗口共享  
键值对  
本地存储只能存储字符串类型数据
```js
localStorage.setItem(key, value)
localStorage.getItem(key)
localStorage.removeItem(key)
```

#### 2.3 sessionStorage
生命周期为浏览器窗口关闭  
同一个窗口下数据共享  
键值对方式存储  
用法与localStorage相同  

#### 2.4 存储复杂数据类型  
复杂类型转成字符串，然后存入本地存储  
```js
// 转json字符串
JSON.stringfy(复杂数据类型)
// json字符串转对象
JSON.parse(字符串)
```

#### 2.5 map() join()方法
- map()
  遍历数组处理数据，并返回新的数组  
  映射，两个元素的集合之间元素相互对应  
  forEach没有返回值  
  ```js
  // ele 是每一个元素
  // index 是每一个元素的索引 
  arr.map(function(ele, index) {

  })
  ```
- join()  
  把数组转换为字符串  
  arr.join() // 默认逗号分割








