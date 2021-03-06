# CSS和HTML相关的知识

## 1.重排和重绘

* **重排：** 部分渲染树（或者整个渲染树）需要重新分析并且节点尺寸需要重新计算。这被称为重排，注意这里至少会有一次重排——初始化页面布局。
* **重绘：** 由于节点的几何属性发生改变或者由于样式发生改变，例如改变元素背景色时，屏幕上的部分内容需要更新。这样的更新被称为重绘。

**什么情况下会触发重排和重绘：**

* 添加、删除、更新DOM节点
* 通过display:none隐藏一个DOM节点，触发重排和重绘
* 通过visibility:hidden隐藏一个DOM节点，只触发重绘，因为没有发生几何变化
* 移动或者给页面中的DOM节点添加动画
* 添加一个样式表，调整样式属性
* 用户行为，例如调整窗口大小，改变字号，或者滚动

## 2.页面导入样式时，使用link和@import的区别

1. link属于XHTML标签，除了加载CSS以外，还能用于定义RSS，定义rel连接属性等作用；而@import是CSS提供的，只能用于加载CSS；
2. 页面被加载时，link会同时被加载，而@import引用的CSS会等到页面被加载完后再加载。
3. import是CSS2.1提出的，只在IE5以上才被识别，而link是XHTML标签，无兼容问题。

## 3.Doctype的作用，标准模式和兼容模式的区别

1. `<!DOCTYPE>`声明位于HTML文档中的第一行，处于`<html>`标签之前，告知浏览器的解析器以什么文档标准来解析这个文档。
2. 标准模式的排版和JS运作模式都是以该浏览器支持的最高标准运行。在兼容模式中，页面以宽松的向后兼容的方式显示，模拟老浏览器的行为以防止站点无法工作。

## 4.HTML语义化的理解

一句话总结：**用正确的标签做正确的事情**。

1. HTML语义化让页面的内容结构化，结构更清晰，便于对浏览器、搜索引擎解析。
2. 即使在没有样式CSS情况下也以一种文档格式显示，并且是容易阅读的。
3. 搜索引擎的爬虫也依赖于HTML标记来确定上下文和各个关键字的权重，有利于SEO。
4. 是阅读源代码的人对网站更容易将网站分块，便于阅读维护理解。 

## 5.Label的作用是什么，怎么用

&emsp;&emsp;Label标签用来定义表单控制间的关系，当用户选择该标签时，浏览器会自动将焦点转到和标签相关的表单控件上。
```html
<label for='Name'>Number;</label>
<input type='text' name='Name' id='Name'/>
<label>Date:<input type='text' name='B'></label>
```

## 6.position的值以及定位原点

**absolute**

&emsp;&emsp;生成绝对定位的元素。相对于值不为static的第一个父元素进行定位。

**fixed**

&emsp;&emsp;生成绝对定位的元素，固定定位。相对于浏览器窗口进行定位。

**relative**

&emsp;&emsp;生成相对定位的元素。相对于其正常位置进行定位。

**static**

&emsp;&emsp;默认值。没有定位，元素出现在正常流中。

**inherit**

&emsp;&emsp;从父元素继承position的值。

## 7.超链接样式设置顺序

&emsp;&emsp;被点击访问过的超链接不再具有hover和active样式，解决方法是改变CSS属性的排列顺序：<font color=red>**L-V-H-A**</font>: a:link{}, a:visited{}, a:hover{}, a:active{}。

## 8. ::before和:after中双冒号和单冒号有什么区别及它们的作用

&emsp;&emsp;单冒号（:）用于**CSS3伪类**，双冒号（::）用于**CSS3伪元素**。（伪元素由双冒号和伪元素名称组成）。

&emsp;&emsp;双冒号是在当前规范中引入的，用于区分伪类和伪元素。不过浏览器需要同时支持旧的已经存在的伪元素写法，比如：:first-line、:first-letter、:before、:after等，而新的在CSS3中引入的伪元素则不允许再支持旧的单冒号的写法。

&emsp;&emsp;想让插入的内容出现在其他内容前，使用::before，否则，使用::after；在代码顺序上，::after生成的内容也比::before生成的内容靠后。如果按堆栈视角，::after生成的内容会在::before生成的内容之上。

## 9.设置元素浮动后，该元素的display值

&emsp;&emsp;自动变成了<font color=red>**display:block**</font>。

## 10.CSS选择符有哪些，哪些属性可以继承

1. **!important**选择器。
2. **id选择器（#myid）**
3. **类选择器（.myclassname）**
4. **标签选择器（div, h1, p）**
5. **相邻选择器（h1+p）**
6. **子选择器（ul>li）**
7. **后代选择器（li a）**
8. **通配符选择器（*）**
9. **属性选择器（a[rel='external']）**
10. **伪类选择器（a:hover， li:nth-child）**
 
**可继承的样式：** font-size、font-familycolor、ul、li、dl、dd、dt;

**不可继承的样式：** border、padding、marginwidth、height。

## 11.CSS的优先级计算

&emsp;&emsp;优先级就近原则，同权重情况下样式定义近者为准；载入样式以最后载入的定位为准；

&emsp;&emsp;优先级为（同权重）：内联样式表（标内部）>嵌入样式表（当前文件中）>外部样式表（外部件中）。

&emsp;&emsp;!important > id > class > tagimportant比内联优先级高。

## 12.display的取值以及他们的作用

1. **none**：缺省值。像行内元素类型一样显示。
2. **block**：块类型。默认宽度为父元素宽度，可设置宽高，换行显示。
3. **inline**：行内元素类型。默认宽度为内容宽度，***不可设置宽高***，同行显示。
4. **inline-block**：默认宽度为内容宽度，***可以设置宽高***，同行显示。
5. **list-item**：像块元素一样显示，并添加样式列表标记。
6. **table**：此元素会作为块级表格来显示。
7. **inherit**：规定应该从父元素继承display属性的值。

## 13.为什么要初始化CSS样式

&emsp;&emsp;因为浏览器的兼容问题，不同浏览器对有些标签的默认值是不同的，如果没对CSS初始化往往会出现浏览器之间的页面显示差异。当然，初始化样式会对SEO有一定的影响，但鱼与熊掌不可兼得，但力求影响最小的情况下初始化。

## 14.让页面中的字体变清晰，变细用CSS怎么做？

&emsp;&emsp;**-webkit-font-smoothing:antialiased;** 这里，antialiased的意思是抗锯齿、反混淆的意思。

## 15.display:inline-block什么时候会显示间隙？

&emsp;&emsp;移除空格、使用margin赋值、使用font-size:0、letter-spacing、word-spacing。

## 16. img的alt与title有何异同

&emsp;&emsp;**a:alt(alt text):** 为不能显示图像、窗体或applets的用户代理（UA），alt属性用来指定替换文字。替换文字的语言有lang属性指定。（在IE浏览器下会没有title时把alt当成tool tip显示）

&emsp;&emsp;**title(tool tip):** 该属性为设置该属性的元素提供建议性的信息。

## 17. strong与em的异同

&emsp;&emsp;**em**：表现为斜体，语义表示强调；

&emsp;&emsp;**strong**：表现为粗体，语义为强烈语气，强调程度超过em。

## 18. 为什么利用多个域名来存储网站资源会更有效。

&emsp;&emsp;CDN缓存更方便、突破浏览器并发限制、节约cookie带宽、节约主域名的连接数，优化页面响应速度、防止不必要的安全问题。

## 19. cookies、sessionStorage和localStorage的区别

&emsp;&emsp;sessionStorage用于本地存储一个会话(session)中的数据，这些数据只有在同一个会话中的页面才能够访问并且当会话结束后数据也随之销毁。因此sessionStorage不是一种持久化的本地存储，仅仅是会话级别的存储。而localStorage用于持久的本地化存储，除非主动删除数据，否则数据是永远不会消失的。

&emsp;&emsp;webstorage和cookie的区别：web storage的概念和cookie相似，区别是它是为了更大容量的存储设计的。Cookie的大小是受限的，并且每次你请求一个新的页面的时候cookie都会被发送过去，这样无形中浪费了带宽，另外cookie还需要指定作用域，不可以跨域调用。除此之外，web storage拥有setItem、getItem、removeItem、clear等方法，不想cookie需要前端开发者自己封装setCookie、getCookie。但是cookie也是不可或缺的：cookie的作用是与服务器进行交互，作为HTTP规范的一部分而存在，而web storage仅仅是为了在本地“存储”数据而生。

## 20. src与href的区别

&emsp;&emsp;src用于替换当前元素，href用于在当前文档和引用资源之间确立联系。

&emsp;&emsp;src是 **source** 的缩写，指向外部资源的位置，指向的内容将会 **嵌入到文档中当前标签所在的位置**；在请求src资源时会将其指向的资源下载并应用到文档内，例如js脚本、img图片和frame等元素。像：`<script src="myJS.js"></script>` 。当浏览器解析到该元素时，会暂停其他资源的下载和处理，直到将该资源加载、编译、执行完毕，图片和框架等元素也是如此，类似于将所指向资源嵌入当前的标签内，这也是为什么将js脚本放在底部而不是头部。

&emsp;&emsp;href是 **Hypertext Reference** 的缩写，指向网络资源所在位置，建立和当前元素（锚点）或当前文档（链接）之间的链接，如果我们在文档中添加`<link href="commom.css" rel="stylesheet"/>`，那么浏览器会识别该文档为css文件，就会并行下载资源并且不会停止对当前文档的处理。这也是为什么建议 **使用link方式**来加载css，而不是使用@import方式。

## 21. 网页制作用到的图片格式有哪些

&emsp;&emsp;png-8、png-24、JPEG、gif、svg。但是最重要的是 **WebP**，Webp格式是Google开发的一种旨在加快图片加载速度的图片格式。图片压缩体积大约只有JPEG的2/3，并能节省大量的服务器带宽资源和数据空间。Facebook、eBay等知名网站已经开始测试并使用Webp格式。在质量相同的情况下，WebP格式图像的体积要比JPEG格式图像小40%

## 22. 从用户刷新网页开始，一次js请求一般情况下有哪些地方会缓存处理

&emsp;&emsp;DNS缓存、CDN缓存、浏览器缓存、服务器缓存。

## 23. 一个页面上有大量的图片（大型电商网站），加载很慢，有哪些方法优化这些图片的加载，给用户更好的体验

&emsp;&emsp;1. **图片懒加载**：在页面上的未可视区域可以添加一个滚动条事件，判断图片位置与浏览器顶端的距离与页面的距离，如果前者小于后者，优先加载。

&emsp;&emsp;2.**图片预加载**：如果为幻灯片、相册等，可以使用图片预加载，将当前展示的前一张和后一张优先下载。

&emsp;&emsp;3.如果图片为CSS图片，可以使用CSSsprite、SVGsprite、Iconfont、Base64等技术。

&emsp;&emsp;4.**缩略图**：如果图片过大，可以使用特殊编码的图片，加载时会先加载一张压缩得特别厉害的缩略图，以提高用户体验。

&emsp;&emsp;5.如果图片展示区域小于图片的真实大小，则应在服务器端根据业务需要先行进行图片压缩，图片压缩后大小与展示一致。

## 24. 理解HTML的语义化

&emsp;&emsp;1.更符合W3C统一的规范标准，是技术趋势。

&emsp;&emsp;2.没有样式时，浏览器的默认样式也能让页面结构很清晰。

&emsp;&emsp;3.对功能障碍用户友好。屏幕阅读器（如果访客有视障）会完全根据你的标记来“读”你的网页。

&emsp;&emsp;4.对其他非主流终端设备友好。例如机顶盒、PDA、各种移动终端。

&emsp;&emsp;5.对SEO友好。

## 25.前端角度出发要做好SEO需要考虑什么

&emsp;&emsp;搜索引擎主要以： **外链数量和质量**、**网页内容和结构** 来决定某关键字下的网页搜索排名。

&emsp;&emsp;前端应该注意网页结构和内容方面的情况。

&emsp;&emsp;Meta标签优化，主要包括主题（Title），网站描述（Description）。还有一些其他的隐藏文字比如Author（作者），Category（目录），Language（编码语种）等。

&emsp;&emsp;符合W3C规范的语义性标签的使用。

&emsp;&emsp;如何选取关键词并在网页中放置关键词。搜索就得用关键词。关键词分析和选择是SEO最重要的工作之一。首先要给网站确定关键词（一般在5个上下），然后针对这些关键词进行优化，包括关键词密度（Density）、相关度（Relavancy）、突出性（Prominency）等等。

## 26.有哪些方式可以对一个DOM设置它的CSS样式

&emsp;&emsp;1.外部样式表：引入一个外部CSS文件。

&emsp;&emsp;2.内部样式表：将CSS代码放在`<head>`标签内。

&emsp;&emsp;3.将CSS样式直接定义在HTML元素内部。