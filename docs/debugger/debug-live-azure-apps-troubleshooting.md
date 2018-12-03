---
title: 快照调试疑难解答和已知问题 |Microsoft Docs
ms.date: 11/07/2017
ms.technology: vs-ide-debug
ms.topic: troubleshooting
helpviewer_keywords:
- debugger
ms.assetid: 511a0697-c68a-4988-9e29-8d0166ca044a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9d5b5eeefe2bbed542ef18689fd7e16073174bd3
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2018
ms.locfileid: "44284102"
---
# <a name="troubleshooting-and-known-issues-for-snapshot-debugging-in-visual-studio"></a>Visual Studio 中的快照调试疑难解答和已知问题

如果在这篇文章中所述的步骤未解决你遇到的问题，请联系snaphelp@microsoft.com。

## <a name="issue-snappoint-does-not-turn-on"></a>问题： 快照点不能开启

如果看到警告图标![快照点警告图标](../debugger/media/snapshot-troubleshooting-snappoint-warning-icon.png "快照点警告图标") 代替快照点常规图标，然后快照点没有打开。

![快照点不能开启](../debugger/media/snapshot-troubleshooting-dont-turn-on.png "快照点不能开启")

执行以下步骤：

1. 请确保用于生成和部署你 app.isua1 的源代码具有相同版本。请确保为你的部署加载正确的符号。若要执行此操作，在快照调试和验证符号文件列中，显示在调试时加载模块的.pdb文件时，查看**模块**窗口。快照调试器将尝试自动下载并为你部署使用的符号。

## <a name="issue-symbols-do-not-load-when-i-open-a-snapshot"></a>问题： 当我打开快照时符号不加载

如果看到以下窗口时，符号未加载。

![未加载符号](../debugger/media/snapshot-troubleshooting-symbols-wont-load.png "未加载符号")

执行以下步骤：

- 单击 **更改符号设置...** 此页上的链接。 在 **调试 > 符号** 中设置，添加一个符号缓存目录。 设置符号路径后，重新启动快照调试。

   符号或你的项目中可用的.pdb 文件必须匹配你的应用服务部署。 大多数部署 (通过 Visual Studio、 Azure 管道或 Kudu 中，使用 CI/CD 部署等) 将发布符号文件到应用服务。设置符号缓存目录可使 Visual Studio 使用这些符号。

   ![符号设置](../debugger/media/snapshot-troubleshooting-symbol-settings.png "符号设置")

- 或者，如果你的组织使用符号服务器，或者将符号放入不同的路径，使用符号设置以加载你部署正确的符号。

## <a name="issue-i-cannot-see-the-attach-snapshot-debugger-option-in-the-cloud-explorer"></a>问题： 我无法看到云资源管理器中的"附加快照调试器"选项

执行以下步骤：

- 请确保安装了快照调试器组件。 打开 Visual Studio 安装程序，并检查 **快照调试器** 组件中的 Azure 工作负荷。
- 请确保您的应用程序支持。 目前，只支持 ASP.NET (4.6.1+) 和 ASP.NET Core （2.0 +） 应用部署到 Azure 应用程序服务。

## <a name="issue-i-only-see-throttled-snapshots-in-the-diagnostic-tools"></a>问题： 我只看到在诊断工具中限制快照

![Throttled 被阻止的 snappoint](../debugger/media/snapshot-troubleshooting-throttled-snapshots.png "限制快照点")

执行以下步骤：

- 快照占用的内存很少，但仍占用内存。 如果快照调试器检测到你的服务器内存负载过高下，它将不会创建快照。 可以通过停止快照调试器会话，然后重试删除已捕获的快照。

## <a name="known-issues"></a>已知问题

- 当前不支持使用多个 Visual Studio 客户端对同一个应用服务进行快照调试。
- ASP.NET Core 项目不完全支持 Roslyn IL 优化。 对于某些 ASP.NET Core 项目，你可能无法看到某些变量或条件语句中使用某些变量。 
- 特殊变量，如 *$FUNCTION*或 *$CALLER*，在 ASP.NET Core 项目中无法计算条件语句或 logpoints。
- 快照调试不适用于具有[本地缓存]的应用服务(/azure/app-service/app-service-local-cache)开启。
- 目前不支持调试 API 应用的快照。

## <a name="site-extension-upgrade"></a>站点扩展升级

快照调试和 Application Insights 依赖于 ICorProfiler，它将加载到站点过程并在升级过程中将导致文件锁定问题。 我们建议使用此过程以确保没有任何停机的情况下为您的生产站点。

- 创建[部署槽](/azure/app-service/web-sites-staged-publishing)让应用服务中并将您的网站部署到槽。
- 从 Visual Studio 中的云资源管理器或从 Azure 门户交换使用的生产槽。
- 停止槽站点。 这将需要几秒钟来关闭从所有实例的站点 w3wp.exe 进程终止。
- 从 Kudu 站点或 Azure 门户升级槽站点扩展 (*应用服务边栏选项卡 > 开发工具 > 扩展 > 更新*)。
- 启动槽站点。 我们建议访问网站来再次预热。
- 使用的生产槽交换。

## <a name="see-also"></a>请参阅

[在 Visual Studio 中进行调试](../debugger/index.md)  
[调试实时 ASP.NET 应用中使用快照调试程序](../debugger/debug-live-azure-applications.md)  
[快照调试常见问题解答](../debugger/debug-live-azure-apps-faq.md)  
