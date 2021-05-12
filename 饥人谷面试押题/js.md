## 1.(必考)ES6 语法知道哪些, 分别怎么用?

- let const 块级作用域
- 箭头函数
- 展开运算符
- 析构赋值
- 模板字符串
- import / export

---

## 2.(必考) Promise  、 Promise.all 、Promise.race分别怎么用？

- Promise用法

```javascript
function fn(){
    return new Promise((resolve, reject)=>{
        resolve('成功的回调')
        reject('失败的回调')
    })
}
fn().then(success, fail).then(success2.fail2)
```

- Promise.all 用法
  - promise和promise2都成功才会调用success1,否则调用fail1

```javascript
Promise.all([promise1,promise2]).then(success1,fail1)
```

- Promise.race 用法
  - 谁第一个成功或失败，就认为是race的成功或失败

```java
Promise.reace([promise1,promise2]).then(success1, fail1)
```

---

## 3.（必考）手写防抖和节流

节流（冷却时间）

```javascript
function throttle(fn,delay){
    let canUse = true
    return function(){
       if(canUse){
           fn.apply(this,arguments)
            canUse = false
            setTimeout(()=>{
                canUse = true
            },delay)
       }
    }
}
const throttld = throttle(()=>{console.log('hello')})
throttld()
```

防抖

```java
function debounce(fn,delay){
    let timerId = null;
    return function(){
        const context = this
        if(timerId){
            window.cleartimeout(timerId)
        }
        timerId = setTimeout(()=>{
        	fn.apply(context,arguments)
             timerId = null
        },delay)
    }
}
const debounced = debounce(()=>{console.log('hello')})
debounced()
```

---

## 4.(必考)手写AJAX

```javascript
var request = new XMLHttpRequest()
request.open('GET',url,true)
request.onload = ()=> console.log(request.responseText)
request.send()
```

---

## 5.(必考)这段代码里的this是什么

```
a.fn() // this => window/global
b.obj.fn() // this => obj
c.fn.call(xxx) // this => xxx
d.fn.apply(xxx) // this => xxx
e.fn.bind(xxx) // this => xxx
f.new Fn() // this => 新对象
g.fn = () => {} // this => 外面的this
```

---

## 6.(必考)闭包&立即执行函数是是什么？

- 闭包 函数和函数内部能访问到的变量的总和，叫做闭包，通俗来说里层函数访问到外层函数的变量就做闭包。
  - 缺点 ： 内存泄露，函数销毁后变量依然在内存中，不被销毁
  - 用途： 常常用来【间接访问一个变量】或这隐藏一个变量
  - 场景： 防抖和节流
- 立即执行函数
  - 声明一个匿名函数-马上调用这个匿名函数

```javascript
(function(){alert('我是匿名函数')})()
/**
作用:
	创建一个独立的作用域,这个作用域里面的变量,外面访问不到
*/
```

示例代码:

```javascript
for(var i=0;i<6;i++){
    setTimeout(()=>{console.log(i)},0)
}
// 立即执行函数
for(var i=0;i<6;i++){
    !(function(i){
        setTimeout(()=>{console.log(i)},0)
    })(i)
}
```

---

## 7.(必考) 什么是JSONP,什么是CORS,什么是跨域

- JSONP是通过 script 标签加载数据的方式去获取当做js代码来执行

```java
//创建script标签
var script=document.createElement('script')

//设置回调函数
function getData(data){
    //数据请求回来会被触发的函数
    console.log(data);
}
//设置script的src属性，设置请求地址
script.src="http://localhost:3000?callback=getData";

//让script生效
document.body.appendChild(script);
```

- CORS  跨资源共享

```javascript
Access-Control-Allow-Origin: 协议+域名
```

- 跨域 当跨协议+域名+端口号,不一致时就会出现跨域

---

## 8.(常考) async / await 怎么用, 如何捕获异常



