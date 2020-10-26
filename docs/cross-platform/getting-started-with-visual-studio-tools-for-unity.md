---
title: Visual Studio Tools for Unity 入门 | Microsoft Docs
description: Visual Studio Tools for Unity 入门。 安装 Visual Studio，配置 Unity 以与 Visual Studio 一起使用，并了解对较旧版本的支持。
ms.custom: ''
ms.date: 05/11/2020
ms.technology: vs-unity-tools
ms.topic: how-to
ms.assetid: 66b5b4eb-13b5-4071-98d2-87fafa4598a8
author: indiesaudi
ms.author: crdun
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: 223458a448a4b32c3e9480f7189d5dc636ce8375
ms.sourcegitcommit: 01c1b040b12d9d43e3e8ccadee20d6282154faad
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/14/2020
ms.locfileid: "92039446"
---
# <a name="get-started-with-visual-studio-tools-for-unity"></a>Visual Studio Tools for Unity 入门

## <a name="install-visual-studio"></a>安装 Visual Studio

### <a name="unity-bundled-installation"></a>Unity 捆绑安装

从 Unity 2018.1 开始，Visual Studio 是 Unity 的默认 C# 脚本编辑器，并且包含在 Unity 下载助手以及 Unity Hub 安装工具中。

- 前往 [store.unity.com](https://store.unity.com/) 下载 Unity。

在安装过程中，请确保在要与 Unity 一起安装的组件列表中选中 Visual Studio ：

#### <a name="unity-hub"></a>Unity Hub

:::moniker range="vs-2017"
![unity 中心安装](media/vs-2017/vstu-unity-hub.png)
:::moniker-end
:::moniker range=">=vs-2019"
![unity 中心安装](media/vs-2019/vstu-unity-hub.png)
:::moniker-end

:::moniker range="vs-2017"

#### <a name="unity-download-assistant"></a>Unity 下载助手

![unity 下载助手安装](media/vs-2017/vstu-download-assistant.png)

随附于 Unity 安装的 Visual Studio 版本可能不是最新版本。 如果要求安装 Visual Studio 2017，建议手动安装较新版本的 Visual Studio。
:::moniker-end

### <a name="manual-installation"></a>手动安装

如果已安装 Visual Studio 或者希望手动安装，请运行 Visual Studio 安装程序。

1. [下载 Visual Studio 安装程序](../install/install-visual-studio.md)，如已安装，则打开它。

1. 为所需的 Visual Studio 版本单击“修改”（如已安装）或“安装”（适用于新安装）。

1. 在“工作负载”选项卡上，滚动到“移动和游戏”部分，并选择“使用 Unity 的游戏开发”工作负载。

   :::moniker range="vs-2017"
   ![Unity 工作负载](media/vs-2017/vstu-unity-workload.png)
   :::moniker-end
   :::moniker range=">=vs-2019"
   ![Unity 工作负载](media/vs-2019/vstu-unity-workload.png)
   :::moniker-end

1. 单击安装程序窗口右下角的“修改”（如已安装）或“安装”（适用于新安装）。

#### <a name="check-for-updates-to-visual-studio"></a>检查 Visual Studio 的更新

建议检查 Visual Studio 中的更新，确保可访问最新工具和功能。 这不会中断 Unity 项目。

- [更新 Visual Studio](../install/update-visual-studio.md)

## <a name="configure-unity-for-use-with-visual-studio"></a>配置 Unity 以与 Visual Studio 一起使用

自 Unity 2018.1 起，Visual Studio 应为 Unity 的默认外部脚本编辑器。 可以确认下是否如此，或者将外部脚本编辑器更改为特定版本的 Visual Studio：

1. 从 **Edit** 菜单选择 **Preferences** 。

   :::moniker range="vs-2017"
   ![选择首选项](media/vs-2017/vstu-unity-preferences.png)
   :::moniker-end
   :::moniker range=">=vs-2019"
   ![选择首选项](media/vs-2019/vstu-unity-preferences.png)
   :::moniker-end

2. 在“Preferences”对话框中，选择“External Tools”选项卡。

3. 从 **External Script Editor** 下拉列表中，选择所需版本的 Visual Studio（如果列出此项），否则选择 **Browse...** 。

   :::moniker range="vs-2017"
   ![选择 Visual Studio](media/vs-2017/vstu-unity-external-tools.png)
   :::moniker-end
   :::moniker range=">=vs-2019"
   ![选择 Visual Studio](media/vs-2019/vstu-unity-external-tools.png)
   :::moniker-end

4. 如果已选择 **Browse...** ，请导航到 Visual Studio 安装目录中的 **Common7/IDE** 目录，然后选择 **devenv.exe** 。 然后单击 **Open** 。

   :::moniker range="vs-2017"
   ![选择“打开”](media/vs-2017/vstu-browse-for-application.png)
   :::moniker-end
   :::moniker range=">=vs-2019"
   ![选择“打开”](media/vs-2019/vstu-browse-for-application.png)
   :::moniker-end

5. 在 **External Script Editor** 列表中选择 Visual Studio 后，确认已选中 **Editor Attaching** 复选框。

6. 关闭 **Preferences** 对话框以完成配置过程。

## <a name="support-for-older-versions"></a>支持旧版本

从 Visual Studio Marketplace 下载并安装 Visual Studio Tools for Unity。 你需要安装所用 Visual Studio 版本的正确软件包。

- 对于 Visual Studio 2015 Community、Visual Studio 2015 Professional 或 Visual Studio 2015 Enterprise：

   [下载 Visual Studio 2015 Tools for Unity](https://marketplace.visualstudio.com/items?itemName=SebastienLebreton.VisualStudio2015ToolsforUnity)

> [!NOTE]
> Visual Studio Tools for Unity 要求 Unity 5.2 和更高版本，以及支持扩展的 Visual Studio 版本，例如，Visual Studio Community、Professional、Premium 或 Enterprise。 若要验证你安装的 Unity 是否启用了 Visual Studio Tools for Unity，请从“帮助”菜单中选择“关于 Unity”，并在对话框左下角查看“Microsoft Visual Studio Tools for Unity 已启用”文本。
> ![关于 Unity](media/vs-2019/vstu-about-unity.png)

## <a name="next-steps"></a>后续步骤

 要学习如何在 Visual Studio 中使用和调试 Unity 项目，请参阅 [Visual Studio Tools for Unity](../cross-platform/using-visual-studio-tools-for-unity.md)。
