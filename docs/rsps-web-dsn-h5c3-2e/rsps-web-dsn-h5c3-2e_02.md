# 第二章：媒体查询-支持不同的视口

在上一章中，我们简要介绍了响应式网页的基本组件：流体布局、流体图像和媒体查询。

本章将详细介绍媒体查询，希望能够提供充分理解它们的能力、语法和未来发展所需的一切。

在本章中，我们将：

+   了解为什么响应式网页设计需要媒体查询

+   了解媒体查询语法

+   学习如何在`link`标签中使用媒体查询，以及在 CSS 文件中使用 CSS `@import`语句和媒体查询本身

+   了解我们可以测试的设备功能

+   使用媒体查询来促进视觉变化，取决于可用的屏幕空间

+   考虑媒体查询是否应该被分组在一起或根据需要编写

+   了解`meta`视口标签，以便在 iOS 和 Android 设备上使媒体查询按预期工作

+   考虑未来媒体查询规范提出的功能

CSS3 规范由许多模块组成。媒体查询（Level 3）只是其中之一。媒体查询允许我们根据设备的功能来定位特定的 CSS 样式。例如，只需几行 CSS，我们就可以根据视口宽度、屏幕宽高比、方向（横向或纵向）等来改变内容的显示方式。

媒体查询被广泛实现。除了古老版本的 Internet Explorer（8 及以下）之外，几乎所有浏览器都支持它们。简而言之，没有任何理由不使用它们！

### 提示

W3C 的规范经过一系列的批准过程。如果你有一天空闲，可以去看看它们在[`www.w3.org/2005/10/Process-20051014/tr`](http://www.w3.org/2005/10/Process-20051014/tr)上的官方解释。简化版本是，规范从**工作草案**（**WD**）到**候选推荐**（**CR**），再到**建议推荐**（**PR**），最后在许多年后到达 W3C 推荐（REC）。比其他模块更成熟的模块通常更安全使用。例如，CSS 变换模块 Level 3（[`www.w3.org/TR/css3-3d-transforms/`](http://www.w3.org/TR/css3-3d-transforms/)）自 2009 年 3 月以来一直处于 WD 状态，而它的浏览器支持要比 CR 模块如媒体查询差得多。

# 为什么响应式网页设计需要媒体查询

CSS3 媒体查询使我们能够将特定的 CSS 样式定位到特定的设备功能或情况上。如果你前往 W3C 的 CSS3 媒体查询模块规范（[`www.w3.org/TR/css3-mediaqueries/`](http://www.w3.org/TR/css3-mediaqueries/)），你会看到这是他们对媒体查询的官方介绍：

> “媒体查询由媒体类型和零个或多个表达式组成，用于检查特定媒体特征的条件。可以在媒体查询中使用的媒体特征包括'宽度'、'高度'和'颜色'。通过使用媒体查询，演示可以根据特定范围的输出设备进行定制，而不改变内容本身。”

没有媒体查询，我们将无法仅使用 CSS 大幅改变网站的视觉效果。它们使我们能够编写防御性的 CSS 规则，以预防诸如纵向屏幕方向、小或大视口尺寸等情况。

尽管流体布局可以在很大程度上实现设计，但考虑到我们希望覆盖的屏幕尺寸范围，有时我们需要更全面地修改布局。媒体查询使这成为可能。把它们看作是 CSS 的基本条件逻辑。

## CSS 中的基本条件逻辑

真正的编程语言都有一些设施，可以处理两种或更多可能的情况。这通常采用条件逻辑的形式，以`if/else`语句为典型。

如果编程术语让你的眼睛发痒，不要害怕；这是一个非常简单的概念。每当你去咖啡馆时让朋友帮你点餐时，你可能都在规定条件逻辑，“如果他们有三重巧克力松饼，我就要一个，如果没有，我就要一块胡萝卜蛋糕”。这是一个简单的条件语句，有两种可能的结果（在这种情况下同样好）。

在撰写本文时，CSS 不支持真正的条件逻辑或编程特性。循环、函数、迭代和复杂的数学仍然完全属于 CSS 处理器的领域（我是否提到了一本关于 Sass 预处理器的精彩书籍，名为*Sass and Compass for Designers*？）。然而，媒体查询是 CSS 中允许我们编写基本条件逻辑的一种机制。通过使用媒体查询，其中的样式根据是否满足某些条件而作用域。

### 注意

**编程特性即将到来**

CSS 预处理器的流行使得负责 CSS 规范的人们开始注意到这一点。现在有一个 CSS 变量的 WD 规范：[`www.w3.org/TR/css-variables/`](http://www.w3.org/TR/css-variables/)

然而，目前浏览器支持仅限于 Firefox，因此目前真的不值得考虑在实际中使用。

# 媒体查询语法

CSS 媒体查询是什么样的，更重要的是，它是如何工作的？

在任何 CSS 文件的底部输入以下代码，并预览相关的网页。或者，你可以打开`example_02-01`：

```html
body {
  background-color: grey;
}
@media screen and (min-width: 320px) {
  body {
    background-color: green;
  }
}
@media screen and (min-width: 550px) {
  body {
    background-color: yellow;
  }
}
@media screen and (min-width: 768px) {
  body {
    background-color: orange;
  }
}
@media screen and (min-width: 960px) {
  body {
    background-color: red;
  }
}
```

现在，在浏览器中预览文件并调整窗口大小。页面的背景颜色将根据当前的视口大小而变化。我们将很快介绍语法的工作原理。首先，重要的是要知道如何以及在哪里可以使用媒体查询。

## 链接标签中的媒体查询

自 CSS2 以来一直在使用 CSS 的人会知道，可以使用`<link>`标签的媒体属性来指定样式表适用的设备类型（例如，`screen`或`print`）。考虑以下示例（你会将其放在你的标记的`<head>`标签中）：

```html
<link rel="style sheet" type="text/css" media="screen" href="screen-styles.css">
```

媒体查询增加了根据设备的能力或特性来定位样式的能力，而不仅仅是设备类型。把它看作是对浏览器的一个问题。如果浏览器的答案是“true”，那么封闭的样式将被应用。如果答案是“false”，它们就不会。媒体查询不仅仅询问浏览器“你是屏幕吗？”——就像我们只能用 CSS2 来问的那样——媒体查询问得更多。相反，媒体查询可能会问，“你是屏幕，你是纵向的吗？”让我们以此为例：

```html
<link rel="stylesheet" media="screen and (orientation: portrait)" href="portrait-screen.css" />
```

首先，媒体查询表达式询问类型（你是屏幕吗？），然后是特性（你的屏幕是纵向的吗？）。`portrait-screen.css`样式表将应用于任何具有纵向屏幕方向的屏幕设备，并对其他设备忽略。通过在媒体查询的开头添加 not，可以颠倒任何媒体查询表达式的逻辑。例如，以下代码将否定我们之前例子中的结果，将文件应用于任何不是纵向屏幕的屏幕：

```html
<link rel="stylesheet" media="not screen and (orientation: portrait)" href="portrait-screen.css" />
```

# 组合媒体查询

也可以将多个表达式串联在一起。例如，让我们扩展我们之前的一个例子，并将文件限制为视口大于 800 像素的设备。

```html
<link rel="stylesheet" media="screen and (orientation: portrait) and (min-width: 800px)" href="800wide-portrait-screen.css" />
```

此外，我们可以有一个媒体查询列表。如果列出的任何查询为 true，则将应用该文件。如果没有一个为 true，则不会应用。以下是一个例子：

```html
<link rel="stylesheet" media="screen and (orientation: portrait) and (min-width: 800px), projection" href="800wide-portrait-screen.css" />
```

这里有两点需要注意。首先，逗号分隔每个媒体查询。其次，在投影后，你会注意到括号中没有尾随的特性/值组合。这是因为在没有这些值的情况下，媒体查询将应用于所有媒体类型。在我们的例子中，样式将应用于所有投影仪。

### 提示

你应该知道，可以使用任何 CSS 长度单位来指定媒体查询。**像素**（**px**）是最常用的，但**ems**（**em**）和**rems**（**rem**）同样适用。关于每种单位的优点，我在这里写了更多内容：[`benfrain.com/just-use-pixels`](http://benfrain.com/just-use-pixels)

因此，如果你想在 800px（但以 em 单位指定）处设置断点，只需将像素数除以 16。例如，800px 也可以指定为 50em（800 / 16 = 50）。

## 使用@import 的媒体查询

我们还可以使用 CSS 的`@import`功能将样式表有条件地加载到现有样式表中。例如，以下代码将导入名为`phone.css`的样式表，前提是设备基于屏幕，并且视口最大为 360 像素：

```html
@import url("phone.css") screen and (max-width:360px);
```

请记住，使用 CSS 的`@import`功能会增加 HTTP 请求（影响加载速度），因此请谨慎使用此方法。

## CSS 中的媒体查询

到目前为止，我们已经将它们作为链接到我们将放置在 HTML 的`<head></head>`部分中的 CSS 文件，并作为`@import`语句。但是，更有可能的是，我们将希望在 CSS 样式表中使用媒体查询。例如，如果我们将以下代码添加到样式表中，它将使所有`h1`元素变为绿色，前提是设备的屏幕宽度为 400 像素或更小：

```html
@media screen and (max-device-width: 400px) {
  h1 { color: green }
}
```

首先，我们指定要使用`@media`规则的媒体查询，然后指定要匹配的类型。在前面的示例中，我们只想将封闭的规则应用于屏幕（例如不适用于`print`）。然后，在括号内输入查询的具体内容。然后像任何 CSS 规则一样，我们打开大括号并编写所需的样式。

在这一点上，我可能需要指出的是，在大多数情况下，实际上不需要指定`screen`。这是规范中的关键点：

> *“媒体查询提供了适用于所有媒体类型的简写语法；关键字'all'可以省略（以及末尾的'and'）。也就是说，如果媒体类型没有明确给出，它就是'all'。”*

因此，除非你想要针对特定媒体类型的样式，否则可以省略`screen and`部分。这是我们从现在开始在示例文件中编写媒体查询的方式。

## 媒体查询可以测试什么？

在构建响应式设计时，最常使用的媒体查询通常与设备的视口宽度（`width`）有关。根据我的经验，我发现除了分辨率和视口高度偶尔需要使用外，几乎没有必要使用其他功能。但是，以防万一需要，这里是媒体查询级别 3 可以测试的所有功能列表。希望其中一些能引起你的兴趣：

+   `width`：视口宽度。

+   `height`：视口高度。

+   `device-width`：渲染表面的宽度（对于我们的目的，这通常是设备的屏幕宽度）。

+   `device-height`：渲染表面的高度（对于我们的目的，这通常是设备的屏幕高度）。

+   `orientation`：此功能检查设备是纵向还是横向。

+   `aspect-ratio`：基于视口宽度和高度的宽高比。16:9 的宽屏显示可以写为`aspect-ratio: 16/9`。

+   `device-aspect-ratio`：此功能类似于`aspect-ratio`，但是基于设备渲染表面的宽度和高度，而不是视口。

+   `color`：每个颜色分量的位数。例如，`min-color: 16`将检查设备是否具有 16 位颜色。

+   `color-index`：设备颜色查找表中的条目数。值必须是数字，不能为负数。

+   `monochrome`：此功能测试单色帧缓冲区中每像素的位数。值将是一个数字（整数），例如，`monochrome: 2`，不能为负数。

+   `resolution`：此功能可用于测试屏幕或打印分辨率；例如，`min-resolution: 300dpi`。它还可以接受每厘米的点数；例如，`min-resolution: 118dpcm`。

+   `scan`：这可以是渐进式或隔行扫描功能，主要适用于电视。例如，720p 高清电视（720p 中的 p 表示“渐进式”）可以使用`scan: progressive`进行定位，而 1080i 高清电视（1080i 中的 i 表示“隔行扫描”）可以使用`scan: interlace`进行定位。

+   `grid`：此功能指示设备是基于网格还是位图。

所有前述功能，除了`scan`和`grid`，都可以用`min`或`max`进行前缀处理以创建范围。例如，考虑以下代码片段：

```html
@import url("tiny.css") screen and (min-width:200px) and (max-width:360px);
```

在这里，宽度应用了最小（`min`）和最大（`max`）来设置一个范围。tiny.css 文件只会被导入到视口宽度最小为 200 像素，最大为 360 像素的屏幕设备中。

### 注意

**CSS 媒体查询级别 4 中弃用的功能**

值得注意的是，媒体查询级别 4 的草案规范弃用了一些功能（[`dev.w3.org/csswg/mediaqueries-4/#mf-deprecated`](http://dev.w3.org/csswg/mediaqueries-4/#mf-deprecated)）；其中最明显的是`device-height`、`device-width`和`device-aspect-ratio`。浏览器将继续支持这些查询，但建议您不要编写使用它们的新样式表。

# 使用媒体查询来改变设计

由于它们的本质，样式表中更下面的样式（对我们来说是 CSS 文件）会覆盖更上面的等效样式（除非更上面的样式更具体）。因此，我们可以在样式表的开头设置基本样式，适用于我们设计的所有版本（或者至少提供我们的“基本”体验），然后在文档中进一步使用媒体查询来覆盖相关部分。例如，我们可能选择在有限的视口中将导航链接设置为纯文本（或者只是较小的文本），然后使用媒体查询来在更大的视口中覆盖这些样式，以便在更大的空间可用时为我们提供文本和图标。

让我们看看这在实践中是什么样子（`example_02-02`）。首先是标记：

```html
<a href="#" class="CardLink CardLink_Hearts">Hearts</a>
<a href="#" class="CardLink CardLink_Clubs">Clubs</a>
<a href="#" class="CardLink CardLink_Spades">Spades</a>
<a href="#" class="CardLink CardLink_Diamonds">Diamonds</a>
```

现在 CSS：

```html
.CardLink {
    display: block;
    color: #666;
    text-shadow: 0 2px 0 #efefef;
    text-decoration: none;
    height: 2.75rem;
    line-height: 2.75rem;
    border-bottom: 1px solid #bbb;
    position: relative;
}

@media (min-width: 300px) {
    .CardLink {
        padding-left: 1.8rem;
        font-size: 1.6rem;
    }
}

.CardLink:before {
    display: none;
    position: absolute;
    top: 50%;
    transform: translateY(-50%);
    left: 0;
}

.CardLink_Hearts:before {
    content: "♥";
}

.CardLink_Clubs:before {
    content: "♣";
}

.CardLink_Spades:before {
    content: "♠";
}

.CardLink_Diamonds:before {
    content: "♦";
}

@media (min-width: 300px) {
    .CardLink:before {
        display: block;
    }
}
```

### 提示

**下载示例代码**

您可以从您在[`www.packtpub.com`](http://www.packtpub.com)的帐户中下载您购买的所有 Packt 图书的示例代码文件。如果您在其他地方购买了这本书，您可以访问[`www.packtpub.com/support`](http://www.packtpub.com/support)并注册，以便将文件直接通过电子邮件发送给您。

这是一个小视口中链接的屏幕截图：

![使用媒体查询来改变设计](img/B03777_02_01.jpg)

这是它在较大的视口中的截图：

![使用媒体查询来改变设计](img/B03777_02_02.jpg)

## 任何 CSS 都可以包含在媒体查询中

重要的是要记住，您通常在 CSS 中编写的任何内容也可以包含在媒体查询中。因此，可以使用媒体查询在不同情况下（通常是不同的视口大小）完全改变站点的布局和外观。

## HiDPI 设备的媒体查询

媒体查询的另一个常见用例是在高分辨率设备上查看站点时更改样式。考虑这个：

```html
@media (min-resolution: 2dppx) {
  /* styles */
}
```

在这里，我们的媒体查询指定，我们只希望封闭的样式应用于屏幕分辨率为 2 像素每像素单位（2dppx）的情况。这将适用于 iPhone 4 等设备（苹果的 HiDPI 设备被称为“Retina”）以及大量的 Android 设备。您可以通过减少 dppx 值来将该媒体查询应用于更广泛的设备范围。

### 提示

在编写最小分辨率媒体查询时，确保运行有一个添加前缀的工具，以提供相关的供应商前缀，以获得尽可能广泛的支持。如果现在对供应商前缀这个术语不太理解，也不用担心，因为我们将在下一章更详细地讨论这个主题。

# 组织和编写媒体查询的考虑

在这一点上，我们将进行一个简短的偏离，考虑作者在编写和组织他们的媒体查询时可以采取的一些不同方法。每种方法都有一些好处和一些权衡，因此至少了解这些因素是值得的，即使您认为它们对您的需求基本上无关紧要。

## 链接到不同的 CSS 文件，带有媒体查询

从浏览器的角度来看，CSS 被认为是“渲染阻塞”的资源。浏览器需要在渲染页面之前获取和解析链接的 CSS 文件。

然而，现代浏览器足够聪明，可以区分哪些样式表（在头部链接的带有媒体查询的样式表）需要立即分析，哪些可以推迟到初始页面渲染之后再进行。

对于这些浏览器，链接到不适用媒体查询的 CSS 文件（例如，如果屏幕太小，媒体查询不适用）可以在初始页面加载后“推迟”，从而提供一些性能优势。

关于这个主题，Google 的开发者页面上有更多内容：[`developers.google.com/web/fundamentals/performance/critical-rendering-path/render-blocking-css`](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/render-blocking-css)

然而，我想特别提醒您注意这一部分：

> “...请注意，“渲染阻塞”只是指浏览器是否必须在该资源上保持页面的初始渲染。无论哪种情况，浏览器都会下载 CSS 资源，尽管对于非阻塞资源，它的优先级较低。”

再次强调，所有链接的文件仍然会被下载，只是如果它们不立即应用，浏览器不会延迟页面的渲染。

因此，现代浏览器加载一个响应式网页（查看`example_02-03`）时，会下载链接了不同媒体查询的四个不同样式表（以适应不同的视口范围），但可能只会在渲染页面之前解析适用的样式表。

## 分离媒体查询的实际性

尽管我们刚刚了解到分割媒体查询的过程可能会带来一些好处，但将不同的媒体查询样式分开到不同的文件中并不总是有很大的实际优势（除了个人偏好和/或代码的分隔）。

毕竟，使用单独的文件会增加呈现页面所需的 HTTP 请求的数量，这反过来可能会使页面在某些其他情况下变慢。在网络上没有什么是容易的！因此，这实际上是一个问题，评估您的网站的整体性能，并在不同设备上测试每种情况。

我对此的默认立场是，除非项目有足够的时间进行性能优化，否则这是我寻求性能提升的最后一个地方。只有当我确定：

+   所有图像都已经压缩

+   所有脚本都被连接并进行了最小化

+   所有资产都以 gzip 方式提供

+   所有静态内容都通过 CDN 进行缓存

+   所有多余的 CSS 规则已被删除

也许那时我会开始考虑将媒体查询拆分成单独的文件以获得性能提升。

### 提示

gzip 是一种压缩和解压缩文件格式。任何好的服务器都应该允许对 CSS 等文件进行 gzip 压缩，这将大大减小文件在从服务器到设备的传输过程中的大小（在这一点上，它被解压缩为其原生格式）。您可以在维基百科上找到 gzip 的一个很好的摘要：[`en.wikipedia.org/wiki/Gzip`](http://en.wikipedia.org/wiki/Gzip)

## 嵌套媒体查询“内联”

除了极端情况外，我建议在现有样式表中添加媒体查询，与“正常”的规则一起。

如果您愿意这样做，还有一个考虑因素：媒体查询应该在相关选择器下声明吗？还是分离出一个单独的代码块，包含所有相同的媒体查询？我很高兴你问了。

# 合并媒体查询还是根据需要编写媒体查询？

我喜欢在原始的“正常”定义下编写媒体查询。例如，假设我想要根据视口宽度在样式表的不同位置更改一些元素的宽度，我会这样做：

```html
.thing {
    width: 50%;
}

@media screen and (min-width: 30rem) {
    .thing {
        width: 75%;
    }
}

/* A few more styles would go between them */

.thing2 {
    width: 65%;
}

@media screen and (min-width: 30rem) {
    .thing2 {
        width: 75%;
    }
}
```

这乍一看似乎是疯狂的。我们有两个媒体查询都与屏幕最小宽度为 30rem 有关。重复相同的`@media`声明肯定是冗长和浪费的吧？我应该主张将所有相同的媒体查询分组到一个单独的代码块中，就像这样：

```html
.thing {
    width: 50%;
}

.thing2 {
    width: 65%;
}

@media screen and (min-width: 30rem) {
    .thing {
        width: 75%;
    }
    .thing2 {
        width: 75%;
    }
}
```

这当然是一种方法。然而，从维护的角度来看，我觉得这更加困难。没有“正确”的方法，但我更喜欢为单个选择器定义一条规则，并在其后立即定义该规则的任何变体（例如在媒体查询中的更改）。这样我就不必搜索单独的代码块，找到与特定选择器相关的声明。

### 注意

通过 CSS 预处理器和后处理器，这甚至可以更加方便，因为媒体查询的“变体”可以直接嵌套在规则集中。我的另一本书*Sass and Compass for Designers*中有一个完整的章节介绍这个。

从冗长的角度来看，对前一种技术提出异议似乎是公平的。单单文件大小就足以成为不以这种方式编写媒体查询的理由了吧？毕竟，没有人希望为用户提供一个臃肿的 CSS 文件。然而，简单的事实是，gzip 压缩（应该压缩服务器上的所有可能的资源）将这种差异减少到完全可以忽略的程度。我过去做过各种测试，所以如果您想了解更多信息，请访问：[`benfrain.com/inline-or-combined-media-queries-in-sass-fight/`](http://benfrain.com/inline-or-combined-media-queries-in-sass-fight/)。最重要的是，如果您宁愿直接在标准样式之后编写媒体查询，我认为您不应该担心文件大小。

### 提示

如果您想直接在原始规则之后编写媒体查询，但希望所有相同的媒体查询定义合并为一个，那么有许多构建工具（在撰写本文时，Grunt 和 Gulp 都有相关插件）可以实现这一点。

# viewport meta 标签

为了充分利用媒体查询，您希望较小的屏幕设备以其原生尺寸显示网页（而不是在 980px 窗口中渲染，然后您必须放大和缩小）。

2007 年苹果发布 iPhone 时，他们引入了一个名为 viewport `meta`的专有`meta`标签，Android 和越来越多的其他平台现在也支持这个标签。viewport `meta`标签的目的是为了让网页与移动浏览器通信，告诉它们希望如何渲染页面。

在可预见的未来，任何您希望响应式的网页，并在小屏设备上良好呈现的网页，都需要使用这个`meta`标签。

### 提示

**在模拟器和仿真器上测试响应式设计**

尽管在真实设备上测试开发工作是无法替代的，但 Android 有模拟器，iOS 有仿真器。

对于一丝不苟的人来说，模拟器只是模拟相关设备，而仿真器实际上试图解释原始设备代码。

Windows、Linux 和 Mac 的 Android 模拟器可通过下载和安装 Android**软件开发工具包**（**SDK**）免费获取，网址为[`developer.android.com/sdk/`](http://developer.android.com/sdk/)。

iOS 模拟器仅适用于 Mac OS X 用户，并作为 Xcode 软件包的一部分（可从 Mac App Store 免费获取）。

浏览器本身也在其开发工具中包含了不断改进的模拟移动设备的工具。Firefox 和 Chrome 目前都有特定的设置来模拟不同的移动设备/视口。

viewport `<meta>`标签添加在 HTML 的`<head>`标签中。它可以设置为特定宽度（例如，我们可以指定为像素）或作为比例，例如`2.0`（实际大小的两倍）。以下是 viewport `meta`标签的示例，设置为显示浏览器为实际大小的两倍（200％）：

```html
<meta name="viewport" content="initial-scale=2.0,width=device-width" />
```

让我们分解前面的`<meta>`标签，以便我们了解发生了什么。`name="viewport"`属性是显而易见的。然后，`content="initial-scale=2.0`部分表示“将内容缩放到原始大小的两倍”（其中 0.5 表示原始大小的一半，3.0 表示原始大小的三倍，依此类推），而`width=device-width`部分告诉浏览器页面的宽度应等于设备宽度。

`<meta>`标签还可以用于控制用户在页面上放大和缩小的程度。此示例允许用户放大到设备宽度的三倍，缩小到设备宽度的一半：

```html
<meta name="viewport" content="width=device-width, maximum-scale=3, minimum-scale=0.5" />
```

您还可以完全禁用用户缩放，尽管缩放是一个重要的辅助工具，但在实践中很少会适用：

```html
<meta name="viewport" content="initial-scale=1.0, user-scalable=no" />
```

`user-scalable=no` 是相关部分。

好了，我们将缩放比例更改为`1.0`，这意味着移动浏览器将以其视口的 100％呈现页面。将其设置为设备的宽度意味着我们的页面应该在所有支持的移动浏览器的宽度的 100％呈现。对于大多数情况，这个`<meta>`标签是合适的：

```html
<meta name="viewport" content="width=device-width,initial-scale=1.0" />
```

### 提示

注意到 viewport `meta`元素的使用越来越多，W3C 正在努力将相同的功能引入 CSS。前往[`dev.w3.org/csswg/css-device-adapt/`](http://dev.w3.org/csswg/css-device-adapt/)，了解有关新的`@viewport`声明的所有信息。这个想法是，您可以在 CSS 中写`@viewport { width: 320px; }`，而不是在标记的`<head>`部分中写`<meta>`标签。这将把浏览器宽度设置为 320 像素。然而，浏览器支持有限，尽管为了尽可能覆盖所有基础并尽可能具有未来的性能，您可以使用`meta`标签和`@viewport`声明的组合。

到目前为止，您应该已经对媒体查询及其工作原理有了扎实的掌握。然而，在我们完全转移到另一个话题之前，我认为考虑一下媒体查询的下一个版本可能会有什么可能性是很好的。让我们来偷偷看一眼！

# 媒体查询 4 级

在撰写本文时，虽然 CSS 媒体查询 4 级有一个草案规范（[`dev.w3.org/csswg/mediaqueries-4/`](http://dev.w3.org/csswg/mediaqueries-4/)），但草案中的功能并没有得到很多浏览器的实现。这意味着虽然我们将简要介绍此规范的亮点，但它非常不稳定。在使用这些功能之前，请确保检查浏览器支持并仔细检查语法更改。

目前，虽然 4 级规范中还有其他功能，但我们只关注脚本、指针和悬停以及亮度。

## 脚本媒体特性

在 HTML 标签上设置一个类来指示默认情况下没有 JavaScript，然后在 JavaScript 运行时用不同的类替换该类是一种常见做法。这提供了一个简单的能力来根据新的 HTML 类分叉代码（包括 CSS）。具体来说，使用这种做法，你可以编写特定于启用 JavaScript 的用户的规则。

这可能会让人困惑，所以让我们考虑一些示例代码。默认情况下，这将是在 HTML 中编写的标签：

```html
<html class="no-js">
```

当 JavaScript 在页面上运行时，它的第一个任务之一将是替换`no-js`类：

```html
<html class="js">
```

完成后，我们可以编写特定的 CSS 规则，这些规则只在 JavaScript 存在时才适用。例如，`.js .header { display: block; }`。

然而，CSS Media Queries Level 4 的脚本媒体特性旨在提供一种更标准的方式直接在 CSS 中执行此操作：

```html
@media (scripting: none) {
    /* styles for when JavaScript not working */
}
```

当 JavaScript 存在时：

```html
@media (scripting: enabled) {
    /* styles for when JavaScript is working */
}
```

最后，它还旨在提供确定 JavaScript 是否存在但仅在最初时。W3C 规范中给出的一个例子是，可以最初布置打印页面，但之后没有 JavaScript 可用。在这种情况下，你应该能够这样做：

```html
@media (scripting: initial-only) {
    /* styles for when JavaScript works initially */
}
```

这个功能的当前编辑草案可以在这里阅读：[`dev.w3.org/csswg/mediaqueries-4/#mf-scripting`](http://dev.w3.org/csswg/mediaqueries-4/#mf-scripting)

## 交互媒体特性

以下是 W3C 对指针媒体特性的介绍：

> *“指针媒体特性用于查询指针设备（如鼠标）的存在和准确性。如果设备有多个输入机制，则指针媒体特性必须反映“主要”输入机制的特性，由用户代理确定。”*

指针特性有三种可能的状态：`none`，`coarse`和`fine`。

`粗糙`指针设备可能是触摸屏设备上的手指。然而，它也可以是游戏控制台上没有鼠标那样精细控制的光标。

```html
@media (pointer: coarse) {
    /* styles for when coarse pointer is present */
}
```

`fine`指针设备可能是鼠标，但也可能是触控笔或任何未来的精细指针机制。

```html
@media (pointer: fine) {
    /* styles for when fine pointer is present */
}
```

就我而言，浏览器越早实现这些指针特性越好。目前，要知道用户是否有鼠标、触摸输入或两者都有是非常困难的。以及他们在任何时候使用的是哪一个。

### 提示

最安全的做法总是假设用户使用基于触摸的输入，并相应地调整用户界面元素的大小。这样，即使他们使用鼠标，也不会难以轻松使用界面。然而，如果你假设鼠标输入，并且无法可靠地检测触摸以修改界面，可能会导致困难的体验。

对于同时开发触摸和指针的挑战的很好概述，我推荐 Patrick H. Lauke 的这组幻灯片*Getting touchy*：[`patrickhlauke.github.io/getting-touchy-presentation/`](https://patrickhlauke.github.io/getting-touchy-presentation/)

在这里阅读这个功能的编辑草案：[`dev.w3.org/csswg/mediaqueries-4/#mf-interaction`](http://dev.w3.org/csswg/mediaqueries-4/#mf-interaction)

## 悬停媒体特性

正如你所想象的，悬停媒体特性测试用户在屏幕上悬停元素的能力。如果用户有多个输入设备（例如触摸和鼠标），则使用主要输入的特性。以下是可能的值和示例代码：

对于没有悬停能力的用户，我们可以以`none`的值为他们定制样式。

```html
@media (hover: none) {
    /* styles for when the user cannot hover */
}
```

对于可以悬停但必须执行重要操作来启动它的用户，可以使用`on-demand`。

```html
@media (hover: on-demand) {
    /* styles for when the user can hover but doing so requires significant effort */
}
```

对于可以悬停的用户，可以单独使用`hover`。

```html
@media (hover) {
    /* styles for when the user can hover */
}
```

请注意，还有`any-pointer`或`any-hover`媒体特性。它们类似于前面的 hover 和 pointer，但测试任何可能的输入设备的功能。

## 环境媒体特性

如果我们能够根据环境特征（如环境光水平）来改变我们的设计，那不是挺好的吗？这样，如果用户在较暗的房间里，我们可以降低所使用颜色的亮度。或者相反，在更明亮的阳光下增加对比度。环境媒体特性旨在解决这些问题。请考虑以下示例：

```html
@media (light-level: normal) {
    /* styles for standard light conditions */
}
@media (light-level: dim) {
    /* styles for dim light conditions */
}
@media (light-level: washed) {
    /* styles for bright light conditions */
}
```

请记住，目前很少有这些 Level 4 媒体查询的实现。在我们能够安全使用它们之前，规范很可能会发生变化。然而，了解未来几年我们将拥有哪些新功能是有用的。

阅读此功能的编辑草案：[`dev.w3.org/csswg/mediaqueries-4/#mf-environment`](http://dev.w3.org/csswg/mediaqueries-4/#mf-environment)

# 摘要

在本章中，我们学习了什么是 CSS3 媒体查询，如何在 CSS 文件中包含它们，以及它们如何帮助我们创建响应式网页设计。我们还学习了如何使用`meta`标签使现代移动浏览器呈现页面，就像我们想要的那样。

然而，我们也了解到，单独使用媒体查询只能提供一个适应性的网页设计，从一个布局切换到另一个布局。而不能实现一个真正响应式的设计，能够平稳地从一个布局过渡到另一个布局。为了实现我们的最终目标，我们还需要利用流动布局。它们将允许我们的设计在媒体查询处理的断点之间灵活变化。在下一章中，我们将介绍如何创建流动布局，以平滑过渡我们的媒体查询断点之间的变化。
