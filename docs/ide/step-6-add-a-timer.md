---
title: 步骤 6：添加计时器
description: 了解如何向匹配游戏添加 <xref:System.Windows.Forms.Timer> 控件。
ms.custom: SEO-VS-2020
ms.date: 03/31/2020
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: 09e7930b-cab6-4a22-9a6f-72e23f489585
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2b983108793b07e1752b88afed90346cd5ff017f
ms.sourcegitcommit: 6d88913a8b5a9e5eda01d3f95205b4d138f440f8
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/13/2021
ms.locfileid: "107297101"
---
# <a name="step-6-add-a-timer"></a>步骤 6：添加计时器
接下来，要向匹配游戏中添加 <xref:System.Windows.Forms.Timer> 控件。 计时器等待指定的毫秒数后，触发一个称为“Tick”  的事件。 这对于启动操作或定时重复操作很有用。 在本例中，你将使用一个计时器，让玩家开始选择两个图标，而如果图标不匹配，则在短暂时间后再次隐藏这两个图标。

## <a name="to-add-a-timer"></a>添加计时器

1. 在“Windows 窗体设计器”  的“工具箱”中，选择“Timer”  （位于“组件”  类别中），然后按 Enter  键，或双击该计时器，向窗体中添加一个计时器控件。 该计时器的图标名为 Timer1  ，应显示在窗体下的空间中，如下图所示。

     ![计时器](../ide/media/express_timer.png)<br/>
***计时器***

    > [!NOTE]
    > 如果工具箱是空的，请确保在打开工具箱前选择窗体设计器，而不是窗体的后台代码。

2. 选择 **Timer1** 图标以选中该计时器。 在“属性”  窗口中，从查看事件切换到查看属性。 然后将计时器的 **Interval** 属性设置为 **750**，但保留 **Enabled** 属性的设置“False”  。 “Interval”  属性将通知计时器两个始终周期  之间的等待时长，或何时触发 <xref:System.Windows.Forms.Timer.Tick> 事件。 值为 750 时，将通知计时器等待四分之三秒（750 毫秒）后触发 Tick 事件。 只有在玩家选择第二个标签后，你才能调用 <xref:System.Windows.Forms.Timer.Start> 方法启动计时器。

3. 选择“Windows 窗体设计器”  中的计时器控件图标，然后按 Enter  键或双击该计时器，以添加空的“Tick”事件处理程序。 用下列代码替换该代码，或手动将下列代码输入到事件处理程序。

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step6/cs/form1.cs" id="Snippet7":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step6/vb/form1.vb" id="Snippet7":::

      > [!IMPORTANT]
      > 使用此页右上角的编程语言控件查看 C# 代码片段或 Visual Basic 代码片段。<br><br>![Docs.Microsoft.com 的编程语言控件](../ide/media/docs-programming-language-control.png)

     Tick 事件处理程序将执行三项操作：首先，通过调用 <xref:System.Windows.Forms.Timer.Stop> 方法确保计时器没有运行。 然后，它使用两个引用变量 `firstClicked` 和 `secondClicked`，使得玩家选择的两个标签的图标再次不可见。 最后，它将 `firstClicked` 和 `secondClicked` 引用变量重置为 `null`（C# 中）或 `Nothing`（Visual Basic 中）。 这一步很重要，因为程序本身就是这样重置的。 现在，它不跟踪任何 <xref:System.Windows.Forms.Label> 控件，并已准备好让玩家再次选择标签。

    > [!NOTE]
    > Timer 对象具有 `Start()` 方法和 `Stop()` 方法，分别用以启动和停止计时器。 如果你在“属性”  窗口中将计时器的“Enabled”  属性设置为“True”  ，则只要程序开始运行，计时器就会开始计时。 但是，如果将该属性保留设置为“False”  ，则在调用计时器的 `Start()` 方法之前，计时器不会开始计时。 通常，计时器会使用 **Interval** 属性确定在计时周期之间等待的毫秒数，从而反复触发其 Tick 事件。 您可能已经注意到在 Tick 事件中调用计时器的 `Stop()` 方法的方式。 这会将计时器置于“单触发模式”  ，意味着调用 `Start()` 方法时，计时器会等待指定的间隔时间，触发单个 Tick 事件，然后停止。

4. 若要查看正在使用的新计时器，请转至代码编辑器，将以下代码添加到 `label_Click()` 事件处理程序方法的顶部和底部。 （将两个 `if` 语句添加到顶部，将三个语句添加到底部；该方法的其余部分保持相同。）

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step6/cs/form1.cs" id="Snippet8":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step6/vb/form1.vb" id="Snippet8":::

     该方法顶部的代码通过检查 **Enabled** 属性的值来检查计时器是否已启动。 这样，如果玩家选择第一个和第二个 Label 控件，且计时器启动，则选择第三个控件将不会执行任何操作。 此外，它还可以防止玩家在游戏准备再次第一次单击之前进行第三次快速单击。 

     该方法底部的代码将 `secondClicked` 引用变量设置为跟踪玩家选择的第二个 Label 控件，然后将该标签的图标颜色设置为黑色以使其可见。 然后，它在单触发模式下启动计时器，以便在等待 750 毫秒后触发单个 Tick 事件。 计时器的 Tick 事件处理程序会隐藏这两个图标，并重置 `firstClicked` 和 `secondClicked` 引用变量，以便窗体准备就绪供玩家选择另一对图标。

5. 保存并运行程序。 选择一个图标，它将显示出来。

6. 选择另一个图标。 它会短暂显示，然后两个图标都消失。 多次重复此操作。 窗体现在跟踪你选择的第一个和第二个图标，并使用计时器在使图标消失之前暂停。

## <a name="to-continue-or-review"></a>继续或查看

- 要转到下一个教程步骤，请参阅[步骤 7：保持对可见](../ide/step-7-keep-pairs-visible.md)。

- 要返回上一个教程步骤，请参阅[步骤 5：添加标签引用](../ide/step-5-add-label-references.md)。
