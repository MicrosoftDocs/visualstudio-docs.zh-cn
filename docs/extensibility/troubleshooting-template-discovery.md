---
title: 排查 Visual Studio 中的模板发现问题 |Microsoft Docs
description: 了解如何启用诊断日志记录，以便在 Visual Studio SDK 中部署自定义项目和模板。
ms.custom: SEO-VS-2020
ms.date: 01/02/2018
ms.topic: troubleshooting
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 23e30ddb5f43a755fc2dc0206509e403e802c3e7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2021
ms.locfileid: "99893485"
---
# <a name="troubleshooting-template-installation"></a>模板安装故障排除

如果在部署项目或项模板时遇到问题，可以启用诊断日志记录。

::: moniker range="vs-2017"

1. 在 *Common7\IDE\CommonExtensions* 文件夹中为你的安装创建 .pkgdef 文件。 例如， *C:\Program 文件 (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\IDE\CommonExtensions\EnablePkgDefLogging.pkgdef*。

::: moniker-end

::: moniker range=">=vs-2019"

1. 在 *Common7\IDE\CommonExtensions* 文件夹中为你的安装创建 .pkgdef 文件。 例如， *C:\Program 文件 (x86) \Microsoft Visual Studio\2019\Enterprise\Common7\IDE\CommonExtensions\EnablePkgDefLogging.pkgdef*。

::: moniker-end

2. 将以下内容添加到 .pkgdef 文件：

    ```
    [$RootKey$\VsTemplate]
    "EnableTemplateDiscoveryLog"=dword:00000001
    ```

3. 打开安装的 [开发人员命令提示](/dotnet/framework/tools/developer-command-prompt-for-vs) ，然后运行 `devenv /updateConfiguration` 。

::: moniker range="vs-2017"

4. 打开 Visual Studio 并启动 "新建项目" 和 "新建项" 对话框以初始化两个模板树。

   模板日志现在显示在 **%LOCALAPPDATA%\Microsoft\VisualStudio\15.0_ [instanceid] 中 \VsTemplateDiagnosticsList.csv** (instanceid 对应于 Visual Studio) 实例的安装 ID。 每个模板树初始化都会向此日志追加条目。

::: moniker-end

::: moniker range=">=vs-2019"

4. 打开 Visual Studio 并启动 "新建 **项目** " 和 " **新建项** " 对话框以初始化两个模板树。

   模板日志现在显示在 **%LOCALAPPDATA%\Microsoft\VisualStudio\16.0_ [instanceid] 中 \VsTemplateDiagnosticsList.csv** (instanceid 对应于 Visual Studio) 实例的安装 ID。 每个模板树初始化都会向此日志追加条目。

::: moniker-end

日志文件包含以下列：

- **FullPathToTemplate**，它具有以下值：

  - 1用于基于清单的部署

  - 对于基于磁盘的部署为0

- **TemplateFileName**

- 其他模板属性

> [!NOTE]
> 若要禁用日志记录，请删除 .pkgdef 文件，或将的值更改 `EnableTemplateDiscoveryLog` 为 `dword:00000000` ，然后 `devenv /updateConfiguration` 再次运行。

## <a name="see-also"></a>另请参阅

- [创建自定义项目和项模板](creating-custom-project-and-item-templates.md)
- [Visual Studio 故障排除](/troubleshoot/visualstudio/welcome-visual-studio/)
