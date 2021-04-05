# 箭头函数中的this

- 箭头函数中的this是在定义函数的时候绑定的,而不是在执行函数的时候绑定.
- 箭头函数中,this指向的固化,并不是因为箭头函数内部有绑定this的机制.实际原因是箭头函数根本没有自己的this,导致内部的this就是外层代码块的this.正因为他没有this,所以也就不能做构造函数.



箭头函数中的this是在定义函数的时候绑定

```javascript
var x = 11;
var obj = {
    x:22,
    say:()=>{
        console.log(this.x)
    }
}
obj.say();
```

所谓的定义时候绑定,就是this是继承自父执行上下文中的this,比如这里的箭头函数中的this.x,箭头函数本身与say平级以key:value的形式,也就是箭头函数本身所在的对象为obj,而obj的父执行上下文就是window,因此这里的this.x实际上表示的是window.x,因此输出的是11.

---

## 实例二

```javascript
var obj = {
    birth:1990,
    getAge:function(){
        var b = this.birth; //1990
        var fn = ()=>{
            return newDate().getFullYear() - this.birth; // this指向obj对象
        }
        return fn();
    }
}
```

例子中的箭头函数本身是getAge方法中定义的,因此,getAge方法的父执行上下文是obj,因此这里的this指向则为obj对象

