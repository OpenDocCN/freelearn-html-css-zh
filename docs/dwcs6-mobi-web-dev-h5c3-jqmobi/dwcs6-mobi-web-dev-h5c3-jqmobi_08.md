# 第八章：增强移动站点

在第七章中，*使用 jQuery Mobile 创建移动页面*，我们介绍了在 Dreamweaver 中构建 jQuery Mobile 站点所需的基本步骤。在这个过程中，我们专注于向 jQuery Mobile HTML 页面添加页面元素，并构建链接到这些页面的列表视图。

通过这样做，我们涵盖了构建功能性 jQuery Mobile 站点所需的大部分内容。您可以使用移动设备浏览网络，并找到许多仅依赖于 jQuery Mobile 页面元素和列表视图的专业级站点。事实上，拿出您最近的移动设备稍微浏览一下可能是值得的。您会欣赏到基本列表视图对于 jQuery Mobile 站点的重要性——类似于以下截图中为旧金山纪事报所示的内容：

![增强移动站点](img/4742_08_01.jpg)

然而，移动页面设计不仅仅是列表视图！还有其他方式可以在移动设备上提供页面内容。您可以设计带有网格（列）的页面。您还可以使用可扩展块，允许用户在垂直方向展开或收缩以呈现内容。

如果您进行更多的移动浏览，您会发现一些具有可展开/可折叠元素形式的站点。例如，Google 新闻使用可展开元素来显示（或者默认情况下隐藏）新闻故事的**更多来源**。

![增强移动站点](img/4742_08_02.jpg)

此外，还有一个挑战，即为移动设备构建真正具有吸引力和可访问性的表单，而不会让用户因为被迫尝试用指甲点击微小的复选框或单选按钮而感到烦恼，而是提供易于在智能手机上轻击的漂亮大表单元素。

我们将在本章中解决所有这些挑战；以下是本章涵盖的主题：

+   插入布局网格

+   使用可折叠块设计移动页面

+   添加 jQuery 表单对象

+   使用可折叠块和表单构建一个网页友好的站点

# 插入布局网格

与为全尺寸视口设计的页面相比，为移动设备设计的页面中，列的作用要小得多。

如果您允许文本行横跨全尺寸浏览器中 960 像素页面的整个宽度，那么文本将很难阅读。因此，出于这个原因和其他原因，两列或三列布局通常是在全尺寸浏览环境中使内容具有吸引力和可访问性的最佳方式。

然而，移动视口是不同的：移动电话的视口宽度不大，甚至平板电脑的屏幕也比笔记本电脑窄。尽管如此，在移动友好的页面中，设计页面内容以列的方式是非常有用的。在这种情况下，工具就是 jQuery 网格。网格允许您轻松地将列构建到 jQuery Mobile 页面元素中，如下菜单所示：

![插入布局网格](img/4742_08_03.jpg)

## 表格、div 标签和网格

长久以来，或者至少有几年，表格是网页设计页面布局技术的主要内容。有创意的设计师改编了原本用于呈现数据行和列的东西，以在网页上布局内容。

我们现在已经过了那个时代。相反，全尺寸网页是使用`div`标签设计的，这是我们在第一章中探讨过的内容，特别是在*使用 ID 和类 div 样式进行布局*部分。表格仍然存在；使用表格设计的旧网站仍然在线。如今，表格已经被 ID 和类`div`标签样式取代，因为后者是设计页面的更强大和灵活的方式。

那么在移动页面布局中*使用*表格呢？嗯，这种技术在 jQuery Mobile 中得到支持。但我们在 jQuery 页面中不使用表格进行页面布局的原因与我们在全尺寸页面设计中不使用它们的原因相同：表格笨重，难以应用全局样式，难以更新，并且不支持许多`div`容器支持的属性。也就是说，表格设计爱好者请注意：您*可以*在 jQuery Mobile 页面中使用表格设计页面布局。

我们能否使用在 HTML 中为我们服务良好的老式`<div>`标签来布置页面内容的列？是的。但我们必须以一种特殊的方式来实现这一点，以便实现 jQuery Mobile 中如此宝贵的格式化、动画和交互。我将在一会儿向您介绍这是如何工作的。

在 jQuery Mobile 页面中设计列布局的最灵活、标准的方法是使用网格。标准的 jQuery Mobile CSS 文件带有一组定义的类样式，称为`ui-block`和`ui-grid`。此外，这些样式有两套，一套用于两列布局，另一套用于三列布局。

Dreamweaver 的 jQuery Mobile 小部件为布局网格的生成做了非常完整的工作，可以生成各种各样的网格，包括可定义的列数和行数。请记住，当您生成这样的网格时，您是在为某种相对较窄的视口设计，并且希望在生成多少列（和行）时保持克制。

但是，从设计的角度来看，您可以在技术上放松。Dreamweaver 中的布局网格小部件将相当复杂的 2 列和 3 列网格组合在一起，以创建四、五、六列甚至更多列的网格，如果您选择这样做的话。

## 在 Dreamweaver 中生成网格

要在 jQuery Mobile 页面中生成布局网格，请确保插入点位于`content` div data-role 中。一种简单的方法是选择在创建 jQuery Mobile“页面”时生成的代码中的文本内容，并将其替换为布局网格，或者将光标放在`content`占位符文本之后。

然后，导航到**插入** | **jQuery Mobile** | **布局网格**。**jQuery Mobile 布局网格**对话框将打开。选择**行**和**列**的值，然后单击**确定**生成布局网格，如下截图所示：

![在 Dreamweaver 中生成网格](img/4742_08_04.jpg)

## 定义布局网格的样式

jQuery Mobile 布局网格使用两个类样式——`.ui-grid-a`用于两列网格，`.ui-grid-b`用于三列网格。如前所述，Dreamweaver 将从**jQuery Mobile 布局网格**对话框中生成 HTML，以串联这两个网格的组合，以创建超过三列的网格。此外，Dreamweaver 生成`.ui-grid`类样式来定义特定的块格式。

重点是？通过编辑`.ui-grid`和`.ui-block`类样式的属性，您可以定义布局网格元素的外观。

在这样做时，避免编辑网格或块的宽度，或者边距、填充或边框尺寸。更改这些属性将破坏生成的布局。但您可以编辑背景颜色和图像。

让我们看看这是如何工作的。

`.ui-grid-a`类样式（定义了两列网格）可以被本地网格类样式覆盖。但这并不会带来太多的格式自由度，因为网格本身只提供了容纳两个块的框架。

要编辑左侧块（`.ui-block-a`）的外观，请按以下步骤操作：

1.  单击**CSS 样式**面板底部的**新 CSS 样式规则**图标。**新 CSS 规则**对话框将打开。

1.  在**选择器类型**字段中，选择**类**。

1.  在**选择器名称**字段中，输入`.ui-block-a`。

1.  在**规则定义**框中，选择**仅限本文档**。

1.  单击**确定**关闭对话框，并打开`.ui-block-a`的**CSS 规则定义**对话框。

1.  在**背景颜色**字段中，选择一个背景颜色。

1.  在框类别中，输入高度为`200px`。

1.  单击**确定**以定义此本地样式，并在**实时**视图中检查效果，并在**CSS 样式**面板中检查样式规则。![为布局网格定义样式](img/4742_08_05.jpg)

让我们反思发生了什么以及为什么。`.ui-block-a`类样式的许多属性，定义了网格内左侧块的外观，作为使 jQuery Mobile 正常工作的通用 CSS 样式文件的一部分是固定的。在 Dreamweaver 中生成新的 jQuery Mobile 页面时，我们链接到了该 CSS 文件。

但是，`.ui-block-a`类样式的一些属性是不固定的，我们可以在仅适用于我们的 HTML 页面的本地样式表中进行编辑。`background-color`和`height`是我们可以编辑的两个属性，并提供了一种自定义网格外观的方法。

当然，我们也可以将相同的技术应用于定义了网格内右侧块的`.ui-block-b`类样式，如下面的屏幕截图所示：

![为布局网格定义样式](img/4742_08_06.jpg)

格式化的网格和块有多大用处？它们越来越有用，因为越来越多的移动设计师正在使用 jQuery Mobile 为较大和中等尺寸的平板电脑创建多列布局。块和网格为 jQuery Mobile 中的列布局提供了最灵活、可访问的工具。

# 使用可折叠块设计移动页面

正如您在上一章中看到的（第七章，“使用 jQuery Mobile 创建移动页面”），jQuery Mobile 页面本质上创建了从页面到页面的导航感觉，同时依靠 JavaScript 来实际显示和隐藏内容。这是在 Dreamweaver 中生成的示例 jQuery Mobile 页面中使用的技术。

可展开块的操作原理类似——根据访问者的操作来显示和隐藏内容。但是，对于可展开面板，这是通过页面的部分出现扩展或收缩来实现的，如下面的屏幕截图所示：

![使用可折叠块设计移动页面](img/4742_08_07.jpg)

## 构建可折叠块

与其他 jQuery Mobile 对象一样，可折叠面板需要一个 jQuery Mobile 页面的框架。因此，实现它们的第一步是创建一个 jQuery Mobile 页面。这可以通过导航到**插入** | **jQuery Mobile** | **页面**来完成。我们在本章的前面已经探讨了在 Dreamweaver 中生成 jQuery Mobile 页面的选项。

一旦您生成了一个带有所有相关 CSS 和 JavaScript 文件的 jQuery Mobile 页面，您就可以定义可折叠面板。通过设置插入点来完成这一操作（在**分割**视图的代码侧上最容易完成，同时打开**实时**视图）。

导航到**插入** | **jQuery Mobile** | **可折叠块**。没有对话框出现，Dreamweaver 会为块内的三个可折叠部分生成 HTML 代码。

在上一章的起始页面和本章的布局网格以及您在 HTML5 和 CSS 方面的背景知识的基础上，您已经构思了我们将如何自定义可折叠块的外观和内容。我们可以通过使用 jQuery Mobile 数据主题集和自定义 CSS 样式的组合来更改格式。此外，我们可以通过编辑 HTML 来更改内容，包括复制和粘贴可折叠块。

## 更改初始块状态

整个可折叠元素集由以下代码定义：

```js
<div data-role="collapsible-set">
```

在可折叠集的开头和结尾的`<div>`标签之间是单独的可展开块：

```js
<div data-role="collapsible" data-collapsed="true"> </div>
```

或者默认情况下在页面打开时展开的块，使用以下代码定义：

```js
<div data-role="collapsible">
```

默认情况下，打开页面时，三个可展开部分中的第一个部分会展开，其他两个部分会折叠。将`data-collapsed="true"`参数添加到最初打开的面板会在页面打开时将其更改为折叠状态。

![更改初始块状态](img/4742_08_08.jpg)

此外，从面板中相反地移除`data-collapsed="true"`会使其在页面打开时显示为展开状态。

## 更改块数据主题和样式

我们可以向任何数据块添加`data-theme`参数。例如，将`<div data-role="collapsible">`更改为`<div data-role="collapsible" data-theme="e">`会将数据主题`e`（黄色和红色配色方案）应用于该块，如下截图所示：

![更改块数据主题和样式](img/4742_08_09.jpg)

显然，对于默认的主题颜色方案，您可以做的事情有相当严格的限制。不用担心，在下一章中，我们将探索自定义主题。

与可折叠面板相关的 CSS 样式可以在**CSS 样式**面板中进行自定义。这些样式通常以`.ul-collapsible`开头。

例如，`.ui-collapsible-contain`样式控制展开块的内容的许多属性，如下截图所示：

![更改块数据主题和样式](img/4742_08_10.jpg)

### 提示

在更改`.ul-collapsible`类样式的尺寸时要小心。避免更改填充、边距和边框，因为这些参数的混乱可能会破坏可折叠的列。您可以自定义字体、颜色、字体大小、背景颜色和其他属性。而且，我们将在下一章中探索主题自定义的整个世界。

## 编辑可折叠块 HTML

根据您的倾向，您可以在设计视图中编辑可折叠块的内容，关闭实时视图，或者在实时视图中，通过编辑分割视图的代码一侧来编辑内容。在任何情况下，您只需添加 HTML 标签（如标题、段落标签、有序或无序列表等），以及文本、图像和媒体。

如果您在**分割**视图的**代码**一侧编辑内容，请定期单击**文档**工具栏中的**刷新**按钮以更新视图的**设计**一侧。

![编辑可折叠块 HTML](img/4742_08_11.jpg)

在游戏的这个阶段，您已经自己找出了如何向集合添加可折叠块的一部分解决方案：只需复制、粘贴和编辑现有块。

![编辑可折叠块 HTML](img/4742_08_12.jpg)

### 提示

既然你问了（我读懂了你的心思），是的，您可以在可折叠块内嵌入可折叠块。但是，请记住，保持移动页面布局相当简单是重点，所以，俗话说，当为移动设备组织内容时，少即是多。

# 添加 jQuery 表单对象

在移动设备环境中填写表单的体验与在笔记本电脑或台式机上填写表单的体验大不相同。没有鼠标，甚至（通常）没有*Tab*键在表单字段之间导航。大手指和弹出菜单中的微小选项不搭配。

在全尺寸浏览器中可能正常工作的表单在移动设备上可能会非常不友好和不方便。以苹果的商店定位器（如下截图所示）为例，它对移动用户设计不佳，需要移动用户调用他们令人沮丧的键盘来输入邮政编码到一个小小的文本字段中：

![添加 jQuery 表单对象](img/4742_08_13.jpg)

解决这个挑战的部分解决方案是，移动设备通常会将表单字段转换为更易访问的元素。例如，选择菜单中的选项在点击时可能会显示得更大，这样更容易进行选择。我刚才批评的同样是苹果表单，它有一个更好的选择产品的选项——一个下拉菜单，更容易在移动设备和像我这样的粗手指上访问。

![添加 jQuery 表单对象](img/4742_08_14.jpg)

解决在移动设备上使表单可访问和吸引人的另一部分是实现新的表单字段，例如滑块（访问者可以通过在条上滑动拇指来选择一系列值）或翻转切换开关（具有易于使用的“开”和“关”开关选项），以使在线填写表单更加功能齐全和有趣。

以下表单同时使用了翻转切换（**开**开关）和值滑块（0-100）：

![添加 jQuery 表单对象](img/4742_08_15.jpg)

## Dreamweaver 中的表单

Dreamweaver 在历史上提供了三种创建表单的方法。当然，您可以在代码视图中使用 HTML 定义表单和表单字段。您可以通过导航到**插入** | **表单**并定义一个表单来生成表单，然后在其中插入表单字段（例如文本字段）和必需的按钮（例如**提交**按钮以使表单执行某些操作）。

包括 Dreamweaver CS6 在内的较新版本的 Dreamweaver 已经添加了 Spry 验证表单字段，首先测试数据（例如，查看它是否看起来像一个电子邮件地址），然后允许访问者提交表单。我提到这段历史是因为 a）如果你不知道你曾经在哪里，你就无法到达目的地，或者无论那句话是什么；和 b）所有这些技术在移动设备上仍然有效，所以如果您了解其中任何一种或全部技术，您可以用这些工具补充 Dreamweaver 中的新 jQuery Mobile 表单工具。

然而，在这里，我们将专注于旨在创建移动设备友好表单的 jQuery Mobile 表单工具，并包括到目前为止在 Dreamweaver 中不易访问的表单字段，如滑块和切换开关。

在深入研究这些工具之前，这里是在 Dreamweaver 中创建表单的世界上最紧缩的课程（通常情况下，不仅仅是使用 jQuery Mobile 表单工具）：

1.  所有表单字段（如文本字段或**提交**按钮）都必须包含在一组`<form>`标签中。

1.  为了使其工作，表单必须有一个定义的操作。对于连接到服务器端脚本（使用 PHP 或 Perl 等编程语言编写的脚本，并驻留在服务器上）的表单，操作是将数据发布到服务器上该脚本的位置的链接。有许多免费的，相当直观的在线资源可用于生成此类脚本，并提供有关如何将它们上传到您的服务器并将它们连接到表单的说明。其中一个资源是[TheSiteWizard.com](http://TheSiteWizard.com)。一个非常简单但功能齐全的操作是简单地使用操作`mailto:xxx@xxx.xxx`将表单内容发送到电子邮件地址，其中`xxx@xxx.xxx`是电子邮件地址。然后，这个简单的解决方案启动一个电子邮件客户端（程序）并提示用户将表单内容发送到提供的电子邮件地址。

牢记这两条基本规则，让我们来看看 Dreamweaver 中用于创建特别适合移动设备的表单字段的工具。

## 创建 jQuery Mobile 表单

与本章中我们已经检查过的其他 jQuery Mobile 对象一样，jQuery Mobile 表单元素只能插入到已经生成的 jQuery Mobile 页面中。但除此之外，还需要使用 Dreamweaver 中更传统的表单功能来创建表单和**提交**按钮。因此，设置将包含 jQuery Mobile 表单元素的表单的过程如下：

1.  创建一个 jQuery Mobile 页面。

1.  在该 jQuery Mobile 页面中插入一个带有**提交**（按钮）的表单。

1.  然后，您可以向该表单添加特定的移动设备友好的 jQuery Mobile 表单字段。

这个三步过程并不是创建 jQuery Mobile 表单的唯一方法，也没有涵盖所有可能的选项。但这是一个基本的基础，使得实现 jQuery Mobile 表单元素成为可能。

让我们通过一个例子来工作，创建一个基本表单，当提交时，将通过电子邮件客户端将内容发送到一个电子邮件地址。当然，这些步骤假设您正在一个定义好的 Dreamweaver 网站中工作，并且已经创建了一个带有 jQuery 移动页面的 HTML5 页面。有了这些部分，以下步骤将更详细地阐述之前粗略概述的“三步流程”：

1.  在 jQuery 移动页面内（您可以在**代码**视图或**设计**视图中选择占位符“内容”文本，以确保您操作正确），导航到**插入** | **表单** | **表单**。**标签编辑器-表单**对话框出现。只有**常规**选项卡中的选项对于创建表单是必不可少的。

1.  在**动作**字段中，输入`mailto:[电子邮件地址]`，当然，使用真实的电子邮件地址。如果您正在使用与服务器端脚本链接的表单，您将在此处输入该脚本的 URL。

1.  从**方法**弹出窗口中选择**post**，这是几乎总是用来将表单数据发送到一个位置的方法。

1.  **编码类型**参数由管理数据的脚本定义。如果您通过电子邮件上传，输入`text/plain`。

1.  在**名称**框中输入表单名称。

1.  **目标**弹出窗口允许您选择`_blank`，如果您希望在新的浏览器窗口中打开链接的表单脚本（通常这是不必要的）。

1.  完成**标签编辑器-表单**对话框后，单击**确定**生成表单。

![创建 jQuery 移动表单](img/4742_08_16.jpg)

这一系列步骤只是定义了一个表单。目前表单中还没有表单字段，所以**实时**视图中没有任何表单字段。当然，您可以在**代码**视图中看到表单代码，并且在**设计**视图中关闭**实时**视图后，可以看到表单本身，用红色轮廓表示。

记住前面这一节的规则#1：为了被表单动作执行，*所有表单字段都必须在表单内*。因此，请确保您清楚您的表单在页面上的位置，即使它目前还没有内容。

将光标放在*表单内*，导航到**插入** | **表单** | **按钮**。我们还没有完全集成特殊的 jQuery 移动表单字段，所以通过导航到**插入** | **表单** 就可以使用这个选项。当**输入表单可访问属性**对话框出现时，您不需要在任何字段中输入任何内容，只需单击**确定**生成一个**提交**按钮。

现在我们有了一个表单的基本元素：具有定义动作的表单和一个**提交**按钮。接下来，是时候添加 jQuery 移动表单字段了。

![创建 jQuery 移动表单](img/4742_08_17.jpg)

## 特殊的移动表单字段

正如前面提到的，移动设备通常具有内置的界面工具，使表单内容更易访问。jQuery 移动也是如此。当您放置标准的 HTML 表单字段，如文本框、复选框和按钮时，jQuery 移动会替换为在移动设备上更易访问的自定义表单字段。复选框变大，选择菜单弹出大按钮的列表，表单字段标签和字段名称被调整大小以最大化屏幕空间利用率。

因此，jQuery 移动子菜单中提供的一些“特殊”表单字段只是标准 HTML 表单字段的适应。其他的是 HTML 表单字段集中的新内容。无论哪种情况，jQuery 移动表单字段都包括特殊的格式，使它们更适合移动设备。

让我们来看看其中三个表单字段的例子，根据这些例子，您将能够使用 jQuery 移动设置中的其他表单字段。在这些例子中，*确保您在*`<form>`*标签集内插入 jQuery 移动表单字段*。

### 插入文本输入字段

文本字段是在表单中收集数据的最灵活的方式。它们用于收集用户名、密码、电子邮件地址、送货地址等。

要在表单中插入 jQuery Mobile 文本输入字段，请导航至**插入** | **jQuery Mobile** | **文本输入**（如果要允许多行输入，请选择**文本区域**）。jQuery Mobile 文本输入字段会自动调整大小，但您必须用自己的文本替换标签占位符文本（**Text Input**）。您可以在设计视图（关闭实时视图）或分割视图中进行此操作。

您还可以通过编辑代码`name="textinput"`来更改文本字段的默认字段名称，以替换输入名称。但是避免使用空格和特殊字符（只使用字母和数字）。例如，要重命名名为`email`的文本输入字段，您需要将此代码更改为`name="email"`。

![插入文本输入字段](img/4742_08_18.jpg)

### 插入滑块

这些天每个人都在评价一切。也许你没有读过太多物理学，但你会如何在 1-100 的范围内评价玻色弦理论？好吧，也许……确实有*有效的理由在移动表单中包含评分选项。而且，如果你要在表单中包含“评价这个……（什么的）”，你应该让人们很容易地做到这一点。

输入*滑块*，这是在移动表单中输入值的一个特别方便的方式。

要在 jQuery Mobile 表单中插入滑块，请导航至**插入** | **jQuery Mobile** | **滑块**。自定义滑块如下：

1.  用你自己的文本替换**Slider**标签文本。

1.  用默认值替换`value="0"`代码。

1.  用你选择的任何值替换`min="0"`代码，这将是最小值。

1.  用你选择的任何值替换`max="0"`代码，这将是最大值。

![插入滑块](img/4742_08_19.jpg)

### 插入切换开关

切换开关为大手指提供了一个方便的方式来轻松选择“是”或“否”；“内”或“外”；或在移动设备上做出其他两个选择。

要在 jQuery Mobile 表单中插入一个切换开关，请导航至**插入** | **jQuery Mobile** | **翻转切换开关**。

自定义切换开关如下：

1.  用你自己的文本替换**Option**标签文本。

1.  用你自己的文本替换代码`<option value="off">Off</option>`中的`Off`（不带引号）。

1.  用你自己的文本替换代码`<option value="on">On</option>`中的`On`（不带引号）。

# 构建一个带有可折叠块和移动友好表单的页面

让我们通过一个具体的例子来总结、审查、充实，并提供一个在 Dreamweaver 中构建 jQuery Mobile 可折叠块的模型，并混入一个移动友好表单。

调查告诉我们，寻找某个地方吃塔可的人中有很大比例会在移动设备上在线搜索。因此，让我们以我在康尼岛上不存在的塔可摊作为这个配方的模型，你可以很容易地根据自己的需求进行调整。

我们构建的移动页面将有四个可折叠块：菜单、位置、下订单和关于塔可店的一些信息。在构建过程中，我们将演示创建四个可折叠块，并在其中一个块中嵌入一个表单。我们开始吧：

1.  当然，我们假设您正在 Dreamweaver 站点中工作。如果没有，请创建一个新站点或打开一个现有站点。然后导航至**文件** | **新建**，在**新建文档**对话框中，在**类别**列中选择**空白页**，在**页面类型**列中选择**HTML**，在**布局**列中选择**<none>**，并从**文档类型**弹出窗口中选择**HTML5**。然后点击**创建**。

1.  导航至**文件** | **保存**，并将文件保存为`index.html`。由于这将是一个单页面站点，当站点的 URL 在浏览器中被访问时，`index.html`文件名将打开页面。将页面标题设置为“移动塔可”。

1.  在此过程的这个阶段，默认情况下，您的光标位于一组 `<body>` 标签之间。这正是它应该在的地方。通过导航到 **插入** | **jQuery Mobile** | **页面** 来插入一个 jQuery Mobile 页面。由于我们将保持这个项目相对简单和标准（但不是*太*简单或标准 - 不用担心），您可以选择 **远程（CDN）** 链接类型选项，我们将使用 jQuery Mobile CSS 文件的在线版本。选择 **远程（CDN）**，然后单击 **确定**。

1.  **jQuery Mobile 页面** 对话框会打开。使用默认设置单击 **确定**。

1.  用 "Coney Island Tacos" 替换原始的 `Header` 占位文本。或者，您可以从一开始就偏离我的食谱，自由发挥您自己的内容。用 Coney Island Tacos 的虚构网站 - `www.coneyislandtacos.com` 替换页脚文本。如果您希望定义超链接，请导航到 **插入** | **超链接**。![使用可折叠块和移动友好表单构建页面](img/4742_08_NEW.jpg)

1.  定义工作环境：选择 **分割视图**，然后从 **设计** 视图底部的 **窗口大小** 弹出菜单中选择 **480x800**。打开 **实时视图**。

1.  开始应用一个 jQuery Mobile 主题进行格式化。在 **分割** 视图的代码侧面，输入代码 `data-theme="e"` 或尝试其他主题（尝试 `a`、`b`、`c`、`d` 或 `e`）。![使用可折叠块和移动友好表单构建页面](img/4742_08_21.jpg)

现在让我们一起来添加四个可折叠面板到我们的网站上：

1.  选择占位符 `content` 文本，然后导航到 **插入** | **jQuery Mobile** | **可折叠块**。复制并粘贴一组可折叠块代码以创建第四个块。这段代码是：

```js
  <div data-role="collapsible" data-collapsed="true">
      <h3>Header</h3>
    <p>Content</p>
  </div>
```

1.  自定义四个块的标题。您会发现标题被包含在 `<h3>` 代码中。我选择：**菜单**，**电子邮件订单**，**寻找/联系我们** 和 **关于 Coney Island Tacos** 作为标题，但请随意发挥创意。

1.  自定义所有可折叠块的内容*除了* **Email Order** 块 - 我们将为下一个创建一个表单。

1.  在 **Email Order** 块（或您在自定义项目中用于输入表单的任何块）中，选择占位符 `content` 文本，导航到 **插入** | **表单** | **表单**。在 **标签编辑器 - 表单** 对话框中，将操作设置为 `mailto:youremail@youremail.xxx`（替换为您自己的电子邮件地址）。将方法更改为 **POST**。在 **编码类型** 字段中输入 `text/plain`，然后单击 **确定**。在这里，弹出实时视图可能会有所帮助，以创建输入表单。在表单内输入 `Order Form`，然后按 *Return* 或 *Enter* 创建新行。![使用可折叠块和移动友好表单构建页面](img/4742_08_22.jpg)

1.  确保插入点在表单内，导航到 **插入** | **jQuery Mobile** | **选择菜单**。将标签更改为 **Taco**。单击 **选择** 菜单本身，并使用 **属性** 检查器中的 **列表值** 按钮打开 **列表值** 对话框。使用 **+** 按钮添加新行，并使用上下箭头根据需要重新排序项目。![使用可折叠块和移动友好表单构建页面](img/4742_08_23.jpg)

1.  添加额外的选择菜单，以允许人们选择玉米饼。

1.  在表单内，导航到 **插入** | **jQuery Mobile** | **复选框**。在 **jQuery Mobile 复选框** 对话框中，在 **名称** 框中输入 `Sides`，然后选择四个复选框和水平布局，最后单击 **确定**。在 **设计** 视图中的 **文档** 窗口中直接编辑标签，并使用 **属性** 检查器为每个复选框定义与标签匹配的值。![使用可折叠块和移动友好表单构建页面](img/4742_08_24.jpg)

1.  通过插入**提交**按钮完成表单。再次确保插入点位于表单内部，并导航到**插入** | **表单** | **按钮**。单击**确定**，而不进行任何选择，因为**提交**按钮是默认选项。

1.  要自定义页面的外观，创建一个新的类样式。使用**CSS 样式**面板底部的**新 CSS 规则**选项创建新的 CSS 规则。将类样式命名为`Format`。由于我们使用的是相关 CSS 文件的远程版本，并且这是一个单页面站点，我们可以打破仅依赖链接的外部样式表的规则，因此从**新 CSS 规则**对话框底部的弹出菜单中选择**(仅限本文档)**，然后单击**确定**。

1.  定义一些自定义属性，例如字体系列，字体大小和字体颜色。使用**属性**检查器，如下截图所示，将类样式应用于页面上选择的元素：![使用可折叠块和移动友好表单构建页面](img/4742_08_25.jpg)

1.  您可以通过创建其他类样式并应用它们来进一步自定义项目。

1.  您可以在浏览器中测试订单表格。![使用可折叠块和移动友好表单构建页面](img/4742_08_26.jpg)

# 摘要

jQuery Mobile 中的一个页面设计技术是布局网格。布局网格与块一起，基本上是`div`样式的列，但具有使列在移动设备上有效显示的特殊属性。

我们在本章介绍的两个最重要的 jQuery Mobile 技术是可折叠块和 jQuery Mobile 表单对象。可折叠块可以展开和折叠，并提供了一种在小视口中呈现内容的非常舒适的方式。添加 jQuery 表单对象可以创建更多移动友好版本的熟悉输入表单对象（例如文本框），还可以启用新的表单字段，如滑块和切换翻转开关。

要自定义 jQuery Mobile 页面的外观和感觉，我们可以利用数据主题的广泛格式，辅以自定义 CSS。但要真正发挥主题的力量，我们需要创建自己的自定义主题颜色样本。我们将在下一章中进行。