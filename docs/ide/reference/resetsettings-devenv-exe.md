---
title: -ResetSettings (devenv.exe)
description: 了解如何使用 ResetSettings devenv 命令行开关来还原 Visual Studio 默认设置并自动启动 Visual Studio IDE。
ms.custom: SEO-VS-2020
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- Devenv, /ResetSettings switch
- ResetSettings switch
- /ResetSettings Devenv switch
- settings [Visual Studio], resetting
ms.assetid: 1d41021c-6f58-4bd5-b122-d1c995812192
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 22b3308b3bd1fed6ff1bc3d1f3a5622eb6f8284f
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/25/2020
ms.locfileid: "96040025"
---
# <a name="resetsettings-devenvexe"></a>/ResetSettings (devenv.exe)

还原 Visual Studio 的默认设置，自动启动 Visual Studio IDE。 此开关视需要将这些设置重置为指定的设置文件。

默认设置来自在 Visual Studio 首次启动时被选择的配置文件。

> [!TIP]
> 若要了解如何使用集成开发环境 (IDE) 重置设置，请参阅[重置设置](../environment-settings.md#reset-settings)。

## <a name="syntax"></a>语法

```shell
devenv /ResetSettings [SettingsFile|DefaultCollectionSpecifier]
```

## <a name="arguments"></a>参数

- *SettingsFile*

  可选。 应用于 Visual Studio 的设置文件的完整路径和文件名。

- DefaultCollectionSpecifier

  可选。 表示要还原的默认设置集合的说明符。 从表中列出的默认集合说明符中选择一个。

  | 默认集合名称 | 集合说明符 |
  | --- | --- |
  | **常规** | `General` |
  | **JavaScript** | `JavaScript` |
  | **Visual Basic** | `VB` |
  | **Visual C#** | `CSharp` |
  | **Visual C++** | `VC` |
  | **Web 开发** | `Web` |
  | **Web 开发（仅代码）** | `WebCode` |

## <a name="remarks"></a>备注

如果没有指定 SettingsFile，IDE 使用现有设置打开。

## <a name="example"></a>示例

第一个示例应用文件 `MySettings.vssettings` 中存储的设置。

第二个示例还原 Visual C# 默认配置文件。

```shell
devenv /resetsettings "%USERPROFILE%\MySettings.vssettings"

devenv /resetsettings CSharp
```

## <a name="see-also"></a>另请参阅

- [环境设置](../environment-settings.md)
- [个性化设置 Visual Studio IDE](../../ide/personalizing-the-visual-studio-ide.md)
- [Devenv 命令行开关](../../ide/reference/devenv-command-line-switches.md)
