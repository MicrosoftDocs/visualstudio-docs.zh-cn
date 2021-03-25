---
title: 正在为文件扩展名注册谓词 |Microsoft Docs
description: 了解如何使用 Shell 键注册与文件扩展名的编程标识符关联的谓词。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- verbs, registering
ms.assetid: 81a58e40-7cd0-4ef4-a475-c4e1e84d6e06
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 9936efc2e01c0d82d5cc9fce140d543eb95247ad
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/25/2021
ms.locfileid: "105068474"
---
# <a name="register-verbs-for-file-name-extensions"></a>注册文件扩展名的谓词
与应用程序的文件扩展名的关联通常具有一个在用户双击文件时发生的首选操作。 此首选操作链接到对应于操作的谓词，例如 "open"。

 你可以通过使用位于 **HKEY_CLASSES_ROOT \{ progid} \Shell** 的 Shell 键，来注册与编程标识符关联的谓词 (ProgID) 。 有关详细信息，请参阅 [文件类型](/windows/desktop/shell/fa-file-types)。

## <a name="register-standard-verbs"></a>注册标准谓词
 操作系统可识别以下标准谓词：

- 打开

- 编辑

- 显示

- 打印

- 预览

  请尽可能注册标准谓词。 最常见的选择是打开谓词。 仅当打开文件和编辑该文件时，才使用编辑谓词。 例如，打开 *.htm* 文件会在浏览器中显示该文件，而编辑 *.htm* 文件会启动 HTML 编辑器。 标准谓词已本地化为操作系统区域设置。

> [!NOTE]
> 注册标准谓词时，请不要设置 "打开" 键的默认值。 默认值包含菜单上的显示字符串。 操作系统为标准谓词提供此字符串。

 当用户打开文件时，应注册项目文件以启动新实例 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 。 下面的示例演示了项目的标准谓词注册 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 。

```
[HKEY_CLASSES_ROOT\.csproj]
@="VisualStudio.csproj.8.0"

[HKEY_CLASSES_ROOT\.csproj\OpenWithList]
[HKEY_CLASSES_ROOT\.csproj\OpenWithList\VSLauncher.exe]
@=""

[HKEY_CLASSES_ROOT\.csproj\OpenWithProgids]
"VisualStudio.csproj.8.0"=""

[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe]
[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe\Shell]
[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe\Shell\Open]
[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe\Shell\Open\Command]
@="C:\\Program Files\\Common Files\\Microsoft Shared\\MSEnv\\VSLauncher.exe \"%1\""

[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0]
@="C# Project file"

[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\DefaultIcon]
@="C:\\VisualStudioPath\\VC#\\VCSPackages\\csproj.dll,0"

[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\shell]
[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\shell\Open]
[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\shell\Open\Command]
@="\"C:\\Program Files\\Common Files\\Microsoft Shared\\MSEnv\\VSLauncher.exe\" \"%1\""
```

 若要在的现有实例中打开文件 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ，请注册 DDEEXEC 键。 下面的示例演示 .cs 文件的标准谓词注册 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]  。

```
[HKEY_CLASSES_ROOT\.cs]
@="VisualStudio.cs.8.0"

[HKEY_CLASSES_ROOT\.cs\OpenWithList]
[HKEY_CLASSES_ROOT\.cs\OpenWithList\devenv.exe]
@=""

[HKEY_CLASSES_ROOT\.cs\OpenWithProgids]
"VisualStudio.cs.8.0"=""

[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0]
@="C# Source file"

[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\DefaultIcon]
@="C:\\VisualStudioPath\\VC#\\VCSPackages\\csproj.dll,1"

[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell]
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open]
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\Command]
@="\"C:\\VisualStudioPath\\Common7\\IDE\\devenv.exe\" /dde \"%1\""

[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\ddeexec]
@="Open(\"%1\")"

[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\ddeexec\Application]
@="VisualStudio.8.0"

[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\ddeexec\Topic]
@="system"
```

## <a name="set-the-default-verb"></a>设置默认谓词
 默认谓词是用户在 Windows 资源管理器中双击文件时执行的操作。 默认谓词是指定为 **HKEY_CLASSES_ROOT \\ *progid*\Shell** 密钥的默认值的谓词。 如果未指定任何值，则默认谓词是在 **HKEY_CLASSES_ROOT \\ *progid*\Shell** 键列表中指定的第一个谓词。

> [!NOTE]
> 如果计划在并行部署中更改扩展的默认谓词，请考虑对安装和删除的影响。 在安装期间，将覆盖原始默认值。

## <a name="see-also"></a>另请参阅
- [管理并行文件关联](../extensibility/managing-side-by-side-file-associations.md)
