## 1.（必考）两个和模型分别说一下

- 标准盒模型：content
- 怪异盒模型： content +padding + border  
- 通过box-sizing: border-box/ content-box

---

## 2.(必考) 如何垂直居中

https://www.yuque.com/docs/share/708bd899-0c46-47ea-a94c-d7a189c0f7dc?#

- table自带功能
- 100% 高度的 afrer before 加上 inline block
- div 装成 table
- margin-top： -50%
- translate： -50%
- flex

---

## 3.（必考）flex 怎么用，常用属性有哪些？

```css
display：flex
flex: 0 1 auto
// 属性决定主轴的方向
flex-direction：row | row-reverse | column | column-reverse
// 是否换行
flex-wrap： nowrap | wrap | wrap-reverse
// 主轴对齐
justify-content: flex-start | flex-end | conter | space-betwen | space-around
// 交叉轴如何对齐
align-items： flex-start | flex-end | center | baseline | stretch
```

---

## 4.BFC是什么

字面解释： 块级格式化上下文

举例： 比如说overflow: hidden， 就是标准的BFC

BFC触发的条件：

- 浮动元素（元素的float不是none）
- 绝对定位元素（元素的 position 为 asolute 或 fixed）
- 行内块元素
- overfloe 值不为 visible 的块元素
- 弹性元素（display 为 flex 或 inline-flex元素的直接子元素）

---

## 5.CSS选择器优先级

- 越具体优先级越高
- 同样优先级写在后面的覆盖之前的
- !important 优先级最高，但是要少用

---

6. ## 清除浮动

```css
.clearfix:after{
    content:'';
    displa： block;
    clear:both;
}
.clearfix{
    zoom:1; /*IE 兼容*/
}
```

