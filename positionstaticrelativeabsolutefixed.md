position:static|relative|absolute|fixed

> 大家下面示例代码先放在浏览器上跑，**感性认识一下**

- static 默认值  （你啥都没有设置的时候就是默认值）**没有脱离文档流**

- relative 

  > 设置了relative的元素会相对于**自身原来在文档流**的位置进行定位，不会影响其他元素的位置，
  >
  > 

  ```html
  <style>
          * {
              padding: 0;
              margin: 0;
          }
          
          body {
              height: 100%;
          }
          
          ul,
          li {
              list-style: none;
          }
          
          .item {
              border: 1px solid red;
              margin-top: 10px;
              background-color: aqua;
          }
      </style>
  </head>
  
  <body>
      <ul>
          <li class="item">我是第1项</li>
          <li class="item">我是第2项</li>
          <li class="item">我是第3项</li>
          <li class="item" style="position: relative;top:20px;left:20px;">我是第4项</li>
          <li class="item">我是第5项</li>
          <li class="item">我是第6项</li>
      </ul>
  </body>
  ```

  

- absolute

  > 1. 设置了 top、left 值时，元素是相对于最近的**定位上下文**来定位的(定位上下文这玩意儿下文解释)
  >
  > 2. 脱离文档流了, 导致父元素坍塌了
  >
  > 3. 包裹性：p元素宽度本来是整个屏幕的宽度，现在只是内容的宽度

  ```html
  <style>
          * {
              padding: 0;
              margin: 0;
          }
          
          ul,
          li {
              list-style: none;
          }
          
          .item {
              border: 1px solid red;
              margin-top: 10px;
              background-color: aqua;
          }
      </style>
  </head>
  
  <body>
      <ul>
          <li class="item">我是第1项</li>
          <li class="item">我是第2项</li>
          <li class="item">我是第3项</li>
          <li class="item" style="position:absolute;left:20px;top:20px;">我是第4项</li>
          <li class="item">我是第5项</li>
          <li class="item">我是第6项</li>
      </ul>
  </body>
  ```

  

- fixed

  > 相对于浏览器的窗口的位置来定位的

  ```html
  <style>
          * {
              padding: 0;
              margin: 0;
          }
          
          body {
              height: 100%;
          }
          
          ul,
          li {
              list-style: none;
          }
          
          .item {
              border: 1px solid red;
              margin-top: 10px;
              background-color: aqua;
          }
          
          .container {
              border: 2px solid black;
          }
      </style>
  </head>
  
  <body>
      <ul class="container">
          <li class="item">我是第1项</li>
          <li class="item">我是第2项</li>
          <li class="item">我是第3项</li>
          <li class="item" style="position: fixed;top:20px;left:20px;">我是第4项</li>
          <li class="item">我是第5项</li>
          <li class="item">我是第6项</li>
      </ul>
  </body>
  ```



### 定位上下文

1. relative元素定位永远是相对于元素自身的，以自身为定位上下文
2. fixed元素是相对于window（或者iframe)边界的，和其他元素没有关系。但是具有破坏性，

影响其他元素的排列

3. absolute：浏览器会递归的查找元素的所有父级元素，如果找到了一个为position： relative|absolute|fixed的元素，就以该元素为基准定位，如果没有找到，就以浏览器的边界为定位。



### 参考

- [Web 前端面试指南与高频考题解析](https://juejin.cn/book/6844733713780047886)

- MDN