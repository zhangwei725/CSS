# CSS概述

## 一、什么是CSS?​	

1. CSS 指层叠样式表 (**C**ascading **S**tyle **S**heets)
2. 样式定义**如何显示** HTML 元素
3. 样式通常存储在**样式表**中
4. 把样式添加到 HTML 4.0 中，是为了**解决内容与表现分离的问题**
5. **外部样式表**可以极大提高工作效率
6. 外部样式表通常存储在 **CSS 文件**中
7. 多个样式定义可**层叠**为一

## 二、为何使用CSS？

​	CSS帮助您将文档信息的内容 和如何展现它的细节相分离,如何展现文档的细节即为样式(style)。您可以将样式从它的内容分离出来，能使我们在开发中：

1. 避免重复


1. 更容易维护

## 三、发展史

1. 1996年12月，发布了CSS 1.0规范。


1. 1998年 5月，发布了CSS 2.0规范。
2. 2004年 6月，发布了CSS 2.1规范。
3. 2011年 9月，发布了CSS 3.0规范。

## 四、如何使用CSS

### 1、外部样式表(External style sheet)

1. 说明

   ```
   就是把css样式代码写在单独的一个文件中,文件以“.css”为扩展名，在 head 标签内使用 link 标签,将 css 样式文件链接到HTML文件内,当样式需要应用于很多页面时，一般我们都会使用外部样式表
   ```

   ​

2. 示例代码

   ```html
   <head>
   	<link href="css/style.css"  rel="stylesheet" type="text/css">
   </head>
   ```

3. 特点

   ```
   1、外部式css样式，写在单独的一个文件中
   2、
   ```

4. 注意事项

   1、css样式文件名称以有意义的英文字母命名，如 main.css。

   2、rel="stylesheet" type="text/css" 是固定写法不可修改。
   3、link 标签位置一般写在 head 标签之内最上面。

### 2、内部样式表(Internal style sheet)

1. 说明

   ```
   	把样式代码写在 <style type="text/css"></style> 标签之间,当单个文档需要特殊的样式时，就应该使用内部样式表,我们可以使用 <style> 标签在文档头部定义内部样式表
   ```

2. 示例代码

   ```
   <head>
     <style type="text/css">
           div{
               width: 50px;
               height: 50px;
               background: red;
           }
       </style>
   </head>
   ```

3. 注意：

   ```
   嵌入式css样式必须写在 <style></style> 之间，并且一般情况下内部样式写在 <head></head> 之间
   ```

### 3、内联样式(Inline style)

1. 说明

   内联式css样式，直接写在在HTML标签中，同时css样式代码写在 style="" 双引号中，如果有多条css样式代码设置可以写在一起，中间用分号 ; 隔开。当样式只在一个元素使用一次时,可以直接元素上使用sytle属性,由于内连样式跟内容混合在一起,一般在开发中尽量去使用

2. 示例代码

   ```
   <div style="width:50px;
               height:50px;
               background:red">
   </div>
   ```

### 4、多重样式(样式继承)

1. 说明

   ```
   如果某些属性在不同的样式表中被同样的选择器定义，那么属性值将从更具体的样式表中被继承过来
   ```

2. 示例代码

   ```
    <head>
       <style type="text/css">
           p{
               color:red;
               text-align:center;
               font-size:16px;
           }
           p{
               font-size:20px;
           }
       </style>
   </head>
   ```

   那么最终我们设置的p标签的样式应该为

   ```
   p{
    color:red;
    text-align:center;
    font-size:20px;
   }
   ```

3. 一般情况下的优先级

   ```
   内联样式）Inline style > （内部样式）Internal style sheet >（外部样式）External style sheet > 浏览器默认样式
   ```

### 5、权重计算

1. 详细说明查看网站

   http://www.nowamagic.net/librarys/veda/detail/1606

2. 经验

   1、要优化考虑使用样式规则的优先级来解决问题而不是 !important

   2、永远不要在全站范围的 css 上使用!important

   3、 永远不要在你的插件中使用 !important



