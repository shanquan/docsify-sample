> 本文由 [简悦 SimpRead](http://ksria.com/simpread/) 转码， 原文地址 [blog.csdn.net](https://blog.csdn.net/qq_33744228/article/details/80910377)

Emmet—写 HTML/CSS 快到飞起
=====================

在前端开发的过程中，最费时间的工作就是写 HTML、CSS 代码。一堆的标签、属性、括号等，头疼。这里推荐一个 Emmet 语法规则，让你写的时候爽到飞起，能大大提高代码书写，只需要敲一行代码就能生成你想要的完整 HTML 结构，下面会介绍如何使用。

Emmet 是一款插件，只要能安装他的编辑器都能使用，大部分编辑器都可以使用该语法规则, 我们平时开发的`Sublime Text`、`Eclipse`、`Notepad++`、`VS code`、`Atom`、`Dreamweaver`等等编辑器都可以使用。

安装方式和平时安装插件一样搜索这个 emmet 插件安装，每个编辑器安装方式不同，请各自尝试

#### 先来个例子：

![](https://img-blog.csdn.net/20180704125033835?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzMzNzQ0MjI4/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
这个普通的 HTML 结构，你需要多久打出来呢？  
我只需要**几秒钟**，写好下面这条语句，按下键盘`Tab`键即可看到上图中的结构了

```
div#box>p.title+ul.list>li.child${我是第$个}*3^div#box2

```

是不是很爽，很快~~ 啊 ~ 啊~，仅仅一行代码就生成了一个复杂的 HTML 结构，并且 id，class，内容都对应的上

开始讲解语法吧
-------

### 1：html 初始结构

下图中的结构，偷懒的都会直接一个！=> Tab 解决，这样可以快速生成基础的结构，同时防止手写时忘记某个代码块，输入错误的代码。  
![](https://img-blog.csdn.net/20180704125559312?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzMzNzQ0MjI4/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

### 2：id（#）,class（.）

`id指令:# ; class指令:.`

*   **div#test**

```
<div id="test"></div>

```

*   **div.test**

```
<div class="test"></div>

```

### 3：子节点（>），兄弟节点（+），上级节点（^）

`子节点指令:> ; 兄弟节点指令:+ ; 上级节点:^`

*   **div>ul>li>p**

```
<div>
   <ul>
     <li>
       <p></p>
     </li>
   </ul>
 </div>

```

*   **div+ul+p**

```
<div></div>
<ul></ul>
<p></p>

```

*   **div>ul>li^div** (这里的`^`是接在`li`后面所以在`li`的上一级，与`ul`成了兄弟关系, 当然两个 ^^ 就是上上级）

```
<div>
   <ul>
     <li></li>
   </ul>
   <div></div>
 </div>

```

### 4：重复（*）

`重复指令：*`

*   div*5（*** 号后面添加数字表示重复的元素个数**）

```
   <div></div>
   <div></div>
   <div></div>
   <div></div>
   <div></div>

```

### 5：分组（()）

`分组指令：()`

*   div>(ul>li>a)+div>p  
    （**括号里面的内容为一个代码块，表示与括号内部嵌套和外面的的层级无关**）

```
<div>
   <ul>
     <li><a href=""></a></li>
   </ul>
   <div>
     <p></p>
   </div>
 </div>

```

解释：这里如果不加括号的话，猜想下，`a+div`这样 div 就是和 a 是兄弟关系了，会包含在 li 里面。懂了吧哈哈

```
 <div>
   <ul>
     <li>
       <a href=""></a>
       <div>
         <p></p>
       </div>
     </li>
   </ul

```

### 6：属性（[attr]）——id，class 都有怎么能少了属性呢

`属性指令：[]`

*   a[href=’###’ name=‘xiaoA’] （**中括号内填写属性键值对的形式，并且空格隔开**）

```
<a href="###" ></a>

```

###6：编号（$）  
`编号指令：$`

*   ul>li.test$*3 （**$ 代表一位数，后面更上 * 数字就代表从 1 递增到填写的数字**）

```
 <ul>
   <li class="test1"></li>
   <li class="test2"></li>
   <li class="test3"></li>
 </ul>

```

**注意**：

*   一个 $ 代表一位数， 
    
    $$就是两位数了,以此类推就可以形成$(1),$$
    
    (01),$$$(001)
*   如果想自定义从几开始递增的话就利用：$@+ 数字 * 数字  
    例如：ul>li.test$@3*3

```
 <ul>
   <li class="test3"></li>
   <li class="test4"></li>
   <li class="test5"></li>
 </ul>

```

### 7：文本（{}）

`文本指令：{}`

*   ul>li.test$*3{测试 $} （**{里面填写内容，可以和 $ 一起组合使用哦}**）

```
<ul>
  <li class="test1">测试1</li>
  <li class="test2">测试2</li>
  <li class="test3">测试3</li>
</ul>

```

### 8：隐式标签

这个标签没有指令，而是部分标签可以不使用输入标签，直接输入指令，即可识别父类标签。

**默认 div** 例如：`.test`

```
<div class="test"></div>

```

**li**： 可在 ul 和 ol 中使用 例如：`ul>.test$*3`

```
 <ul>
   <li class="test1"></li>
   <li class="test2"></li>
   <li class="test3"></li>
 </ul>

```

**option**：可在 select 中使用例如：`select>.test$*5`

```
<select >
  <option class="test1"></option>
  <option class="test2"></option>
  <option class="test3"></option>
  <option class="test4"></option>
  <option class="test5"></option>
</select>

```

等等…

*   **tr**：可在 table、tbody、thead 和 tfoot 中使用
*   **td**：可在 tr 中使用

最后就是：**看没用，操作几遍，几分钟你就能掌握这些指令，然后飞快的撸码**