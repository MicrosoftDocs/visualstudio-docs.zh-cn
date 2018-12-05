---
title: VS 2017 调试入门
description: 开始调试应用程序使用 Visual Studio 调试器
ms.custom: mvc
ms.date: 06/15/2018
ms.technology: vs-ide-debug
ms.topic: quickstart
helpviewer_keywords:
- debugger
ms.assetid: c763d706-3213-494f-b4d2-990b6e1ec456
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d5c479251b7002e506f1dff5e64a028875aa8f80
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/23/2018
ms.locfileid: "49882661"
---
# <a name="first-look-at-the-visual-studio-debugger"></a>先来看一下 Visual Studio 调试器

本主题介绍了 Visual Studio 提供的调试器工具。 在 Visual Studio 环境中, 当您*调试应用* 时，这通常意味着调试器已附加到运行中的应用程序 (即，在调试器模式下)。 当调试器执行此操作时，调试器提供多种途径查看你的代码，在运行时如何执行操作。 可以逐行执行代码，并查看存储在变量中的值，可以设置监视变量以查看更改，可以检查您的代码执行路径，等等。如果这是你第一次尝试调试代码，可能需要阅读[零基础调试](../debugger/debugging-absolute-beginners.md)再浏览本主题。

此处所述的功能都适用于 C#、 c + +、 Visual Basic、 JavaScript 和其他语言支持的 Visual Studio （除非另有说明）。

## <a name="set-a-breakpoint-and-start-the-debugger"></a>设置断点并启动调试器

若要调试，在应用程序启动后，使用调试器附加该进程。 **F5** (**调试 > 启动调试**) 是执行该操作最常见的方法。 但是，现在您可能没有设置任何断点，用来检查应用程序代码，因此我们先设置断点，然后开始调试。 断点是可靠的调试技术中最基本和最重要的功能。 断点指示 Visual Studio 应在哪个位置挂起运行中的代码，以使您可以查看变量的值或内存的行为，或确定代码的分支是否运行。 

如果在代码编辑器中打开一个文件，可以通过单击代码行左侧边距来设置断点。

![设置断点](../debugger/media/dbg-tour-set-a-breakpoint.gif "设置断点")

在调试工具栏中按**F5** (**调试 > 启动调试**) 或**启动调试**按钮![开始调试](../debugger/media/dbg-tour-start-debugging.png "开始调试")，则调试器将运行到遇到的第一个断点处。 如果应用尚未运行，F5 启动调试器，并在第一个断点处停止。

当您知道要详细检查的代码行或代码片段时，断点是一个有用的特性。

## <a name="navigate"></a> 在调试器中使用单步执行命令浏览代码

我们提供很多键盘快捷键命令，因为它们使浏览应用代码更快。如在括号中显示菜单命令的快捷键。）

使用调试器附加启动的应用后，按**F11** (**调试 > 逐语句**)。 F11**逐语句**命令在应用中每次只执行一条语句。 使用 F11 启动应用时，调试器将在中断在第一个语句上。

![F11 逐语句](../debugger/media/dbg-tour-f11.png "F11 逐语句")

黄色箭头表示调试器暂停在该语句上，应用在同一时间也被挂起 （此语句还未执行）。

F11 是详细检查执行流的好方法。 （若要更快的浏览代码，我们同样介绍其他一些选项。）默认情况下，调试器跳过非用户代码 (如果需要详细信息，请参阅[仅我的代码](../debugger/just-my-code.md))。

>[!NOTE]
> 在托管代码中，将看到一个对话框，询问您是否要在自动逐过程执行属性和运算符 （默认行为） 时得到通知。 如果你想要更改之后的设置，禁用置**工具 > 选项**下的菜单**调试**中的**逐过程执行属性和运算符**。

## <a name="step-over-code-to-skip-functions"></a>逐过程跳过函数

当前代码行是函数或方法调用时，可按**F10** (**调试 > 逐过程**) 而不是 F11。

在应用的代码中，按 F10 使用调试器无需单步步入函数或方法 （其中的代码仍执行）。 按 F10，您可以跳过您不感兴趣的代码。 这样一来，你可以快速转到你更感兴趣的代码。

## <a name="step-into-a-property"></a> 单步执行属性

如前所述，默认情况下，调试器跳过托管的属性和字段，但**单步执行特定函数**命令允许你重写此行为。

右键单击某个属性或字段，然后选择**单步执行特定函数**，然后选择一个可用的选项。

![单步执行特定函数](../debugger/media/dbg-tour-step-into-specific.png "单步执行特定函数")

在此示例中，**单步执行特定函数**获取我们的代码`Path.set`。

![单步执行特定函数](../debugger/media/dbg-tour-step-into-specific-2.png "单步执行特定函数")

## <a name="run-to-a-point-in-your-code-quickly-using-the-mouse"></a>使用鼠标将代码快速运行到指定位置

在调试器中，悬停在一行代码直到**运行到光标处**（执行运行到此处） 按钮![运行到光标处](../debugger/media/dbg-tour-run-to-click.png "RunToClick")显示在左侧。

![运行到光标处](../debugger/media/dbg-tour-run-to-click-2.png "运行到光标处")

> [!NOTE]
> **运行到光标处**（执行运行到此处） 按钮中的新增功能[!include[vs_dev15](../misc/includes/vs_dev15_md.md)]。

单击**运行到光标处**（执行运行到此处） 按钮。 调试器将进入到代码行上单击的位置。

使用此按钮将类似于设置临时断点。 这个命令还可以方便的在应用程序代码的可见区域内快速移动。 可以使用**运行到光标处**中任何打开的文件。

## <a name="advance-the-debugger-out-of-the-current-function"></a>将调试器跳出当前函数之外

有时，你可能想要继续调试会话，但要调试器跳过当前函数。

按**Shift + F11** (或**调试 > 跳出**)。

此命令将当前函数返回，恢复应用程序执行 （和调试器）。

## <a name="run-to-cursor"></a>运行到光标处

通过按停止调试器**停止调试**红色按钮![停止调试](../debugger/media/dbg-tour-stop-debugging.png "停止调试")或者**Shift**  + **F5**。

右键单击应用程序中的代码行，然后选择**运行到光标处**。 此命令启动调试，并在当前代码行上设置临时断点。

![运行到光标处](../debugger/media/dbg-tour-run-to-cursor.png "运行到光标处")

如果已设置断点，调试器会抵达的第一个断点处暂停。

按**F5**直至到达其中所选的代码行**运行到光标处**。

当你编辑代码并想要快速设置临时断点，并在同时启动调试器时，此命令很有用。

> [!NOTE]
> 可以使用**运行到光标处**中**调用堆栈**窗口进行调试时。

## <a name="restart-your-app-quickly"></a>快速重新启动您的应用程序

单击**重新启动**![重新启动应用程序](../debugger/media/dbg-tour-restart.png "重新启动应用程序")调试工具栏中的按钮 (**Ctrl + Shift + F5**)。

当您按下**重新启动** 按键时，节省了调试器停止应用程序并重新启动的时间。 调试器会在执行代码被命中的第一个断点处暂停。

如果你想要停止调试器并返回到代码编辑器中，可以按红色停止![停止调试](../debugger/media/dbg-tour-stop-debugging.png "停止调试")按钮而非**重启**。

## <a name="inspect-variables-with-data-tips"></a>检查数据提示中的变量

现在，有点知道自己的方式，因此可以开始检查应用状态 （变量） 与调试器的最佳时机。 可以检查变量是调试器最有用的功能之一，并通过不同的方式来执行此操作。当你尝试调试解决问题时，通常是在尝试找出变量在程序的特定状态下，是否拥有预期的值。

在调试器暂停时，将鼠标悬停到对象，查看其默认属性值 (在此示例中，文件名`market 031.jpg`是默认属性值)。

![查看数据提示](../debugger/media/dbg-tour-data-tips.gif "查看数据提示")

展开要查看其属性的对象 (如`FullPath`在此示例中的属性)。

通常情况下，在调试时，想要快速检查对象的属性值和数据提示，执行此操作是一种好方法。

> [!TIP]
> 在最受支持语言中，在调试会话期间可修改代码。有关详细信息，请参阅[编辑并继续](../debugger/edit-and-continue.md)。

## <a name="inspect-variables-with-the-autos-and-locals-windows"></a>检查与自动和局部变量窗口中的变量

调试时，看看 **自动** 窗口底部的代码编辑器。

![自动变量窗口](../debugger/media/dbg-tour-autos-window.png "自动窗口")

在 **自动** 窗口中，你将看到变量当前值和类型。 **自动** 窗口显示当前行或前面行上使用的所有变量 （在 c + + 中，窗口将都显示前三行代码中的变量。 查看文档，了解特定于语言的行为）。

> [!NOTE]
> 在 JavaScript 中，支持 **局部变量** 窗口但不支持 **自动** 窗口。

接下来，看看 **局部变量** 窗口。 **局部变量** 窗口显示当前作用域内的变量。

![局部变量窗口](../debugger/media/dbg-tour-locals-window.png "局部变量窗口")

在此示例中，`this`对象和对象`f`在作用域中。 有关详细信息，请参阅[检查自动和局部变量窗口中的变量](../debugger/autos-and-locals-windows.md)。

## <a name="set-a-watch"></a>设置监视

可以使用**监视**窗口上指定一个变量 （或表达式），进行密切关注。

调试时，右键单击某个对象，然后选择**添加监视**。

![监视窗口](../debugger/media/dbg-tour-watch-window.png "监视窗口")

在此示例中，必须上设置监视`f`对象，您可以看到当调试器在代码行中移动时，其值发生变化。 与其他变量窗口中不同，**监视**窗口始终显示正在监视的变量（当超出范围时它们变灰）。

有关详细信息，请参阅[设置使用监视和快速监视窗口监视](../debugger/watch-and-quickwatch-windows.md)

## <a name="examine-the-call-stack"></a>检查调用堆栈

在调试时单击**调用堆栈**窗口，这是默认情况下在右下窗格中打开。

![检查调用堆栈](../debugger/media/dbg-tour-call-stack.png "检查调用堆栈")

**调用堆栈** 窗口将显示代码中，调用方法和函数获取顺序。 最上面一行显示当前函数 (`Update`方法在此示例中)。 第二行从`Path.set`属性中显示`Update`调用，依次类推。 调用堆栈是检查和了解应用的执行流的好方法。

> [!NOTE]
> **调用堆栈**窗口类似于某些IDE中的透视图，如 Eclipse。

您可以双击某行代码以查看源代码,也改变当前调试器检查的作用域。 这不改变调试器在源代码中的位置。

此外可以使用从右键单击菜单**调用堆栈**窗口中执行其他操作。 例如，可以将断点插入到特定函数，重新启动应用程序使用**运行到光标处**，并去检查源代码。 请参阅[如何： 检查调用堆栈](../debugger/how-to-use-the-call-stack-window.md)。

## <a name="exception"></a> 检查异常

当您的应用程序引发了异常时，则调试器将导航到引发异常的代码行。

![异常帮助器](../debugger/media/dbg-tour-exception-helper.png "异常帮助器")

在此示例中，**异常帮助程序**演示了`System.Argument`异常和错误消息，指出该路径不是合法的窗体。 因此，我们知道该错误出现在方法或函数的参数。

在此示例中，`DirectoryInfo`调用`value`变量中的空字符串引发错误。

异常帮助器是一项帮助你调试错误的强大功能。 此外可以执行诸如查看错误详细信息，并从异常帮助程序中添加监视。 或者，如果需要可以更改引发特定异常的条件。

> [!NOTE]
> 异常帮助器将替换中[!include[vs_dev15](../misc/includes/vs_dev15_md.md)]的助手异常。

展开**异常设置**节点以查看更多如何处理此异常类型的选项，但你无需更改此教程中的任何内容 ！

## <a name="debug-live-aspnet-apps-in-azure-app-service"></a>调试 Azure 应用服务中的实时 ASP.NET 应用

**快照调试器** 在执行感兴趣的代码时，可给生产中的应用创建快照。 要指示调试器创建快照，可在代码中设置快照点和 记录点。 使用调试器，可精确查看出错的内容，而不影响生产应用程序的流量。 快照调试程序有助于大幅减少在解决生产环境中处理问题的时间。

![启动快照调试器](../debugger/media/snapshot-launch.png "启动快照调试器")

快照集合是可用于在 Azure 应用服务中运行的 ASP.NET 应用程序。 必须在.NET Framework 4.6.1 或更高版本中运行 ASP.NET 应用程序，且必须在.NET Core 2.0 或更高版本的 Windows 中运行 ASP.NET Core 应用程序。

有关详细信息，请参阅[使用快照调试器调试实时 ASP.NET 应用](../debugger/debug-live-azure-applications.md)。

## <a name="view-snapshots-with-intellitrace-step-back-visual-studio-enterprise"></a>查看快照和IntelliTrace 后退 (Visual Studio 企业版) 

**IntelliTrace 后退** 每次调试器断点和单步执行事件，都会自动创建应用程序的快照。 凭借记录的快照便可以返回到上一个断点或步骤，并查看当时应用程序的状态。 如果希望查看应用程序之前的状态，但不想重新启动调试或重新创建所需应用状态，可使用 IntelliTrace 后退节省时间。

可以通过使用调试工具栏中的“后退”和前进”按钮浏览和查看快照。 这些按钮用于浏览“诊断工具”窗口中“事件”选项卡上显示的事件。

![单步执行向后和向前按钮](../debugger/media/intellitrace-step-back-icons-description.png  "后退一步和前进按钮")

有关详细信息，请参阅[检查上一应用程序状态使用 IntelliTrace](../debugger/view-historical-application-state.md)页。

## <a name="next-steps"></a>后续步骤

在本教程中，您已快速看一下许多调试器功能。 您可以更深入了解这些功能的示例应用程序

> [!div class="nextstepaction"]
> [了解如何使用 Visual Studio 进行调试](../debugger/getting-started-with-the-debugger.md)
