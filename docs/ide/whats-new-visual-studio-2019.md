---
title: Visual Studio 2019 中的新增功能
titleSuffix: ''
description: 了解 Visual Studio 2019 中的新增功能。
ms.date: 07/23/2019
helpviewer_keywords:
- Visual Studio, what's new
- what's new [Visual Studio]
ms.assetid: 00bec66b-bcee-46f5-91d9-f73a2b469744
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.topic: conceptual
ms.workload:
- multiple
ms.openlocfilehash: 2c9526a0cbf33278bbc3cab8120bb20ab0f5377a
ms.sourcegitcommit: 9c07ae6fb18204ea080c8248994a683fa12e5c82
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/04/2019
ms.locfileid: "70293720"
---
# <a name="whats-new-in-visual-studio-2019"></a>Visual Studio 2019 中的新增功能

已针对[版本 16.2](/visualstudio/releases/2019/release-notes/) 进行更新 

>[!div class="button"]
>[下载 Visual Studio 2019](https://visualstudio.microsoft.com/downloads)

使用 Visual Studio 2019，你将获得面向任何开发人员、应用程序和平台的一流工具和服务。 无论是首次使用 Visual Studio 还是已经使用多年，此新版本都有很多值得称赞的地方！

以下是对新增功能的简要概括：

* **[开发](#develop)** ：通过改进的性能、即时代码清理和更好的搜索结果来保持专注和高效。
* **[协作](#collaborate)** ：在 Visual Studio 中，通过 Git 优先工作流、实时编辑和调试，以及代码评审，即可尽情享受自然协作。
* **[调试](#debug)** ：突出显示并导航到特定值、优化内存使用，并对应用程序的执行进行自动快照。

有关此版本中所有新增功能的完整列表，请参阅[发行说明](/visualstudio/releases/2019/release-notes/)。

## <a name="develop"></a>开发

查看以下视频，以了解如何使用新功能来节省时间。 <br><br>*视频长度：3.00 分钟*

> [!VIDEO https://www.youtube.com/embed/n5sJ4EewKGk]

### <a name="improved-search"></a>改进的搜索

（以前称为快速启动）我们的新搜索体验更快、更有效。 现在，搜索结果会在键入时动态显示。 并且，搜索结果通常可以包括命令的键盘快捷方式，更便于记忆以备将来使用。

   ![Visual Studio 2019 中的新搜索体验动画](media/vs-2019/new-search-feature.gif)

新的模糊搜索逻辑将找到你需要的所有内容，而不考虑拼写错误。 因此，无论你是在寻找命令、设置、文档还是其他有用的操作，新的搜索功能都可以让你更轻松地找到所需内容。

### <a name="refactorings"></a>重构

C# 中有很多新颖有用的重构，更便于组织代码。 它们在灯泡中显示为建议，并且包括将成员移动到接口或基类、调整命名空间以匹配文件夹结构、将 foreach 循环转换为 Linq 查询等操作。

   ![Visual Studio 2019 中的重构体验动画](media/vs-2019/refactorings.gif)

只需通过按 Ctrl+.  并选择要采取的操作调用重构。

### <a name="intellicode"></a>IntelliCode

[Visual Studio IntelliCode](/visualstudio/intellicode/) 通过使用人工智能 (AI) 来提高软件开发工作的效率。 IntelliCode 将在 GitHub 上训练 2,000 个开源项目（每个项目包含 100 个星级）以生成这些建议。

![Visual Studio 2019 中的 IntelliCode 动画](media/vs-2019/IntelliCode.gif)

下面是 Visual Studio IntelliCode 帮助提高生产力的几种方法：

* 提供上下文感知代码完成
* 指导开发人员遵守团队的模式和样式
* 发现难以察觉的代码问题
* 将关注点集中到重要领域，从而专注代码评审

在首次预览作为 Visual Studio 扩展的 IntelliCode 时，我们最初仅支持 C#。 现在，在 16.1 的新增功能中，我们添加了对 C# 和 XAML“in-the-box”的支持  。 （但是，对 C++ 和 TypeScript/JavaScript 的支持仍处于预览状态。）

如果你使用的是 C#，我们还添加了在你自己的代码上训练自定义模型的功能。

有关 IntelliCode 的详细信息，请参阅 [Announcing the general availability of IntelliCode plus a sneak peek](https://devblogs.microsoft.com/visualstudio/announcing-the-general-availability-of-intellicode-plus-a-sneak-peek/)（宣布 IntelliCode 的正式发布以及快速浏览）和 [Code more, scroll less with Visual Studio IntelliCode](https://devblogs.microsoft.com/visualstudio/code-more-scroll-less-with-visual-studio-intellicode/)（使用 Visual Studio IntelliCode 编写更多代码，更少滚动）博客文章。

### <a name="code-cleanup"></a>代码清理

与新文档运行状况指示符配对是一种新的代码清理命令。 可以使用此新命令通过单击按钮来识别并修复警告和建议。

清理将格式化代码并应用[当前设置](code-styles-and-code-cleanup.md)和 [.editorconfig 文件](create-portable-custom-editor-options.md)建议的任何代码修复程序。

   ![Visual Studio 2019 中新代码清理控件的屏幕截图](media/vs-2019/code-cleanup-profile.png)

此外可以将修复程序集合另存为配置文件。 例如，如果你有一小组在编写代码时经常应用的目标修复程序，然后在进行代码评审之前应用另一组全面的修复程序，则可以配置配置文件来处理这些不同的任务。

   ![在 Visual Studio 2019 中配置代码清理控件的屏幕截图](media/vs-2019/code-cleanup-profile-configure.png)

### <a name="per-monitor-aware-pma-rendering"></a>按监视器感知 (PMA) 呈现

如果使用配置了不同显示比例因子的监视器，或远程连接到显示比例因子与主设备不同的计算机，你可能会发现 Visual Studio 看起来比较模糊或以错误的比例呈现。

随着 Visual Studio 2019 的发布，我们正在使 Visual Studio 成为按监视器感知 (PMA) 应用程序。 现在，无论使用何种显示比例因子，Visual Studio 都会正确呈现。

   ![Visual Studio 2019 中的按监视器感知 (PMA) 呈现](media/vs-2019/pma-dpi-scaling.png)

有关详细信息，请参阅[通过 Visual Studio 2019 创建更出色的多监视器体验](https://devblogs.microsoft.com/visualstudio/a-better-multi-monitor-experience-with-visual-studio-2019/)博客文章。

### <a name="test-explorer"></a>测试资源管理器

**16.2 中的新增功能**：更新了测试资源管理器，改进了大型测试集的处理，简化了筛选，增加了可发现的命令和选项卡式播放列表视图，并增加了允许微调所显示测试信息的可自定义列。

   ![在测试资源管理器中显示用户界面改进的屏幕截图](media/vs-2019/test-explorer-ui.png)

## <a name="collaborate"></a>协作

查看以下视频，以了解如何建立团队来解决问题。 <br><br>*视频长度：4.22 分钟*

> [!VIDEO https://www.youtube.com/embed/dKLJsiK1QU8]

### <a name="cloud-first-workflow"></a>云优先工作流

打开 Visual Studio 2019 时，你会注意到它是一个新的启动窗口。

   ![Visual Studio 2019 中新启动窗口的屏幕截图](media/vs-2019/start-window-dark.png)

启动窗口提供了几个选项，帮助你快速编写代码。 首先，我们布置了从存储库克隆或签出代码的选项。

   ![Visual Studio 2019 中的“Git 优先”体验动画](media/vs-2019/git-first.gif)

启动窗口还包括用于打开项目或解决方案、打开本地文件夹，或创建新项目的选项。

有关详细信息，请参阅博客文章 [Get to code:How we designed the new Visual Studio start window](https://devblogs.microsoft.com/visualstudio/get-to-code-how-we-designed-the-new-visual-studio-start-window/)（开始编码：我们是如何设计了新的 Visual Studio 开始窗口）。

### <a name="live-share"></a>Live Share

[Visual Studio Live Share](https://visualstudio.microsoft.com/services/live-share/) 是一项开发者服务，可让你与团队成员共享代码库及其上下文，并直接从 Visual Studio 内获得即时双向协作。 利用“实时共享”，团队成员可以无缝且安全地读取、导航、编辑和调试已与他们共享的项目。

Visual Studio 2019 中会默认安装此服务。

![显示 Visual Studio 2019 中 Live Share 协作功能的动画](media/vs-2019/live-share.gif)

有关详细信息，请参见博客文章[用于实时代码评审和交互式教育的 Visual Studio Live Share](https://devblogs.microsoft.com/visualstudio/visual-studio-live-share-for-real-time-code-reviews-and-interactive-education/)和 [Live Share 现在包含在 Visual Studio 2019 中](https://devblogs.microsoft.com/visualstudio/live-share-now-included-with-visual-studio-2019/)。

### <a name="integrated-code-reviews"></a>集成的代码评审

我们正在推出一个新的扩展，你可以下载该扩展与 Visual Studio 2019 一起使用。 使用此新扩展，可以查看、运行甚至调试团队的拉取请求，而无需离开 Visual Studio。 我们支持 GitHub 和 Azure DevOps 存储库中的代码。

   ![Visual Studio 2019 中新启动窗口的屏幕截图](media/vs-2019/pr-experience.png)

有关详细信息，请参阅 [Code reviews using the Visual Studio Pull Requests extension](https://devblogs.microsoft.com/visualstudio/code-reviews-using-the-visual-studio-pull-requests-extension/)（使用 Visual Studio 拉取请求扩展的代码评审）博客文章。

## <a name="debug"></a>调试

查看以下视频，以了解如何在调试时通过精准定位瞄准。 <br><br>*视频长度：3.54 分钟*

> [!VIDEO https://www.youtube.com/embed/hr72Fs8n_9c]

### <a name="performance-gains"></a>性能提升

我们采用了曾经排他的 C++ 数据断点，并将其用于 .NET Core 应用程序。

   ![显示 Visual Studio 2019 中的调试数据断点的动画](media/vs-2019/debug-data-breakpoints.gif)

因此，无论是使用 C++ 还是 .Net Core 编写代码，数据断点都是一个很好的替代方法，而不只是放置常规断点。 数据断点还非常适合用于查找修改、添加或从列表中删除全局对象的位置之类的方案。

而且，如果你是开发大型应用程序的 C++ 开发人员，Visual Studio 2019 已经将过程符号化，这允许你调试这些应用程序，而不会遇到与内存相关的问题。

### <a name="search-while-debugging"></a>调试时搜索

你可能曾经体验过在监视窗口中查找一组值中的字符串。 在 Visual Studio 2019 中，我们在监视、局部变量和自动窗口中添加了搜索，以帮助你查找要查找的对象和值。

   ![显示 Visual Studio 2019 调试搜索窗口的动画](media/vs-2019/debug-window-search.gif)

还可以格式化监视、本地和自动窗口中值的显示方式。  双击任何窗口中的一个项目并添加逗号 (",") 以访问可能的格式说明符下拉列表，每个列表都包含其预期效果的说明。

   ![Visual Studio 2019 中的新监视窗口和格式化值的功能](media/search-watch-window.png)

有关详细信息，请参阅 [Visual Studio 2019 中的增强功能：在 Watch、Autos、Locals 窗口中搜索对象和属性](https://devblogs.microsoft.com/visualstudio/enhanced-in-visual-studio-2019-search-for-objects-and-properties-in-the-watch-autos-and-locals-windows/)博客文章。

### <a name="snapshot-debugger"></a>快照调试程序

获取应用程序在云中执行的快照，以了解具体发生的情况。 （此功能仅在 Visual Studio Enterprise 中提供。）

   ![显示 Visual Studio 2019 Enterprise Snapshot Debugger 的动画](media/vs-2019/snapshot-debugger.gif)

我们增加了对在 Azure VM 上运行的 ASP.NET（Core 和桌面）应用程序的支持。 此外还增加了对在 Azure Kubernetes 服务中运行的应用程序的支持。 Snapshot Debugger 有助于大幅减少解决生产环境中出现的问题所需的时间。

有关详细信息，请参阅[使用 Snapshot Debugger 调试实时 ASP.NET Azure 应用](../debugger/debug-live-azure-applications.md)页，和 [Visual Studio Enterprise 2019 按时间顺序查看调试简介](https://devblogs.microsoft.com/visualstudio/introducing-time-travel-debugging-for-visual-studio-enterprise-2019/)博客文章。

### <a name="microsoft-edge-insider-support"></a>Microsoft Edge Insider 支持

**16.2 中的新增功能**：你可通过使用 [Microsoft Edge Insider](https://www.microsoftedgeinsider.com/) 浏览器设置 JavaScript 应用程序中的断点并启动调试会话。 执行此操作时，Visual Studio 会在启用调试的情况下打开一个新的浏览器窗口，以允许你在 Visual Studio 中单步调试 JavaScript 应用程序。

   ![在浏览器中显示 JavaScript 代码呈现的屏幕截图](media/vs-2019/edge-chromium-breakpoint.png)

## <a name="whats-next"></a>后续步骤

我们经常更新 Visual Studio 2019 的新功能，不断提升开发体验。 若要了解有关我们最新创新的详细信息，请查看 [Visual Studio 博客](https://devblogs.microsoft.com/visualstudio/)。 对于我们迄今为止在预览版中发布的内容记录，请参阅[预览发行说明](/visualstudio/releases/2019/release-notes-preview/)。

想要了解更多关于 Visual Studio 2019 的其他功能吗？ 请参阅 [Visual Studio 路线图](/visualstudio/productinfo/vs-roadmap/)。

## <a name="give-us-feedback"></a>给我们提供反馈

为什么将反馈发送至 Visual Studio 团队？ 因为我们严肃对待客户反馈。 这会给予我们巨大的行事动力。

* 如果想对如何改进 Visual Studio 提出建议，可以使用[功能建议](suggest-a-feature.md)工具。

* 如果遇到挂起、崩溃或其他性能问题，可利用[报告问题](how-to-report-a-problem-with-visual-studio.md)工具与我们轻松共享重现步骤和支持文件。

## <a name="see-also"></a>请参阅

* [Visual Studio 2019 发行说明](/visualstudio/releases/2019/release-notes/)
* [Visual Studio 2019 SDK 的新增功能](../extensibility/whats-new-visual-studio-2019-sdk.md)
* [Visual Studio 2019 for Mac 发行说明](/visualstudio/releasenotes/vs2019-mac-relnotes/)
* [Microsoft Build 2019 会议](https://www.microsoft.com/build)
* [Microsoft Connect()；2018 会议](https://www.microsoft.com/connectevent)
