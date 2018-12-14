

[MarkDoc (v0.11)](https://GitHub.com/LongTengDao/MarkDoc/)
=================

— A Markdown-like [jDoc](https://GitHub.com/LongTengDao/jDoc/)\-based e-book writing format by [LongTengDao](http://www.LongTengDao.com/).


TOC
---------

1.	[Philosophy](#user-content-1)
	
2.	[Syntax Specification](#user-content-2)
	
	1.	[Paragraph](#user-content-2.1)
	2.	[Outline Tree](#user-content-2.2)
	3.	[List Tree](#user-content-2.3)
		1.	[Basic List](#user-content-2.3.1)
		2.	[Ordered List](#user-content-2.3.2)
		3.	[Foldable List](#user-content-2.3.3)
	4.	[Table](#user-content-2.4)
	5.	[Pre-formatted Block](#user-content-2.5)
		1.	[Highlight Code](#user-content-2.5.1)
		2.	[Renderable Code](#user-content-2.5.2)
		3.	[Math Formula](#user-content-2.5.3)
		4.	[Media Embed](#user-content-2.5.4)
	6.	[Semantic–Style Block](#user-content-2.6)
		1.	[Horizontal Line](#user-content-2.6.1)
		2.	[Block Quote](#user-content-2.6.2)
		3.	[Figure](#user-content-2.6.3)
		4.	[Custom Field Set](#user-content-2.6.4)
	7.	[Inline](#user-content-2.7)
		1.	[Row Style](#user-content-2.7.1)
		2.	[Text Style](#user-content-2.7.2)
		3.	[Link](#user-content-2.7.3)
		4.	[Image](#user-content-2.7.4)
		6.	[Todo](#user-content-2.7.5)
	8.	[Decorator](#user-content-2.8)
		1.	[Inline Decorator](#user-content-2.8.1)
		2.	[Block Decorator](#user-content-2.8.2)
	9.	[Context Syntax](#user-content-2.9)
	
3.	[Filename Extension](#user-content-3)
	
4.	[Standard Implementation](#user-content-4)


[1. Philosophy](#user-content-1)<a id="user-content-1">&nbsp;</a>
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


[2. Syntax Specification](#user-content-2)<a id="user-content-2">&nbsp;</a>
-----------------------------------


### [2.1 Paragraph](#user-content-2.1)<a id="user-content-2.1">&nbsp;</a>

````````markdoc
Paragraph 1 row 1
Paragraph 1 row 2

Paragraph 2 row 1 \
Paragraph 2 row 1 rest
````````


### [2.2 Outline Tree](#user-content-2.2)<a id="user-content-2.2">&nbsp;</a>

````````markdoc

Article heading
===============


Chapter 1 heading
-------	
	
	Section 1.1 heading
	-------	
		
		Paragraph
	
	Section 1.2 heading
	-------	
		
		Paragraph


Chapter 2 heading
-------	
	
	Section 2.1 (in exclusive page) heading (also as link text in menu bar)
	+++++++	
		
		Paragraph
	
	Section 2.2 link text in menu bar (specify it separately)
	+++++++	
		
		Section 2.2 heading (specify it separately)
		===================
		
		Paragraph

````````


### [2.3 List Tree](#user-content-2.3)<a id="user-content-2.3">&nbsp;</a>

#### [2.3.1 Basic List](#user-content-2.3.1)<a id="user-content-2.3.1">&nbsp;</a>

````````markdoc
*	list item 1 row 1
	list item 1 row 2
	
*	list item 2 row 1
	list item 2 row 2
	
*	list item 3 paragraph
	
	*	sub list 1 item 1
	*	sub list 1 item 2
	
	list item 3 paragraph
````````

#### [2.3.2 Ordered List](#user-content-2.3.2)<a id="user-content-2.3.2">&nbsp;</a>

````````markdoc
1.	ordered list item 1 row 1
	ordered list item 1 row 2
2.	ordered list item 2
3.	ordered list item 3
````````

````````markdoc
1.	ordered list style 1-1
A.	ordered list style 2-1
a.	ordered list style 3-1
I.	ordered list style 4-1
i.	ordered list style 5-1
一、	ordered list style 6-1 (Chinese)
甲、	ordered list style 7-1 (Chinese)

(1)	ordered list style 1-2
(A)	ordered list style 2-2
(a)	ordered list style 3-2
(I)	ordered list style 4-2
(i)	ordered list style 5-2
（一）	ordered list style 6-2 (Chinese)
（甲）	ordered list style 7-2 (Chinese)

1)	ordered list style 1-3
A)	ordered list style 2-3
a)	ordered list style 3-3
I)	ordered list style 4-3
i)	ordered list style 5-3
一）	ordered list style 6-3 (Chinese)
甲）	ordered list style 7-3 (Chinese)
````````

#### [2.3.3 Foldable List](#user-content-2.3.3)<a id="user-content-2.3.3">&nbsp;</a>

````````markdoc
-	summary
	=======
	detail paragraph (default open)
+	summary
	=======
	detail paragraph (default fold)
````````


### [2.4 Table](#user-content-2.4)<a id="user-content-2.4">&nbsp;</a>

````````markdoc
|	cell	cell
|	cell	cell
````````

````````markdoc
|_	head	head
|	cell	cell
|	cell	cell
````````

````````markdoc
|_	head	head
|	cell	cell
|	cell	cell
|=	Table Caption (below)
````````

````````markdoc
|=	Table Caption (above)
|_	head	head
|	cell	cell
|	cell	cell
````````

````````markdoc
|=	Multi-lines cell syntax example:
|_		A	B	C	D
|	1	line	line	line	line
|	2	line 1	line 1	line 1	line 1
		line 2	line 2	line 2	line 2
|	3	line	line	line	line
````````


### [2.5 Pre-formatted Block](#user-content-2.5)<a id="user-content-2.5">&nbsp;</a>

#### [2.5.1 Highlight Code](#user-content-2.5.1)<a id="user-content-2.5.1">&nbsp;</a>

````````markdoc
```	.codeType
	code row 1
	code row 2
	code row 3
````````

````````markdoc
```	.codeType
	code row 10
11	code row 11
	code row 12
````````

````````markdoc
```	.codeType
	code row 10
11	code row 11
	code row 12
...	
	code row 19
20	code row 20
	code row 21
	code row 22
````````

&nbsp; &nbsp; &nbsp;Code block which type is not implemented, should be implemented as plain (no highlight) by default.

#### [2.5.2 Renderable Code](#user-content-2.5.2)<a id="user-content-2.5.2">&nbsp;</a>

````````markdoc
~~~	rendererName.codeType
	code row 1
	code row 2
````````

&nbsp; &nbsp; &nbsp;Examples (just examples, not promised, each type need implementation supporting):

````````markdoc
~~~	.html
	<button onclick="alert('I am a HTML fragment.');">click me</button>
````````

````````markdoc
~~~	.css
	strong {
		font-weight: normal;
		font-family: 黑体, STXihei;
	-webkit-text-emphasis: filled circle;
		text-emphasis: filled circle;
	-webkit-text-emphasis-position: under right;
		text-emphasis-position: under right;
	}
````````

````````markdoc
~~~	.rst
	+---------+--------+----------+
	| group   | item   |   desc   |
	+=========+========+==========|
	|         | item 1 | - desc 1 |
	| group 1 +--------+ - desc 2 |
	|         | item 2 | - desc 3 |
	+---------+--------+----------+
````````

````````markdoc
~~~	gantt
	
	dateFormat YYYY-MM-DD
	
	title      Plan
	
	section    A
	           
	           task 1:   done,   1979-01-01,  2000-01-01
	           task 2:  active,  1990-06-01,  28d
	           task 3:           2018-11-26,  1d
	
	section    B
````````

&nbsp; &nbsp; &nbsp;Renderable code block which renderer is not implemented, should be implemented by default like:

~~~~~~~~html
<fieldset>
	<legend>rendererName.codeType</legend>
	pre code, highlight better (if code type is implemented)
</fieldset>
~~~~~~~~

#### [2.5.3 Math Formula](#user-content-2.5.3)<a id="user-content-2.5.3">&nbsp;</a>

````````markdoc
$$	formula expression row 1
	formula expression row 2
````````

&nbsp; &nbsp; &nbsp;It is short for (not promised, everything could be customed):

````````markdoc
~~~	math
	formula expression row 1
	formula expression row 2
````````

#### [2.5.4 Media](#user-content-2.5.4)<a id="user-content-2.5.4">&nbsp;</a>

````````markdoc
::	./small.png
````````

````````markdoc
::	./small.png
	
	Alternative text description of the image, like ":)".
	The description could be multi-line, but only treated as plain.
````````

````````markdoc
::	audio/ogg	./laugh.ogg
	audio/mpeg	./laugh.mp3
	audio/wav	./laugh.wav
	
	Alternative information, like "Your browser does not support audio."
	Not only plain.
````````

&nbsp; &nbsp; &nbsp;This is also ok:

````````markdoc
::	video/	./laugh
	ogg	.ogv
	mp4	.mp4
	webm	.webm
	
	Your browser does not support video.
````````

&nbsp; &nbsp; &nbsp;The syntax of audio and video is more complex than image, this is because the file types supported by each browser are different, maybe you want to apply them all. If you don't mind that, you can just write:

````````markdoc
::	video	./laugh.mp4
````````


### [2.6 Semantic–Style Block](#user-content-2.6)<a id="user-content-2.6">&nbsp;</a>

### [2.6.1 Horizontal Line](#user-content-2.6.1)<a id="user-content-2.6.1">&nbsp;</a>

````````markdoc
***

___
````````

#### [2.6.2 Block Quote](#user-content-2.6.2)<a id="user-content-2.6.2">&nbsp;</a>

````````markdoc
>	block quote 1 row 1
>	block quote 1 row 2

>	block quote 2 row 1
	block quote 2 row 2

>	block quote 3 row 1
	block quote 3 row 2
>	block quote 3 row 3
````````

#### [2.6.3 Figure](#user-content-2.6.3)<a id="user-content-2.6.3">&nbsp;</a>

&nbsp; &nbsp; &nbsp;In syntax, figure is a named list item without name.

&nbsp; &nbsp; &nbsp;Semantically, it's usually used for illustration, which has not a precise position, just for reference. Of cause, there could be a appendix table inside, or anything else.

````````markdoc
:	FigCaption (above)
	==================
	|_	No	English                                  	Chinese (Simplified)
	|	01	Oh stranger, tell the Lacedaemonians that	过路人，请捎个口信给斯巴达人，告诉他们，
	|	02	we lie here, obedient to their words.    	为了他们的嘱托，我们躺在这里。
````````

````````markdoc
:	::	./small.png
	
	FigCaption (below)
	==================
````````

````````markdoc
:	$$	E=mc^2
	=======================
	Mass–Energy Equivalence
````````

````````markdoc
:<-	left float

->:	right float
````````

#### [2.6.4 Custom Field Set](#user-content-2.6.4)<a id="user-content-2.6.4">&nbsp;</a>

````````markdoc
type	content paragraph 1
	
	content paragraph 2
````````

&nbsp; &nbsp; &nbsp;Examples (you need to implement it via the programming api by yourself!):

````````markdoc
!	Mixed-types array is invalid! (Probably an error block)
````````

````````markdoc
#	Note that mixed-types array is not recommended! (Probably a warning block)
````````

&nbsp; &nbsp; &nbsp;Block level symbols that not implemented, should be implemented by default like:

~~~~~~~~html
<fieldset>
	<legend>type</legend>
	content paragraph
</fieldset>
~~~~~~~~


### [2.7 Inline](#user-content-2.7)<a id="user-content-2.7">&nbsp;</a>

#### [2.7.1 Row Style](#user-content-2.7.1)<a id="user-content-2.7.1">&nbsp;</a>

````````markdoc
     5en indent row (usually used in English)
　　2em indent row (usually used in Chinese)
   3en indent row (usually used in English)

|-> Center align row <-|

|-> Right align row (method 1) ->|

Right align row (method 2) ->|

|-> Right align row (method 3)
````````

#### [2.7.2 Text Style](#user-content-2.7.2)<a id="user-content-2.7.2">&nbsp;</a>

| MarkDoc                     | Preview                             | Explain                                                        |
|:---------------------------:|:-----------------------------------:|----------------------------------------------------------------|
| `normal`                    | normal                              |                                                                |
| <code>pre&nbsp;&nbsp;spaces</code> | pre&nbsp;&nbsp;spaces        | Two or more spaces is reserved.                                |
| `__strong__`                | __strong__                          |                                                                |
| `*emphasize*`               | *emphasize*                         |                                                                |
| `\*escaped*`                | \*escaped*                          | The back slash is the escape symbol.                           |
| `<U+9F99>`<br>`<U+D842+DFB7>`<br>`<U+20BB7>` | 龙<br>𠮷<br>𠮷     | Unicode escape format is allowed.                              |
| `~~delete~~`                | ~~delete~~                          |                                                                |
| `++insert++`                | <ins>insert</ins>                   |                                                                |
| `normal^^sup^^`             | normal<sup>sup</sup>                |                                                                |
| `normal//sub//`             | normal<sub>sub</sub>                |                                                                |
| `很𠮷<ji2>利`               | 很<ruby>𠮷<rt>jí</rt></ruby>利      | `很<U+20BB7><ji2>利` should also be parsed correctly.          |
| <code>\` code \`</code><br><code>\`\\\`<U+9F99>\\\`\`</code> | <code>\`&nbsp;code&nbsp;\`</code><br><code>\`龙\`</code> | Codes quoted by single back quote are allowed to contain escape format. |
| <code>\`\` \\\` \`\`</code><br><code>\`\` \`\`\` \`\`</code><br><code>\`\`&nbsp;&nbsp;\`\`\`&nbsp;&nbsp;\`\`</code> | <code>\\\`</code><br><code>\`\`\`</code><br><code>&nbsp;\`\`\`&nbsp;</code> | Code quoted by two or more back quotes are not allowed to contain escape format, and must be wrapped inside by one space on each side, which will be trimmed. |
| `$E=mc^2$`                  | *E＝mc<sup><small>2</small></sup>*  | Math expressions wrapped by dollar will not parse escaped characters at all. |

&nbsp; &nbsp; &nbsp;And some GitHub not support for previewing:

|       MarkDoc                                            |       HTML                                                                                  |
|----------------------------------------------------------|---------------------------------------------------------------------------------------------|
| <code>\*\`lang\`\*\`.js\`</code>                         | `<code><em>lang</em>.txt</code>`                                                            |
| `==mark==`                                               | `<mark style="background-color:yellow;">mark</mark>`                                        |
| <code>\|\|bordered\|\|</code>                            | `<span style="border-style:solid;">bordered</span>`                                         |
| `normal^^sup^^//sub//text`<br>`normal//sub//^^sup^^text` | `normal<small style="display:inline-block;vertical-align:-0.5em;">sup<br />sub</small>text` |

#### [2.7.3 Link](#user-content-2.7.3)<a id="user-content-2.7.3">&nbsp;</a>

|       MarkDoc                                 |       HTML                                                                                       |
|-----------------------------------------------|--------------------------------------------------------------------------------------------------|
| `>> www.龙腾道.com <<`                        | `<a href="http://www.xn--r70at71adql.com/" target="_blank">`<br>&nbsp;&nbsp;`www.龙腾道.com</a>` |
| `>> 龙腾道 ~> http://www.LongTengDao.com/ <<` | `<a href="http://www.LongTengDao.com/" target="_blank">龙腾道</a>`                               |
| `>> top -> # <<`                              | `<a href="#">top</a>`                                                                            |
| `>> [ -> home ] -> / <<`                      | `<a href="/"> -> home </a>`                                                                      |

&nbsp; &nbsp; &nbsp;The wrapper `>` and `<` can be two or more.

#### [2.7.4 Image](#user-content-2.7.4)<a id="user-content-2.7.4">&nbsp;</a>

|       MarkDoc                                           |       HTML                                         |
|---------------------------------------------------------|----------------------------------------------------|
| `{{ ./small.png }}`                                     | `<img src="./small.png" />`                        |
| <code>{{ ./small.png \| :) }}</code>                    | `<img src="./small.png" alt=":)" />`               |
| <code>{{ ./small.png \| \` :) \<U+000A> ~~ \` }}</code> | `<img src="./small.png" alt=" :) &#x000A; ~~ " />` |

#### [2.7.5 Todo](#user-content-2.7.5)<a id="user-content-2.7.5">&nbsp;</a>

|   MarkDoc   | checked | color |  decoration  | HTML |
|:-----------:|:-------:|:-----:|:------------:|------|
|  `[ ] text` |         |       |              | `<label><input type="checkbox" /> text</label>` |
|  `[-] text` |         | gray  | line-through | `<label style="color:gray;text-decoration:line-through;">`<br>&nbsp;&nbsp;`<input type="checkbox" disabled /> text</label>` |
|  `[v] text` | checked |       |              | `<label><input type="checkbox" checked /> text</label>` |
|  `[x] text` | checked | gray  | line-through | `<label style="color:gray;text-decoration:line-through;">`<br>&nbsp;&nbsp;`<input type="checkbox" checked disabled /> text</label>` |
| `\[x] text` |         |       |              | `[x] text` |
| `[\x] text` |         |       |              | `<span>x</span> text` |


### [2.8 Decorator](#user-content-2.8)<a id="user-content-2.8">&nbsp;</a>

#### [2.8.1 Inline Decorator](#user-content-2.8.1)<a id="user-content-2.8.1">&nbsp;</a>

````````markdoc
*MarkDoc*{: title=`a kind of e-book writing format` .coinage } is \
a { .coinage :}[markdown]{: title=`relative to markup` } style language.
to parent if there is no previous{ .row-class }
````````

&nbsp; &nbsp; &nbsp;means (in HTML):

````````html
<p>
	<span style="display:block;">
		<em title="a kind of e-book writing format" class="coinage">MarkDoc</em> is <wbr />
		a <span title="relative to markup" class="coinage">markdown</span> style language.
	</span>
	<span style="display:block;" class="row-class">
		to parent if there is no previous
	</span>
</p>
````````

#### [2.8.2 Block Decorator](#user-content-2.8.2)<a id="user-content-2.8.2">&nbsp;</a>

````````markdoc
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
````````


### [2.9 Context Syntax](#user-content-2.9)<a id="user-content-2.9">&nbsp;</a>

````````markdoc
I need auto ordered ["footnote"]{: mean }, the first#n#, and the second#[*Inline* format for simple content.]#.
You ask why?
Watch >>>wall<<< and ponder it. :small:

我需要自动编号的[“脚注”]{: mean }，第一个##n##，和第二个##[简单内容的*内联*写法。]##。
你问为什么？
面>>>壁 => wall <<<思之。:small:


#n#	footnote paragraph.
	can be implemented at footer, sidebar, hover text, pop-up box, etc.

:small:	./small.png

>wall<	~> about:blank

{mean}	title=`Not have to display at footer.<LF>不是必须在页脚显示。`

<LF>	<U+000A>
````````

&nbsp; &nbsp; &nbsp;You can explicitly specify a position to display the "footnotes" (it's also the page break symbol):

````````markdoc
^^^

^^^	A4

^^^	A4 A5
````````


[3. Filename Extension](#user-content-3)<a id="user-content-3">&nbsp;</a>
-----------------------------------


`.markdoc`


[4. Standard Implementation](#user-content-4)<a id="user-content-4">&nbsp;</a>
--------------------------------------


### Editor

&nbsp; &nbsp; &nbsp;For writers, you can edit the MarkDoc file using any text editor. I'm developing [jMarkDoc](https://GitHub.com/LongTengDao/jMarkDoc/) (a MarkDoc reader) that will give you a standalone live preview.

&nbsp; &nbsp; &nbsp;Usually these editor software allows you to set the Tab character visible (you can enable the feature for `.markdoc` alone), and this will greatly facilitate the edit of any file format based on jDoc.

&nbsp; &nbsp; &nbsp;Most of them, however, are too smart to automatically remove whitespace characters of empty lines, which can be devastating for MarkDoc that based on jDoc. Unfortunately, many programs don't allow you to turn this feature off. But fortunately, `.editorconfig` allows you to set that, which these text editors that smart enough can also support. `.editorconfig`.

&nbsp; &nbsp; &nbsp;Place an `.editorconfig` file in the folder which the MarkDoc files placed, or their parent folder (unlimited layers), and write in below:

````````editorconfig
# http://editorconfig.org

[*.markdoc]
trim_trailing_whitespace = false
````````

&nbsp; &nbsp; &nbsp;Windows prohibit you creating dot files directly, you need to use `.editorconfig.`, then system will automatically trim the ending dot for you.


### Parser

&nbsp; &nbsp; &nbsp;For developers, if you're implementing your own local/online preview interface, you might want to call an existing parser API instead of implementing one from scratch:

&nbsp; &nbsp; &nbsp;<https://GitHub.com/LongTengDao/j-markdoc/>


### Get Involved

&nbsp; &nbsp; &nbsp;Actually, The standard implementation is an example, because:

1.	There could be many verbose details in the specification, if we enumerate the edge cases one by one. These fuzzy areas can refer to the standard implementation.
	
2.	The only programming language I know well is JavaScript, and I can only provide full-stack implementations in that. Contributions from the community are needed, to complete implementations in other languages.
	
3.	The format as parsed result I mainly used is HTML, if users need their MarkDoc to be transformed to other formats directly or indirectly, it still depends on the power of open source community.

