### 1. 深拷贝 浅拷贝
```js
// 引用类型数据
// 赋值，是浅浅拷贝
const a = {
    uname: 'kexia'
}
b = a
// 改变b a也会改变
b.uname = 'yue'
// 浅拷贝
// 只能拷贝第一层，如果有嵌套，还是会影响原来的变量
const a = {
    uname: 'kexia',
    obj: {
        uu: 'yue'
    }
}
const b = {}
Object.assign(b, a)
//或者用展开运算符
const b = {...a}
// b的uname成员变化，不影响a的uname
// 但是b.obj改变了uu, a的obj.uu也会改变

// 数组的浅拷贝
const a = [1, 2, {uname: 'kexia'}]
const b = [...a]
// 改变b[2].uname a还是会受到影响

// 深拷贝，可以基于递归来实现
const a = {
    uname: 'kexia',
    obj: {
        uu: 'yue'
    }
}
const b = {}
function deepCopy(b, a) {
    for (let k in a) {
        if (a[k] instanceof Array) {
            // 如果是数组，对数组递归调用
            b[k] = []
            deepCopy(b[k], a[k])
        } else if (a[k] instanceof Object) {
            // 如果是对象，对对象递归调用
            b[k] = {}
            deepCopy(b[k], a[k])
        } else {
             b[k] = a[k]
        } 
    }    
}

// 深拷贝，使用lodash库
// 先引入lodash
const a = {
    uname: 'kexia',
    obj: {
        uu: 'yue'
    }
}
const b = _.cloneDeep(a)

// JSON.stringigy实现
const a = {
    uname: 'kexia',
    obj: {
        uu: 'yue'
    }
}
// 先转成字符串
const b = JSON.parse(JSON.stringify(a))
```
### 2. 异常处理
```js
// 异常抛出
function hifun(a) {
    if (a > 0) {
        throw new Error('a greater 0') //抛异常后，会中断程序
    }
    return a * a
}

// 异常捕获
function hifun(a) {
    try {
        a = a * a
    }
    catch (error) {
        console.log(error.message)
    }
    finally {
        a = a * a
    }

    console.log('捕获异常不会中断程序')
}


function hifun(a) {
    try {
        debugger // 打个调试断点
        a = a * a
    }
    catch (error) {
        console.log(error.message)
    }
    finally {
        a = a * a
    }

    console.log('捕获异常不会中断程序')
}

```
### 3. 处理this
```js
// 普通函数的this指向者

// 箭头函数的this，本身没有this, 网上逐层找，直到找到

// call 方法改变this
function fn(x, y) {
    console.log(x, y)
    console.log(this)
}

obj = {
    uname: 'kexia'
}
fn.call(obj, x, y) // this指向obj

fn.apply(obj,[x, y]) // 参数是数组

const max = Math.max.apply(Math, [1, 2, 3])
// 数组作为参数, 传入函数

const fnnew = fn.bind(obj, x, y) // 只是改变this指向，但是不会立马调用函数
fnnew() // 新函数的调用

// btn 两秒后开启
const btn = document.querySelector('button')
btn.addEventListener('click', function() {
    this.disabled = true
    setTimeout(function() {
        //this.disabled = false // 没有绑定btn之前这里的定时器是window 调用，this是window,可以改成箭头函数,

        this.disabled = false
    }.bind(this), 2000) // 绑定了this，也就是绑定了btn
})
```

### 4. 性能优化
```js 
// 防抖，单位时间内，频繁触发事件，只执行最后一次
// 触发后一次，把上一次取消
// 后一次的触发，先取消上一次

// 节流，单位时间内，频繁触发事件，只执行一次，后面的不再执行
// 第一次触发执行，并把后面的触发都给取消，这一次执行后，恢复到可执行状态
```js