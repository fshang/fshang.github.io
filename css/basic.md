# css 基础
## css是干什么？
css 的作用是‌控制网页的样式和布局‌，实现内容与表现的分离
## 为啥用css来做控制？
早期（1996年）以前，网页的样式和布局都是通过HTML标签来实现的。比如\<table>\<tr>\<td>\,代码臃肿，语义性差，严重混淆内容与表现层
## css怎么控制样式？
CSS通过以下核心机制实现对网页样式的精确控制：

### 一、CSS基础语法结构
CSS规则由‌选择器‌和‌声明块‌组成：

``` css
选择器 {
  属性: 值;
  属性: 值;
}
```
这种结构实现了对HTML元素的精准定位和样式设置

### 二、CSS选择器类型
1. 基本选择器
‌元素选择器‌：p { color: blue; } (选择所有<p>元素)
‌类选择器‌：.warning { color: red; } (选择class="warning"的元素)
‌ID选择器‌：#header { height: 100px; } (选择id="header"的元素)
2. 组合选择器
‌后代选择器‌：div p (选择div内的所有p元素)
‌子元素选择器‌：ul > li (只选择ul的直接子元素li)
‌相邻兄弟选择器‌：h1 + p (选择紧接在h1后的p元素)
3. 属性选择器
[type="text"] (选择type="text"的元素)
[href^="https"] (选择href以"https"开头的元素)
4. 伪类和伪元素
- a:hover (鼠标悬停时的链接样式)
- p::first-line (选择p元素的第一行)

### 三、CSS属性与值
CSS提供了丰富的属性来控制各种样式：

1. 文本样式

``` css

p {
  font-family: Arial, sans-serif;
  font-size: 16px;
  line-height: 1.5;
  text-align: center;
  text-decoration: underline;
}
```
2. 盒模型样式

``` css

div {
  width: 300px;
  height: 200px;
  padding: 20px;
  margin: 10px auto;
  border: 1px solid #ccc;
  border-radius: 5px;
}
```
3. 颜色与背景

``` css

body {
  color: #333;
  background-color: #f5f5f5;
  background-image: url('bg.png');
  background-size: cover;
}
```
4. 布局控制

``` css
.container {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 20px;
}
```
### 四、CSS引入方式
1. 内联样式

``` html
<p style="color: red;">紧急通知</p>
```
2. 内部样式表

``` html
<head>
  <style>
    body { font-family: Arial; }
  </style>
</head>
```
3. 外部样式表（推荐）

``` html
<head>
  <link rel="stylesheet" href="styles.css">
</head>
```
### 五、CSS的层叠与继承
1. 层叠规则
‌来源顺序‌：后定义的样式会覆盖先定义的样式
‌特异性‌：ID选择器 > 类选择器 > 元素选择器
‌!important规则‌：color: red !important; (最高优先级)
2. 继承特性
某些属性（如font、color）会自动继承给子元素
使用inherit值强制继承父元素样式
### 六、现代CSS新特性
1. CSS变量

``` css
:root {
  --primary-color: #4285f4;
}

button {
  background-color: var(--primary-color);
}
```
2. 过渡与动画

``` css
.button {
  transition: all 0.3s ease;
}

@keyframes slide {
  from { transform: translateX(-100%); }
  to { transform: translateX(0); }
}
```
3. 响应式设计

``` css
@media (max-width: 768px) {
  .menu { display: none; }
}
```