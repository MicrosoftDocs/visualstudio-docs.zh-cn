---
title: 如何： 将扩展性项目迁移到 Visual Studio 2017 |Microsoft Docs
ms.custom: ''
ms.date: 11/09/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 8ca07b00-a3ff-40ab-b647-c0a93b55e86a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 669f3625827d923a0951caa1bb0137d38c0daacc
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/08/2018
ms.locfileid: "39637492"
---
# <a name="how-to-migrate-extensibility-projects-to-visual-studio-2017"></a>如何： 将扩展性项目迁移到 Visual Studio 2017

本文档介绍如何将扩展性项目升级到 Visual Studio 2017。 除了介绍如何更新项目文件，它还介绍了如何从扩展清单版本 2 (VSIX v2) 升级到新的版本 3 VSIX 清单格式 (VSIX v3)。

## <a name="install-visual-studio-2017-with-required-workloads"></a>使用所需的工作负荷安装 Visual Studio 2017

请确保您的安装包括以下工作负荷：

* .NET 桌面开发
* Visual Studio 扩展开发

## <a name="open-vsix-solution-in-visual-studio-2017"></a>在 Visual Studio 2017 中打开 VSIX 解决方案

所有的 VSIX 项目将需要主版本单向升级到 Visual Studio 2017。

项目文件 (例如 **.csproj*) 将更新：

* MinimumVisualStudioVersion-现在将设置为 15.0
* OldToolsVersion (如果以前存在)-现在将设置为 14.0

## <a name="update-the-microsoftvssdkbuildtools-nuget-package"></a>Microsoft.VSSDK.BuildTools NuGet 包更新

>**注意：** 如果你的解决方案不引用 Microsoft.VSSDK.BuildTools NuGet 包，可以跳过此步骤。

若要生成新的 VSIX v3 中扩展 （版本 3） 格式，你的解决方案将需要使用新的 VSSDK 生成工具生成。 此功能将安装使用 Visual Studio 2017，但您的 VSIX v2 扩展可能会保存到通过 NuGet 较旧版本的引用。 如果是这样，您将需要手动安装用于你的解决方案的 Microsoft.VSSDK.BuildTools NuGet 包的更新。

若要更新到 Microsoft.VSSDK.BuildTools NuGet 引用：

* 右键单击解决方案并选择**为解决方案管理 NuGet 包**。
* 导航到**更新**选项卡。
* 选择**Microsoft.VSSDK.BuildTools （最新版本）**。
* 按**更新**。

![VSSDK 生成工具](media/vssdk-build-tools.png)

## <a name="make-changes-to-the-vsix-extension-manifest"></a>对 VSIX 扩展清单进行更改

若要确保 Visual Studio 的用户的安装已运行扩展所需的所有程序集，请扩展清单文件中指定的所有系统必备组件或包。 当用户尝试安装该扩展时，vsixinstaller 找将检查是否已安装所有必备组件。 如果有一些丢失，将提示用户安装缺少的组件作为扩展安装过程的一部分。

>**注意：** 至少，所有扩展应作为必备组件都指定 Visual Studio 核心编辑器组件。

* 编辑扩展清单文件 (通常称为*source.extension.vsixmanifest*)。
* 确保`InstallationTarget`包括 15.0。
* 添加所需的安装必备组件 （如下面的示例中所示）。
  * 我们建议您指定仅组件的安装必备组件的 Id。
  * 请参阅本文档末尾[标识组件 Id 的说明](#find-component-ids)。

示例:

```xml
<PackageManifest>
 ...
    <Prerequisites>
        <Prerequisite Id="Microsoft.VisualStudio.Component.CoreEditor" Version="[15.0,16.0)" />
        <Prerequisite Id="Microsoft.VisualStudio.Component.DiagnosticTools" Version="[15.0.25814.0,16.0)" />
        <Prerequisite Id="Microsoft.VisualStudio.Shell.12.0" Version="[12.0]" />
    </Prerequisites>
 ...
</PackageManifest>
```

### <a name="option-use-the-designer-to-make-changes-to-the-vsix-extension-manifest"></a>选项： 使用设计器对 VSIX 扩展清单进行更改

而不是直接编辑清单 XML，可以使用新**先决条件**将为你更新清单设计器选择必备组件和 XML 的选项卡。

>**注意：** 清单设计器将仅允许您选择当前的 Visual Studio 实例安装的组件 （不工作负荷或包）。 如果需要添加为工作负荷、 包或当前未安装的组件的必备组件，请直接编辑清单 XML。

* 打开*source.extension.vsixmanifest [设计]* 文件。
* 选择**先决条件**选项卡并按**新建**按钮。

  ![VSIX 清单设计器](media/vsix-manifest-designer.png)

* **添加新先决条件**窗口将打开。

  ![添加 vsix 必备组件](media/add-vsix-prerequisite.png)

* 单击下拉列表**名称**，然后选择所需的必备组件。
* 如果需要，更新的版本。

  >注意: 版本字段将使用当前安装的组件，与范围最多跨越 （但不是包括） 的版本的预填充下一个主要版本的组件。

  ![添加 roslyn 必备组件](media/add-roslyn-prerequisite.png)

* 按**确定**。

## <a name="update-debug-settings-for-the-project"></a>更新项目的调试设置

如果你想要调试你的 Visual Studio 实验实例中的扩展，请确保项目设置**调试** > **启动操作**具有**启动外部程序：** 值设置为*devenv.exe* Visual Studio 2017 安装的文件。

它可能如下所示： *C:\Program Files (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\IDE\devenv.exe*

![启动外部程序](media/start-external-program.png)

>**注意：** 调试启动操作通常存储在 *。 csproj.user*文件。 此文件通常包括在 *.gitignore*文件，并因此，通常不会保存与其他项目文件时提交到源代码管理。 在这种情况下，如果已经读取你的解决方案从源代码管理全新很可能此项目将具有为启动操作设置的任何值。 使用 Visual Studio 2017 创建的新 VSIX 项目将具有 *。 csproj.user*文件创建包含指向当前 Visual Studio 安装目录的默认值。 但是如果要迁移 v2 VSIX 扩展，则很可能该 *。 csproj.user*文件将包含到上一 Visual Studio 版本的安装目录的引用。 值设置**调试** > **启动操作**将允许正确的 Visual Studio 实验实例启动时尝试调试您的扩展插件。

## <a name="check-that-the-extension-builds-correctly-as-a-vsix-v3"></a>检查扩展构建正确 （作为 VSIX v3)

* 生成 VSIX 项目。
* 将解压缩生成的 VSIX 中。
  * 默认情况下，VSIX 文件位于*bin/Debug*或*bin/Release*作为 *[YourCustomExtension].vsix*。
  * 重命名 *.vsix*到 *.zip*轻松查看内容。
* 检查存在的三个文件：
  * *extension.vsixmanifest*
  * *manifest.json*
  * *catalog.json*

## <a name="check-when-all-required-prerequisites-are-installed"></a>时所有所需的必备项检查

VSIX 将会成功安装在计算机安装所需的所有必备组件使用的测试。

>**注意：** 之前安装任何扩展，请关闭 Visual Studio 的所有实例。

尝试安装该扩展：

* 在 Visual Studio 2017

![在 Visual Studio 2017 的 VSIX 安装程序](media/vsixinstaller-vs-2017.png)

* 可选： 检查以前版本的 Visual Studio。
  * 事实证明，向后兼容性。
  * 应适用于 Visual Studio 2012，Visual Studio 2013，Visual Studio 2015。
* 可选： 检查，VSIX 安装程序版本检查器提供了多种版本。
  * 包括 Visual Studio 的早期版本 （如果已安装）。
  * 包含 Visual Studio 2017。

如果最近打开 Visual Studio，你可能会看到如下对话框：

![与正在运行的进程](media/vs-running-processes.png)

等待进程关闭，或手动结束任务。 所列的名称，或在括号中列出的 PID，您可以找到进程。

>**注意：** 这些进程将不会自动关闭 Visual Studio 实例正在运行时。 请确保已关闭的情况下在计算机中-包括来自其他用户，使用 Visual Studio 的所有实例，然后继续重试。

## <a name="check-when-missing-the-required-prerequisites"></a>时缺少所需的先决条件检查

* 尝试安装该扩展的计算机上使用 Visual Studio 2017，不包含系统必备组件 （上述） 中定义的所有组件。
* 检查安装标识缺少的组件/s 和列表作为 vsixinstaller 找中的必备组件。
* 注意： 如果任何系统必备组件需要安装该扩展程序的提升将是所需。

![vsixinstaller 找缺少的先决条件](media/vsixinstaller-missing-prerequisite.png)

## <a name="decide-on-components"></a>确定组件

当查找依赖项，您会发现一个依赖关系可映射到多个组件。 若要确定哪些依赖项应指定为你的先决条件，我们建议您选择的组件的功能类似于您的扩展插件和同时考虑您的用户和已进行哪种类型的组件的它们很可能已安装或不会介意安装。 我们还建议的构建你的扩展的必备组件，其中满足将允许你运行的扩展的最小的方式和其他功能将处于激活状态，如果某些组件未检测到它们。

若要提供更多指南，我们已确定几个常见的扩展类型和其建议的系统必备组件：

扩展类型 | 显示名称 | Id
--- | --- | ---
编辑器 | Visual Studio 核心编辑器  | Microsoft.VisualStudio.Component.CoreEditor
Roslyn | C# 和 Visual Basic | Microsoft.VisualStudio.Component.Roslyn.LanguageServices
WPF | 托管桌面工作负载核心 | Microsoft.VisualStudio.Component.ManagedDesktop.Core
调试器 | 实时调试器 | Microsoft.VisualStudio.Component.Debugger.JustInTime

## <a name="find-component-ids"></a>查找组件 Id

组件按 Visual Studio 产品排序的列表位于[Visual Studio 2017 工作负载和组件 Id](https://aka.ms/vs2017componentIDs)。 为你先决条件 Id 在清单中使用这些组件 Id。

如果不确定哪个组件包含特定的二进制文件，下载[组件-> 二进制映射电子表格](https://aka.ms/vs2017componentid-binaries)。

### <a name="vs2017-componentbinarymappingxlsx"></a>vs2017 ComponentBinaryMapping.xlsx

Excel 工作表中有四个列：**组件名称**， **ComponentId**，**版本**，以及**二进制 / 文件名称**。  可以使用筛选器来搜索和查找特定组件和二进制文件。

对于所有引用，首先确定哪些是核心编辑器 (Microsoft.VisualStudio.Component.CoreEditor) 组件中。  最小值，我们需要指定为所有扩展的必备组件的核心编辑器组件。 将保留不在核心编辑器中的引用，将添加中的筛选器**二进制文件 / 文件名称**部分，若要查找具有任何这些引用的子集的组件。

示例：

* 如果你有调试器扩展，知道你的项目具有对引用*VSDebugEng.dll*并*VSDebug.dll*，单击筛选器按钮中**二进制文件 / 文件名称**标头。  搜索"VSDebugEng.dll"并选择*确定*。  下一步中的筛选器按钮单击**二进制文件 / 文件名称**再次标头并搜索"VSDebug.dll"。  选中该复选框**添加当前所选内容来筛选**，然后选择**确定**。  现在看**组件名称**查找一个组件，是大多数与您的扩展类型相关。 在此示例中，将选择实时中调试程序并将其添加到你 vsixmanifest。
* 如果您知道您的项目处理调试器元素，可以在"调试器"筛选器搜索框中以查看哪些组件包含在其名称中的调试器中进行搜索。

## <a name="specify-a-visual-studio-2017-release"></a>指定 Visual Studio 2017 版本

如果您的扩展插件需要特定版本的 Visual Studio 2017，例如，这取决于在 15.3 中发布的功能，必须在 vsix 中指定的内部版本号**InstallationTarget**。 例如，版本 15.3 有"15.0.26730.3"内部版本号。 您所见发布生成号的映射[此处](../install/visual-studio-build-numbers-and-release-dates.md)。 使用发行版号"15.3"将无法正常工作。

如果您的扩展插件需要 15.3 或更高版本，则需要声明**InstallationTarget 版本**作为 [15.0.26730.3, 16.0):

```xml
<Installation>
  <InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[15.0.26730.3, 16.0)" />
</Installation>
```