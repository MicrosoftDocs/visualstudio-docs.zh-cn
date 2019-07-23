---
title: 衡量应用中的 CPU 使用情况
description: 使用集成了调试器的诊断工具，分析应用程序中的 CPU 性能问题。
ms.custom: seodec18
ms.date: 04/03/2019
ms.topic: tutorial
f1_keywords:
- vs.performance.wizard.intropage
helpviewer_keywords:
- Profiling Tools, quick start
- Diagnostics Tools, CPU Usage
- CPU Usage
- Diagnostics Tools
ms.assetid: da2fbf8a-2d41-4654-a509-dd238532d25a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a79bcf2aade3a84e0453aec1d64e37c8a6a5c24c
ms.sourcegitcommit: 91c7f1b525e0c22d938bc4080ba4ceac2483474f
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/12/2019
ms.locfileid: "67033040"
---
# <a name="measure-application-performance-by-analyzing-cpu-usage"></a>通过分析 CPU 使用情况衡量应用程序性能 <!--test-->
可使用 Visual Studio 分析工具来分析应用程序中的性能问题。 此过程演示如何使用诊断工具的“CPU 使用率”  选项卡获取应用的性能数据。 Visual Studio 中的 .NET 开发（包括 ASP.NET、和本机 /C++ 开发）支持此诊断工具。

调试中断时，**CPU 使用率**工具收集有关应用程序中正在执行的函数的信息。 该工具将列出执行工作的函数，并提供时间线图，可专用于采样会话的特定部分。

诊断中心提供了大量其他选项来运行和管理诊断会话。 如果**CPU 使用率**未提供所需数据，[其他分析工具](../profiling/profiling-feature-tour.md)可提供可能有帮助的不同种类的信息。 在许多情况下，CPU 以外的因素可能会导致应用程序性能瓶颈，例如内存、呈现 UI 或网络请求时间。 诊断中心提供大量其他选项，可用于记录和分析此种数据。

本文讨论在常规调试工作流中分析 CPU 使用情况。 还可以在不附加调试程序的情况下，或通过定目标到正在运行的应用来分析 CPU 使用率。有关详细信息，请参阅[在使用或不使用调试程序的情况下运行分析工具](../profiling/running-profiling-tools-with-or-without-the-debugger.md)中的[在不使用调试程序的情况下收集分析数据](../profiling/running-profiling-tools-with-or-without-the-debugger.md#collect-profiling-data-without-debugging)。

可 Windows 7 及更高版本中使用不带调试器的分析工具。 要运行带调试器的分析工具（“诊断工具”窗口），需具备 Windows 8 及更高版本  。

在本教程中，你将：

> [!div class="checklist"]
> * 收集 CPU 使用量数据
> * 分析 CPU 使用量数据

## <a name="step-1-collect-profiling-data"></a>步骤 1：收集分析数据

1. 打开要在 Visual Studio 中调试的项目，并在应用中设置检查 CPU 使用率的断点。

2. 在函数末尾或想要分析的代码区域中设置第二个断点。

    > [!TIP]
    > 通过设置两个断点，可将数据收集限制到想要分析的代码部分。

3. 将自动显示 **“诊断工具”** 窗口，除非你已将其关闭。 若要再次显示该窗口，请依次单击“调试”   > “Windows”   > “显示诊断工具”  。

4. 可以使用工具栏上的“选择工具”  设置，选择是否查看 **CPU 使用率**[内存使用](../profiling/Memory-Usage.md)或同时查看两者。 如果运行的是 Visual Studio Enterprise，还可以在“工具”   > “选项”   > “IntelliTrace”  中启用或禁用 IntelliTrace。

     ![显示诊断工具](../profiling/media/diag-tools-select-tool.png "DiagToolsSelectTool")

     我们将主要查看 CPU 使用率，因此请确保已启用**CPU 使用率**（默认情况下已启用）。

5. 依次单击“调试”   > “启动调试”  或单击工具栏上的“启动”  或按 F5  。

     当应用完成加载后，将显示诊断工具的“摘要”视图。 如果需要打开窗口，请依次单击“调试”   > “Windows”   > “显示诊断工具”  。

     ![诊断工具“摘要”选项卡](../profiling/media/diag-tools-summary-tab.png "DiagToolsSummaryTab")

     有关事件的详细信息，请参阅[搜索和筛选“诊断工具”窗口中的“事件”选项卡](https://devblogs.microsoft.com/devops/searching-and-filtering-the-events-tab-of-the-diagnostic-tools-window/)。

6. 运行会触发第一个断点的方案。

7. 调试器暂停时，启用收集 CPU 使用率数据，然后打开“CPU 使用率”  选项卡。

     ![诊断工具启用 CPU 分析](../profiling/media/diag-tools-enable-cpu-profiling.png "DiagToolsEnableCPUProfiling")

     选择“记录 CPU 配置文件”  时，Visual Studio 将开始记录函数和执行这些函数所用的时间。 应用程序在断点处中断时，仅可以查看此收集的数据。

8. 按 F5 将应用运行到第二个断点。

     现在将拥有应用程序特定于在两个断点间运行的代码区域的性能数据。

     探查器开始准备线程数据。 等待其完成。

     ![诊断工具准备线程](../profiling/media/diag-tools-preparing-data.png "DiagToolsPreparingThreads")

     CPU 使用率工具在“CPU 使用率”  选项卡中显示报表。

     ![诊断工具“ CPU 使用率”选项卡](../profiling/media/diag-tools-cpu-usage-tab.png "DiagToolsCPUUsageTab")

9. 如果想要选择要分析的更具体的代码区域，请在 CPU 时间轴中选择一个区域（它必须是显示分析数据的区域）。

     ![诊断工具选择时间段](../profiling/media/diag-tools-select-time-segment.png "DiagToolsSelectTimeSegment")

     现在可以开始分析数据。

## <a name="step-2-analyze-cpu-usage-data"></a>步骤 2：分析 CPU 使用量数据

建议通过检查 CPU 使用率下的函数列表开始分析数据，然后确定执行大部分工作的函数，最后仔细查看每一个函数。

1. 在函数列表中，检查执行大部分工作的函数。

    ![诊断工具 CPU 使用率函数列表](../profiling/media/diag-tools-cpu-usage-function-list.png "DiagToolsCPUUsageFunctionList")

    > [!TIP]
    > 函数将按执行工作量从多到少排列（不按调用顺序）。 这有助于快速标识运行时间最长的函数。

2. 在函数列表中，双击一个执行大量工作的应用函数。

    双击该函数时，将在左侧窗格中打开“调用方/被调用方”  视图。

    ![诊断工具调用方和被调用方视图](../profiling/media/diag-tools-caller-callee.png "DiagToolsCallerCallee")

    在此视图中，所选函数显示在标题和“当前函数”  框中（本例中为 GetNumber）。 调用当前函数的函数显示在“调用函数”  左下方，当前函数调用的任何函数均显示在右侧的“被调用函数”  框中。 （可选择其中一个框来更改当前函数。）

    此视图显示总时间及函数完成执行所用的总体应用运行时间的百分比。
    **函数体**还显示函数体中所用的时间总量（及百分比），其中不包括调用和被调用函数中所用的时间。 （在此示例中，共花费 2389 毫秒，函数体内花费 2367 毫秒，其余 22 毫秒花费在此函数调用的外部代码中）。

    > [!TIP]
    > **函数体**中的较高值可能指示函数自身内部的性能瓶颈。

3. 若要按调用函数的顺序来查看较高级别的视图，请在顶部窗格的下拉列表中选择“调用关系树”  。

    图中每个带编号的区域都与过程中的一个步骤相关。

    ::: moniker range=">=vs-2019"
    ![诊断工具调用关系树](../profiling/media/vs-2019/diag-tools-call-tree.png "DiagToolsCallTree")
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![诊断工具调用关系树](../profiling/media/diag-tools-call-tree.png "DiagToolsCallTree")
    ::: moniker-end

    |||
    |-|-|
    |![第 1 步](../profiling/media/ProcGuid_1.png "ProcGuid_1")|CPU 使用量调用关系树中的顶级节点是一个伪节点|
    |![第 2 步](../profiling/media/ProcGuid_2.png "ProcGuid_2")|在大多数应用中，当禁用 [“显示外部代码”](#view-external-code) 选项时，二级节点是 **[外部代码]** 节点，该节点包含系统和框架代码，它可以启动和停止应用、绘制 UI、控制线程计划以及向应用提供其他低级服务。|
    |![第 3 步](../profiling/media/ProcGuid_3.png "ProcGuid_3")|二级节点的子级为用户代码方法和异步例程，它们由二级系统和框架代码进行调用或创建。|
    |![第 4 步](../profiling/media/ProcGuid_4.png "ProcGuid_4")|方法的子节点仅包含用于父方法调用的数据。 禁用“显示外部代码”  后，应用方法只能包含 **[外部代码]** 节点。|

    下面是列值的详细信息：

    - **总 CPU** 指示函数及由它调用的任何函数完成的工作量。 较高的总 CPU 值指向总体成本最高的函数。

    - **自 CPU**指示函数体中的代码完成的工作量，不包括由它调用的函数完成的工作。 较高的**自 CPU** 值可能指示函数自身内部的性能瓶颈。

    - **模块**包含函数的模块名或包含 [外部代码] 节点中的函数的模块数量。

    ::: moniker range=">=vs-2019"
    要查看调用树视图中使用最高 CPU 百分比的函数调用，请单击“展开热路径”  。

    ![诊断工具热路径](../profiling/media/vs-2019/diag-tools-hot-path.png "DiagToolsHotPath")
    ::: moniker-end

    > [!NOTE]
    > 如果看到调用树中的代码标记为“已损坏”代码或“不可走堆栈”，则表示可能已删除 Windows事件跟踪 (ETW) 事件。 尝试第二次收集相同的跟踪以解决问题。

## <a name="view-external-code"></a>查看外部代码

外部代码是你编写的代码执行的系统和框架组件中的函数。 外部代码包含函数，可启动和停止应用、绘制 UI、控制线程以及向应用提供其他低级别服务。 在大多数情况下，你不会对外部代码感兴趣，因此 CPU 使用率工具可将用户方法的外部函数收集到一个 [外部代码]  节点中。

若要查看外部代码的调用路径，请从“筛选器视图”  列表中选择“显示外部代码”  ，然后选择“应用”  。

![选择“筛选器视图”，然后选择“显示外部代码”](../profiling/media/diag-tools-show-external-code.png "DiagToolsShowExternalCode")

请注意，许多外部代码调用链已深度嵌套，因此函数名列的宽度可能超过所有计算机监视器（最大的计算机监视器除外）的显示宽度。 发生这种情况时，函数名将显示为 […]  。

使用搜索框找到要查找的节点，然后滑动水平滚动条将数据带入视图中。

> [!TIP]
> 如果分析调用 Windows 函数的外部代码，应确保具有最新的 .pdb 文件  。 如果没有这些文件，报告视图将列出含义隐晦、难以理解的 Windows 函数名称。 有关如何确保具有所需文件的详细信息，请参阅[在调试器中指定符号 (.pdb) 和源文件](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)。

## <a name="next-steps"></a>后续步骤

本教程中介绍了如何收集和分析 CPU 使用量数据。 完成[首先了解分析工具](../profiling/profiling-feature-tour.md)后，你可能想要快速了解如何分析应用中的内存使用情况。

> [!div class="nextstepaction"]
> [Visual Studio 中的配置文件内存使用](../profiling/memory-usage.md)
