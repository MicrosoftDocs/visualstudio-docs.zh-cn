---
title: 创建自定义数据可视化工具 |Microsoft Docs
ms.custom: ''
ms.date: 11/07/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.visualizer.troubleshoot
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugger, visualizers
- visualizers
ms.assetid: c24c006f-f2ac-429f-89db-677fc0c6e1ea
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4c5f505bfa8032b0f7d59f348835e1e4969b2648
ms.sourcegitcommit: 6a955a2d179cd0e137942389f940d9fcbbe125de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/13/2018
ms.locfileid: "51607817"
---
# <a name="create-custom-data-visualizers"></a>创建自定义数据可视化工具 
 一个*可视化工具* 在[!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]调试器用户界面中，以适当的方式显示数据类型的变量或对象。 例如，HTML 可视化工具如浏览器窗口中一样显示，解释 HTML 字符串，并显示结果。位图可视化工具解释位图结构并显示它所代表的图形。 某些可视化工具可如查看数据一样，修改数据。

 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] 调试器包括六个标准可视化工具。 文本、 HTML、 XML 和 JSON 可视化工具处理字符串对象。 WPF 树可视化工具显示 WPF 对象可视化树的属性。 数据集可视化工具用于 DataSet、 DataView 和 DataTable 对象。 

可从 Microsoft、 第三方和社区下载更多可视化工具。 此外可以编写自己的可视化工具，并将它们安装在[!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]调试器。

在调试器中，可视化工具由一个放大镜图标表示![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "可视化工具图标")。 可以在**数据提示**中，调试器**监视**窗口中，或**快速监视**对话框中选择图标，并选择相应的对象的相应可视化工具。

## <a name="write-custom-visualizers"></a>编写自定义可视化工具

 > [!NOTE]
 > 若要创建的本机代码的自定义可视化工具，请参阅[SQLite 本机调试器可视化工具](https://github.com/Microsoft/VSSDK-Extensibility-Samples/tree/master/SqliteVisualizer)示例。 对于 UWP 和 Windows 8.x 应用程序不支持自定义可视化工具。

您可以编写除<xref:System.Object>和<xref:System.Array>之外，任何托管类对象的自定义可视化工具。  
  
调试器可视化工具的结构由两部分组成：  
  
- 在 Visual Studio 调试器中运行 *调试器端* ，并创建并显示可视化工具用户界面。  
  
- *调试对象端* 在 Visual Studio 正在调试的进程中运行 (*调试对象*)。 调试对象进程中存在要实现可视化效果 （例如，字符串对象） 的数据对象。 调试对象端将对象发送到调试器端，在您创建的用户界面中显示。  

在调试器端从 *对象提供程序* 实现<xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider>接口中接收的数据对象。 调试对象端将通过 *对象源* 发送对象，它派生自<xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource>。 

对象提供程序还可以发送数据返回到对象源，使你可以编写可视化工具，可以编辑数据。 重写对象提供程序，使表达式计算器和对象源通信。  
  
调试对象端和调试器端通过与其他通信<xref:System.IO.Stream>方法，将数据序列化对象插入<xref:System.IO.Stream>和反序列化<xref:System.IO.Stream>返回数据对象。  

如果类型为开放类型，可以为泛型类型编写可视化工具。 此限制与使用 `DebuggerTypeProxy` 特性时的限制相同。 有关详细信息，请参阅[使用 DebuggerTypeProxy 特性](../debugger/using-debuggertypeproxy-attribute.md)。  
  
自定义可视化工具可能有安全性问题。 请参阅[可视化工具安全注意事项](../debugger/visualizer-security-considerations.md)。  
  
以下步骤创建了可视化工具高级概述。 有关详细说明，请参阅[演练： 编写可视化工具C#](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)或[演练： 用 Visual Basic 编写可视化工具](../debugger/walkthrough-writing-a-visualizer-in-visual-basic.md)。  
  
### <a name="to-create-the-debugger-side"></a>创建调试器端  
  
若要在调试器端创建可视化工具用户界面，您可以创建继承的类<xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>，并替代<xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer.Show%2A?displayProperty=fullName>方法来显示的界面。 可以使用<xref:Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService>要在可视化工具中显示 Windows 窗体、 对话框和控件。  
  
1.  使用 <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider> 方法在调试器端获取可视化的对象。  
  
1.  创建一个从 <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer> 继承的类。  
  
1.  重写 <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer.Show%2A?displayProperty=fullName> 方法以显示接口。 使用<xref:Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService>方法，以便在界面中显示 Windows 窗体、 对话框和控件。  
  
4.  将应用<xref:System.Diagnostics.DebuggerVisualizerAttribute>，为其提供要显示的可视化工具 (<xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>)。  
  
### <a name="to-create-the-debuggee-side"></a>创建调试对象端  
  
使用指定调试对象端代码<xref:System.Diagnostics.DebuggerVisualizerAttribute>。  
  
1.  应用 <xref:System.Diagnostics.DebuggerVisualizerAttribute>，为它指定可视化工具 (<xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>) 和对象源 (<xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource>)。 如果省略对象源，可视化工具将使用默认对象源。  
  
1.  若要允许编辑，也显示的数据对象的可视化工具，请重写`TransferData`或`CreateReplacementObject`方法从<xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource>。   
  
## <a name="see-also"></a>请参阅
  
 [演练：用 C# 编写可视化工具](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)  

 [演练：用 Visual Basic 编写可视化工具](../debugger/walkthrough-writing-a-visualizer-in-visual-basic.md)  
  
 [如何：安装可视化工具](../debugger/how-to-install-a-visualizer.md)  
  
 [如何：测试和调试可视化工具](../debugger/how-to-test-and-debug-a-visualizer.md)  
  
 [可视化工具 API 参考](../debugger/visualizer-api-reference.md)  
  
 [在调试器中查看数据](../debugger/viewing-data-in-the-debugger.md)