# 布局

## 一、基础概念

### 1、概念

1. Flex是Flexible Box的缩写，意为"弹性布局"，用来为盒状模型提供最大的灵活性。
2. 任何一个容器都可以指定为Flex布局。

### 2、flex 主要包含两个部分的内容

1. 容器和轴:容器包括外层的容器和内层的子容器，轴包括主轴和交叉轴。

2. flex 布局的全部特性都构建在这两个概念上。

3. flex 布局一共包含 12 个 CSS 属性（不包含 display: flex），其中父容器、子容器各 6 个。

4. 常用的属性 4 个，父容器2个(justify-content,align-items)、子容器2 个(flex,align-self)。

   ​

   ![](http://opzv089nq.bkt.clouddn.com/17-8-20/52803350.jpg)

### 3、注意事项

1. 子元素的float、clear和vertical-align属性将失效
2. CSS columns 在弹性盒子中不起作用

## 二、容器(container)

### flex

1. 作用

   ```
   要想使用弹性盒子首先要设置父容器为 display: flex
   ```

2. 语法格式

   ```
   display: flex | inline-flex
   ```

3. 可选值介绍

   ```
   1、新版本
   	flex：将对象作为弹性伸缩盒显示。
   	inline-flex：将对象作为内联块级弹性伸缩盒显示。
   2、老版本
   	box：将对象作为弹性伸缩盒显示。
   	inline-box：将对象作为内联块级弹性伸缩盒显示。
   3、过渡版
   	flexbox：将对象作为弹性伸缩盒显示。
   	inline-flexbox：将对象作为内联块级弹性伸缩盒显示。
   ```

### 1、flex-direction

1. 作用

   ```
   设置或检索伸缩盒对象的子元素在父容器中的位置
   ```

2. 语法格式

   ```
   flex-direction: row | row-reverse | column | column-reverse
   ```

3. 可选值说明

   | 可选值            | 说明                          |
   | -------------- | --------------------------- |
   | row            | 横向从左到右排列（左对齐），默认的排列方式。      |
   | row-reverse    | 反转横向排列（右对齐，从后往前排，最后一项排在最前面) |
   | column         | 纵向排列                        |
   | column-reverse | 反转纵向排列，从后往前排，最后一项排在最上面      |

4. 示例代码

   - HTML代码

     ```
     <h3>row</h3>
     <ul id="box" class="box">
     	<li>1</li>
     	<li>2</li>
     	<li>3</li>
     </ul>
     <h3>row-reverse</h3>
     <ul id="box2" class="box">
     	<li>1</li>
     	<li>2</li>
     	<li>3</li>
     </ul>
     <h3>column</h3>
     <ul id="box3" class="box">
     	<li>1</li>
     	<li>2</li>
     	<li>3</li>
     </ul>
     <h3>column-reverse</h3>
     <ul id="item4" class="box">
     	<li>1</li>
     	<li>2</li>
     	<li>3</li>
     </ul>
     ```

   - CSS代码

     ```
         <style type="text/css">
             *{
                  margin: 0;
                  padding:0;
             }
             .container {
                 display: flex;
                 background: red;
                 display: -webkit-flex;
                 list-style: none;
             }
             .container li {
                 margin: 5px;
                 text-align: center;
                 background: hotpink;
                 width: 50px;
                 height: 50px;
                 line-height: 50px;
                 border: 1px solid #aaa;
             }
             #item1 {
                 /*兼容webkit内核的浏览器  Safari */
                 -webkit-flex-direction: row;
                 flex-direction: row;
             }
             #items2 {
                 -webkit-flex-direction: row-reverse;
                 flex-direction: row-reverse;
             }
             #items3 {
                 -webkit-flex-direction: column;
                 flex-direction: column;
             }
             #items4 {
                 -webkit-flex-direction: column-reverse;
                 flex-direction: column-reverse;
             }
         </style>
     ```

   - 效果图

     ![](http://opzv089nq.bkt.clouddn.com/17-8-20/19582890.jpg)

### 2、flex-wrap

1. 作用

   ```
   设置或检索弹性盒子的子元素超出父容器时是否换行
   ```

2. 语法格式

   ```
   flex-wrap: nowrap | wrap | wrap-reverse
   ```

3. 可选值说明

   | 可选值          | 说明             |
   | ------------ | -------------- |
   | nowrap       | 当子元素溢出父容器时不换行  |
   | wrap         | 当子元素溢出父容器时自动换行 |
   | wrap-reverse | 反转 wrap 排列     |

4. 示例代码

   - HTML代码

     ```
     <h3>nowrap</h3>
     <ul id="items1" class="container">
         <li>1</li>
         <li>2</li>
         <li>3</li>
     </ul>
     <h3>wrap</h3>
     <ul id="items2" class="container">
         <li>1</li>
         <li>2</li>
         <li>3</li>
     </ul>
     <h3>wrap-reverse</h3>
     <ul id="items3" class="container">
         <li>1</li>
         <li>2</li>
         <li>3</li>
     </ul>
     ```

   - CSS代码

     ```
     <style type="text/css">
         .container {
             display: -webkit-flex;
             display: flex;
             width: 150px;
             margin: 0;
             padding: 10px;
             list-style: none;
             background: red;
         }
         .container li {
             background: hotpink;
             text-align: center;
             line-height: 50px;
             margin: 2px;
             width: 50px;
             height: 50px;
             border: 1px solid black;
         }
         #items1 {
             -webkit-flex-wrap: nowrap;
             flex-wrap: nowrap;
         }
         #items2 {
             -webkit-flex-wrap: wrap;
             flex-wrap: wrap;
         }

         #items3 {
             -webkit-flex-wrap: wrap-reverse;
             flex-wrap: wrap-reverse;
         }
     </style>
     ```

5. 效果图

   ![](http://opzv089nq.bkt.clouddn.com/17-8-20/33908917.jpg)

### 3、flex-flow

1. 作用

   ```
   复合属性,设置或检索弹性盒子的子元素超出父容器时是否换行
   ```

2. 语法格式

   ```
   flex-flow: flex-direction|| flex-wrap
   ```

3. 可选值说明

   | 可选值            | 说明                  |
   | -------------- | ------------------- |
   | flex-direction | 定义弹性盒子元素的排列方向。      |
   | flex-wrap      | 定义弹性盒子元素溢出父容器时是否换行。 |

4. 示例代码

   - HTML代码

     ```
     <h3>row nowrap</h3>
     <ul id="items1" class="container">
         <li>1</li>
         <li>2</li>
         <li>3</li>
     </ul>
     <h3>row wrap-reverse</h3>
     <ul id="items2" class="container">
         <li>1</li>
         <li>2</li>
         <li>3</li>
     </ul>
     <h3>column wrap-reverse</h3>
     <ul id="items3" class="container">
         <li>1</li>
         <li>2</li>
         <li>3</li>
     </ul>
     ```

   - CSS代码

     ```
         <style type="text/css">
             .container {
                 display: -webkit-flex;
                 display: flex;
                 width: 200px;
                 height: 150px;
                 margin: 0;
                 padding: 10px;
                 list-style: none;
                 background: red;
             }

             .container li {
                 background: hotpink;
                 text-align: center;
                 line-height: 50px;
                 margin: 2px;
                 width: 50px;
                 height: 50px;
                 border: 1px solid black;
             }

             #items1 {
                 -webkit-flex-wrap: nowrap;
                 flex-flow: row nowrap;
             }

             #items2 {
                 -webkit-flex-wrap: wrap;
                 flex-flow: row wrap-reverse;
             }
             #items3 {
                 -webkit-flex-wrap: wrap-reverse;
                 flex-flow: column wrap-reverse;
             }
         </style>
     ```

5. 效果图

   ​

### 4、justify-content(常用)

1. 作用

   ```
   设置或检索弹性盒子元素在主轴（横轴）方向上的对齐方式。
   当弹性盒里一行上的所有子元素都不能伸缩或已经达到其最大值时，这一属性可协助对多余的空间进行分配。
   当元素溢出某行时，这一属性同样会在对齐上进行控制。
   ```

2. 语法格式

   ```
   justify-content: flex-start | flex-end | center | space-between | space-around
   ```

3. 可选值说明

   | 可选值           | 说明                                   |
   | ------------- | ------------------------------------ |
   | flex-start    | 默认方式  起始端对齐                          |
   | flex-end      | 末尾段对齐                                |
   | center        | 居中对齐                                 |
   | space-between | 子容器沿主轴均匀分布，位于首尾两端的子容器与父容器相切          |
   | space-around  | 容器沿主轴均匀分布，位于首尾两端的子元素到主容器的距离是子容器间距的一半 |

4. 示例代码

   - HTML代码

     ```
     <h3>flex-start</h3>
     <ul id="items1" class="container">
         <li>1</li>
         <li>2</li>
         <li>3</li>
     </ul>
     <h3>flex-end</h3>
     <ul id="items2" class="container">
         <li>1</li>
         <li>2</li>
         <li>3</li>
     </ul>
     <h3>center</h3>
     <ul id="items3" class="container">
         <li>1</li>
         <li>2</li>
         <li>3</li>
     </ul>
     <h3>space-between</h3>
     <ul id="items4" class="container">
         <li>1</li>
         <li>2</li>
         <li>3</li>
     </ul>
     <h3>space-around</h3>
     <ul id="items5" class="container">
         <li>1</li>
         <li>2</li>
         <li>3</li>
     </ul>
     ```

   - CSS代码

     ```
     <style type="text/css">
             .container {
                 display: -webkit-flex;
                 display: flex;
                 width: 200px;
                 margin: 0;
                 padding: 10px;
                 list-style: none;
                 background: red;
             }

             .container li {
                 background: hotpink;
                 text-align: center;
                 line-height: 50px;
                 margin: 2px;
                 width: 50px;
                 height: 50px;
                 border: 1px solid black;
             }

             /*默认值
               弹性盒子元素将向行起始位置对齐。
               该行的第一个子元素的主起始位置的边界将与该行的主起始位置的边界对齐，
               同时所有后续的伸缩盒项目与其前一个项目对齐
               */
             #items1 {
                 -webkit-justify-content: flex-start;
                 justify-content: flex-start;
             }

             /*弹性盒子元素将向行结束位置对齐。
               该行的第一个子元素的主结束位置的边界将与该行的主结束位置的边界对齐，
               同时所有后续的伸缩盒项目与其前一个项目对齐
              */
             #items2 {
                 -webkit-justify-content: flex-end;
                 justify-content: flex-end;
             }

             /*
              *弹性盒子元素将向行中间位置对齐。
              *该行的子元素将相互对齐并在行中居中对齐，
              *同时第一个元素与行的主起始位置的边距等同与最后一个元素与行的主结束位置的边距
              *（如果剩余空间是负数，则保持两端相等长度的溢出
              */
             #items3 {
                 -webkit-justify-content: center;
                 justify-content: center;
             }

             /*
              *弹性盒子元素会平均地分布在行里。
              *如果最左边的剩余空间是负数，或该行只有一个子元素，则该值等效于'flex-start'。
              *在其它情况下，第一个元素的边界与行的主起始位置的边界对齐，
              *同时最后一个元素的边界与行的主结束位置的边距对齐，
              *而剩余的伸缩盒项目则平均分布，并确保两两之间的空白空间相等
              */
             #items4 {
                 justify-content: space-between;
                 -webkit-justify-content: space-between;
             }
             /*
              * 弹性盒子元素会平均地分布在行里，两端保留子元素与子元素之间间距大小的一半。
              * 如果最左边的剩余空间是负数，或该行只有一个子元素，则该值等效于'center'。
              * 在其它情况下，子项目则平均分布，并确保两两之间的空白空间相等，
              * 同时第一个元素前的空间以及最后一个元素后的空间为其他空白空间的一半
              */
             #items5 {
                 -webkit-justify-content: space-around;
                 justify-content: space-around;
             }
     ```

5. 效果图

   ![](http://opzv089nq.bkt.clouddn.com/17-8-20/18150655.jpg)

### 5、align-items(常用)

1. 作用

   ```
   设置或检索弹性盒子元素在交叉轴（纵轴）方向上的对齐方式
   ```

2. 语法格式

   ```
   align-items: flex-start | flex-end | center | baseline | stretch
   ```

3. 可选值说明

   | 可选值        | 说明                       |
   | ---------- | ------------------------ |
   | flex-start | 起始端对齐                    |
   | flex-end   | 末尾段对齐                    |
   | center     | 居中对齐                     |
   | baseline   | 基线对齐, 默认是指首行文字           |
   | stretch    | 默认,子容器沿交叉轴方向的尺寸拉伸至与父容器一致 |

4. 示例代码

   - HTML代码

     ```
     <h3>flex-start</h3>
     <ul id="items1" class="container">
         <li>1</li>
         <li>2</li>
         <li>3</li>
     </ul>
     <h3>flex-end</h3>
     <ul id="items2" class="container">
         <li>1</li>
         <li>2</li>
         <li>3</li>
     </ul>
     <h3>center</h3>
     <ul id="items3" class="container">
         <li>1</li>
         <li>2</li>
         <li>3</li>
     </ul>
     <h3>baseline</h3>
     <ul id="items4" class="container">
         <li>g</li>
         <li>j</li>
         <li>a</li>
     </ul>
     <h3>stretch</h3>
     <ul id="items5" class="container">
         <li>1</li>
         <li>2</li>
         <li>3</li>
     </ul>
     ```

   - CSS代码

     ```
      <style type="text/css">

             .container {
                 display: -webkit-flex;
                 display: flex;
                 width: 200px;
                 height: 50px;
                 margin: 0;
                 list-style: none;
                 background: red;
             }

             .container li {
                 background: hotpink;
                 text-align: center;
                 margin: 2px;
                 width: 50px;
                 border: 1px solid black;
             }

             /*
              *弹性盒子元素的交叉轴（纵轴）起始位置的边界紧靠住该行的交叉轴（纵轴）起始边界
              */
             #items1 {
                 -webkit-align-items: flex-start;
                 align-items: flex-start;
             }

             /*
              *弹性盒子元素的交叉轴（纵轴）结束位置的边界紧靠住该行的交叉轴（纵轴）结束边界
              */
             #items2 {
                 -webkit-align-items: flex-end;
                 align-items: flex-end;
             }

             /*
              *弹性盒子元素在该行的交叉轴（纵轴）上居中放置。
              *如果该行的尺寸小于弹性盒子元素的尺寸，则会向两个方向溢出相同的长度
              */
             #items3 {
                 -webkit-align-items: center;
                 align-items: center;
             }

             /*
              *弹性盒子元素的行内轴与交叉轴为同一条，则该值与'flex-start'等效。
              *其它情况下，该值将参与基线对齐
              */
             #items4 {
                 -webkit-align-items: baseline;
                 align-items: baseline;
             }

             #items4 li:nth-child(1) {
                 padding: 10px;
             }

             #items4 li:nth-child(2) {
                 padding: 10px 15px;
             }
             #items4 li:nth-child(3) {
                 padding: 5px;
             }
             /*
              *如果指定侧轴大小的属性值为'auto'，则其值会使项目的边距盒的尺寸尽可能接近所在行的尺寸，
              *但同时会遵照'min/max-width/height'属性的限制
              */
             #items5 {
                 -webkit-align-items: stretch;
                 align-items: stretch;
             }
         </style>
     ```

5. 效果图

   ![](http://opzv089nq.bkt.clouddn.com/17-8-20/1327006.jpg)

### 6、align-content

1. 作用

   ```
   设置弹性盒子堆叠伸缩行的对齐方式
   当只有一行子元素时，此属性不起作用
   ```

2. 语法格式

   ```
   align-content: flex-start | flex-end | center | space-between | space-around | stretch
   ```

3. 可选值说明

   | 可选值           | 说明                                    |
   | ------------- | ------------------------------------- |
   | flex-start    | 起始端对齐                                 |
   | flex-end      | 末尾段对齐                                 |
   | center        | 居中对齐                                  |
   | space-between | 子元素均匀分布; 第一行是在容器的开始，而最后一行在结束          |
   | space-around  | 子容器沿主轴均匀分布，位于首尾两端的子容器到父容器的距离是子容器间距的一半 |
   | stretch       | 各行子元素拉升以占用剩余的空间                       |

4. 示例代码

   - HTML代码

     ```
     <h3>flex-start</h3>
     <ul id="items1" class="container">
         <li>1</li>
         <li>2</li>
         <li>3</li>
         <li>4</li>
         <li>5</li>
         <li>6</li>
     </ul>
     <h3>flex-end</h3>
     <ul id="items2" class="container">
         <li>1</li>
         <li>2</li>
         <li>3</li>
         <li>4</li>
         <li>5</li>
         <li>6</li>
     </ul>
     <h3>center</h3>
     <ul id="items3" class="container">
         <li>1</li>
         <li>2</li>
         <li>3</li>
         <li>4</li>
         <li>5</li>
         <li>6</li>
     </ul>
     <h3>space-between</h3>
     <ul id="items4" class="container">
         <li>1</li>
         <li>2</li>
         <li>3</li>
         <li>4</li>
         <li>5</li>
         <li>6</li>
     </ul>
     <h3>space-around</h3>
     <ul id="items5" class="container">
         <li>1</li>
         <li>2</li>
         <li>3</li>
         <li>4</li>
         <li>5</li>
         <li>6</li>
     </ul>
     <h3>stretch</h3>
       <ul id="items6" class="container">
           <li>1</li>
           <li>2</li>
           <li>3</li>
           <li>4</li>
           <li>5</li>
           <li>6</li>
       </ul>
     </body>
     ```

   - CSS代码

     ```
         <style type="text/css">
             * {
                 margin: 0;
                 padding: 0;
             }

             .container {
                 display: -webkit-flex;
                 display: flex;
                 -webkit-flex-wrap: wrap;
                 flex-wrap: wrap;
                 width: 200px;
                 height: 150px;
                 list-style: none;
                 background: red;
             }

             .container li {
                 border-radius: 5px;
                 background: hotpink;
                 text-align: center;
                 line-height: 50px;
                 width: 50px;
                 height: 50px;
                 border: 1px solid black;
             }
             #items1 {
                 -webkit-align-content: flex-start;
                 align-content: flex-start;
             }
             #items2 {
                 -webkit-align-content: flex-end;
                 align-content: flex-end;
             }
             #items3 {
                 -webkit-align-content: center;
                 align-content: center;
             }

             #items4 {
                 -webkit-align-content: space-around;
                 align-content: space-around;
             }
             #items5 {
                 -webkit-align-content: space-between;
                 align-content: space-between;
             }
             #items6 {
                 -webkit-align-content: stretch;
                 align-content: stretch;
             }
     ```

5. 效果图

   ![](http://opzv089nq.bkt.clouddn.com/17-8-20/32224072.jpg)

## 三、子元素

### 1、flex-grow

1. 作用

   ```
   设置弹性盒子的扩展比率,根据弹性盒子的子元素所设置的扩展数值作为比例来分配剩余空间
   ```

2. 语法格式

   ```
   flex-grow: number
   ```

3. 可选值说明

   | 可选值    | 说明                |
   | ------ | ----------------- |
   | number | 数值无单位,不允许负数,默认值为0 |

4. 示例代码

   - HTML代码

     ```
     <ul class="container">
         <li>1</li>
         <li>2</li>
         <li>3</li>
         <li>4</li>
         <li>5</li>
     </ul>
     ```

   - CSS代码

     ```
      <style type="text/css">
             * {
                 margin: 0;
                 padding: 0;
             }
             /*
              * 300-5*52=40
              * 40分成四份 每份10
              * 第一个子元素分配到10px 第二个子元素30px
              * 没有设置该属性的不参与分配
              */
             .container {
                 display: flex;
                 width: 300px;
                 background: red;
                 list-style: none;
             }
             .container > li {
                 background: hotpink;
                 width: 50px;
                 height: 50px;
                 border: 1px solid black;
                 text-align: center;
             }
             .container > li:nth-child(1) {
                 -webkit-flex-grow: 2;
                 flex-grow: 1;
             }
             .container > li:nth-child(2) {
                 -webkit-flex-grow: 2;
                 flex-grow: 3;
             }
         </style>
     ```

5. 效果图

   ![](http://opzv089nq.bkt.clouddn.com/17-8-20/41404449.jpg)

### 2、flex-basis

1. 作用

   ```
   设置该元素的宽度。当然，width也可以用来设置元素宽度。如果元素上同时设置了width和flex-basis,那么flex-basis会覆盖width的值
   ```

2. 语法格式

   ```
   flex-basis: <length> | auto
   ```

3. 可选值说明

   | 可选值        | 说明                   |
   | ---------- | -------------------- |
   | length     | 值是有单位数字，不允许负值。       |
   | auto       | 默认值 无特定宽度值，取决于其它属性值。 |
   | percentage | 用百分比来定义宽度，不允许负值。     |

4. 示例代码

   - HTML代码

     ```
     <ul class="container">
         <li>1</li>
         <li>2</li>
         <li>3</li>
         <li>4</li>
         <li>5</li>
     </ul>
     ```

   - CSS代码

     ```
     <style type="text/css">

             * {
                 margin: 0;
                 padding: 0;
             }

             .container {
                 display: flex;
                 width: 500px;
                 background: red;
                 list-style: none;
             }

             .container > li {
                 background: hotpink;
                 width: 50px;
                 height: 50px;
                 border: 1px solid black;
                 text-align: center;
             }

             /* */
             .container > li:nth-child(1) {
                 -webkit-flex-basis: 200px;
                 flex-basis: 200px;
             }
     ```

5. 效果图

   ![](http://opzv089nq.bkt.clouddn.com/17-8-20/41563172.jpg)

### 3、flex-shrink

1. 作用

   ```
   用来设置当父元素的宽度小于所有子元素的宽度的和时（即子元素会超出父元素），子元素如何缩小自己的宽度的
   ```

2. 语法格式

   ```
   flex-shrink: number
   ```

3. 可选值说明

   | 可选值    | 说明                                 |
   | ------ | ---------------------------------- |
   | number | 默认值为1，如果没有显示定义该属性,不可以为负数,0表示保持设置大小 |

4. 示例代码

   - HTML代码

     ```
     <div class="container">
         <div>子元素1</div>
         <div>子元素2</div>
         <div>子元素3</div>
     </div>
     ```

   - CSS代码

     ```
         <style type="text/css">
             .container {
                 padding: 5px;
                 background: orange;
                 display: flex;
                 border: 1px solid black;
                 width: 300px;
             }

             /*
                 子元素的宽度分别是: 200, 300, 100。主容器的宽度是:300，
                 计算超出的空间就是 300，超出的 105px 就要被 子元素1, 子元素2, 子元素3所消化掉，比例是2：1：1
                 计算步骤
                 第一步:首先是每个项目的width值乘以flex-shrink值求积，
                 子元素1：(200 * 2) = 400
                 子元素2：(300 * 1) = 300
                 子元素3：(100 * 1) =100。
                 第二步: 然后再求和所有项目的乘积。
                 (400 + 300 + 100) = 800
                 第三步:得到求占比之后还要乘以要腾出的空间。
                 子元素1：(400 / 800) * 300 = 150
                 子元素2：(300 / 800) * 300 =112.5
                 子元素3：(100 / 800) * 300 =37.5
                 第四步:得到每一项要腾出的空间后计算最终需要腾出的空间
                 子元素1：(200 - 150) = 50
                 子元素2：(300 - 112.5) = 187.5
                 子元素3：(100 - 37.5) = 62.5
              */
             .container div:nth-child(1) {
                 background: greenyellow;
                 flex-basis: 200px;
                 flex-shrink: 2;
             }

             .container div:nth-child(2) {
                 background: red;
                 flex-basis: 300px;
                 flex-shrink: 1;
             }

             .container div:nth-child(3) {
                 background-color: blue;
                 flex-basis: 100px;
                 flex-shrink: 1;
             }
         </style>
     ```

5. 效果图

   ![](http://opzv089nq.bkt.clouddn.com/17-8-20/57720562.jpg)

6. 小结

   ```
   如果父级的空间足够：flex-grow有效，flex-shrink无效。
   如果父级的空间不够：flex-shrink 有效，flex-grow无效
   ```

### 4、flex(常用)

1. 作用

   ```
   复合属性。设置或检索伸缩盒对象的子元素如何分配空间
   ```

2. 语法格式

   ```
   flex：none |  flex-grow ||  flex-shrink  ||  flex-basis
   ```

3. 可选值说明

   | 可选值         | 说明                     |
   | ----------- | ---------------------- |
   | none        | none关键字的计算值为: 0 0 auto |
   | flex-grow   | 定义弹性盒子元素的扩展比率          |
   | flex-shrink | 定义弹性盒子元素的收缩比率          |
   | flex-basis  | 定义弹性盒子元素的默认基准值         |

   | 值    | 说明                             |
   | ---- | ------------------------------ |
   | 单值   | 无单位:grow,有单位:basis             |
   | 双值   | 无单位:grow和shrink,有单位 grow和basis |
   | 三值   | grow和shrink和basis              |

4. 示例代码

   - HTML代码

     ```
     <h3>单值</h3>
     <ul id="box" class="box">
         <li>flex:1</li>
         <li>flex:1</li>
         <li>flex:1</li>
     </ul>
     <h3>双值</h3>
     <ul id="box2" class="box">
         <li>flex:1 100px</li>
         <li>flex:2 100px</li>
         <li>flex:3 100px</li>
     </ul>
     <h3>三值</h3>
     <ul id="box3" class="box">
         <li>flex:1 1 200px</li>
         <li>flex:1 2 200px</li>
         <li>flex:1 2 200px</li>
     </ul>
     ```

     ​

   - CSS代码

     ```
         <style type="text/css">

             .box {
                 display: -webkit-flex;
                 display: flex;
                 max-width: 400px;
                 height: 100px;
                 margin: 10px 0 0;
                 padding: 0;
                 border-radius: 5px;
                 list-style: none;
                 background-color: #eee;
             }

             .box li {
                 background: #aaa;
                 text-align: center;
             }

             .box li:nth-child(1) {
                 background: #999;
             }

             .box li:nth-child(2) {
                 background: #aaa;
             }

             .box li:nth-child(3) {
                 background: #ccc;
             }

             #box li:nth-child(1) {
                 -webkit-flex: 1;
                 flex: 1;
             }

             #box li:nth-child(2) {
                 -webkit-flex: 1;
                 flex: 1;
             }

             #box li:nth-child(3) {
                 -webkit-flex: 1;
                 flex: 1;
             }

             #box2 li:nth-child(1) {
                 -webkit-flex: 1 0 100px;
                 flex: 1 0 100px;
             }

             #box2 li:nth-child(2) {
                 -webkit-flex: 2 0 100px;
                 flex: 2 0 100px;
             }

             #box2 li:nth-child(3) {
                 -webkit-flex: 3 0 100px;
                 flex: 3 0 100px;
             }

             #box3 {
                 max-width: 800px;
             }

             #box3 li:nth-child(1) {
                 -webkit-flex: 1 1 300px;
                 flex: 1 1 300px;
                 background: #999;
             }
             #box3 li:nth-child(2) {
                 -webkit-flex: 1 2 500px;
                 flex: 1 2 500px;
                 background: #aaa;
             }
             #box3 li:nth-child(3) {
                 -webkit-flex: 1 3 600px;
                 flex: 1 3 600px;
                 background: #ccc;
             }
         </style>
     ```

5. 效果图

   ![](http://opzv089nq.bkt.clouddn.com/17-8-20/42646046.jpg)

### 5、order

1. 作用

   ```
   设置弹性盒子的子元素出現的順序
   ```

2. 语法格式

   ```
   order: <integer>
   ```

3. 可选值说明

   | 可选值     | 说明                        |
   | ------- | ------------------------- |
   | integer | 用整数值来定义排列顺序，数值小的排在前面。可以为负 |

4. 示例代码

   - HTML代码

     ```
     <ul class="container">
         <li>1</li>
         <li>2</li>
         <li>3</li>
         <li>4</li>
         <li>5</li>
     </ul>
     ```

     ​

   - CSS代码

     ```
      <style type="text/css">
             .container {
                 display: -webkit-flex;
                 display: flex;
                 margin: 0;
                 padding: 10px;
                 list-style: none;
                 background:red;
             }

             .container li {
                 background: hotpink;
                 width: 100px;
                 height: 100px;
                 border: 1px solid black;
                 text-align: center;
             }

             .container li:nth-child(3) {
                 -webkit-order: 3;
                 order: 3;
             }

             .container li:nth-child(4) {
                 -webkit-order: 2;
                 order: 2;
             }

             .container li:nth-child(5) {
                 -webkit-order: 1;
                 order: 1;
             }

         </style>
     ```

5. 效果图

   ![](http://opzv089nq.bkt.clouddn.com/17-8-20/92684398.jpg)

### 6、align-self(常用)

1. 作用

   ```
   每个子容器也可以单独定义沿交叉轴排列的方式，此属性的可选值与父容器 align-items 属性完全一致，如果两者同时设置则以子容器的 align-self 属性为准
   ```

2. 语法格式

   ```
   align-self: auto | flex-start | flex-end | center | baseline | stretch
   ```

3. 可选值说明

   | 可选值        | 说明                                       |
   | ---------- | ---------------------------------------- |
   | auto       | 默认值。元素继承了它的父容器的 align-items 属性。如果没有父容器则为 "stretch"。 |
   | flex-start | 起始端对齐                                    |
   | flex-end   | 末尾段对齐                                    |
   | center     | 居中对齐                                     |
   | baseline   | 基线对齐                                     |
   | stretch    | 拉伸对齐                                     |

4. 示例代码(参考align-items)

## 四、综合案例

1. ​
2. ​

## 参考资料

1. https://css-tricks.com/snippets/css/a-guide-to-flexbox/
2. https://developer.mozilla.org/en-US/docs/Web/CSS/justify-content