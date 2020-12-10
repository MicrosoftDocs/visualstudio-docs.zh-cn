---
title: 如何往返扩展
description: 了解如何使 Visual Studio 扩展性项目在 Visual Studio 2015 和 Visual Studio 2019 或 Visual studio 2017 之间往返。
ms.custom: SEO-VS-2020
ms.date: 06/25/2017
ms.topic: how-to
ms.assetid: 2d6cf53c-011e-4c9e-9935-417edca8c486
author: willbrown
ms.author: madsk
manager: justinclareburt
ms.workload:
- willbrown
ms.openlocfilehash: 3db3264bf5226b5679452659928e451e7975b001
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/10/2020
ms.locfileid: "96993609"
---
# <a name="how-to-make-extensions-compatible-with-visual-studio-20192017-and-visual-studio-2015"></a>如何：使扩展与 Visual Studio 2019/2017 和 Visual Studio 2015 兼容

本文档介绍如何在 Visual Studio 2015 和 Visual Studio 2019 或 Visual studio 2017 之间进行扩展。 完成此升级后，项目将能够在 Visual Studio 2015 和 Visual Studio 2019 或2017中打开、生成、安装和运行。 作为参考，可以在 [VS SDK 扩展性示例](https://github.com/Microsoft/VSSDK-Extensibility-Samples)中找到可以在 visual studio 2015 和 visual studio 2019 或2017之间往返的一些扩展。

如果只打算在 Visual Studio 2019/2017 中生成，但希望输出 VSIX 在 Visual Studio 2015 和 Visual Studio 2019/2017 中运行，请参阅 [扩展迁移文档](how-to-migrate-extensibility-projects-to-visual-studio-2017.md)。

> [!NOTE]
> 由于 Visual Studio 在版本之间发生了更改，因此在一个版本中使用的某些功能在另一个版本中不起作用。 确保你尝试访问的功能在两个版本中均可用，或者扩展将产生意外的结果。

下面是你将在此文档中完成的步骤的大纲，用于往返 VSIX：

1. 导入正确的 NuGet 包。
2. 更新扩展清单：
    * 安装目标
    * 先决条件
3. 更新 .Csproj：
    * 更新 `<MinimumVisualStudioVersion>`。
    * 添加 `<VsixType>` 属性。
    * 添加调试属性 `($DevEnvDir)` 3 次。
    * 添加导入生成工具和目标的条件。

4. 生成和测试

## <a name="environment-setup"></a>环境设置

本文档假定计算机上已安装以下各项：

* 安装了 VS SDK 的 Visual Studio 2015
* 安装了扩展性工作负载的 Visual Studio 2019 或2017

## <a name="recommended-approach"></a>推荐的方法

强烈建议使用 Visual Studio 2015 而不是 Visual Studio 2019 或2017开始此次升级。 在 Visual Studio 2015 中进行开发的主要好处是确保不引用 Visual Studio 2015 中没有的程序集。 如果你在 Visual Studio 2019 或2017中进行开发，则你可能会在仅存在于 Visual Studio 2019 或2017中的程序集上引入依赖关系。

## <a name="ensure-there-is-no-reference-to-projectjson"></a>确保没有对 project.js的引用

稍后在本文档中，我们将向你的 **.csproj* 文件中插入条件导入语句。 如果 NuGet 引用存储在 *project.js上*，则此操作不起作用。 因此，建议将所有 NuGet 引用移动到 *packages.config* 文件中。
如果项目包含文件 *上的project.js* ：

* 记下 *project.js上* 的引用。
* 从 **解决方案资源管理器** 中，从项目中删除文件 *project.js* 。 这会删除文件 *上的project.js* ，并将其从项目中删除。
* 将 NuGet 引用添加回项目：
  * 右键单击 **解决方案** ，然后选择 " **管理解决方案的 NuGet 包**"。
  * Visual Studio 将自动为你创建 *packages.config* 文件。

> [!NOTE]
> 如果你的项目包含 EnvDTE 包，则可能需要通过右键单击 " **引用** "，选择 " **添加引用** " 并添加相应的引用来添加它们。 在尝试生成项目时，使用 NuGet 包可能会产生错误。

## <a name="add-appropriate-build-tools"></a>添加适当的生成工具

我们需要确保添加使我们能够相应地生成和调试的生成工具。 Microsoft 为此名为 VisualStudio 的程序集创建了一个程序集。

若要在 Visual Studio 2015 和2019/2017 中生成和部署 VSIXv3，你将需要以下 NuGet 包：

版本 | 构建的工具
--- | ---
Visual Studio 2015 | VisualStudio. BuildTasks。
Visual Studio 2019 或2017 | VSSDK. BuildTool

为此，请执行以下操作：

* 将 NuGet 包 VisualStudio 添加到你的项目。
* 如果你的项目不包含 VSSDK，请添加它。
* 确保 BuildTools 版本为 15. x 或更高版本。

## <a name="update-extension-manifest"></a>更新扩展清单

### <a name="1-installation-targets"></a>1. 安装目标

我们需要告诉 Visual Studio 要以何种版本来生成 VSIX。 通常，这些参考是 14.0 (Visual Studio 2015) ，版本 15.0 (Visual Studio 2017) 或版本 16.0 (Visual Studio 2019) 。 在我们的示例中，我们想要生成一个将为这两个版本都安装扩展的 VSIX，因此我们需要将这两个版本作为目标。 如果希望 VSIX 在14.0 以前的版本上生成并安装，可以通过设置较早的版本号来实现;但不再支持版本10.0 和更早版本。

* 在 Visual Studio 中打开 *source.extension.vsixmanifest* 文件。
* 打开 " **安装目标** " 选项卡。
* 将 **版本范围** 更改为 [14.0，17.0) 。 "[" 告诉 Visual Studio 包含14.0 以及它以前的所有版本。 ") " 通知 Visual Studio 包含版本17.0 之前的所有版本，但不包括版本。
* 保存所有更改并关闭 Visual Studio 的所有实例。

![安装目标映像](media/visual-studio-installation-targets-example.png)

### <a name="2-adding-prerequisites-to-the-extensionvsixmanifest-file"></a>2. 将先决条件添加到 *source.extension.vsixmanifest* 文件

我们需要 Visual Studio 核心编辑器作为必备组件。 打开 Visual Studio，并使用更新的清单设计器插入必备组件。

若要手动执行此操作：

* 在文件资源管理器中导航到项目目录。
* 使用文本编辑器打开 *source.extension.vsixmanifest* 文件。
* 添加以下标记：

```xml
<Prerequisites>
    <Prerequisite Id="Microsoft.VisualStudio.Component.CoreEditor" Version="[15.0,16.0)" DisplayName="Visual Studio core editor" />
</Prerequisites>
```

* 保存并关闭该文件。

> [!NOTE]
> 你可能需要手动编辑必备版本，以确保它与所有版本的 Visual Studio 2019 或2017兼容。 这是因为设计器会将最小版本作为 Visual Studio 的当前版本插入 (例如，15.0.26208.0) 。 但是，因为其他用户可能有较早的版本，你需要手动将其编辑为15.0。

此时，清单文件应如下所示：

![先决条件示例](media/visual-studio-prerequisites-example.png)

## <a name="modify-the-project-file-myprojectcsproj"></a> (myproject 修改项目文件) 

在执行此步骤的同时，强烈建议对修改后的 .csproj 打开引用。 可在 [此处](https://github.com/Microsoft/VSSDK-Extensibility-Samples)找到几个示例。 选择任何扩展性示例，查找 *.csproj* 文件以供参考并执行以下步骤：

* 在 **文件资源管理器** 中导航到项目目录。
* 使用文本编辑器打开 *myproject* 文件。

### <a name="1-update-the-minimumvisualstudioversion"></a>1. 更新 I o n

* 将最小 visual studio 版本设置为 `$(VisualStudioVersion)` ，并为其添加一个条件语句。 如果这些标记不存在，请添加它们。 确保标记设置如下：

```xml
<VisualStudioVersion Condition="'$(VisualStudioVersion)' == ''">14.0</VisualStudioVersion>
<MinimumVisualStudioVersion>$(VisualStudioVersion)</MinimumVisualStudioVersion>
```

### <a name="2-add-the-vsixtype-property"></a>2. 添加 VsixType 属性。

* 将以下标记添加 `<VsixType>v3</VsixType>` 到属性组。

> [!NOTE]
> 建议在标记的下面添加 `<OutputType></OutputType>` 。

### <a name="3-add-the-debugging-properties"></a>3. 添加调试属性

* 添加以下属性组：

```xml
<PropertyGroup>
    <StartAction>Program</StartAction>
    <StartProgram>$(DevEnvDir)devenv.exe</StartProgram>
    <StartArguments>/rootsuffix Exp</StartArguments>
</PropertyGroup>
```

* 从 *.csproj* 文件和任何 *.csproj* 文件中删除以下代码示例的所有实例：

```xml
<StartAction>Program</StartAction>
<StartProgram>$(ProgramFiles)\Microsoft Visual Studio 14.0\Common7\IDE\devenv.exe</StartProgram>
<StartArguments>/rootsuffix Exp</StartArguments>
```

### <a name="4-add-conditions-to-the-build-tools-imports"></a>4. 向生成工具导入添加条件

* 将其他条件语句添加到 `<import>` 具有 VSSDK 引用的标记。 `'$(VisualStudioVersion)' != '14.0' And`在 condition 语句的前面插入。 这些语句将显示在 .csproj 文件的页眉和页脚中。

例如：

```xml
<Import Project="packages\Microsoft.VSSDK.BuildTools.15.0.26201…" Condition="'$(VisualStudioVersion)' != '14.0' And Exists(…" />
```

* 将其他条件语句添加到 `<import>` 具有 VisualStudio 的标记中。 `'$(VisualStudioVersion)' == '14.0' And`在 condition 语句的前面插入。 这些语句将显示在 .csproj 文件的页眉和页脚中。

例如：

```xml
<Import Project="packages\Microsoft.VisualStudio.Sdk.BuildTasks.14.0.14.0…" Condition="'$(VisualStudioVersion)' == '14.0' And Exists(…" />
```

* 将其他条件语句添加到 `<Error>` 具有 VSSDK 引用的标记。 为此，请 `'$(VisualStudioVersion)' != '14.0' And` 在 condition 语句的前面插入。 这些语句将显示在 .csproj 文件的页脚中。

例如：

```xml
<Error Condition="'$(VisualStudioVersion)' != '14.0' And Exists('packages\Microsoft.VSSDK.BuildTools.15.0.26201…" />
```

* 将其他条件语句添加到 `<Error>` 具有 VisualStudio 的标记中。 `'$(VisualStudioVersion)' == '14.0' And`在 condition 语句的前面插入。 这些语句将显示在 .csproj 文件的页脚中。

例如：

```xml
<Error Condition="'$(VisualStudioVersion)' == '14.0' And Exists('packages\Microsoft.VisualStudio.Sdk.BuildTasks.14.0.14.0…" />
```

* 保存 .csproj 文件并将其关闭。 
  * 请注意，如果您在解决方案中使用多个项目，请在项目上下文菜单上使用 "设为启动项目" 将此项目设置为启动项目) 。 这可确保在卸载此项目后，Visual Studio 将重新打开它。

## <a name="test-the-extension-installs-in-visual-studio-2015-and-visual-studio-2019-or-2017"></a>测试在 Visual Studio 2015 和 Visual Studio 2019 或2017中安装的扩展

此时，你的项目应准备好生成可在 Visual Studio 2015 和 Visual Studio 2017 上安装的 VSIXv3。

* 在 Visual Studio 2015 中打开你的项目。
* 生成项目，并在输出中确认 VSIX 生成正确。
* 导航到项目目录。
* 打开 *\bin\Debug* 文件夹。
* 双击 VSIX 文件，并在 Visual Studio 2015 和 Visual Studio 2019/2017 上安装扩展。
* 请确保在  >  "**已安装**" 部分的 "工具 **扩展和更新**" 中可以看到该扩展。
* 尝试运行/使用该扩展来检查它是否正常工作。

![查找 VSIX](media/finding-a-VSIX-example.png)

> [!NOTE]
> 如果项目在 **打开文件** 时停止响应，请强制关闭 Visual Studio，导航到项目目录，显示隐藏文件夹，然后删除 *. vs* 文件夹。
