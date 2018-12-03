---
title: 调试实时 ASP.NET Azure 应用
ms.description: Learn how to set snappoints and view snapshots with the Snapshot Debugger.
ms.custom: mvc
ms.date: 03/16/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- debugger
ms.assetid: adb22512-4d4d-40e5-9564-1af421b7087e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
- azure
ms.openlocfilehash: a2dfc759fbd42dd435133e223c72760ae5c274c3
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/19/2018
ms.locfileid: "39154458"
---
# <a name="debug-live-aspnet-azure-apps-using-the-snapshot-debugger"></a>使用快照调试器调试实时 ASP.NET Azure 应用程序

你感兴趣的代码执行时，快照调试程序给生产中应用创建快照。 要指示调试程序创建快照，可在代码中设置 snappoints 和 logpoints。 使用调试程序可精确查看出错的内容，而不影响生产应用程序的流量。 快照调试程序有助于在生产环境中，大幅减少解决出现的问题花费的时间。

Snappoint 和 logpoint 类似于断点，但与断点不同，snappoint 在命中时不暂停应用程序。 通常情况下，在捕获点捕获快照需 10-20 毫秒。

在本教程中，你将：

> [!div class="checklist"]
> * 启动快照调试器
> * 设置捕获点，以及查看快照
> * 设置记录点

## <a name="prerequisites"></a>系统必备

* 快照调试器功能仅适用于 Visual Studio 2017 Enterprise 版本 15.5 或更高版本与**ASP.NET 和 web 开发工作负荷**。 有关 ASP.NET Core，你还需要已安装 **.NET 核心开发** 的工作负荷。

    如果尚未安装，安装[Visual Studio 2017 Enterprise 版本 15.5](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)或更高版本。 如果要从以前的 Visual Studio 2017 安装更新，运行 Visual Studio 安装程序并签入的快照调试器组件**ASP.NET 和 web 开发工作负荷**。

* 基本或更高版本的 Azure 应用服务计划。

* 快照集合适用于在 Azure App Service 中运行的以下 Web 应用：

    * 在 .NET Framework 4.6.1 或更高版本上运行的 ASP.NET 应用程序。
    * 在 Windows 中的 .Net Core 2.0 或更高版本上运行的 ASP.NET Core 应用程序。

## <a name="open-your-project-and-start-the-snapshot-debugger"></a>打开你的项目并启动快照调试器

1. 打开你想要快照调试的项目。

    > [!IMPORTANT]
    > 对于快照调试，您需要打开与发布到 Azure 应用服务**相同版本的源代码**。

1. 在云资源管理器 (**视图 > 云资源管理器**)，右键单击您的项目部署到 Azure 应用服务，然后选择**附加快照调试器**。

   ![启动快照调试程序](../debugger/media/snapshot-launch.png)

    选择第一次**附加快照调试器**，系统会提示你在 Azure 应用服务上安装快照调试器站点扩展。 此安装需要重新启动你的 Azure 应用服务。

   Visual Studio 现在处于快照调试模式下。

    > [!NOTE]
    > Application Insights 站点扩展还支持快照调试。 如果你遇到的"站点扩展已过期"错误消息，请参阅[故障排除提示和已知的问题的快照调试](../debugger/debug-live-azure-apps-troubleshooting.md)升级的详细信息。

   ![快照调试模式](../debugger/media/snapshot-message.png)

   **模块**窗口中会显示在Azure 应用服务中，所有已加载模块 (选择**调试 / Windows / 模块**要打开此窗口)。

   ![检查模块窗口](../debugger/media/snapshot-modules.png)

## <a name="set-a-snappoint"></a>设置捕获点

1. 在代码编辑器中，单击你感兴趣设置捕获点的代码行旁边的左滚动条槽。 请确保它是您知道将执行的代码。

   ![设置捕获点](../debugger/media/snapshot-set-snappoint.png)

2. 单击**开始收集**若要打开捕获点。

   ![开启捕获点](../debugger/media/snapshot-start-collection.png)

    > [!TIP]
    > 查看快照时，不能执行步骤，但可以在你的代码执行的不同代码行处，放置多个捕获点。 如果在代码中有多个捕获点，快照调试器可以确保对应的快照，来自相同的最终用户会话。 即使有多个用户点击您的应用程序，快照调试器仍然执行此操作。

## <a name="take-a-snapshot"></a>创建快照

捕获点启用后，则它将在捕获点所在的代码行执行时捕获快照。 此执行可能由您服务器上的实际请求引起。 若要强制您命中捕获点，请通过浏览器访问您的网站，采取任何命中捕获点的行为。

## <a name="inspect-snapshot-data"></a>检查快照数据

1. 当命中捕获点时，快照将出现在诊断工具窗口。 若要打开此窗口，请选择**调试 / 窗口 / 显示诊断工具**。

   ![打开捕获点](../debugger/media/snapshot-diagsession-window.png)

1. 双击捕获点，用于在代码编辑器中打开快照。

   ![检查快照数据](../debugger/media/snapshot-inspect-data.png)

   从此视图中，你可以悬停在变量，以查看数据提示，请使用**局部变量**，**监视**，和**调用堆栈**窗口，并计算表达式。

    网站本身仍然时实时的，最终用户不会受到影响。 默认情况下捕获每个吸附点，只有一个快照： 吸附点捕获快照后关闭。 如果你想要捕获吸附点在另一个快照，您可以将吸附点重新打开通过单击**更新集合**。

此外可以向应用添加更多的吸附点，并将其具有**更新集合**按钮。

**需要帮助？** 请参阅[疑难解答和已知的问题](../debugger/debug-live-azure-apps-troubleshooting.md)并[快照调试常见问题解答](../debugger/debug-live-azure-apps-faq.md)页。

## <a name="set-a-conditional-snappoint"></a>设置条件的吸附点

如果很难重新创建应用程序中的某一特定状态，请考虑使用的条件的吸附点是否可以帮助。 条件的吸附点帮助您避免拍摄快照，直到应用程序进入所需的状态，例如当一个变量具有你想要检查的特定值。 可以设置使用表达式，筛选器条件或命中次数。

#### <a name="to-create-a-conditional-snappoint"></a>若要创建条件的吸附点

1. 右键单击吸附点图标 （空心球），然后选择**设置**。

   ![选择设置](../debugger/media/snapshot-snappoint-settings.png)

1. 在吸附点设置窗口中，键入一个表达式。

   ![键入一个表达式](../debugger/media/snapshot-snappoint-conditions.png)

   在上图中，仅拍摄快照的吸附点时`visitor.FirstName == "Dan"`。

## <a name="set-a-logpoint"></a>设置记录点

除了在命中吸附点时，拍摄快照，还可以配置吸附点将消息记录 （即，创建记录点）。 您可以设置个记录点，而无需重新部署您的应用程序。 记录点几乎执行，并会导致没有影响或负面影响到你正在运行的应用程序。

#### <a name="to-create-a-logpoint"></a>若要创建的记录点

1. 右键单击吸附点图标 （蓝色六边形），然后选择**设置**。

1. 在吸附点设置窗口中，选择**操作**。

    ![创建记录点](../debugger/media/snapshot-logpoint.png)

1. 在消息字段中，可以输入想要记录新的日志消息。 您也可以通过将它们放在大括号内将日志消息中计算变量。

    如果愿意**将发送到输出窗口**，当命中记录点，请在诊断工具窗口中将显示该消息。

    ![Diagsession 窗口中的记录点数据](../debugger/media/snapshot-logpoint-output.png)

    如果你选择**将发送到应用程序日志**、 logpoint 命中时，任何位置，你可以看到消息从显示的消息`System.Diagnostics.Trace`(或`ILogger`.NET Core 中)，如[App Insights](/azure/application-insights/app-insights-asp-net-trace-logs)。

## <a name="next-steps"></a>后续步骤

在本教程中，已学习了如何使用快照调试程序。 您可能想要阅读有关此功能的更多详细信息。

> [!div class="nextstepaction"]
> [快照调试常见问题解答](../debugger/debug-live-azure-apps-faq.md)
