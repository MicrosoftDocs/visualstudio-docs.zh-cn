---
title: 创建脱机安装
description: 了解如何在 Internet 连接不可靠或带宽较低时脱机安装 Visual Studio。
ms.date: 10/22/2019
ms.custom: seodec18
ms.topic: conceptual
f1_keywords:
- offline installation [Visual Studio]
- offline install [Visual Studio]
- layout [Visual Studio]
ms.assetid: f8625d5e-f6ea-4db0-83c0-619b77fab3cf
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 2e4a7e0f9335971bb026ccc1c6b977680d9e3121
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2021
ms.locfileid: "99949553"
---
# <a name="create-an-offline-installation-of-visual-studio"></a>创建 Visual Studio 的脱机安装

::: moniker range="vs-2017"

Visual Studio 2017 经过精心设计，可在各种网络和计算机配置中良好运行。 虽然我们建议你试用 [Visual Studio Web 安装程序](https://visualstudio.microsoft.com/vs/older-downloads)&mdash;这是一个小巧文件，可及时提供最新修补程序和功能&mdash;但我们知道对你而言这也许并不可行。

::: moniker-end

::: moniker range="vs-2019"

Visual Studio 2019 经过精心设计，可在各种网络和计算机配置中良好运行。 虽然我们建议你试用 [Visual Studio Web 安装程序](https://visualstudio.microsoft.com/downloads)&mdash;这是一个小巧文件，可及时提供最新修补程序和功能&mdash;但我们知道对你而言这也许并不可行。

::: moniker-end

例如，你的 Internet 连接不可靠或带宽较低。 如果是这样，可选择：在安装之前使用新的“全部下载后再安装”功能下载文件，或使用命令行创建文件的本地缓存。

> [!NOTE]
> 如果你是企业管理员，并且要将 Visual Studio 部署到客户端工作站网络（与 Internet 之间设有防火墙），请参阅[创建 Visual Studio 的网络安装](../install/create-a-network-installation-of-visual-studio.md)和[安装 Visual Studio 脱机安装所需的证书](../install/install-certificates-for-visual-studio-offline.md)页面。

## <a name="use-the-download-all-then-install-feature"></a>使用“全部下载，然后安装”功能

::: moniker range="vs-2017"

[**15.8 版的新增功能**](/visualstudio/releasenotes/vs2017-relnotes-v15.8#install)：下载 Web 安装程序后，从 Visual Studio 安装程序中选择新的“全部下载后再安装”选项  。 然后，继续安装。

   ![“全部下载后再安装”选项](media/download-all-then-install.png)

::: moniker-end

::: moniker range="vs-2019"

下载 Web 安装程序后，从 Visual Studio 安装程序中选择新的“全部下载后再安装”选项  。 然后，继续安装。

   ![“全部下载后再安装”选项](media/vs-2019/download-all-then-install-from-installer.png)

::: moniker-end

我们设计了“全部下载后再安装”功能，以便为进行下载的同一台计算机下载 Visual Studio 作为一个单独安装。 这样就可以在安装 Visual Studio 之前安全断开 Web。

> [!IMPORTANT]
> 请勿使用“全部下载后再安装”功能来创建要传输到另一台计算机的脱机缓存。 这不是该功能的运作方式。 <br><br>如果要创建脱机缓存以在另一台计算机上安装 Visual Studio，请参阅本页面的[使用命令行创建本地缓存](#use-the-command-line-to-create-a-local-cache)部分，了解有关如何创建本地缓存的信息，或参阅[创建 Visual Studio 的网络安装](../install/create-a-network-installation-of-visual-studio.md)页面，了解有关如何创建网络缓存的信息。

## <a name="use-the-command-line-to-create-a-local-cache"></a>使用命令行创建本地缓存

下载小型引导程序后，使用命令行创建本地缓存。 然后，使用本地缓存安装 Visual Studio。 （此过程替换了以前版本中可用的 ISO 文件。）

操作方法如下。

### <a name="step-1---download-the-visual-studio-bootstrapper"></a>步骤 1 - 下载 Visual Studio 引导程序

必须具有 Internet 连接才能完成此步骤。

::: moniker range="vs-2017"

若要获取 Visual Studio 2017 的引导程序，请参阅 [Visual Studio 早期版本](https://visualstudio.microsoft.com/vs/older-downloads/)下载页，获取关于如何执行此操作的详细信息。

安装程序可执行文件&mdash;具体而言是引导程序文件&mdash;应与下面其中一项匹配，或与之类似。

| 版本 | Filename |
|-------------|-----------------------|
|Visual Studio Community | vs_community.exe |
|Visual Studio Professional | vs_professional.exe |
|Visual Studio Enterprise | vs_enterprise.exe |
|Visual Studio 生成工具   | vs_buildtools.exe |

::: moniker-end

::: moniker range="vs-2019"

首先，下载选定 Visual Studio 版本的 Visual Studio 引导程序。 安装程序文件&mdash;或引导程序&mdash;将是以下项之一，或与之类似。

| 版本                    | 文件                                                                    |
|----------------------------|-------------------------------------------------------------------------|
| Visual Studio Community    | [vs_community.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=community&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2019)       |
| Visual Studio Professional | [vs_professional.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=professional&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2019) |
| Visual Studio Enterprise   | [vs_enterprise.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=enterprise&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2019)     |
| Visual Studio 生成工具   | [vs_buildtools.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=buildtools&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2019)     |

::: moniker-end

>[!TIP]
>如果以前下载过引导程序文件，并且想要验证其版本，则操作方法如下。 在 Windows 中，打开文件资源管理器，右键单击引导程序文件，依次选择“属性”、“详细信息”选项卡，然后查看“产品版本”号    。 若要将该编号与 Visual Studio 的版本匹配，请参阅 [Visual Studio 内部版本号和发布日期](visual-studio-build-numbers-and-release-dates.md)页。

### <a name="step-2---create-a-local-install-cache"></a>步骤 2 - 创建本地安装缓存

必须具有 Internet 连接才能完成此步骤。

> [!IMPORTANT]
> 如果已安装 Visual Studio Community，必须在安装后的 30 天内激活它。 必须连接到 Internet，才能执行此操作。

请打开命令提示符，并使用以下示例中的任一命令。 此处列出的示例假定用户使用的是 Visual Studio 社区版；请根据版本相应调整命令。

> [!TIP]
> 为了防止错误出现，请确保完全安装路径的长度小于 80 个字符。

- 对于 .NET Web 和.NET 桌面开发，请运行：

   ```cmd
    vs_community.exe --layout c:\vslayout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional --lang en-US
    ```

- 对于 .NET 桌面和 Office 开发，请运行：

   ```cmd
    vs_community.exe --layout c:\vslayout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.Office --includeOptional --lang en-US
    ```

- 对于 C++ 桌面开发，请运行：

   ```cmd
    vs_community.exe --layout c:\vslayout --add Microsoft.VisualStudio.Workload.NativeDesktop --includeRecommended --lang en-US
    ```

- 若要创建包含所有功能的完整本地布局（耗时将很长 &mdash; 我们提供的功能 _非常多_！），请运行：

   ```cmd
    vs_community.exe --layout c:\vslayout --lang en-US
    ```

::: moniker range="vs-2017"

   > [!NOTE]
   > 完整的 Visual Studio 布局至少需要 35 GB 磁盘空间。 有关详细信息，请参阅[系统要求](/visualstudio/productinfo/vs2017-system-requirements-vs/)。 要了解如何创建仅包含要安装的组件的布局，请参阅[使用命令行参数安装 Visual Studio](use-command-line-parameters-to-install-visual-studio.md)。

::: moniker-end

::: moniker range="vs-2019"

   > [!NOTE]
   > 完整的 Visual Studio 布局至少需要 35 GB 磁盘空间。 有关详细信息，请参阅[系统要求](/visualstudio/releases/2019/system-requirements/)。 要了解如何创建仅包含要安装的组件的布局，请参阅[使用命令行参数安装 Visual Studio](use-command-line-parameters-to-install-visual-studio.md)。

::: moniker-end

如果要安装非英语语言，请从[语言区域设置列表](#list-of-language-locales)中将 `en-US` 更改为区域设置。 然后，使用此[可用组件和工作负载列表](workload-and-component-ids.md)，进一步自定义安装缓存。

### <a name="step-3---install-visual-studio-from-the-local-cache"></a>步骤 3 - 从本地缓存安装 Visual Studio

> [!TIP]
> 当你从本地安装缓存运行时，安装程序会使用其中每个文件的本地版本。 不过，如果在安装过程中选择的组件不在缓存中，安装程序会尝试从 Internet 下载它们。

::: moniker range="vs-2019"
> [!IMPORTANT]
> 对于脱机安装，如果收到一条错误消息，指出“找不到与以下参数匹配的项目”，请确保将 `--noweb` 开关用于版本 16.3.5 或更高版本。
>
::: moniker-end

若要确保仅安装先前下载的文件，请使用在创建布局缓存时所用的相同命令行选项。 例如，如果使用以下命令创建了布局缓存：

```cmd
vs_community.exe --layout c:\vslayout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional --lang en-US
```

然后使用此命令运行安装：

```cmd
c:\vslayout\vs_community.exe --noweb --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional
```

有关如何使用[命令行参数](use-command-line-parameters-to-install-visual-studio.md)的更多示例，请参阅 [Visual Studio 安装的命令行参数示例](command-line-parameter-examples.md)页面。 

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

- [创建 Visual Studio 的网络安装](../install/create-a-network-installation-of-visual-studio.md)
- [更新基于网络的 Visual Studio 安装](update-a-network-installation-of-visual-studio.md)
- [安装 Visual Studio 脱机安装所需的证书](../install/install-certificates-for-visual-studio-offline.md)
- [使用命令行参数安装 Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
- [Visual Studio 工作负荷和组件 ID](workload-and-component-ids.md)
