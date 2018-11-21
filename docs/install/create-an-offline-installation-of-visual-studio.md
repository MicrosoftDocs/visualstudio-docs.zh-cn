---
title: 创建 Visual Studio 的脱机安装
description: 了解如何在 Internet 连接不可靠或带宽较低时脱机安装 Visual Studio。
ms.custom: ''
ms.date: 08/28/2018
ms.technology: vs-acquisition
ms.prod: visual-studio-dev15
ms.topic: conceptual
f1_keywords:
- offline installation [Visual Studio]
- offline install [Visual Studio]
- layout [Visual Studio]
ms.assetid: f8625d5e-f6ea-4db0-83c0-619b77fab3cf
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 079416a411af5b5a953bd9cccd03681a4dddaefb
ms.sourcegitcommit: 12d6398c02e818de4fbcb4371bae9e5db6cf9509
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "50050062"
---
# <a name="create-an-offline-installation-of-visual-studio-2017"></a>创建 Visual Studio 2017 脱机安装缓存

Visual Studio 2017 经过精心设计，可在各种网络和计算机配置中良好运行。 虽然我们建议你试用 [Visual Studio Web 安装程序](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)&mdash;这是一个小巧文件，可及时提供最新修补程序和功能&mdash;但我们知道对你而言这也许并不可行。

例如，你的 Internet 连接不可靠或带宽较低。 如果是这样，可选择：在安装之前使用新的“全部下载后再安装”功能下载文件，或使用命令行创建文件的本地缓存。

> [!NOTE]
> 如果你是企业管理员，并且要将 Visual Studio 2017 部署到客户端工作站网络（与 Internet 之间设有防火墙），请参阅[创建 Visual Studio 2017 的网络安装](../install/create-a-network-installation-of-visual-studio.md)和[安装 Visual Studio 脱机安装所需的证书](../install/install-certificates-for-visual-studio-offline.md)页。

## <a name="use-the-download-all-then-install-feature"></a>使用“全部下载，然后安装”功能

[15.8 中的新增功能](/visualstudio/releasenotes/vs2017-relnotes?context=visualstudio/default&contextView=vs-2017#install
)：下载 Web 安装程序后，从 Visual Studio 安装程序中选择新的“全部下载后再安装”选项********。 然后，继续安装。

   ![“全部下载后再安装”选项](media/download-all-then-install.png)

## <a name="use-the-command-line-to-create-a-local-cache"></a>使用命令行创建本地缓存

下载小型引导程序后，使用命令行创建本地缓存。 然后，使用本地缓存安装 Visual Studio。 （此过程替换了以前版本中可用的 ISO 文件。）

操作方法如下。

### <a name="step-1---download-the-visual-studio-bootstrapper"></a>步骤 1 - 下载 Visual Studio 引导程序

必须具有 Internet 连接才能完成此步骤。

首先，下载选定 Visual Studio 版本的 Visual Studio 引导程序。 安装程序文件&mdash;或引导程序&mdash;将是以下项之一，或与之类似。

| 版本                    | 文件                                                                    |
|----------------------------|-------------------------------------------------------------------------|
| Visual Studio Community    | [vs_community.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=community&rel=15?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2017)       |
| Visual Studio Professional | [vs_professional.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=professional&rel=15?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2017) |
| Visual Studio Enterprise   | [vs_enterprise.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=enterprise&rel=15?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2017)     |

### <a name="step-2---create-a-local-install-cache"></a>步骤 2 - 创建本地安装缓存

必须具有 Internet 连接才能完成此步骤。

> [!IMPORTANT]
> 如果已安装 Visual Studio Community 2017，必须在安装后的 30 天内激活它。 必须连接到 Internet，才能执行此操作。

请打开命令提示符，并使用以下示例中的任一命令。 此处列出的示例假定用户使用的是 Visual Studio 社区版；请根据版本相应调整命令。

- 对于 .NET Web 和.NET 桌面开发，请运行：

   ```vs_community.exe --layout c:\vs2017layout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional --lang en-US```

- 对于 .NET 桌面和 Office 开发，请运行：

   ```vs_community.exe --layout c:\vs2017layout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.Office --includeOptional --lang en-US```

- 对于 C++ 桌面开发，请运行：

   ```vs_community.exe --layout c:\vs2017layout --add Microsoft.VisualStudio.Workload.NativeDesktop --includeRecommended --lang en-US```

- 若要创建包含所有功能的完整本地布局（耗时将很长 &mdash; 我们提供的功能_非常多_！），请运行：

   ```vs_community.exe --layout c:\vs2017layout --lang en-US```

如果要安装非英语语言，请从[语言区域设置列表](#list-of-language-locales)中将 `en-US` 更改为区域设置。 然后，使用此[可用组件和工作负载列表](workload-and-component-ids.md)，进一步自定义安装缓存。

> [!IMPORTANT]
> 完整的 Visual Studio 2017 布局至少需要 35 GB 磁盘空间，可能需要一段时间才能下载完成。 有关如何创建仅具有要安装的组件的布局的信息，请参阅[使用命令行参数安装 Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md)。

### <a name="step-3---install-visual-studio-from-the-local-cache"></a>步骤 3 - 从本地缓存安装 Visual Studio

> [!TIP]
> 当你从本地安装缓存运行时，安装程序会使用其中每个文件的本地版本。 不过，如果在安装过程中选择的组件不在缓存中，安装程序会尝试从 Internet 下载它们。

若要确保仅安装先前下载的文件，请使用在创建布局缓存时所用的相同命令行选项。 例如，如果使用以下命令创建了布局缓存：

```vs_community.exe --layout c:\vs2017layout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional --lang en-US```

然后使用此命令运行安装：

```c:\vs2017layout\vs_community.exe --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional```

> [!NOTE]
> 如果你遇到签名无效的错误，则必须安装更新的证书。 在脱机缓存中打开证书文件夹。 双击每个证书文件，然后单击完成证书管理器向导。 如果要求输入密码，请将密码留空。

### <a name="list-of-language-locales"></a>语言区域设置列表

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

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>请参阅

- [创建 Visual Studio 2017 的网络安装](../install/create-a-network-installation-of-visual-studio.md)
- [安装 Visual Studio 脱机安装所需的证书](../install/install-certificates-for-visual-studio-offline.md)
- [使用命令行参数安装 Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
- [Visual Studio 2017 工作负载和组件 ID](workload-and-component-ids.md)
