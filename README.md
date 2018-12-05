

[MarkDoc／标档（v0.7）][MarkDoc]
================================

— A Markdown-like [jDoc]-based e-book writing format by [LongTengDao][LTD].  
—— 一个由 [龙腾道][LTD] 研发，基于 [jDoc]，类 Markdown 的电子书编纂格式。

[LTD]: http://www.LongTengDao.com/
[jDoc]: https://GitHub.com/LongTengDao/jDoc/
[MarkDoc]: https://GitHub.com/LongTengDao/MarkDoc/
[jMarkDoc]: https://GitHub.com/LongTengDao/jMarkDoc/


TOC／目录
---------

1.	[Philosophy／哲学](#user-content-1)
	
2.	[Syntax Specification／语法规范](#user-content-2)
	
	1.	[Paragraph／段落](#user-content-2.1)
	2.	[Outline Tree／大纲树](#user-content-2.2)
	3.	[List Tree／列表树](#user-content-2.3)
		1.	[Basic List／普通列表](#user-content-2.3.1)
		2.	[Ordered List／序号列表](#user-content-2.3.2)
		3.	[Named List／具名列表](#user-content-2.3.3)
		4.	[Foldable List／折叠列表](#user-content-2.3.4)
	4.	[Table／表格](#user-content-2.4)
	5.	[Pre-fomatted Block／预格式块](#user-content-2.5)
		1.	[Highlight Code／源码高亮](#user-content-2.5.1)
		2.	[Renderable Code／脚本渲染](#user-content-2.5.2)
		3.	[Math Formula／数学公式](#user-content-2.5.3)
		4.	[Media Embed／嵌入多媒体](#user-content-2.5.4)
	6.	[Semantic–Style Block／语义样式块](#user-content-2.6)
		1.	[Horizontal Line／水平线](#user-content-2.6.1)
		2.	[Block Quote／引文](#user-content-2.6.2)
		3.	[Figure／插注](#user-content-2.6.3)
		4.	[Custom Field Set／自定义容器](#user-content-2.6.4)
	7.	[Inline／行内语法](#user-content-2.7)
		1.	[Row Style／行样式](#user-content-2.7.1)
		2.	[Text Style／字样式](#user-content-2.7.2)
		3.	[Link／超链接](#user-content-2.7.3)
		4.	[Image／表情图](#user-content-2.7.4)
		6.	[Todo／待办项](#user-content-2.7.5)
	8.	[Decorator／装饰器](#user-content-2.8)
		1.	[Inline Decorator／行内装饰器](#user-content-2.8.1)
		2.	[Block Decorator／块级装饰器](#user-content-2.8.2)
	9.	[Context Syntax／上下文语法](#user-content-2.9)
	
3.	[Filename Extension／文件扩展名](#user-content-3)
	
4.	[Standard Implementation／标准实现](#user-content-4)


[1. Philosophy／哲学](#user-content-1)<a id="user-content-1">&nbsp;</a>
---------------------


&nbsp; &nbsp; &nbsp;MarkDoc's underlying format, jDoc, is a format invented for writing books on almost any scale. For book writing, it is acceptable to freely use the most appropriate symbols for each book, and to write a separate typesetting program for each book. But when writing small things like articles, posts, and even comments, or compiling medium-sized papers or technical documents with relatively fixed purposes, this is awkward and unsafe.

&nbsp; &nbsp; &nbsp;MarkDoc is the very solution for this problem. It's sort of a dialect of jDoc, with the most useful symbolic functionalities built-in.


&nbsp; &nbsp; &nbsp;The choice of symbols in MarkDoc mainly draws on Markdown (and extra syntax from various implementations), which is a very reasonable combination of historical practices. In addition,

*	Block-level media syntax (`::` add Tab) is derived from not only emoji syntax in Markdown on GitHub. but also the file including syntax in AsciiDoc;
*	Inline media syntax (`{{ picture_address }}`) reference the Mustache interpolation syntax;
*	Unicode characters eval syntax (such as `<U+000A>`) refer to the Unicode standard notation, so as to avoid the `\` with both escape and eval function, which is really confusing.

&nbsp; &nbsp; &nbsp;Other symbols not mentioned above come from personal practical experience based on general reason.


**Note:**

&nbsp; &nbsp; &nbsp;MarkDoc is based on the jDoc format, so a valid MarkDoc document should first be a well-formatted jDoc document. Although jDoc is a very, very simple format (with almost only two key rules, line feed and tab indentation), if you don't pay attention, it's still possible to get a WTF rendering result.

&nbsp; &nbsp; &nbsp;The biggest difference between jDoc and Markdown is that jDoc is sensitive to indentation of empty lines. Therefore, when reading this documentation (and writing books or articles using MarkDoc), you should pay particular attention to how many tabs there are in the empty lines of the example code blocks (on GitHub, you can only check this by select the text, to see how wide the blue background is).


__________


　　MarkDoc 的底层格式 jDoc，是一个为写几乎任意规模的电子书而发明的文档格式。对于书籍撰写，因地制宜而自由地使用最为合适的符号，并为每本书单独写一个排版解释器是可以接受的。但是在书写小型文章、帖子乃至评论时，或编纂用途相对固定的中型论文或技术文档时，这就实在不便，而且不安全。

　　而 MarkDoc 正是为了解决这个问题而生的。它可以算是 jDoc 的一种方言，内置了上述特定场景中最为实用的符号功能。


　　MarkDoc 中的符号选用，主要借鉴了集历史实践之大成、实在太合理的 Markdown（及各种实现自行扩充的语法）。此外，

*	块级多媒体语法（`::` 加 Tab）参考了 GitHub 上 Markdown 的表情图语法的同时，也参照了 AsciiDoc 中的文件引用语法；
*	行内表情图语法（`{{ 图片地址 }}`）参考了 Mustache 插值语法标记；
*	Unicode 字符估值语法（如 `<U+000A>`）参考了 Unicode 的标准写法，从而避免了 `\` 既有转义功能、又有估值功能的混乱局面。

　　其它以上没有提及的符号，来自基于一般理性的个人实践经验。


**注意：**

　　MarkDoc 是基于 jDoc 格式的，因此一个有效的 MarkDoc 文档首先应当是一个良好的 jDoc 文档。虽然 jDoc 是一个非常非常简单的文档格式（几乎只有换行和 Tab 缩进两个关键规则），但是如果不注意，却可能得到荒腔走板的渲染结果。

　　jDoc 与 Markdown 最大的区别，就是对空行的缩进情况敏感。因此，在阅读本文档（以及使用 MarkDoc 撰写书籍、文章）时，应当尤其注意示例代码块中，貌似空行的位置究竟有多少个 Tab（在 GitHub 上，你可能只能通过选中这些文字，看蓝色背景的部分有多宽，来确认这一点）。


[2. Syntax Specification／语法规范](#user-content-2)<a id="user-content-2">&nbsp;</a>
-----------------------------------


### [2.1 Paragraph／段落](#user-content-2.1)<a id="user-content-2.1">&nbsp;</a>

````markdoc
Paragraph 1 row 1
Paragraph 1 row 2

Paragraph 2 row 1 \
Paragraph 2 row 1 rest
````


### [2.2 Outline Tree／大纲树](#user-content-2.2)<a id="user-content-2.2">&nbsp;</a>

````markdoc
===============
Article heading
文章标题
===============


Chapter 1 heading
第 1 章标题
-------	
	
	
	Section 1.1 heading
	第 1 节标题
	-------	
		
		Paragraph
		段落
	
	
	Section 1.2 heading
	-------	
		
		Paragraph


Chapter 2 heading row 1
Chapter 2 heading row 2
-------	
	
	
	Section 2.1 (in exclusive page) heading (also as link text in menu bar)
	第 2.1 节（位于独立页面）标题（也作为菜单栏链接文字）
	+++++++	
		
		Paragraph
	
	
	Section 2.2 link text in menu bar (specify it separately)
	第 2.2 节菜单栏链接文字（单独指定）
	+++++++	
		
		Section 2.2 heading (specify it separately)
		第 2.2 节标题（单独指定）
		===================
		
		Paragraph

````


### [2.3 List Tree／列表树](#user-content-2.3)<a id="user-content-2.3">&nbsp;</a>

#### [2.3.1 Basic List／普通列表](#user-content-2.3.1)<a id="user-content-2.3.1">&nbsp;</a>

````markdoc
*	list item 1 row 1
	list item 1 row 2
	
*	list item 2 row 1
	list item 2 row 2
	
*	list item 3 paragraph
	
	*	sub list 1 item 1
	*	sub list 1 item 2
	
	list item 3 paragraph
````

#### [2.3.2 Ordered List／序号列表](#user-content-2.3.2)<a id="user-content-2.3.2">&nbsp;</a>

````markdoc
1.	ordered list item 1 row 1
	ordered list item 1 row 2
2.	ordered list item 2
3.	ordered list item 3
````

````markdoc
1.	ordered list style 1-1
A.	ordered list style 2-1
a.	ordered list style 3-1
I.	ordered list style 4-1
i.	ordered list style 5-1

(1)	ordered list style 1-2
(A)	ordered list style 2-2
(a)	ordered list style 3-2
(I)	ordered list style 4-2
(i)	ordered list style 5-2

1)	ordered list style 1-3
A)	ordered list style 2-3
a)	ordered list style 3-3
I)	ordered list style 4-3
i)	ordered list style 5-3
````

#### [2.3.3 Named List／具名列表](#user-content-2.3.3)<a id="user-content-2.3.3">&nbsp;</a>

````markdoc
term 1
:	term 1 description paragraph
term 2
:	term 2 description 1 paragraph
:	term 2 description 2 paragraph
term 3
term 4
:	term 3 & 4 description paragraph
````

#### [2.3.4 Foldable Tree／折叠列表](#user-content-2.3.4)<a id="user-content-2.3.4">&nbsp;</a>

````markdoc
summary (default open)
-	
	detail paragraph
	
summary (default fold)
+	
	detail paragraph
````

````markdoc

-	summary (default open)
	======================
	
	detail paragraph
	
	
+	summary (default fold)
	======================
	
	detail paragraph
	
````


### [2.4 Table／表格](#user-content-2.4)<a id="user-content-2.4">&nbsp;</a>

````markdoc
|	cell	cell
|	cell	cell
````

````markdoc
|_	head	head
|	cell	cell
|	cell	cell
````

````markdoc
|_	head	head
|	cell	cell
|_	cell	cell
|	foot	foot
````

````markdoc
|_	head	head
|	cell	cell
|_	cell	cell
|	foot	foot
|=	Table Caption (below)
````

````markdoc
|=	Table Caption (above)
|_	head	head
|	cell	cell
|_	cell	cell
|	foot	foot
````

````markdoc
|	cell	cell
	cell	cell
	cell	cell
````


### [2.5 Pre-fomatted Block／预格式块](#user-content-2.5)<a id="user-content-2.5">&nbsp;</a>

#### [2.5.1 Highlight Code／源码高亮](#user-content-2.5.1)<a id="user-content-2.5.1">&nbsp;</a>

````markdoc
```	.codeType
	code row 1
	code row 2
	code row 3
````

````markdoc
```	.codeType
	code row 10
11	code row 11
	code row 12
````

````markdoc
```	.codeType
	code row 10
11	code row 11
	code row 12
...	
	code row 19
20	code row 20
	code row 21
	code row 22
````

&nbsp; &nbsp; &nbsp;Code block which type is not implemented, should be implemented as plain (no highlight) by default.  
　　渲染组件未实现的代码块，应当被默认实现为纯文本（无高亮）。

#### [2.5.2 Renderable Code／脚本渲染](#user-content-2.5.2)<a id="user-content-2.5.2">&nbsp;</a>

````markdoc
~~~	rendererName.codeType
	code row 1
	code row 2
````

&nbsp; &nbsp; &nbsp;Examples (just examples, not promised, each type need implementation supporting):  
　　例子（仅仅是例子，不做保证，每种类型都需要实现支持）：

````markdoc
~~~	.html
	<button onclick="alert('I am a html fragment.');">click me</button>
````

````markdoc
~~~	.css
	strong {
		font-weight: normal;
		font-family: 黑体, STXihei;
	-webkit-text-emphasis: filled circle;
		text-emphasis: filled circle;
	-webkit-text-emphasis-position: under right;
		text-emphasis-position: under right;
	}
````

````markdoc
~~~	.rst
	+---------+--------+----------+
	| group   | item   |   desc   |
	+=========+========+==========|
	|         | item 1 | - desc 1 |
	| group 1 +--------+ - desc 2 |
	|         | item 2 | - desc 3 |
	+---------+--------+----------+
````

````markdoc
~~~	gantt
	
	dateFormat	YYYY-MM-DD
	
	title	Plan
	
	section	A
		task 1:	done,	1979-01-01,	2000-01-01
		task 2:	active,	1990-06-01,	28d
		task 3:		2018-11-26,	1d
	
	section	B
````

&nbsp; &nbsp; &nbsp;Renderable code block which renderer is not implemented, should be implemented by default like:  
　　渲染组件未实现的可渲染代码块，应当被默认实现为类似：

~~~~html
<fieldset>
	<legend>rendererName.codeType</legend>
	pre code, highlight better (if code type is implemented)
</fieldset>
~~~~

#### [2.5.3 Math Formula／数学公式](#user-content-2.5.3)<a id="user-content-2.5.3">&nbsp;</a>

````markdoc
$$	formula expression row 1
	formula expression row 2
````

&nbsp; &nbsp; &nbsp;It is short for (not promised, everything could be customed):  
　　它是下面形式的简写（不做保证，任何东西都可能被自定义过）：

````markdoc
~~~	math
	formula expression row 1
	formula expression row 2
````

#### [2.5.4 Media／多媒体](#user-content-2.5.4)<a id="user-content-2.5.4">&nbsp;</a>

````markdoc
::	./small.png
````

````markdoc
::	./small.png
	
	Alternative text description of the image, like ":)".
	The description could be multi-line, but only treated as plain.
	
	图片的替代文本描述，比如“:)”。
	描述可以多行，不过只会被作为纯文本对待。
````

````markdoc
::	audio/ogg	./laugh.ogg
	audio/mpeg	./laugh.mp3
	audio/wav	./laugh.wav
	
	Alternative information, like "Your browser does not support audio."
	Not only plain.
	
	替代信息，诸如“你的浏览器不支持音频”。
	不限于纯文本。
````

&nbsp; &nbsp; &nbsp;This is also ok:  
　　这样也行：

````markdoc
::	video/	./laugh
	ogg	.ogv
	mp4	.mp4
	webm	.webm
	
	Your browser does not support video.
	你的浏览器不支持视频。
````

&nbsp; &nbsp; &nbsp;The syntax of audio and video is more complex than image, this is because the file types supported by each browser are different, maybe you want to apply them all. If you don't mind that, you can just write:  
　　音频和视频的写法比图片复杂，这是因为不同浏览器支持的文件种类不同，可能你会想要逐一指定。如果你的用途中不包含这一点，那么你可以简写为：

````markdoc
::	video	./laugh.mp4
````


### [2.6 Semantic–Style Block／语义块](#user-content-2.6)<a id="user-content-2.6">&nbsp;</a>

### [2.6.1 Horizontal Line／水平线](#user-content-2.6.1)<a id="user-content-2.6.1">&nbsp;</a>

````markdoc
***

---

___
````

#### [2.6.2 Block Quote／引文](#user-content-2.6.2)<a id="user-content-2.6.2">&nbsp;</a>

````markdoc
>	block quote 1 row 1
>	block quote 1 row 2

>	block quote 2 row 1
	block quote 2 row 2

>	block quote 3 row 1
	block quote 3 row 2
>	block quote 3 row 3
````

#### [2.6.3 Figure／插注](#user-content-2.6.3)<a id="user-content-2.6.3">&nbsp;</a>

&nbsp; &nbsp; &nbsp;In syntax, figure is a named list item without name.  
　　从语法的角度看，插注是一个没有名的具名列表项。

&nbsp; &nbsp; &nbsp;Semantically, it's usually used for illustration, which has not a precise position, just for reference. Of cause, there could be a appendix table inside, or anything else.  
　　从语义的角度讲，它通常用于插图，而且是那种在行文中没有精确位置，只是供参考的插图。当然，里面也可以放附录表，或其它任何东西。

````markdoc
:	FigCaption (above)
	====================================================================================================
	|_	No	English                                  	简体中文
	|	01	Oh stranger, tell the Lacedaemonians that	过路人，请捎个口信给斯巴达人，告诉他们，
	|	02	we lie here, obedient to their words.    	为了他们的嘱托，我们躺在这里。
````

````markdoc
:	::	./small.png
	
	FigCaption (below)
	==================
````

````markdoc
:	$$	E=mc^2
	=======================
	Mass–Energy Equivalence
````

````markdoc
:<-	left float／居左（文字右侧环绕）

->:	right float／居右（文字左侧环绕）
````

#### [2.6.4 Custom Field Set／自定义容器](#user-content-2.6.4)<a id="user-content-2.6.4">&nbsp;</a>

````markdoc
type	content paragraph 1
	
	content paragraph 2
````

&nbsp; &nbsp; &nbsp;Examples (you need to implement it via the programming api by yourself!):  
　　例子（你需要通过编程接口自己实现！）：

````markdoc
!	Mixed-types array is invalid! (Probably an error block)
````

````markdoc
#	Note that mixed-types array is not recommended! (Probably a warning block)
````

&nbsp; &nbsp; &nbsp;Block level symbols that not implemented, should be implemented by default like:  
　　未实现的块级符号，应当被默认实现为类似：

~~~~html
<fieldset>
	<legend>type</legend>
	content paragraph
</fieldset>
~~~~


### [2.7 Inline／行内语法](#user-content-2.7)<a id="user-content-2.7">&nbsp;</a>

#### [2.7.1 Row Style／行样式](#user-content-2.7.1)<a id="user-content-2.7.1">&nbsp;</a>

````markdoc
     5en indent row (usually used in English)
　　2em 缩进的行（通常用在中文里）

|-> Center align row <-|
|-> 居中对齐的行 <-|

|-> Right align row (method 1) ->|
|-> 右对齐的行（方式一） ->|

Right align row (method 2) ->|
右对齐的行（方式二） ->|

|-> Right align row (method 3)
|-> 右对齐的行（方式三）
````

#### [2.7.2 Text Style／字样式](#user-content-2.7.2)<a id="user-content-2.7.2">&nbsp;</a>

| MarkDoc                     | Preview<br>预览                 | Explain／解释                                                  |
|:---------------------------:|:-------------------------------:|----------------------------------------------------------------|
| `normal`                    | normal                          |                                                                |
| <code>pre&nbsp;&nbsp;spaces</code> | pre&nbsp;&nbsp;spaces    | Two or more spaces is reserved.／连续多个空格会被保留。        |
| `__strong__`                | __strong__                      |                                                                |
| `*emphasize*`               | *emphasize*                     |                                                                |
| `\*escaped*`                | \*escaped*                      | The back slash is the escape symbol.／反斜杠是转义符号。       |
| `<U+9F99>`<br>`<U+D842+DFB7>`<br>`<U+20BB7>` | 龙<br>𠮷<br>𠮷 | Unicode escape format is allowed.／允许使用 Unicode 转义格式。 |
| `~~delete~~`                | ~~delete~~                      |                                                                |
| `++insert++`                | <ins>insert</ins>               |                                                                |
| `normal^^sup^^`             | normal<sup>sup</sup>            |                                                                |
| `normal//sub//`             | normal<sub>sub</sub>            |                                                                |
| `很𠮷<ji2>利`               | 很<ruby>𠮷<rt>jí</rt></ruby>利 | `很<U+20BB7><ji2>利` should also be parsed correctly.<br>`很<U+20BB7><ji2>利` 也应当能够被正确解析。 |
| <code>\` code \`</code><br><code>\`\\\`<U+9F99>\\\`\`</code> | <code>\`&nbsp;code&nbsp;\`</code><br><code>\`龙\`</code> | Codes quoted by single back quote are allowed to contain escape format.<br>单个反引号包裹的代码允许包含转义。 |
| <code>\`\` \\\` \`\`</code><br><code>\`\` \`\`\` \`\`</code><br><code>\`\`&nbsp;&nbsp;\`\`\`&nbsp;&nbsp;\`\`</code> | <code>\\\`</code><br><code>\`\`\`</code><br><code>&nbsp;\`\`\`&nbsp;</code> | Code quoted by two or more back quotes are not allowed to contain escape format, and must be wrapped inside by one space on each side, which will be trimmed.<br>两个以上反引号包裹的代码不允许包含转义，并且内侧必须各有一个会被剔除的空格。 |
| `$E=mc^2$`               | *E＝mc<sup><small>2</small></sup>* | Math expressions wrapped by dollar will not parse escaped characters at all.<br>由美元包裹的数学表达式完全不解释字符转义。 |

&nbsp; &nbsp; &nbsp;And some GitHub not support for previewing:  
　　以及一些 GitHub 不支持预览的：

|       MarkDoc                                    |       HTML                                                                              |
|--------------------------------------------------|-----------------------------------------------------------------------------------------|
| `==mark==`                                       | `<mark style="background-color:yellow;">mark</mark>`                                    |
| <code>\|\|bordered\|\|</code>                    | `<span style="border-style:solid;">bordered</span>`                                     |
| `normal^^sup^^//sub//`<br>`normal//sub//^^sup^^` | `normal<small style="display:inline-block;vertical-align:-0.5em;">sup<br />sub</small>` |

#### [2.7.3 Link／超链接](#user-content-2.7.3)<a id="user-content-2.7.3">&nbsp;</a>

|       MarkDoc                                 |       HTML                                                                      |
|-----------------------------------------------|---------------------------------------------------------------------------------|
| `>> www.龙腾道.com <<`                        | `<a href="http://www.xn--r70at71adql.com/" target="_blank">www.龙腾道.com</a>`  |
| `>> 龙腾道 ~> http://www.LongTengDao.com/ <<` | `<a href="http://www.LongTengDao.com/" target="_blank">龙腾道</a>`              |
| `>> top -> # <<`                              | `<a href="#">top</a>`                                                           |
| `>> [ -> home ] -> / <<`                      | `<a href="/"> -> home </a>`                                                     |

&nbsp; &nbsp; &nbsp;The wrapper `>` and `<` can be two or more.  
　　包裹的 `>` 和 `<` 在两个以上就行。

#### [2.7.4 Image／表情图](#user-content-2.7.4)<a id="user-content-2.7.4">&nbsp;</a>

|       MarkDoc                                           |       HTML                                         |
|---------------------------------------------------------|----------------------------------------------------|
| `{{ ./small.png }}`                                     | `<img src="./small.png" />`                        |
| <code>{{ ./small.png \| :) }}</code>                    | `<img src="./small.png" alt=":)" />`               |
| <code>{{ ./small.png \| \` :) \<U+000A> ~~ \` }}</code> | `<img src="./small.png" alt=" :) &#x000A; ~~ " />` |

#### [2.7.5 Todo／待办项](#user-content-2.7.5)<a id="user-content-2.7.5">&nbsp;</a>

| MarkDoc     | checked | color | decoration   | HTML |
|:-----------:|:-------:|:-----:|:------------:|------|
|  `[ ] text` |         |       |              | `<label><input type="checkbox" /> text</label>` |
|  `[-] text` |         | gray  | line-through | `<label style="color:gray;text-decoration:line-through;">`<br>`<input type="checkbox" disabled /> text</label>` |
|  `[v] text` | checked |       |              | `<label><input type="checkbox" checked /> text</label>` |
|  `[x] text` | checked | gray  | line-through | `<label style="color:gray;text-decoration:line-through;">`<br>`<input type="checkbox" checked disabled /> text</label>` |
| `\[x] text` |         |       |              | `[x] text` |
| `[\x] text` |         |       |              | `<span>x</span> text` |


### [2.8 Decorator／装饰器](#user-content-2.8)<a id="user-content-2.8">&nbsp;</a>

#### [2.8.1 Inline Decorator／行内装饰器](#user-content-2.8.1)<a id="user-content-2.8.1">&nbsp;</a>

````markdoc
*MarkDoc*{: title=`a kind of e-book writing format` .coinage } is a { .coinage :}[markdown]{: title=`relative to markup` } style language.
\
{ .row-class }to parent if there is no previous／无前即父{ .行样式 }
\
*MarkDoc*{: title=`一种电子书撰写格式` .生造词 } 是一个 { .生造词 :}[markdown]{: title=`相对于 markup 而言` } 风格的语言。
````

&nbsp; &nbsp; &nbsp;means (in HTML):  
　　意味着 HTML 中的：

````html
<p>
	<span style="display:block;">
		<em title="a kind of e-book writing format" class="coinage">MarkDoc</em> is a 
		<span title="relative to markup" class="coinage">markdown</span> style language.
	</span>
	<span style="display:block;" class="row-class 行样式">
		to parent if there is no previous／无前即父
	</span>
	<span style="display:block;">
		<em title="一种电子书撰写格式" class="生造词">MarkDoc</em> 是一个 
		<span title="相对于 markup 而言" class="生造词">markdown</span> 风格的语言。
	</span>
</p>
````

#### [2.8.2 Block Decorator／块级装饰器](#user-content-2.8.2)<a id="user-content-2.8.2">&nbsp;</a>

````markdoc
paragraph block
>>>	.paragraph-class

heading
=======
>>>	.heading-class-1 title=`I'm heading.`
>>>	.heading-class-2

heading
>>>	.heading-class
---	>>>	.section-class

>>>	.article-class

*	>>>	.ul-li-1-class
*	>>>	.ul-li-2-class
>>>	.ul-class
````


### [2.9 Context Syntax／上下文语法](#user-content-2.9)<a id="user-content-2.9">&nbsp;</a>

````markdoc
I need two auto ordered ["footnote"]{: mean }, the first#n#, and the second#[*Inline* format for simple content.]#.
You ask why?
Watch >>>wall<<< and ponder it. :small:

我需要两个自动编号的[“脚注”]{: mean }，第一个##n##，和第二个##[简单内容的*内联*写法。]##。
你问为什么？
面>>>壁 => wall <<<思之。:small:


#n#	footnote paragraph (can be implemented at footer, sidebar, hover text, pop-up box, etc.)
	脚注段落（可实现于页脚、侧栏、悬停浮框、弹出框等）

:small:	./small.png

>wall<	~> about:blank

{mean}	title=`Not have to display at footer.<LF>不是必须在页脚显示。`

<LF>	<U+000A>
````

&nbsp; &nbsp; &nbsp;You can explicitly specify a position to display the "footnotes" (it's also the page break symbol):  
　　你可以为“脚注”明确指定插入位置（它同时也是分页符）：

````markdoc
^^^

^^^	A4

^^^	A4 A5
````


[3. Filename Extension／文件扩展名](#user-content-3)<a id="user-content-3">&nbsp;</a>
-----------------------------------


`.markdoc`


[4. Standard Implementation／标准实现](#user-content-4)<a id="user-content-4">&nbsp;</a>
--------------------------------------


### Editor／编辑器

&nbsp; &nbsp; &nbsp;For writers, you can edit the MarkDoc file using any text editor. I'm developing [jMarkDoc] (a MarkDoc reader) that will give you a standalone live preview.

&nbsp; &nbsp; &nbsp;Usually these editor software allows you to set the Tab character visible (you can enable the feature for `.markdoc` alone), and this will greatly facilitate the edit of any file format based on jDoc.

&nbsp; &nbsp; &nbsp;Most of them, however, are too smart to automatically remove whitespace characters of empty lines, which can be devastating for MarkDoc that based on jDoc. Unfortunately, many programs don't allow you to turn this feature off. But fortunately, `.editorconfig` allows you to set that, which these text editors that smart enough can also support. `.editorconfig`.

&nbsp; &nbsp; &nbsp;Place an `.editorconfig` file in the folder which the MarkDoc files placed, or their parent folder (unlimited layers), and write in below:

````.editorconfig
# http://editorconfig.org

[*.markdoc]
trim_trailing_whitespace = false
````

&nbsp; &nbsp; &nbsp;Windows prohibit you creating dot files directly, you need to use `.editorconfig.`, then system will automatically trim the ending dot for you.

____

　　对于写作者，你可以使用任何你惯用的文本编辑器软件，来编辑 MarkDoc。我正在开发 MarkDoc 的专用阅读器 [jMarkDoc]，它可以为你提供单独的实时预览。

　　通常这些编辑器软件允许你将 Tab 字符设置为可见（你可以为 `.markdoc` 文件单独开启这项功能），这会大大方便任何基于 jDoc 的文件格式的编辑。

　　不过它们中的多数会过于智能地自动剔除空行中的空白字符，而这对基于 jDoc 的 MarkDoc 来说是毁灭性的。不幸的是，很多软件并不允许你关闭这项功能。而万幸的是，`.editorconfig` 允许你对此进行设置，而这些足够智能的文本编辑器往往也能够支持 `.editorconfig`。

　　在 MarkDoc 文档所在的文件夹或其父文件夹（不限层数）放置一个 `.editorconfig` 文件（Windows 禁止直接创建点文件，你需要在创建时使用 `.editorconfig.`，系统会自动为你剔除结尾的点），并在其中写上：

````.editorconfig
# http://editorconfig.org

[*.markdoc]
trim_trailing_whitespace = false
````


### Parser／解析器

&nbsp; &nbsp; &nbsp;For developers, if you're implementing your own local/online preview interface, you might want to call an existing parser API instead of implementing one from scratch:  
　　对于开发者，如果你要实现自己的本地/在线预览界面，你可能会想要调用现成的解析器接口，而不是从头自己实现一个：

<https://GitHub.com/LongTengDao/j-markdoc/>


### Get Involved／参与贡献

&nbsp; &nbsp; &nbsp;Actually, The standard implementation is an example, because:

1.	The only programming language I know well is JavaScript, and I can only provide full-stack implementations in that. Contributions from the community are needed, to complete implementations in other languages.
	
2.	There could be many verbose details in the specification, if we enumerate the edge cases one by one. These fuzzy areas can refer to the standard implementation.
	
3.	The format as parsed result I mainly used is HTML, if users need their MarkDoc to be transformed to other formats directly or indirectly, it still depends on the power of open source community.

　　标准实现事实上是一个示例，因为：

1.	我只会 JavaScript，只能提供该语言的全栈实现，其它语言需要来自社区的贡献，大家共同完成。
	
2.	规范中有很多细说极其啰嗦，难以一一穷举的边缘情况，这些模糊地带可以参考标准实现的解析结果。
	
3.	我主要用到的是 HTML 格式的解析结果，如果使用者需要将 MarkDoc 直接或间接地译作其它文件格式，那依然需要依赖开源社区的力量。

