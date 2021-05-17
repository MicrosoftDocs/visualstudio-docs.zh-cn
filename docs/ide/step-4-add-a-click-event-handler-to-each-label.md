---
title: 步骤 4：向每个标签添加一个 Click 事件处理程序
description: 了解如何将 click 事件处理程序添加到每个标签。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- vb
ms.assetid: 16bdbc7c-4129-411d-bace-f4a3e5375975
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ffaa3986ee5ef23f007d6e66a30b75eb8b06bff4
ms.sourcegitcommit: 6d88913a8b5a9e5eda01d3f95205b4d138f440f8
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/13/2021
ms.locfileid: "107296256"
---
# <a name="step-4-add-a-click-event-handler-to-each-label"></a>步骤 4：向每个标签添加一个 Click 事件处理程序

匹配游戏的运行原理如下所示：

1. 当玩家选择一个带有隐藏图标的方块时，程序会通过将图标颜色更改为黑色来向玩家显示该图标。

2. 然后玩家选择另一个隐藏的图标。

3. 如果图标互相匹配，则它们保持可见。 如果不匹配，则两个图标都会再次隐藏。

   为了使程序按此方式运行，需要添加一个 <xref:System.Windows.Forms.Control.Click> 事件处理程序以更改所选择的标签的颜色。

## <a name="to-add-a-click-event-handler-to-each-label"></a>向每个标签添加一个 click 事件处理程序

1. 在“Windows 窗体设计器”中打开窗体。 在“解决方案资源管理器”中，选择“Form1.cs”或“Form1.vb”。 在菜单栏上，依次选择“视图” > “设计器”。

2. 选择第一个标签控件以选中它。 然后，按住 Ctrl 键选择其他每个标签，将它们选中。 确保选中每个标签。

3. 选择“属性”窗口工具栏上的“事件”按钮，在“属性”窗口中查看“事件”页面。 向下滚动到“Click”事件，在框中输入“label_Click”，如以下屏幕截图所示。

     ![显示 Click 事件的“属性”窗口](../ide/media/express_labelclick.png)

4. 选择 **Enter** 键。 IDE 将称为 `label_Click()` 的 `Click` 事件处理程序添加到代码中，并将其挂钩到窗体上的每个标签。

5. 填写其余代码，如下所示：

    :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/cs/form1.cs" id="Snippet4":::
    :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/vb/form1.vb" id="Snippet4":::

    > [!IMPORTANT]
    > 使用此页右上角的编程语言控件查看 C# 代码片段或 Visual Basic 代码片段。<br><br>![Docs.Microsoft.com 的编程语言控件](../ide/media/docs-programming-language-control.png)

    > [!NOTE]
    > 如果你复制和粘贴 `label_Click()` 代码块，而不是手动输入代码，请确保替换现有的 `label_Click()` 代码。 否则，你将得到重复的代码块。

    > [!NOTE]
    > 可能发现事件处理程序顶部的 `object sender` 与[教程 2：创建计时数学测验](../ide/tutorial-2-create-a-timed-math-quiz.md)教程中使用的相同。 这是因为你将不同的 Label 控件 click 事件与一个事件处理程序方法挂钩，因此无论用户选择哪个标签，都调用同一方法。 该事件处理程序方法需要知道选定的标签，以便使用名称 `sender` 标识 Label 控件。 该方法的第一行通知程序：它并不是一般对象，而是专门的 Label 控件，并使用名称 `clickedLabel` 访问标签的属性和方法。

     该方法首先检查是否已将 `clickedLabel` 成功从对象转换（强制转换）为 Label 控件。 如果不成功，其值为 `null` (C#) 或 `Nothing` (Visual Basic)，你不需要执行该方法中的其余代码。 接下来，该方法使用标签的“ForeColor”属性检查所选标签的文本颜色。 如果标签的文本颜色为黑色，则表示已选择该图标并且该方法执行完毕。 （这就是 `return` 语句的作用：它通知程序停止执行该方法。）否则，表示图标尚未被选择，因此程序将标签的文本颜色更改为黑色。

6. 在菜单栏上，依次选择“文件” > “全部保存”保存进度，然后在菜单栏上选择“调试” > “开始调试”运行程序。 您应该看到一个背景为蓝色的空窗体。 在窗体中选择任意单元格，其中一个图标应变为可见。 继续在窗体中选择不同位置。 当选择图标时，它们应显示。

## <a name="to-continue-or-review"></a>继续或查看

- 要转到下一个教程步骤，请参阅[步骤 5：添加标签引用](../ide/step-5-add-label-references.md)。

- 要返回上一个教程步骤，请参阅[步骤 3：向每个标签分配一个随机图标](../ide/step-3-assign-a-random-icon-to-each-label.md)。
