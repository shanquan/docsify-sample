> 本文由 [简悦 SimpRead](http://ksria.com/simpread/) 转码， 原文地址 [www.cnblogs.com](https://www.cnblogs.com/goloving/p/13220359.html)

　　直接想在 div 上监听键盘事件是不行的，但是比如 input 那些是可以的，为什么？等会解释

一、解决方案

　　如果需要在 div 上监听键盘事件怎么办呢？

　　其实也很简单，只需要在需要监听 keydown 事件的 div 的属性中加上 tabIndex=0 即可，即：

```
<div tabindex="0" οnkeydοwn="alert('keydown');">...</div>

```

二、tabindex 属性的作用

　　**当使用键盘时，tabindex 是个关键因素，它用来定位 html 元素**。

　　tabindex 有三个值：0 ，-1， 以及 X（X 里 32767 是界点，稍后说明）

　　原本**在 Html 中，只有链接 a 和表单元素可以被键盘访问（即使是 a 也必须加上 href 属性才可以)，但是 aria 允许 tabindex 指定给任何 html 元素**。

　　**当 tabindex=0 时，该元素可以用 tab 键获取焦点，且访问的顺序是按照元素在文档中的顺序来 focus，即使采用了浮动改变了页面中显示的顺序，依然是按照 html 文档中的顺序来定位**。

　　当 tabindex=-1 时，该元素用 tab 键获取不到焦点，但是可以通过 js 获取，这样就便于我们通过 js 设置上下左右键的响应事件来 focus，在 widget 内部可以用到。

　　当 tabindex>=1 时，该元素可以用 tab 键获取焦点，而且优先级大于 tabindex=0；不过在 tabindex>=1 时，数字越小，越先定位到。

　　在 IE 中，tabindex 范围在 1 到 32767 之间（包括 32767），在 FF， Chrome 无限制，不过一旦超出 32768，顺序跟 tabindex=0 时一样。这个估计跟各个浏览器对 int 型的解析有关。