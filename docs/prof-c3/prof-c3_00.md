# 前言

CSS 通常被认为是一种简单的语言。实际上，尽管它是声明性的并且表面上看起来简单，但它很难维护。对于不断增长的大规模网络应用程序，可维护性至关重要。本书介绍了利用已知的技巧和黑客、新的 CSS 3 模块技术、预处理器和其他工具来创建真正高质量的产品的方法。这将包括如处理浮动和基于组件的 CSS 等技术的示例。

# 本书涵盖的内容

第一章，“基础和工具”，介绍了可以帮助您构建更好的 CSS 代码的工具。它描述了预处理器的特性，然后提供了关于 SASS 的基础知识。在这一章中，您将获得有关使用 GULP.js 在前端开发中自动化可重复流程的基础知识。您还将找到一个文件结构的示例，您可以使用它将项目分成小文件，易于编辑和维护。

第二章，“基础的掌握”，帮助您掌握框模型、浮动 CSS、定位故障排除和显示类型。在本章之后，您将更加了解 HTML 和 CSS 的基础知识。

第三章，“伪类和伪元素的掌握”，描述了伪类和伪元素以及如何使用它们。它将涵盖绘制基本图形的问题以及如何将其作为优化 CSS 代码的一部分使用。

第四章，“响应式网站-为特定设备准备您的代码”，提供了关于 RWD 以及如何准备项目的知识。它将涵盖现代网站的问题和优化技术。

第五章，“在 CSS 中使用背景图片”，解决了几乎每个网页上都有图片的事实。本章将教您如何在现代设备的广泛范围上正确显示图片，包括手机和平板电脑。

第六章，“样式化表单”，教您如何样式化表单以及您可以使用哪些 CSS 元素和不能使用哪些 CSS 元素。

第七章，“解决经典问题”，是关于解决 CSS 中经典问题的故障排除：处理不透明度、变换和居中元素。

第八章，“Flexbox 变换的使用”，教您有关 CSS 的新特性以及在哪里使用它们。

第九章，“Calc、渐变和阴影”，将提供有关在 CSS 中进行数学运算的 calc 函数的信息。本章将揭示渐变函数以及您如何在 HTML 布局中使用它们。在本章中，您还将获得有关 CSS 阴影及其用法的基础知识。在本章之后，您将知道如何向框和文本添加阴影。

第十章，“不要重复自己-让我们创建一个简单的 CSS 框架”，是关于构建可重用代码以及如何稍后将其用作自己项目的基础的问题。本章将涵盖与创建基本 CSS 框架相关的问题。

第十一章, *邮件发送基础知识*，是对邮件发送和在邮件发送过程中可能出现的问题的简短介绍。本章侧重于基础知识。

第十二章, *可扩展性和模块化*，教你如何准备可扩展的 CSS 代码。

第十三章, *代码优化*，涉及在构建 CSS 代码后发生的最终过程。主要是关于优化和缩小工具。它涵盖了在开始编码之前和在创建 CSS 代码期间准备代码时涉及的问题。

第十四章, *最终自动化和流程优化*，涉及对 CSS 代码进行操作的自动化。

# 您需要什么

为了使用本书，建议您安装您喜欢的 IDE，该 IDE 应支持以下内容：

+   HTML

+   SASS

+   CSS

为了更好地理解代码及其调试，您将需要像这样的浏览器：

+   Google Chrome

+   Mozilla Firefox

+   Internet Explorer 9+

此外，您还需要以下内容：

+   Ruby（用于安装 SASS）

+   SASS

+   Node.js（用于安装 Gulp.js）

+   Gulp.js

# 这本书适合谁

本书适用于所有希望学习如何使用 CSS 和 SASS 功能的前端开发人员。本书涵盖了许多对每个级别的开发人员都可能感兴趣的主题。如果您是初学者，它将向您介绍 CSS 和 SASS。如果您是中级/高级程序员，本书可以是一本关于一些 CSS 和 SASS 功能的良好复习书。此外，最后一章适用于所有希望开始作为前端开发人员工作并希望自动化大量任务（例如缩小 CSS 代码）的开发人员。

# 约定

在本书中，您将找到许多工具。主要是 SASS 和 CSS 代码，但是如您所知，CSS 不能单独工作，我们将使用基本的 HTML 结构。此外，还将有大量 JS 代码，用于描述 Gulp.js 任务。

文本中的代码词、数据库表名、文件夹名、文件名、文件扩展名、路径名、虚拟 URL、用户输入和 Twitter 句柄显示如下："使用预处理器，每个`@import`都会为您进行合并，在这个位置，您将拥有所提到文件的内容"

代码块设置如下：

```css
@import "typography.css"
@import "blocks.css"
@import "main.css"
@import "single.css"
```

任何命令行输入或输出都将按如下方式编写：

```css
npm init
npm install gulp-compass gulp --save-dev

```

**新术语**和**重要单词**以粗体显示。例如，屏幕上看到的单词，例如菜单或对话框中的单词，会在文本中显示为这样："调用检查器的最简单方法是右键单击元素，然后选择**检查**。"

### 注意

警告或重要说明会出现在这样的框中。

### 提示

提示和技巧会出现在这样。
