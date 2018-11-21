---
title: Visual Studio 2017 概述
ms.date: 10/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
author: gewarren
f1_keywords:
- vs.startpage
- VS.StartPage.HowDoI
- MSDNSTART
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bc5961e2565c8618ad0f34a8c58d149e4a82c935
ms.sourcegitcommit: 401be39a42ffe007593528b5bba62583ca9fcafd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/30/2018
ms.locfileid: "50244445"
---
# <a name="welcome-to-the-visual-studio-ide"></a>欢迎使用 Visual Studio IDE

Visual Studio 集成开发环境是一种创新启动板，可用于编辑、调试并生成代码，然后发布应用。 集成开发环境 (IDE) 是一个功能丰富的程序，可用于软件开发的许多方面。 除了大多数 IDE 提供的标准编辑器和调试器之外，Visual Studio 还包括编译器、代码完成工具、图形设计器和许多其他功能，以简化软件开发过程。

![Visual Studio IDE](../ide/media/visualstudioide.png)

本图片显示了Visual Studio中打开一个项目和几个重要工具窗口，你可以如下使用这些窗口：

- 可通过[**解决方案资源管理器**](../ide/solutions-and-projects-in-visual-studio.md)（右上方）查看、导航和管理代码文件。 **解决方案资源管理器** 可将代码文件分组为[解决方案和项目](quickstart-projects-solutions.md)，从而帮助整理代码。

- [编辑器窗口](../ide/writing-code-in-the-code-and-text-editor.md)（中心）用于显示文件内容，你可能会在该窗口花费大部分时间。 可在该窗口编辑代码或设计用户界面，例如带有按钮和文本框的窗口。

- [“输出”窗口](../ide/reference/output-window.md)（底部中心）是 Visual Studio 发送通知（例如，调试和错误消息、编译器警告、发布状态消息等）的位置。 每个消息源都有自己的选项卡。

- 利用版本控制技术（如 [Git](https://git-scm.com/) 和 [Team Foundation 版本控制 (TFVC)](/azure/devops/repos/tfvc/overview?view=vsts)），[团队资源管理器](/azure/devops/user-guide/work-team-explorer?view=vsts)（右下方）可让你跟踪工作项并与他人共享代码。

## 版本

Visual Studio 适用于 Windows 和 Mac。 [Visual Studio for Mac](/visualstudio/mac/) 的许多功能与 Visual Studio 2017 相同，并针对开发跨平台应用和移动应用进行了优化。 本文重点介绍 Visual Studio 2017 的 Windows 版本。

Visual Studio 2017 有三个版本：Community、Professional 和 Enterprise。 请参阅[比较 Visual Studio 2017 IDE](https://visualstudio.microsoft.com/vs/compare/)，了解各个版本支持哪些功能。

### <a name="popular-productivity-features"></a>高效性方面的常用功能

Visual Studio 中的一些常用功能可帮助你在开发软件时提高工作效率，这些功能包括：

- [重构](../ide/refactoring-in-visual-studio.md)

   重构包括智能重命名变量、将一个或多个代码行提取到新方法中、更改方法参数的顺序等操作。

   ![在 Visual Studio 中重构](../ide/media/refactoring-menu.png)

- [IntelliSense](../ide/using-intellisense.md)

   IntelliSense 由一组功能构成，它可用于在编辑器中直接显示代码相关信息，还能在某些情况下编写小段代码。 如同在编辑器中拥有了基本文档内联，从而节省了在其他位置查看类型信息的时间。 IntelliSense 功能因语言而异。 有关详细信息，请参阅 [C# IntelliSense](../ide/visual-csharp-intellisense.md)、[Visual C++ IntelliSense](../ide/visual-cpp-intellisense.md)、[JavaScript IntelliSense](../ide/javascript-intellisense.md) 和 [Visual Basic IntelliSense](../ide/visual-basic-specific-intellisense.md)。 下图显示了 IntelliSense 如何显示类型的成员列表：

   ![Visual Studio 成员列表](../ide/media/intellisense-list-members.png)

- [快速启动](../ide/reference/quick-launch-environment-options-dialog-box.md)

   visual Studio 有时会因为有如此多的菜单、选项和属性而让人不知所措。 使用**快速启动**搜索框可以在 Visual Studio 中快速找到所需内容。 开始键入要查找内容的名称时，Visual Studio 会列出结果，这些结果可以准确地将你导向目标位置。 如果需要向 Visual Studio 添加功能，例如添加对其他编程语言的支持，**快速启动** 提供了打开 Visual Studio 安装程序以安装工作负载或单个组件的结果。

   ![Visual Studio 中的“快速启动”搜索框](../ide/media/quick-launch-nuget.png)

- 波形曲线和[快速操作](../ide/quick-actions.md)

   波形曲线是波浪形下划线，它可以在键入时对代码中的错误或潜在问题发出警报。 这些可视线索使你能立即修复问题，而无需等待在生成期间或运行程序时发现错误。 如果将鼠标悬停在波形曲线上，将看到关于此错误的其他信息。 左边距中也可能会出现一个灯泡，提供修复此错误的“快速操作”建议。

   ![Visual Studio 中的波形曲线](../ide/media/squiggles-error.png)

- [调用层次结构](../ide/reference/call-hierarchy.md)

   **调用层次结构** 窗口显示调用所选方法的方法。 考虑更改或删除方法时，或者尝试追踪 bug 时，这可能是有用的信息。

   ![“调用层次结构”窗口](../ide/reference/media/call-hierarchy-csharp-expanded.png)

- [CodeLens](../ide/find-code-changes-and-other-history-with-codelens.md)

   CodeLens 可帮助查找代码引用、代码更改、链接错误、工作项、代码评审和单元测试，所有操作都在编辑器上进行。

   ![CodeLens](../ide/media/codelensoverview.png)

- [转到定义](../ide/go-to-and-peek-definition.md)

   “转到定义”功能可将你直接带到定义函数或类型的位置。

   ![转到定义](../ide/media/go-to-definition-menu.png)

- [查看定义](../ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md)

   **速览定义**窗口显示方法或类型的定义，而无需实际打开一个单独的文件。

   ![查看定义](../ide/media/peek-definition.png)

## <a name="install-the-visual-studio-ide"></a>安装 Visual Studio IDE

本概述文章介绍了 IDE 的基本功能。 文中将演示一些可使用 Visual Studio 完成的操作，包括创建简单项目、使用 [IntelliSense](using-intellisense.md) 辅助编码以及调试应用，以便在程序执行过程中查看变量的值。首先，请[下载 Visual Studio 2017](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) 并将其安装到系统上。

通过模块化安装程序，可以选择和安装工作负荷。工作负荷是你习惯使用的编程语言或平台所需的一些功能。 若要执行[创建程序](#create-a-program)所需的步骤，请务必在安装过程中选择 **.NET Core 跨平台开发** 工作负载。

![Visual Studio 安装程序中的 .NET Core 跨平台开发工作负载](../ide/media/dotnet-core-cross-platform-workload.png)

首次启动 Visual Studio 时，可选择使用 Microsoft 帐户或者工作或学校帐户[登录](signing-in-to-visual-studio.md)。

## <a name="create-a-program"></a>创建程序

现在我们来深入了解并创建一个简单的程序。

1. 打开 Visual Studio。 在菜单上，依次选择 **文件** > **新建** > **项目**。

   ![菜单栏上的“文件”>“新建项目”](../ide/media/file-new-project-menu.png)

2. **新建项目** 对话框中会显示几个项目模板。 模板包含给定项目类型所需的基本文件和设置。 在**Visual C#**下选择**.NET Core** 类别，然后选择 **控制台应用(.NET Core)** 模板。 在 **名称** 文本框中，键入 **HelloWorld**，然后选择“确定”按钮。

   ![.NET Core 应用模板](../ide/media/overview-new-project-dialog.png)

   Visual Studio 随即创建项目。 它是简单的“Hello World”应用程序，可调用 <xref:System.Console.WriteLine?displayProperty=nameWithType> 方法在控制台窗口中 显示文本字符串“Hello World!”。

   > [!NOTE]
   > 如果未看到 **.NET Core** 类别，则需要安装 **.NET Core 跨平台开发** 工作负载。 为此，选择**新建项目**对话框左下角的 **打开 Visual Studio 安装程序** 链接。 **Visual Studio 安装程序** 打开后，向下滚动并选择 **.NET Core 跨平台开发** 工作负载，然后选择**修改**。

   稍后，将看到类似于以下的内容：

   ![Visual Studio IDE](../ide/media/overview-ide-console-app.png)

   应用程序的 C# 代码显示于编辑器窗口中，会占用大部分空间。 请注意，文本已自动着色，用于指示代码的不同方面，如关键字或类型。 此外，代码中的垂直短虚线指示哪两个大括号相匹配，行号能够帮助你在以后查找代码。 可以通过选择带减号的小方形来折叠或展开代码块。 此代码大纲功能可以隐藏不需要的代码，最大程度地减少屏幕混乱。 右侧名为**解决方案资源管理器**的窗口中列出了项目文件。

   ![具有红色框的 Visual Studio IDE](../ide/media/overview-ide-console-app-red-boxes.png)

   还提供了一些其他的菜单和工具窗口，但是现在我们继续下一步操作。

3. 现在启动该应用。 可从菜单栏的“调试”菜单中选择**开始执行(不调试)**，以执行此操作。 还可按 **Ctrl** + **F5**。

   ![“调试”>“开始执行(不调试)”菜单](../ide/media/overview-start-without-debugging.png)

   Visual Studio 生成应用，控制台窗口随即打开并显示消息 **Hello World!** 。 现在你拥有了一个正在运行的应用！

   ![控制台窗口](../ide/media/overview-console-window.png)

4. 要关闭控制台窗口，请在键盘上按任意键。

5. 接下来，向应用添加一些附加代码。 在 `Console.WriteLine("Hello World!");` 行的前面添加以下 C# 代码：

   ```csharp
   Console.WriteLine("\nWhat is your name?");
   var name = Console.ReadLine();
   ```

   此代码在控制台窗口中显示“What is your name?”，然后等待用户输入文本并按 Enter 键。

6. 将显示 `Console.WriteLine("Hello World!");` 的行更改为以下代码：

   ```csharp
   Console.WriteLine($"\nHello {name}!");
   ```

7. 选择**调试** > **开始执行(不调试)**，或按 **Ctrl** + **F5** ，再次运行该应用。

   Visual Studio 重新生成应用，控制台窗口随即打开，并提示输入姓名。

8. 在控制台窗口中输入姓名，并按 **Enter**。

   ![控制台窗口输入](media/overview-console-input.png)

9. 按任意键关闭控制台窗口，并停止正在运行的程序。

## <a name="use-refactoring-and-intellisense"></a>使用重构和 IntelliSense

让我们了解一下如何借助[重构](refactoring-in-visual-studio.md)和[IntelliSense](using-intellisense.md) 更有效地进行编码。

首先，重命名 `name` 变量：

1. 双击 `name` 变量将其选中。

2. 为变量 **username** 键入新名称。

   请注意，变量周围将显示灰色框且边距中会出现灯泡。

3. 选择灯泡图标，显示可用的[快速操作](quick-actions.md)。 选择 **将 'name' 重命名为 'username'**。

   ![Visual Studio 中的重命名操作](media/rename-quick-action.png)

   该变量会在整个项目中进行重命名，本例中只有两处。

   ![显示 Visual Studio 中重命名重构的 gif 动图](media/rename-refactoring.gif)

4. 接下来介绍 IntelliSense。 在 `Console.WriteLine($"\nHello {username}!");` 行的下方，键入 **DateTime now = DateTime.** 。

   此时，框中显示 <xref:System.DateTime> 类的成员。 另外，当前所选成员的说明会显示在单独的框中。

   ![Visual Studio 中的 IntelliSense 列表成员](media/intellisense-list-members.png)

5. 通过双击或按 **Tab** 选择名为 **Now**（该类的一个属性）的成员。通过添加分号 **;** 结束该代码行。

6. 在其下方，键入或复制以下代码行：

   ```csharp
   int dayOfYear = now.DayOfYear;

   Console.Write("Day of year: ");
   Console.WriteLine(dayOfYear);
   ```

   > [!TIP]
   > <xref:System.Console.Write%2A?displayProperty=nameWithType> 与 <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> 稍有不同，它在打印后不会添加行终止符。 这意味着发送到输出的下一段文本将打印在同一行上。 将鼠标悬停在代码中的每个方法上，即可查看其说明。

7. 接下来，我们将再次使用重构来使代码更加简洁。 单击 `DateTime now = DateTime.Now;` 行中的 `now` 变量。

   请注意，该行的边距中会显示一个小螺丝刀图标。

8. 单击螺丝刀图标，查看 Visual Studio 提供的建议。 在本示例中，它显示[内联临时变量](reference/inline-temporary-variable.md)重构，可在无需更改整体行为的情况下删除代码行：

   ![Visual Studio 中的内联临时变量重构](media/inline-temporary-variable-refactoring.png)

9. 单击**内联临时变量**，重构代码。

10. 按 **Ctrl** + **F5** 重新运行程序。 输出的内容与以下类似：

   ![显示程序输出的控制台窗口](../ide/media/overview-console-final.png)

## <a name="debug-code"></a>调试代码

编写代码时，需要运行并测试该代码是否存在 bug。 可通过 Visual Studio 的调试系统逐句执行代码，一次执行一条语句，逐步检查变量。 可设置停止在特定行执行代码的断点。 可观察变量的值如何随代码运行而更改等。

通过设置断点，可查看程序处于飞行模式时 `username` 变量的值。

1. 查找显示 `Console.WriteLine($"\nHello {username}!");` 的代码行。 要在此代码行上设置一个断点，即让程序在该行暂停执行，请单击编辑器的最左侧边距。 还可单击代码行上的任意位置，然后按 **F9**。

   此时，最左侧边距中将显示一个红圈，代码突出显示为红色。

   ![Visual Studio 中代码行上的断点](media/breakpoint.png)

1. 选择**调试** > **启动调试**或按 **F5**，开始调试。

1. 控制台窗口出现并询问姓名时，请键入姓名，然后按 **Enter**。

   请注意，焦点返回到 Visual Studio 代码编辑器，设置有断点的代码行突出显示为黄色。 这表示它是程序将执行的下一个代码行。

1. 将鼠标悬停在 `username` 变量上，即可查看它的值。 或者，可以右键单击 `username` 并选择**添加监视**，将变量添加到**监视**窗口，这样也可查看它的值。

   ![在 Visual Studio 中进行调试时的变量值](media/debugging-variable-value.png)

1. 若要让程序运行至结束，请再次按 **F5**。

有关在 Visual Studio 中进行调试的详细信息，请参阅[调试器功能简介](../debugger/debugger-feature-tour.md)。

## <a name="customize-visual-studio"></a>自定义 Visual Studio

可个性化设置 Visual Studio 用户界面，包括更改默认颜色主题。 更改为**深色**主题：

1. 在菜单栏中，选择**工具** > **选项**，打开**选项**对话框。

2. 在**环境** > **常规** 选项页上，将选择的**颜色主题** 更改为**深色**，然后选择**确定**。

   此时，整个 IDE 的颜色主题更改为**深色**。

   ![深色主题中的 Visual Studio](media/quickstart-personalize-dark-theme.png)

若要了解有关 IDE 个性化设置的其他方法，请参阅[个性化设置 Visual Studio](../ide/personalizing-the-visual-studio-ide.md)。

## <a name="next-steps"></a>后续步骤

查看下述一篇介绍性的文章，进一步了解 Visual Studio：

- 在[学习使用代码编辑器](quickstart-editor.md)中熟悉代码编辑器

- 在[了解项目和解决方案](quickstart-projects-solutions.md)中学习 Visual Studio 如何整理代码

如果准备深入了解更多编码，接下来可阅读下述一篇针对语言的快速入门：

- [使用 Visual Studio 创建第一个 Python Web 应用](quickstart-python.md)

- [使用 Visual Studio 创建第一个 C# Web 应用](quickstart-aspnet-core.md)

- [使用 Visual Studio 创建第一个 F# Web 应用](quickstart-fsharp.md)

- [使用 Visual Studio 创建第一个 Node.js 应用](quickstart-nodejs.md)

- [Visual Studio 中的 C++ 入门](getting-started-with-cpp-in-visual-studio.md)

## <a name="see-also"></a>请参阅

- 发现[更多 Visual Studio 功能](../ide/advanced-feature-overview.md)
- 访问 [visualstudio.microsoft.com](https://visualstudio.microsoft.com/vs/)
- 阅读 [Visual Studio 博客](https://blogs.msdn.microsoft.com/visualstudio/)
- 查看 [Microsoft Virtual Academy](https://mva.microsoft.com/product-training/visual-studio-courses#!index=2&lang=1033) 上的免费 Visual Studio 课程
- 从 [Visual Studio 下载](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)中下载 Visual Studio
