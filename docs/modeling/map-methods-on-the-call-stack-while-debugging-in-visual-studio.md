---
title: 调试时映射调用堆栈上的方法
description: 了解如何创建代码图，以便在调试时直观地跟踪调用堆栈。 此外，还可以了解如何在地图上进行注释以跟踪代码执行的操作。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.progression.debugwithcodemaps
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- call stacks, code maps
- Call Stack window, mapping calls
- debugging [Visual Studio], diagramming the call stack
- call stacks, mapping
- Call Stack window, visualizing
- debugging code visually
- debugging [Visual Studio], mapping the call stack
- call stacks, visualizing
- debugging, code maps
- Call Stack window, tracing calls visually
- Call Stack window, show on code map
- debugging [Visual Studio], tracing the call stack visually
- debugging [Visual Studio], visualizing the call stack
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 7196cf06e7d6bcde33bc1e4a6c5d0ebfac486576
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2021
ms.locfileid: "99946483"
---
# <a name="map-methods-on-the-call-stack-while-debugging-in-visual-studio"></a>在 Visual Studio 中调试时映射调用堆栈上的方法

创建代码映射，以便在调试时对调用堆栈进行可视化跟踪。 你可以在图中进行标注以跟踪代码执行的操作，以便专注于查找 Bug。

 ![使用代码图上的调用堆栈调试](../debugger/media/debuggermap_overview.png)

 需要：

 ::: moniker range="vs-2017"

- [Visual Studio Enterprise](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)

::: moniker-end

::: moniker range="vs-2019"

- [Visual Studio Enterprise](https://visualstudio.microsoft.com/downloads)

::: moniker-end

- 可调试的代码，例如 Visual c #、Visual Basic、c + +、JavaScript 或 X + +

  请参阅：

- [视频：利用代码图调试器集成进行可视化调试 (第9频道) ](https://channel9.msdn.com/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012Debug-visually-with-Code-Map-debugger-integration)

- [映射调用堆栈](#MapStack)

- [创建有关代码的注释](#MakeNotes)

- [用下一个调用堆栈更新映射](#UpdateMap)

- [向映射中添加相关代码](#AddRelatedCode)

- [使用地图查找 bug](#FindBugs)

- [问答](#QA)

  有关使用代码图时可以使用的命令和操作的详细信息，请参阅 [浏览和重新排列代码图](../modeling/browse-and-rearrange-code-maps.md)。

## <a name="map-the-call-stack"></a><a name="MapStack"></a>映射调用堆栈

1. 开始调试。  (键盘： **F5**) 

2. 在应用进入中断模式或单步执行函数后，选择 " **代码图**"。  (键盘： **Ctrl**  +  **Shift**  +  **`**) 

     ![选择代码图以开始映射调用堆栈](../debugger/media/debuggermap_choosecodemap.png)

     当前的调用堆栈在新代码图上显示为橙色：

     ![查看代码图上的调用堆栈](../debugger/media/debuggermap_seeundocallstack.png)

     在你继续调试时，该代码图将自动更新。 请参见 [用下一个调用堆栈更新映射](#UpdateMap)。

## <a name="make-notes-about-the-code"></a><a name="MakeNotes"></a>对代码进行标注

 添加注释以跟踪代码发生的情况。 若要在注释中添加新行，请按 **Shift + Return**。

 ![向代码图上的调用堆栈添加注释](../debugger/media/debuggermap_addcomment.png)

## <a name="update-the-map-with-the-next-call-stack"></a><a name="UpdateMap"></a>使用下一个调用堆栈更新映射

 运行你的应用到下一个断点或单步执行某一函数。 此图将添加新的调用堆栈。

 ![使用下一个调用堆栈更新代码图](../debugger/media/debuggermap_addclearcallstack.png)

## <a name="add-related-code-to-the-map"></a><a name="AddRelatedCode"></a>向映射添加相关代码

 现在已经有了一个映射，接下来要做什么？ 如果使用的是 c # 或 Visual Basic，请添加项（如字段、属性和其他方法），以跟踪代码中发生的情况。

 双击某个方法以查看其代码定义，或者使用该方法的快捷菜单。  (键盘：在地图上选择方法，然后按 **F12**) 

 ![转到代码图上某方法的代码定义](../debugger/media/debuggermap_gotocodedefinition.png)

 添加要在图上跟踪的项。

 ![显示调用堆栈代码图上某方法中的字段](../debugger/media/debuggermap_showfields.png)

> [!NOTE]
> 默认情况下，向图添加项还会添加父组节点（如类、命名空间和程序集）。 虽然这很有用，但你可以通过在 "地图" 工具栏上使用 " **包括父级** " 按钮关闭此功能，或者在添加项时按 **CTRL** 来使映射简单。

 ![调用堆栈代码图上与某方法相关的字段](../debugger/media/debuggermap_showedfields.png)

 在这里，你可以轻松查看哪些方法使用了相同的字段。 最近添加的项显示为绿色。

 继续生成图以查看更多代码。

 ![查看使用字段的方法：调用堆栈代码图](../debugger/media/debuggermap_findallreferences.png)

 ![调用堆栈代码图上使用某字段的方法](../debugger/media/debuggermap_foundallreferences.png)

## <a name="find-bugs-using-the-map"></a><a name="FindBugs"></a>使用映射查找 Bug

 通过代码可视化，可帮助你更快发现 Bug。 例如，假设您正在调查绘图程序中的 bug。 当你绘制一条线并尝试撤消该操作时，直到你绘制另一条线后才会发生变化。

 因此，可在 `clear`、`undo` 和 `Repaint` 方法中设置断点，启动调试，然后生成如下所示的图：

 ![向代码图添加另一个调用堆栈](../debugger/media/debuggermap_addpaintobjectcallstack.png)

 你注意到图中所有用户笔势均调用 `Repaint`，但 `undo` 除外。 这可能解释了 `undo` 不立即发挥作用的原因。

 在修复此 Bug 并继续运行程序后，图中增加了从 `undo` 到 `Repaint` 的新调用：

 ![向代码图上的调用堆栈添加新方法调用](../debugger/media/debuggermap_addnewcallforrepaint.png)

## <a name="q--a"></a><a name="QA"></a> 问题解答

- **不是所有的调用都出现在地图上。为什么?**

   默认情况下，只有你自己的代码会显示在图中。 若要查看外部代码，请在 " **调用堆栈** " 窗口中将其打开：

   ![使用“调用堆栈”窗口显示外部代码](../debugger/media/debuggermap_callstackmenu.png)

   或在 Visual Studio 调试选项中关闭 " **启用仅我的代码** ：

   ![使用“选项”对话框显示外部代码](../debugger/media/debuggermap_debugoptions.png)

- **更改图是否会影响代码？**

   更改地图并不会对代码造成任何影响。 你可随意在图上重命名、移动或移除任何内容。

- **此消息的意思是： "关系图可能基于较旧版本的代码"？**

   在你上次更新图后，代码可能已发生更改。 例如，图中的某个调用可能已在代码中不存在了。 请关闭此消息，然后在再次更新图之前，尝试重新生成解决方案。

- **如何实现控制地图的布局？**

   打开地图工具栏上的 " **布局** " 菜单：

  - 更改默认布局。

  - 若要停止自动重新排列映射，请关闭 " **调试时自动布局**"。

  - 若要在添加项时尽可能少地重新排列映射，请关闭 " **增量布局**"。

- **我能否与他人共享此图？**

   如果你有 Microsoft Outlook，则可以导出该映射，将其发送给其他人，或将其保存到你的解决方案中，以便可以将其签入源代码管理。

   ![与他人共享调用堆栈代码图](../debugger/media/debuggermap_sharewithothers.png)

- **我如何停止此图自动添加新的调用堆栈？**

   选择 ![ 按钮 &#45; 在地图工具栏上自动显示代码图上的调用堆栈 ](../debugger/media/debuggermap_automaticupdateicon.gif) 。 若要手动向图中添加当前的调用堆栈，请按 Ctrl + Shift + `  。

   调试时，映射将继续突出显示地图上的现有调用堆栈。

- **项图标和箭头代表什么？**

   若要获取有关项的详细信息，请将鼠标指针移到该项上，并查看项的工具提示。 还可以查看 **图例** 来了解每个图标的含义。

   ![调用堆栈代码图上各图标的含义](../debugger/media/debuggermap_showlegend.png)

  请参阅：

- [映射调用堆栈](#MapStack)

- [创建有关代码的注释](#MakeNotes)

- [用下一个调用堆栈更新映射](#UpdateMap)

- [向映射中添加相关代码](#AddRelatedCode)

- [使用地图查找 bug](#FindBugs)

## <a name="see-also"></a>请参阅

- [映射解决方案中的依赖项](../modeling/map-dependencies-across-your-solutions.md)
- [使用代码图调试应用程序](../modeling/use-code-maps-to-debug-your-applications.md)
- [使用代码图分析查找潜在问题](../modeling/find-potential-problems-using-code-map-analyzers.md)
- [浏览和重新排列代码图](../modeling/browse-and-rearrange-code-maps.md)
