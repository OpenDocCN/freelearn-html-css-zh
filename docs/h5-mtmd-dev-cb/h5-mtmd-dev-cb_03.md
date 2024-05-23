# 第三章。使用 CSS 进行样式设置

在本章中，我们将涵盖：

+   将元素设置为`display:block`

+   为`nav`块元素设置样式

+   使用 background-size 控制背景外观

+   使用`border-radius`添加圆角

+   包括多个背景图片

+   为图像添加盒子阴影

+   为 Internet Explorer 浏览器进行样式设置

# 介绍

> “谢谢你的一切，IE6。在@Mix 上见。我们将展示 IE 天堂的一小部分。-微软的 Internet Explorer 团队”-来自在线查看的 Internet Explorer 6 葬礼的悼词[`ie6funeral.com`](http://ie6funeral.com)。

你已经接受了以不同的方式思考 HTML 的挑战。接下来，你将被挑战扩展你的层叠样式表知识。除此之外，我们将挑战一些关于跨浏览器显示的假设。如果你和你的客户认为网站在每个浏览器中应该看起来一样，我们将改变一些想法。但如果你已经知道跨浏览器显示的谬误，你将成为帮助改变其他人想法的人。

在我们做任何这些事情之前，我们需要问自己和我们的客户一个简单的问题：网站在每个浏览器中需要看起来完全一样吗？*需要吗？*对于简洁的一字答案，请访问[`dowebsitesneedtolookexactlythesameineverybrowser.com`](http://dowebsitesneedtolookexactlythesameineverybrowser.com)在现代浏览器中，如 Chrome，Firefox，Opera 或 Safari。

![介绍](img/1048_03_01.jpg)

还要检查像 Internet Explorer 6 这样的旧版浏览器：

![介绍](img/1048_03_02.jpg)

朋友们，这就是一个已经过时的浏览器的样子。看着某物死去并不美观，是吗？

很明显，网站在不同的浏览器上显示不同。问题是：那又怎样？那重要吗？应该吗？为什么？

我们中很少有人在无菌实验室中工作，我们对所创建的内容的显示具有 100%的创造控制。甚至更少的人有时间或意愿为每个浏览器创建单独的定制体验。肯定有一个中间的方法。有一句老话这位作者非常喜欢：

> “真相在中间。” - Avadhoot Patwardhan

在这种情况下，事实是你将不得不与你的客户合作，无论他们是企业所有者，项目经理还是任何付钱让你为他们创建网站的人。但是，坐视这些人告诉我们如何做我们的工作的日子已经结束了。如果你知道有更好、更快、更高效的开发方式，你必须大声说出来。这是你的责任。如果你不这样做，没有人会为你说话。这对你不利，对你的客户不利，对整个行业也不利。不要成为那个人。

相反，你将不得不教育你的客户，为什么一些浏览器显示的东西略有不同，以及为什么这是完全可以接受的。以下是作者在实际业务情况中使用过的一些策略：

1.  向客户证明为旧版浏览器（尤其是 IE6）进行适配将需要更长时间。准备好证明仅为该浏览器开发可能需要花费你时间的四分之一。打击客户的痛处（钱包），那个人通常会退缩。

1.  强调用户体验即使在 IE 没有其他浏览器所具有的每个圆角或过渡效果时也可以保持完全相同。

### 提示

用户体验*始终*胜过花哨的外观。

CSS 并不是 HTML5 规范的正式部分。事实上，它值得有一本自己的书。但在本章中，作者将向您展示其他人如何使用 CSS 应用视觉效果的真实示例，如将元素显示为块级，模拟导航栏，使用多个背景图像，应用圆角以及高级样式，如添加盒子阴影，并为 Internet Explorer 浏览器进行样式设置。

让我们开始吧！

# 将元素设置为 display:block

默认情况下，现代浏览器将新的 HTML5 元素分配为`display:block`。但是默认情况下，旧版浏览器和大多数版本的 Internet Explorer 会自动回退到`display:inline`。如果你之前有过 CSS 的经验，你就会看到麻烦来临。我们要做的第一件事就是在问题出现之前解决它。

## 准备就绪

首先，让我们识别 HTML5 中的所有新元素。这些包括：

+   `<article>`

+   `<aside>`

+   `<audio>`

+   `<canvas>`

+   `<command>`

+   `<datalist>`

+   `<details>`

+   `<embed>` - 不是一个新标签，但它最终在 HTML5 中得到了验证

+   `<figcaption>`

+   `<figure>`

+   `<footer>`

+   `<header>`

+   `<hgroup>`

+   `<keygen>`

+   `<mark>`

+   `<meter>`

+   `<nav>`

+   `<output>`

+   `<progress>`

+   `<rp>`

+   `<rt>`

+   `<ruby>`

+   `<section>`

+   `<source>`

+   `<summary>`

+   `<time>`

+   `<video>`

+   `<wbr>`

## 如何做...

我们将从通常的页面框架开始，并添加一个样式，使所有这些新元素都显示为`display:block`。

```html
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Blog Title</title>
<!--[if lt IE 9]><script src="img/html5.js"> </script>[endif]-->
<style>
article, aside, audio, canvas, command, datalist, details, embed, figcaption, figure, footer, header, hgroup, keygen, mark, meter, nav, output, progress, rp, rt, ruby, section, source, summary, time, video, wbr {display:block;}
</style>
</head>
<body>
</body>
</html>

```

好了。这并不难。事实上，这些也可以包含在 CSS 重置文件中。

## 它是如何工作的...

使用 CSS，我们将所有新的 HTML5 元素设置为块级元素，确保更可预测的浏览器行为。

## 还有更多...

尽管现代浏览器已经将这些新的 HTML5 标签显示为块级元素，但在样式表中再次声明它们为`display:block`并不会有任何问题。在这里，宁愿安全也不要后悔。

### 不需要一遍又一遍地重复

注意：我们应该将这个简短的样式放在一个外部样式表中，然后在我们网站的每个页面中引用它，而不是在每个页面的顶部内联显示它。最好只声明一次，然后让它在整个网站中生效，而不是一遍又一遍地重复。

### 样式一次

通过一次简单的样式声明，我们可以确保我们的现代浏览器、旧版浏览器和移动浏览器在显示新的 HTML5 元素时会更加可预测。

### 过去的回声

出于某种原因，一些开发人员不想学习 HTML5。你会听到他们说出各种关于规范尚未准备好，在所有浏览器中都没有完全支持，以及需要像 CSS 或 JavaScript 这样的“黑客”来使其工作的无稽之谈。这都是无稽之谈。不要理会他们的抱怨。你真正听到的是恐龙灭绝的声音。如果恐龙决心通过自己的不作为来将自己灭绝，那就让它灭绝吧。只有强者才能生存。

有助于记住进化是分阶段进行的。并非所有生物都会突然进化。与恐龙不同，你可以决定自己是想现在、以后还是根本不想进化。你可以决定自己想站在历史的哪一边。

## 另请参阅

我们并不是点燃了火。它一直在燃烧。自世界开始转动以来。杰弗里·泽尔德曼的《与糟糕的浏览器说再见》一文于 2001 年发表后，在 Web 开发界引起了轰动。在这篇文章中，泽尔德曼，现在被广泛认为是 Web 标准运动的奠基人，激励了一代又一代的网页设计师和开发人员使用 CSS 来进行网页呈现，并抛弃破损的旧版浏览器。阅读这篇开创性的宣言：[`alistapart.com/articles/tohell`](http://alistapart.com/articles/tohell)。

# 对 nav 块元素进行样式设置

在创建 HTML5 规范时，进行了分析，确定最常用的元素之一是`<div id="nav">`或`<div id="navigation">`。在 HTML5 中不再需要这样做。相反，我们有了语义丰富的`<nav>`。现在让我们开始对其进行样式设置。

## 准备就绪

让我们来看看[`css3maker.com`](http://css3maker.com)网站如何使用新的语义丰富的`<nav>`元素。

![准备就绪<nav>元素 about](img/1048_03_03.jpg)

## 如何做...

如果我们查看主页的源代码，我们会发现这段代码：

```html
<!DOCTYPE html>
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
<title>CSS3.0 Maker | CSS3.0 Generator | CSS 3.0 Generator </title>
<link href="style/style.css" rel="stylesheet" type="text/css" />
<script type="text/javascript" src="img/CreateHTML5Elements.js"></script>
</head>
<body>
<div class="main_wrapper">
<nav> elementstyling<div id="wrapper">
<nav class="clearfix">
<ul>
<li class="frest"><a href="index.html" title="CSS 3.0 Maker" class="active">Home</a></li>
<li><a href="border-radius.html" title="Border Radius"> Border Radius</a></li>
<li><a href="css-gradient.html" title="Gradient">Gradient</a></li>
<li><a href="css3-transform.html" title="CSS 3.0 Transform">CSS Transform</a></li>
<li><a href="css3-animation.html" title="CSS 3.0 Animation">CSS Animation</a></li>
<li><a href="css3-transition.html" title="CSS 3.0 Transition">CSS Transition</a></li>
<li><a href="css-3-rgba.html" title="CSS 3.0 RGBA">RGBA</a></li>
<li><a href="text-shadow.html" title="Text Shadow">Text Shadow</a></li>
<li><a href="box-shadow.html" title="Box Shadow">Box Shadow</a></li>
<li><a href="text-rotation.html" title="Text Rotation">Text Rotation</a></li>
<li><a href="font-face.html" title="@Font Face">@Font Face</a></li>
</ul>
</nav>
</div>
</div>
</body>
</html>

```

请注意，到目前为止，HTML 标记非常简单。[`css3maker.com`](http://css3maker.com)的团队创建了一个页面包装器，然后使用新的`<nav>`元素来包含具有所有典型导航元素的无序列表。简单吧？接下来让我们关注他们是如何样式化的。

```html
<style>
nav {
background: url("../images/box_bg.png") repeat scroll 0 0 transparent;
border-radius: 5px;
margin-bottom: 8px;
margin-right: 5px;
}
<nav> elementstylingnav ul {
display: block;
list-style: none outside none;
margin: 0;
padding: 0 0 0 5px;
}
nav ul li.frest {
border-left-width: 0;
}
nav ul li {
border-right: 1px solid #1D1C1C;
display: inline;
float: left;
margin: 0;
padding: 0;
}
nav ul li a {
color: #000;
display: inline;
float: left;
font-size: 13px;
height: 35px;
line-height: 35px;
padding: 0 10px;
text-shadow: 0 -1px 2px #737373;
-webkit-transition: All 0.50s ease;
-moz-transition: All 1s ease;
-o-transition: All 1s ease;
}
</style>

```

## 它是如何工作的...

新的`<nav>`元素不仅成为我们无序列表的容器，还为 Web 浏览器提供了额外的含义以及可访问性增强。通过浮动`<nav>`元素并显示我们的无序列表而不带列表样式，这使我们能够水平显示我们的导航栏。

## 还有更多...

我们还看到了新的 CSS3 `transition`属性的使用。简单地说，这是一个新的浏览器鼠标悬停效果，以前只能通过 Flash 或 JavaScript 实现。现在，CSS 可以改变元素的外观，当鼠标移动到它上面时。

由于`transition`属性在浏览器制造商中只有实验性支持，因此您会看到以单破折号为前缀的供应商特定前缀，例如：

+   `-webkit`（用于 Safari 和 Chrome）

+   `-moz`（用于 Firefox）

+   `-o`（用于 Opera）

此外，Internet Explorer 有自己的供应商前缀，即`-ms`。令人费解的是，Chrome 可以处理`-webkit`前缀以及自己的`-chrome`前缀。

这些破折号只是表示浏览器制造商正在进行的工作。请记住，HTML5 和 CSS3 是不断发展的规范。我们现在可以开始使用它们的元素，但完全支持还没有到位。就像我们在为未来做饭一样。

### 浏览器支持

支持新的`<nav>`元素的 Web 浏览器：

！浏览器支持

### 文本阴影很酷

在前面的代码示例中，您还会注意到新的 CSS3 `text-shadow`属性的巧妙使用，我们在上一章中深入介绍了它。

## 另请参阅

[`cSS3maker.com`](http://cSS3maker.com) 网站是任何需要新的 CSS 属性的浏览器特定前缀的 CSS3 开发人员的绝佳资源：

+   border-radius

+   渐变

+   CSS 变换

+   CSS 动画

+   CSS 过渡

+   RGBA

+   文本阴影

+   盒阴影

+   文本旋转

+   @font-face

# 使用 background-size 控制背景外观

使用 CSS3，我们现在可以指定背景图像的大小。我们可以用像素、宽度和高度或百分比来指定这个大小。当您将大小指定为百分比时，大小是相对于我们使用 background-origin 指定的区域的宽度或高度的。

！使用 background-size 控制背景外观

## 准备就绪

让我们看一个真实的例子，[`miessociety.org`](http://miessociety.org)，这是一个由设计师 Scott Thomas 创建的机构 Simple Honest Work 的美丽网站，致力于保护建筑师 Ludwig Mies van der Rohe 的遗产。

## 如何做... 

如果我们查看样式表的源代码，我们会看到作者为`body`创建了一个规则，然后指定任何使用的背景图像都将覆盖整个`body`。

作者还为每个页面指定了一个背景图像，通过给每个`body`元素附加一个`ID`。

## 它是如何工作的...

在这里，我们看到创建者如何使用一些简单的样式，包括新的`background-size`属性，将大背景图像拉伸到整个页面，无论您的监视器大小或分辨率如何。

```html
<style>
background appearance controlbackground-size property, workingbody {
background: transparent no-repeat scroll 50% 50%;
background-repeat: no-repeat;
background-size: cover;
margin: 0px;
padding: 0px;
}
body#body_home {
background-attachment: inherit;
background-image: url(http://miessociety.org/site_media/library/ img/crownhall_index.jpg);
background-position: 50% 0%;
}
</style>

```

## 还有更多...

新的`background-size`元素通常以像素、宽度和高度或百分比指定。在 Mies van der Rohe Society 网站的示例中，我们看到作者使用了术语“cover”，这使背景图像能够拉伸到“覆盖”整个画布。聪明。

### 浏览器支持

支持新的`background-size`属性的 Web 浏览器：

！浏览器支持背景大小属性

### IE 中可接受

那么当我们在不支持 background-size 的浏览器中查看网站时会发生什么？在这里，我们可以看到 Internet Explorer 10 之前的版本无法拉伸背景图像，而是简单地用黑色填充剩余的画布。这是一个完美的例子，即使不是每个浏览器看起来都一样，但仍然提供了完全令人满意的用户体验。没有网站浏览者——即使是使用 IE6 的浏览者——都不能合理地抱怨他们没有按照作者的意图体验网站。

![IE 中可接受](img/1048_03_07.jpg)

### Simple Scott 简直太棒了

在本节中，我们使用了 Mies van der Rohe Society 网站使用新的 CSS3 `background-size`属性的真实示例，并注意到网站作者巧妙地适应了旧浏览器的使用。

## 另请参阅

[`html5rocks.com`](http://html5rocks.com)网站提供交互式演示、代码播放区、示例和逐步教程，以开发和磨练您的新技术技能。有趣的是，该网站是一个您可以贡献的开源项目。学习它，分享它，回报社会！

# 使用 border-radius 添加圆角

`border-radius`很可能会成为 CSS3 最常用的新属性。由于 Web 上使用了许多按钮和包含元素的圆角，`border-radius`使得通过 CSS 很容易实现，而不是依赖于图像。下面是如何做到的。

## 准备好

让我们来看看[`devinsheaven.com`](http://devinsheaven.com)，这是 iPhone 应用设计师和开发者 Devin Ross 的作品和文章。具体来说，我们将研究 Devin 如何设计他的搜索字段。

![准备好 border-radiusabout](img/1048_03_08.jpg)

## 如何做...

查看 Devin 的代码源，我们看到简单、直接的表单标记，包括所有典型的元素：包装器、表单、标签和两个输入。

```html
<div id="search-form">
<form role="search" method="get" id="searchform" action="http://devinsheaven.com/" >
<div>
<label for="s">Search for:</label>
<input type="text" value="" name="s" id="s" />
<input type="submit" id="searchsubmit" value="Search" />
</div>
</form>
</div>

```

但是 Devin 在样式表中接下来做的事情才实现了现代浏览器中的圆角：

```html
<style>
#navigation-bar #search-form {
background: none repeat scroll 0 0 white;
border-radius: 4px;
margin-left: 180px;
margin-top: 12px;
padding: 2px 6px;
position: absolute;
width: 250px;
}
</style>

```

## 它是如何工作的...

Devin 指定了搜索表单`ID`的四个像素`border-radius`，使其四个角都以相同的量进行了圆角处理。还可以单独指定每个角的`border-radius`。

## 还有更多...

有趣的是，Opera 浏览器将支持新的 CSS3 `border-radius`属性，而无需浏览器特定前缀。干得好，Opera！谢谢！

### 浏览器支持

支持新的`border-radius`样式的 Web 浏览器：

![浏览器支持](img/1048_03_09.jpg)

### IE 中可接受

那么在不支持的浏览器中查看 Devin 设计精美的网站会发生什么？Internet Explorer 8 及更早版本会简单地忽略`border-radius`属性并使角落成方形。再次强调，这是完全可以接受的，但通常需要您向客户解释为什么像素完美并不总是一个现实的目标。

在 Internet Explorer 8 中查看的 Devin's Heaven 网站。请注意方形搜索表单边框。

![IE 中可接受](img/1048_03_10.jpg)

### Devin's Heaven goes to 11

在本节中，我们演示了[`devinsheaven.com`](http://devinsheaven.com)如何使用新的 CSS3 `border-radius`属性轻微地圆角化搜索字段。我们还看了作者对浏览器特定前缀的使用，以及作者选择如何处理像 Internet Explorer 8 及更早版本这样的旧浏览器。

## 另请参阅

要了解更多有关新的 CSS3 `border-radius`属性的出色用法，请访问[`houseofbuttons.tumblr.com`](http://houseofbuttons.tumblr.com)。其中包括许多设计和开发灵感。

# 包括多个背景图像

[`benthebodyguard.com`](http://benthebodyguard.com)在 2010 年 12 月首次亮相时引起了互联网的轰动。作者们使用单页面布局来讲述一个名为 Ben 的虚构法国保镖的互动故事。当页面向下滚动时，多个背景帮助讲述了即将发布的 iPhone 应用的故事。

## 准备好

让我们查看[`benthebodyguard.com`](http://benthebodyguard.com)，并滚动浏览动画。

![准备就绪](img/1048_03_11.jpg)

## 如何做...

让我们专注于源代码的一部分，看看网站作者如何利用多个背景。

```html
<!doctype html>
<html class="" lang="en">
<head>
<meta http-equiv="Content-Type" content="text/html; charset=UTF-8"/>
<title>Ben the Bodyguard. Coming soon to iPhone® and iPod touch®</title>
<meta name="author" content="Ben the Bodyguard">
<link rel="stylesheet" href="css/style.php?v=1">
</head>
<body class="index">
<div id="container">
<div id="hide-wrapper">
<header>
<img id="comingDecember" alt="Ben the Bodyguard is coming for iPhone and iPod touch in january 2011" src="img/red_stamp.png">
<h1>A Frenchman <br>protecting your secrets.<br> Yes, seriously.</h1>
<h3>Ben the Bodyguard</h3>
<p>Protecting your passwords, photos, contacts<br> and other sensitive stuff on your iPhone or iPod touch</p>
</header>
<div id="ben">
<div id="speechBubbleWrapper">
<div id='speechBubble'></div>
</div>
<div id="ben-img"></div>
</div>
<div id="hotel">
<div id="hotelanimation"></div>
</div>
<div id="bridge"></div>
<div id="train"></div>
<div id="hideBenInBeginning"></div>
<div id="city">
<div id="thief"></div>
<div id="stolen"></div>
<div id="yakuza"></div>
</div>
</div>
</div>
</body>
</html>

```

到目前为止，还没有什么特别的，除了几个空的`divs`。这些是作者用来讲故事的多个背景图像的容器。您的容器可以包括文本、图像、视频等。

## 它是如何工作的...

通过为每个`div`指定背景图像，网站作者使用了多个 PNG 文件背景图像，以创建一个无缝的互动在线体验。

## 还有更多...

Mighty 的朋友们创建了一系列迷你网站，以展示我们在上一章中谈到的一些新的排版可能性。Frank Chimero 在[`lostworldsfairs.com/atlantis`](http://lostworldsfairs.com/atlantis)创建了一个单页网站，它的工作方式与`http://benthebodyguard.com`网站类似，都有多个背景。当您滚动浏览这个长页面时，您的头像会下降到亚特兰蒂斯失落的城市。

![还有更多...](img/1048_03_12.jpg)

### 内容在哪里？

查看亚特兰蒂斯失落世界博览会迷你网站的源代码，我们可以看到与多个空的`divs`相似的方法。

```html
<!doctype html>
<html lang="en" class="no-js">
<head>
<meta charset="utf-8">
<title>Atlantis World's Fair</title>
<meta name="Author" content="Friends of Mighty">
<link rel="stylesheet" href="css/all.min.css">
</head>
<body>
<div id="back_to"><a href="http://lostworldsfairs.com">Lost World's Fairs</a></div>
<div id="header">
<div id="img_doc"></div>
<div id="img_ship"></div>
<div class="container">
<p id="txt_below">Below</p>
</div>
<div id="backwave"></div>
<div id="frontwave"></div>
</div>
<div id="tube">
<div class="tube_container">
<div id="tube_dude" class="tube_container"></div>
</div>
<div class="tube_container">
<div id="tube_overlay"></div>
<div id="tube_backtop"></div>
<div id="tube_back"></div>
<div id="tube_fronttop"></div>
<div id="tube_frontbottom"></div>
<div id="tube_front"></div>
</div>
</div>
<div id="depthfinder"><span id="depth-o-meter">0</span> <span id="txt_k">k</span> Leagues</div>
<div id="depthscale"></div>
<div id="content">
<section id="depth1">
<div class="container">
<div id="welcomesign" class="bringFront">
<header>
<h1><span id="txt_date">1962</span> <span id="txt_atlantis">Atlantis</span> <span id="txt_worldsfair">Worlds Fair</span></h1>
<p id="txt_taglines"><span id="txt_worldsfaircircle">The World's Fair</span> <span id="txt_imaginationflag">The Depths Of Imagination</span></p>
</header>
</div>
<aside id="info_1" class="dyk-right">
<div class="didyouknow">
<img src="img/dyk-info.png" alt="info" height="30" width="30"/>
<h4>Did You Know</h4>
<p>Atlantis was<br/> originally built on<br/> the floor of the<br/> sea in 722 BCE<br/> by amphibious<br/> herbivores</p>
</div>
</aside>
</div>
</section>
</div>
</body>
</html>

```

### 坦白说

Chimero 使用了与[`benthebodyguard.com`](http://benthebodyguard.com)网站类似的方法，为这些本来空的`divs`中的每一个指定了背景图像，以创建一个无缝的体验。

## 另请参阅

HTML5 中有很多新东西，就像是最好的技术圣诞节一样。通过访问[`html5test.com`](http://html5test.com)来跟踪您的浏览器支持哪些元素。通过多种浏览器访问该网站会得到令人警醒的结果。

# 为图像添加阴影

以前，像图像下方或周围的阴影这样的视觉效果只能通过使用第二个图像来实现阴影，或者将阴影本身作为图像的一部分来实现。问题在于，如果您想要调整阴影，就必须重新裁剪它。让我们看看使用 CSS3 的现代智能方法。

## 准备就绪

查看[`thebox.maxvoltar.com`](http://thebox.maxvoltar.com)上的视觉元素周围迷人而微妙的阴影。作者 Tim Van Damme 应用了新的 CSS3 `box-shadow`属性。

![准备就绪](img/1048_03_13.jpg)

## 如何做...

让我们检查样式，看看 Tim 是如何实现那种美丽简单的效果的：

```html
<style>
section {
background: none repeat scroll 0 0 #EAEEF1;
border: 1px solid #FFFFFF;
box-shadow: 0 2px 10px rgba(0, 0, 0, 0.5);
margin: 0 auto;
padding: 49px;
position: relative;
width: 300px;
z-index: 50;
}
</style>

```

除了其他样式，我们还可以清楚地看到`box-shadow`属性指定了阴影的颜色和扩散距离。

## 它是如何工作的...

新的 CSS3 `box-shadow`属性的语法与`text-shadow`属性相同。也就是说，网站作者在照片周围应用了一个阴影，该阴影在右侧两个像素，底部十个像素，透明度为 50%。

### 浏览器支持

支持新的`box-shadow`样式的 Web 浏览器。

![浏览器支持](img/1048_03_14.jpg)

### 无知是福

不支持新的 CSS `box-shadow`属性的浏览器会简单地忽略该规则，不会显示阴影。外观会稍微改变，但用户体验不会受到影响。没有伤害，也没有犯错。

### The Box 的 box-shadow

在本节中，我们演示了作者 Tim Van Damme 如何使用新的 CSS3 `box-shadow`属性在他的采访网站周围创建微妙的阴影效果。

## 另请参阅

在为自己的项目创建样式表时，您可以完全控制创建一个 CSS 来统治它们所有，或者为移动和/或打印友好页面创建单独的定制体验。但是当您没有完全控制时会发生什么？这时，我们就需要像[`printfriendly.com`](http://printfriendly.com)这样的工具来帮助我们。

# Internet Explorer 浏览器的样式

现在显而易见，作者强烈主张为现代浏览器提供最佳的 CSS3 体验，让旧版本的 IE 随心所欲。如果在旧浏览器中某个元素缺少圆角或阴影，作者确实不在乎。但事实上，您的客户可能在乎。让我们打开潘多拉盒子，谈谈如何适应过时的浏览器。

## 准备工作

我们将看一系列特定的方法，使 IE 在使用新的 CSS3 属性如`border-radius, box-shadow`和`text-shadow`时表现正常。

## Border-radius

在旧版本的 IE 中也可以实现圆角。让我们访问[`htmlremix.com/css/curved-corner-border-radius-cross-browser`](http://htmlremix.com/css/curved-corner-border-radius-cross-browser)来了解如何做到这一点。在那里，我们将学习如何在样式表中包含一个`.htc`行为：

```html
<style>
.curved {
-moz-border-radius: 10px;
-webkit-border-radius: 10px;
behavior: url(border-radius.htc);
}
<style>

```

请注意，`.htc`文件会导致代码膨胀，并且这种行为会导致您的 CSS 无法验证。

## Box-shadow

我们可以通过使用专有的滤镜来强制 IE 显示`box-shadows`：

```html
<style>
.box-shadow {
-moz-box-shadow: 2px 2px 2px #000;
-webkit-box-shadow: 2px 2px 2px #000;
filter: progid:DXImageTransform.Microsoft.Shadow(color='#000', Direction=145, Strength=3);
}
</style>

```

不幸的是，您将不得不调整该滤镜以实现阴影的方向和深浅。请注意，这个滤镜不如新的 CSS3 `box-shadow`属性强大。

## Text-shadow

在 IE 9 之前的版本中，似乎唯一让`text-shadow`起作用的方法是使用像[`scriptandstyle.com/submissions/text-shadow-in-ie-with-jquery-2`](http://scriptandstyle.com/submissions/text-shadow-in-ie-with-jquery-2)这样的 jQuery 插件来通过 JavaScript 实现。请注意，强制 JavaScript 执行 CSS 的工作永远不是一个好方法，这种技术只会导致代码膨胀。

## 注意

虽然在旧版本的 IE 中可能会出现一些类似 CSS3 的效果，但并不建议使用。每一个效果都需要额外的开发时间，并且可能会影响浏览器的性能。使用时请自行承担风险。

## 另请参阅

Kyle Weems 在[`cssquirrel.com`](http://cssquirrel.com)上创建了一个极其有趣的每周漫画系列，讽刺了网络标准世界中的种种事态。HTML5、CSS3、Twitter、无障碍以及在这些领域中具有重要影响力的主要声音都是 Kyle 经常扭曲的幽默感的对象。

![另请参阅](img/1048_03_15.jpg)
