---
title: 安装第三方分析器
ms.date: 08/27/2020
description: 了解如何在 Visual Studio 中安装第三方分析器。 请参阅如何在 .vsix 文件和 NuGet 分析器包中安装分析器。
ms.custom: SEO-VS-2020
ms.topic: conceptual
helpviewer_keywords:
- code analysis, managed code
- analyzers
- Roslyn analyzers
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 93cd01c0a90f2864843549c3ce11e066a16a8843
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/25/2020
ms.locfileid: "96040376"
---
# <a name="install-third-party-analyzers"></a>安装第三方分析器

Visual Studio 包含一组 .NET Compiler Platform (*Roslyn*) 分析器的核心。 这些分析器始终打开。 可以将其他分析器安装为 NuGet 包，或者安装为 *VSIX* 文件中的 Visual Studio 扩展。

## <a name="to-install-nuget-analyzer-packages"></a>安装 NuGet 分析器包

1. 查找要安装在 www.nuget.org 上的分析器包。

   例如，你可能需要安装 [StyleCop](https://www.nuget.org/packages/stylecop.analyzers/) 来查找代码库中的样式问题。

2. 使用 [包管理器控制台](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console) 或 [包管理器 UI](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console)，在 Visual Studio 中安装包。

   > [!NOTE]
   > 每个分析器包的 "www.nuget.org" 页将显示要粘贴到 **包管理器控制台** 中的命令。 还有一个用于将文本复制到剪贴板的方便的按钮。

   分析器程序集安装并显示在 **引用** 分析器下的 **解决方案资源管理器** 中  >  **Analyzers**。

## <a name="to-install-vsix-analyzers"></a>安装 VSIX 分析器

::: moniker range="vs-2017"

1. 在 Visual Studio 中，选择 " **工具**" " > **扩展和更新**"。

   此时，“扩展和更新”对话框打开。

   > [!NOTE]
   > 另外，还可以从 [Visual Studio Marketplace](https://marketplace.visualstudio.com)中直接查找并下载分析器扩展。

::: moniker-end

::: moniker range=">=vs-2019"

1. 在 Visual Studio 中，选择 " **扩展**" " > **管理扩展**"。

   此时将打开 " **管理扩展** " 对话框。

   > [!NOTE]
   > 另外，还可以从 [Visual Studio Marketplace](https://marketplace.visualstudio.com)中直接查找并下载分析器扩展。

::: moniker-end

2. 在左窗格中展开 " **联机** "，然后选择 " **Visual Studio Marketplace**"。

3. 在 "搜索" 框中，键入要安装的分析器扩展的名称。

4. 选择“下载”。

   此扩展已下载。

5. 选择 **"确定"** 关闭对话框，然后关闭 Visual Studio 的所有实例以启动 **VSIX 安装程序**。

   此时将打开 " **VSIX 安装程序** " 对话框。

   ![适用于 Microsoft 代码分析的 VSIX 安装程序](media/vsix-installer-code-analysis.png)

6. 选择 " **修改** " 以启动安装。

7. 一分钟或两分钟后，安装完成。 选择“关闭”。

8. 重新打开 Visual Studio。

::: moniker range="vs-2017"

如果要检查是否安装了扩展，请选择 "**工具**" "  >  **扩展和更新**"。 在 " **扩展和更新** " 对话框中，选择左侧的 " **已安装** " 类别，然后按名称搜索扩展。

::: moniker-end

::: moniker range=">=vs-2019"

如果要检查是否安装了扩展，请选择 "**扩展**" "  >  **管理扩展**"。 在 " **管理扩展** " 对话框中，选择左侧的 " **已安装** " 类别，然后按名称搜索扩展。

::: moniker-end

## <a name="next-steps"></a>后续步骤

> [!div class="nextstepaction"]
> [在 Visual Studio 中使用代码分析器](../code-quality/use-roslyn-analyzers.md)

## <a name="see-also"></a>请参阅

- [Visual Studio 中的代码分析器概述](../code-quality/roslyn-analyzers-overview.md)
- [安装 .NET 分析器](../code-quality/install-net-analyzers.md)
