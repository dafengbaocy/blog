# day1 
## 描述型列表 
[链接](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Introduction_to_HTML/Advanced_text_formatting) 
&emsp;注意的点：一个术语可以同时有多个描述，如： 
~~~html
<dl>
  <dt>旁白</dt>
  <dd>
    戏剧中，为渲染幽默或戏剧性效果而进行的场景之外的补充注释念白，只面向观众，内容一般都是角色的感受、想法、以及一些背景信息等。
  </dd>
  <dd>
    写作中，指与当前主题相关的一段内容，通常不适于直接置于内容主线中，因此置于附近的其他位置（通常位于主线内容旁边一个文本框内）。
  </dd>
</dl> 
~~~ 
此时，`dd`和`p`元素效果相同，都起到了分段作用 
## 引用 
 * 块引用 (`<blockquote>`)
&emsp;注意的点：cite属性渲染后啥也不显示，且引用的段首会<font color=#ff0000><strong>自动缩进</font></strong>，如以下例子： 
``` 
<p>Here is a blockquote:</p>
<blockquote
  cite="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/blockquote">
  <p>
    The <strong>HTML <code>&lt;blockquote&gt;</code> Element</strong> (or
    <em>HTML Block Quotation Element</em>) indicates that the enclosed text is
    an extended quotation.
  </p>
</blockquote>
``` 

&emsp;渲染后效果如下：
<p>Here is a blockquote:</p>
<blockquote
  cite="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/blockquote">
  <p>
    The <strong>HTML <code>&lt;blockquote&gt;</code> Element</strong> (or
    <em>HTML Block Quotation Element</em>) indicates that the enclosed text is
    an extended quotation.
  </p>
</blockquote> 

* 行引用(`<q>`)
&emsp; 和块引用类似，也会有相同缩进。
## 缩略语(`<abbr>`) 
&emsp;属性`title`：当鼠标放在特定缩略语上，出现提示，类似于超链接`<a>`的**title**属性
## 地址(`<address>`) 
&emsp;感觉没什么用，除了字体变为斜体； 
关于:
>`<address>`元素只能用于提供最近的`<article>` 或 `<body>` 元素所含文件的联系信息。在一个网站的页脚使用它来包括整个网站的联系信息，或者在一篇文章里面使用它来包括作者的联系信息，这都是正确的，但不能用来标记与该页面内容无关的地址列表。
> 
不是很懂
## 上标和下标
*上标(`<sup>`) 
*上标(`<sub>`) 
## 展示计算机代码 
[链接](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Introduction_to_HTML/Advanced_text_formatting) 
## 标记日期和时间 
`<time datetime=''> 用于描述时间的你自己喜欢的方式</time>` 
为什么要这样写：方便计算机抓取