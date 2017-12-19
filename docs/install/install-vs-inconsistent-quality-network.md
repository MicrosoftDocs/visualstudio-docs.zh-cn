---
title: "在低带宽或不可靠的网络环境中安装 | Microsoft Docs"
description: "介绍了 Visual Studio 安装程序在不可靠的网络条件下的运行方式，以及如何在开始安装前下载安装文件。"
ms.date: 08/30/2017
ms.reviewer: tims
ms.suite: 
ms.technology: vs-acquisition
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 44DB1998-68CD-4560-870A-EE5B993DCF6E
author: timsneath
ms.author: tglee
manager: ghogen
ms.openlocfilehash: 7618537fcceb0527b29f5c40584fb69d7ddcca63
ms.sourcegitcommit: eb954434c34b4df6fd2264266381b23ce9e6204a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2017
---
# <a name="install-visual-studio-2017-on-low-bandwidth-or-unreliable-network-environments"></a>在低带宽或不可靠的网络环境中安装 Visual Studio 2017

建议尝试使用 Visual Studio Web 安装程序 &mdash; 使用体验一定会让你在大多数情况下感到满意。

 > [!div class="button"]
 > [下载 Visual Studio 2017](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocsOL)
<br/>

但是，如果 Internet 连接不可用或不可靠，则可以使用命令行创建完成脱机安装所需的文件的本地缓存。 操作方法如下。

> [!NOTE]
> 如果你是企业管理员，并且要将 Visual Studio 2017 部署到客户端工作站网络（与 Internet 之间设有防火墙），请参阅我们的[创建 Visual Studio 2017 的网络安装](../install/create-a-network-installation-of-visual-studio.md)和[在脱机环境中安装 Visual Studio 的特殊注意事项](../install/install-visual-studio-in-offline-environment.md)页面。

## <a name="step-1---download-the-visual-studio-bootstrapper"></a>步骤 1 - 下载 Visual Studio 引导程序

首先，下载选定 Visual Studio 版本的 Visual Studio 引导程序。

安装程序文件（具体而言是引导程序文件）将是下列项之一，或与之类似。

| 版本                    | 文件                                                                    |
|----------------------------|-------------------------------------------------------------------------|
| Visual Studio 社区    | [vs_community.exe](https://aka.ms/vs/15/release/vs_community.exe)       |
| Visual Studio Professional | [vs_professional.exe](https://aka.ms/vs/15/release/vs_professional.exe) |
| Visual Studio Enterprise   | [vs_enterprise.exe](https://aka.ms/vs/15/release/vs_enterprise.exe)     |

## <a name="step-2---create-a-local-install-cache"></a>步骤 2 - 创建本地安装缓存

必须具有 Internet 连接才能完成此步骤。 若要创建本地布局，请打开命令提示符，然后使用以下示例中的命令之一：下面的示例假定用户使用的是 Visual Studio 社区版；请根据版本相应调整命令。

- 对于 .NET Web 和.NET 桌面开发，请运行：

   ```vs_community.exe --layout c:\vs2017layout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional --lang en-US```

- 对于 .NET 桌面和 Office 开发，请运行：

   ```vs_community.exe --layout c:\vs2017layout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.Office --includeOptional --lang en-US```

- 对于 C++ 桌面开发，请运行：

   ```vs_community.exe --layout c:\vs2017layout --add Microsoft.VisualStudio.Workload.NativeDesktop --includeRecommended --lang en-US```

- 若要创建包含所有功能的完整本地布局（耗时将很长 &mdash; 我们提供的功能_非常多_！），请运行：

   ```vs_community.exe --layout c:\vs2017layout --lang en-US```

如果要安装非英语语言，请从此页底部的列表中将 `en-US` 更改为相应的区域设置。 请使用此[可用组件和工作负载列表](workload-and-component-ids.md)，根据需要进一步自定义安装缓存。

> [!IMPORTANT]
> 完整的 Visual Studio 2017 布局至少需要 35 GB 磁盘空间，可能需要一段时间才能下载完成。 有关如何创建仅具有要安装的组件的布局的信息，请参阅[使用命令行参数安装 Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md)。

## <a name="step-3---install-visual-studio-from-the-local-cache"></a>步骤 3 - 从本地缓存安装 Visual Studio

> [!TIP]
> 当你从本地安装缓存运行时，安装程序会使用其中每个文件的本地版本。 不过，如果你在安装过程中选择的组件不在缓存中，我们会尝试从 Internet 下载。

为了确保只安装已下载的文件，请使用在创建布局缓存时所用的相同命令行选项。 例如，如果使用以下命令创建了布局缓存：

```vs_community.exe --layout c:\vs2017layout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional --lang en-US```

请使用以下命令运行安装布局：

```c:\vs2017layout\vs_community.exe --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional```

  > [!NOTE]
  > 如果你遇到签名无效的错误，则必须安装更新的证书。 在脱机缓存中打开证书文件夹。 双击每个证书文件，然后单击完成证书管理器向导。 如果看到输入密码提示，请将密码留空。

## <a name="list-of-language-locales"></a>语言区域设置列表

| **语言-区域设置** | **语言** |
| ----------------------- | --------------- |
| cs-CZ | 捷克语 |
| de-DE | 德语 |
| en-US | 英语 |
| es-ES | 西班牙语 |
| fr-FR | 法语 |
| it-IT | 意大利语 |
| ja-JP | 日语 |
| ko-KR | 朝鲜语 |
| pl-PL | 波兰语 |
| pt-BR | 葡萄牙语 - 巴西 |
| ru-RU | 俄语 |
| tr-TR | 土耳其语 |
| zh-CN | 中文 - 简体 |
| zh-TW | 中文 - 繁体 |

## <a name="get-support"></a>获取支持
有时也会遇到问题。 如果 Visual Studio 安装失败，请参阅 [Visual Studio 2017 安装和升级问题疑难解答](troubleshooting-installation-issues.md)页。 如果所有的疑难解答步骤都没有帮助，请通过实时聊天与我们联系，以获得安装帮助（仅限英语）。 有关详细信息，请参阅 [Visual Studio 支持页](https://www.visualstudio.com/vs/support/#talktous)。

下面是另外几个支持选项：
* 可以通过[报告问题](../ide/how-to-report-a-problem-with-visual-studio-2017.md)工具（会出现在 Visual Studio 安装程序和 Visual Studio IDE 中）向我们报告产品问题。
* 可以在 [UserVoice](https://visualstudio.uservoice.com/forums/121579) 上与我们分享产品建议。
* 可以在 [Visual Studio 开发者社区](https://developercommunity.visualstudio.com/)中跟踪产品问题，并在其中提问和找到答案。
* 此外，还可以通过 [Gitter 社区的 Visual Studio 对话](https://gitter.im/Microsoft/VisualStudio)与我们和其他 Visual Studio 开发人员进行交流。  （此选项需要 [GitHub](https://github.com/) 帐户）。

## <a name="see-also"></a>请参阅
* [安装 Visual Studio](install-visual-studio.md)
* [Visual Studio 管理员指南](visual-studio-administrator-guide.md)
* [使用命令行参数安装 Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
