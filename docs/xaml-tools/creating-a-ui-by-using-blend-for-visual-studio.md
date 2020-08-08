---
title: Blend for Visual Studio 功能导览
titleSuffix: ''
ms.date: 07/31/2019
ms.topic: overview
f1_keywords:
- Blend.Start.Dev12
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8348ba38849b76a745a56f941850d6b61a8f433f
ms.sourcegitcommit: 57d96de120e0574e506dfd80bb7adfbac73f96be
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/24/2020
ms.locfileid: "85332090"
---
# <a name="blend-for-visual-studio-overview"></a>Blend for Visual Studio 概述

Blend for Visual Studio 可用于设计基于 XAML 的 Windows 和 Web 应用程序。 它提供了与 Visual studio 相同的基本 XAML 设计体验，并添加了可视化设计器，以用于高级任务，例如动画和行为。 有关 Blend 和 Visual Studio 之间的比较，请参阅[在 Visual Studio 和 Blend for Visual Studio 中设计 XAML](../xaml-tools/designing-xaml-in-visual-studio.md)。

Blend for Visual Studio 是 Visual Studio 的一个组件。 若要安装 Blend，请在 **Visual Studio 安装程序** 中，选择**通用 Windows 平台开发** 或 **.NET 桌面开发**工作负载。 这两种工作负载均包括 Blend for Visual Studio 组件。

![UWP 工作负载组件](media/installer-uwp.png)&nbsp;&nbsp;&nbsp;&nbsp;![.NET 桌面开发工作负载组件](media/installer-dotnet-desktop.png)

如果是初次接触 Blend for Visual Studio，则要花一些时间来熟悉工作区的特有功能。 本主题将作用快速教程。

## <a name="tools-panel"></a>“工具”面板

可在应用程序中通过 Blend for Visual Studio 的“**工具**”面板创建和修改对象。 打开 .xaml 文件时，“**工具**”面板显示在 XAML 设计器的左侧。

可以通过使用鼠标选择工具并在美工板上进行绘制来创建对象。

![Blend for Visual Studio 中的“工具”面板](media/blend-tools-panel.png)

> [!TIP]
> “**工具**”面板中的某些工具具有变体，例如，可以选择椭圆形或直线，而不是矩形。 要访问这些变体，请右键单击或单击并按住该工具。
>
> ![Blend for Visual Studio 中的形状工具变体](media/blend-rectangle-tool-variations.png)

### <a name="selection-tools"></a>选择工具

选择对象和路径。 使用“**直接选择**”工具可选择嵌套对象和路径段。

### <a name="view-tools"></a>视图工具

调整美工板的视图，例如平移和缩放。

### <a name="brush-tools"></a>画笔工具

使用对象的视觉特性，例如转换画笔或应用渐变。

### <a name="object-tools"></a>对象工具

在美工板上绘制最常用的对象，例如路径、形状、布局面板、文本和控件。

### <a name="asset-tools"></a>资产工具

访问“资产”窗口并显示库中最近用过的资产。

## <a name="assets-window"></a>“资产”窗口

“**资产**”窗口包含所有可用控件，类似于 Visual Studio 中的“**工具箱**”。 除控件外，“**资产**”窗口还包括所有可添加到美工板的内容，例如样式、媒体、行为和效果等。 要打开“**资产**”窗口，请选择“**视图**” > “**资产窗口**” 或按  **Ctrl+Alt+X**。

![Blend for Visual Studio 中的“资产”窗口](media/blend-assets-window.png)

- 在“**搜索资产**”框中输入文本来筛选资产列表。
- 使用右上角的按钮在资产视图的网格模式和列表模式之间切换。

## <a name="objects-and-timeline-window"></a>“对象和时间线”窗口

使用此窗口可在美工板上组织对象以及（如果需要）对它们进行动画处理。 若要打开“**对象和时间线**”窗口，请选择“**查看**” > “**文档大纲**”。 除了 Visual Studio 中的[“文档大纲”窗口](creating-a-ui-by-using-xaml-designer-in-visual-studio.md#document-outline-window)提供的功能外，Blend for Visual Studio 中的“对象和时间线”窗口的右侧具有时间线组合区域。 创建和编辑动画时使用时间线。

![动画模式下的“对象和时间线”窗口](media/storyboard-timeline.png)

使用与情节提要相关的按钮 ![Blend for Visual Studio 中的情节提要按钮](media/storyboard-buttons.png) 用于创建、删除、关闭或选择情节提要。 使用右侧的时间线组合区域可查看时间线并移动关键帧。

将鼠标悬停在窗口中的每个按钮上，以了解有关可用功能的详细信息。

## <a name="see-also"></a>另请参阅

- [动态显示对象](../xaml-tools/animate-objects-in-xaml-designer.md)
- [绘制形状和路径](../xaml-tools/draw-shapes-and-paths.md)
- [在 Visual Studio 和 Blend for Visual Studio 中设计 XAML](../xaml-tools/designing-xaml-in-visual-studio.md)
