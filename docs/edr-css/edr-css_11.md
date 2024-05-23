# 附录 2. 浏览器代表对 CSS 性能的看法

作为附录 1 的补充，*CSS 选择器性能*，以下文字涉及浏览器代表对 CSS 性能的看法。

# TL;DR

如果你不想读这一节的其他内容，那么请读下一段并牢记：

在没有检查自己的*数据*之前，不要记忆与 CSS 性能相关的规则。它们基本上是无用的、短暂的和太主观的。相反，熟悉工具并使用它们来揭示自己场景的相关数据。这基本上是 Chrome 开发者关系人员多年来一直在推广的口号，我相信是 Paul Lewis（下文还有更多）创造了与 Web 性能故障排除相关的术语*工具，而不是规则*。

现在我理解那种情绪。真的理解了。

# 浏览器代表对 CSS 性能的看法

通常情况下，我在编写样式表时不太担心 CSS 选择器（通常我只是在我想要设置样式的任何东西上放一个类并直接选择它），但偶尔我会看到一些比我聪明得多的人对特定的选择器发表评论。以下是*Paul Irish*（[`www.paulirish.com/`](https://www.paulirish.com/)）在与*Heydon Pickering*（[`alistapart.com/article/quantity-queries-for-css`](http://alistapart.com/article/quantity-queries-for-css)）的一篇文章相关的评论，该文章使用了一种特定类型的选择器：

> *这些选择器是可能的最慢的。比像 div.box:not(:empty):last-of-type .title”这样的东西慢大约 500 倍。测试页面 http://jsbin.com/gozula/1/quiet。也就是说，选择器速度很少是一个问题，但如果这个选择器最终出现在一个 DOM 变化非常频繁的动态 Web 应用程序中，它可能会产生很大的影响。因此，对于许多用例来说是不错的，但请记住，随着应用程序的成熟，它可能成为性能瓶颈。这是一个需要在那时进行分析的事情。干杯*

我们应该从中得出什么？我们是否应该在头脑中将这种选择器放在某种*紧急情况下不要使用*的保险库中？

为了得到一些*真正*的答案，我询问了实际在浏览器上工作的聪明人，问他们对 CSS 性能应该关注什么。

在前端世界中，我们很幸运，因为 Chrome 开发者关系团队是如此可及。然而，我喜欢平衡。此外，我还联系了微软和火狐的人，并包括了 WebKit 的一些很好的意见。

# 我们应该担心 CSS 选择器吗？

问题本质上是，*作者是否应该关注与 CSS 性能相关的选择器？*

让我们从开始的地方开始，那里有 CSSOM 和 DOM 实际上被构建。Chrome 开发者关系的开发者倡导者*Paul Lewis*（[`aerotwist.com/`](http://aerotwist.com/)）解释说，*样式计算受两个因素影响：选择器匹配和无效大小。当你首次加载页面时，所有元素的所有样式都需要计算，这取决于树的大小和选择器的数量。*

更详细的内容，Lewis 引用了 Opera 团队的*Rune Lillesveen*（[`docs.google.com/document/d/1vEW86DaeVs4uQzNFI5R-_xS9TcS1Cs_EUsHRSgCHGu8/edit#`](https://docs.google.com/document/d/1vEW86DaeVs4uQzNFI5R-_xS9TcS1Cs_EUsHRSgCHGu8/edit#)）的话：

> *在撰写本文时，大约 50%的时间用于计算元素的计算样式，用于匹配选择器，另一半时间用于从匹配规则构造 RenderStyle（计算样式表示）*

好吧，这对我来说有点*科学*，那是否意味着我们需要担心选择器呢？

Lewis 再次说道，*选择器匹配可能会影响性能，但树的大小往往是最重要的因素*。

这是理所当然的，如果你有一个庞大的 DOM 树和一大堆无关的样式，事情就会开始变得困难。我的自己的*膨胀测试*（[`benfrain.com/selector-test/2-01.html`](https://benfrain.com/selector-test/2-01.html)）支持这一点。再考虑另一种情况。如果我给你两堆各有 1000 张卡片，除了 5 张匹配的卡片外，每堆上的卡片名字都不同，那么很显然要花更长的时间来配对这些匹配的名字，而不是只有 100 张或 10 张卡片。对于浏览器也是同样的道理。

我认为我们都可以同意，样式膨胀比使用的 CSS 选择器更令人担忧。也许这是我们可以信赖的一个规则？

|   | *对于大多数网站，我认为选择器性能不是值得花时间寻找性能优化的最佳领域。我强烈建议专注于括号内的内容，而不是括号外的选择器* |   |
| --- | --- | --- |
|   | --*Greg Whitworth, 微软的项目经理* |

# 那么 JavaScript 呢

然而，Whitworth 也指出，在处理 JavaScript 和 DOM 结构的动态性时需要额外的注意，*如果你一遍又一遍地使用 JavaScript 在事件上添加或替换类，你应该考虑这将如何影响整体的网络管道和你正在操作的盒子的 DOM 结构*。

这与*Paul Irish*（[`www.paulirish.com/`](https://www.paulirish.com/)）早期的评论相吻合。由于类的更改而导致 DOM 区域的快速失效有时可能会显示出复杂的选择器。那么，也许我们应该担心选择器？

|   | *每个规则都有例外，有些选择器比其他选择器更有效，但我们通常只在有大量 DOM 树和 JavaScript 反模式导致 DOM 抖动和额外布局或绘制发生的情况下才会看到这些选择器* |   |
| --- | --- | --- |
|   | --Whitworth |

对于更简单的 JavaScript 更改，Lewis 提供了这样的建议，*解决方案通常是尽可能地紧密地定位元素，尽管 Blink 越来越聪明，可以确定哪些元素真正会受到对父元素的更改的影响*。因此，实际上，如果可能的话，如果你需要影响 DOM 元素的更改，最好是在 DOM 树中直接在它上面添加一个类，而不是在 body 或 html 节点上。

# 处理 CSS 性能

在这一点上，我很高兴地得出了在附录 1 中得出的结论，*CSS 选择器性能* - CSS 选择器在静态页面中很少会出现问题。此外，试图预测哪个选择器会表现良好可能是徒劳的。

然而，对于大型 DOM 和动态 DOM（例如不仅仅是偶尔的类切换，我们说的是大量的 JavaScript 操作），CSS 选择器可能会成为一个问题并不是不可能的。*我不能代表所有的 Mozilla，但我认为当你处理性能问题时，你需要关注什么是慢的。有时候会是选择器；通常会是其他事情*，来自*Mozilla*（[`www.mozilla.org/en-US/`](https://www.mozilla.org/en-US/)）和 W3C 的 CSS 工作组成员*L. David Baron*（[`dbaron.org/`](http://dbaron.org/)）说道。*我确实看到过选择器性能很重要的页面，也确实看到过很多页面选择器性能并不重要*。

那么我们应该怎么做？什么是最实用的方法？

|   | *你应该使用性能分析工具来确定你的性能问题在哪里，然后努力解决这些问题* |   |
| --- | --- | --- |
|   | --*Baron* |

我和所有人交谈的时候都表达了这些观点。

# 总结

如果您在网络上开发了一段时间，就会知道大多数与网络相关的问题的答案是“这取决于情况”。我讨厌在 CSS 性能方面没有简单的、铁一般的规则可以在任何情况下依赖。我真的很想在这里写出那些规则，并相信它们是普遍适用的。但我不能，因为在性能方面根本没有普遍适用的“铁一般”的真理。永远不可能有，因为变量太多了。引擎更新，布局方法变得更加优化，每个 DOM 树都不同，所有的 CSS 文件也都不同。如此循环往复。你明白了吧。

我害怕我能提供的最好建议就是不要提前担心 CSS 选择器或布局方法。它们不太可能是你的问题（但是，你知道，它们可能会是）。相反，集中精力去做“那件事”。然后，当“那件事”做好了，测试“那件事”。如果它慢或者出了问题，找到问题并修复“那件事”。

## 额外信息

+   Greg Whitworth 推荐*2012 年 Build talk*（[`blogs.msdn.com/b/ie/archive/2012/11/20/build-2012-50-performance-tricks-to-make-your-html5-applications-and-sites-faster.aspx`](http://blogs.msdn.com/b/ie/archive/2012/11/20/build-2012-50-performance-tricks-to-make-your-html5-applications-and-sites-faster.aspx)）

+   *CSS Triggers*（[`csstriggers.com/`](https://csstriggers.com/)）由 Paul Lewis 指出了 CSS 中的哪些变化会触发 Blink 引擎（Chrome/Opera）中的布局、绘制和合成操作。