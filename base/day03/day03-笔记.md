### 1. 循环 for  
#### 1.1 基本使用  
```js
for (let i = 0; i < 50; i++) {
    console.log(i)
}
```
最常用的就是用来循环数组  
#### 1.2 循环嵌套  
```js
for (let line = 1; line <= 3; line++) {
    for (let col = 1; col <= 5; col++) {
        console.log(line, col)
    }
}
```
#### 1.3 退出循环  
continue  
break  
```js
// for无限循环
for (:;) {
    console.log('loop forever')
}
```
至于选择while还是true, 根据实际情况选择 


### 2. 数组  
#### 2.1 数组是什么  
Array  
按顺序保存数据的数据类型  
#### 2.2 基本使用  
- 声明数组  
  ```js
  let arr = ['kexia', 'yue']
  let arr = new Array('kexia', 'yue')
  // recommand the first way
  ```
- 取值  
  下标引用
- 术语  
  长度 
  下标  
- 遍历数组  
  for循环
#### 2.3 操作数组  
数组本质是数据集合  
- 查  
  下标获取  
- 改  
  ```js
  // 直接赋值语句修改  
  let arr = []
  arr[0] = 1
  arr[1] = 5
  arr[2] = 'kexia'
  arr[2] = arr[2] + 'yue'
  ```
- 增  
  ```js
  let arr = []
  arr.push('kexia') // 添加到数组末尾，返回数组新的长度
  arr.unsift('yue') // 添加到数组开头，返回数组新的长度
  ```
- 删
  ```js
  let arr = [1, 2, 3]
  arr.pop() //删除数组的最后一个元素，返回该元素的值  
  arr.shift() //删除数组的第一个元素，返回该元素的值
  arr.aplice(start, deleteCount) //删除元素的起始位置（索引号），删除指定数量元素
  // 如果不指定deleteCount，则是从start到最后都删除
  ```
#### 2.4 数组案例  
- 数组筛选  

