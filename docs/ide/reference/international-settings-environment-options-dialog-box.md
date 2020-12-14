---
title: “选项”对话框中的“国际设置”
description: 了解在已安装多个语言版本的 IDE 时，如何通过“环境”部分的“国际设置”页更改默认语言。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Environment.InternationalSettings
- VS.ToolsOptionsPages.Environment.International_Settings
- VS.Environment.International Settings
helpviewer_keywords:
- International Settings dialog box
- languages, environment settings
- Options dialog box, international settings
- languages, specifying default
ms.assetid: e3a8815c-6995-4099-8e88-34f91fad55b2
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 37be8d3e5a652bb55b1d71f66c0e9c8ca4cc2f16
ms.sourcegitcommit: 2cf87f79762906ccaa133a7645aa4c77a0bed7da
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2020
ms.locfileid: "96617365"
---
# <a name="options-dialog-box-environment--international-settings"></a>“选项”对话框：环境 \> 国际设置

当计算机上安装有多个语言版本的集成开发环境 (IDE) 时，可通过国际设置页面更改默认语言。 要访问此对话框，可从“工具”菜单中选择“选项”，然后从“环境”文件夹中选择“区域设置”     。

**语言**

列出已安装产品语言版本的可用语言。 如果产品的多个语言或产品的混合语言安装可共享环境，则将语言选项更改为“与 Microsoft Windows 相同”  。

> [!CAUTION]
> 在安装了多个语言的系统中，Visual C++ 生成工具（cl.exe、link.exe、nmake.exe、bscmake.exe 和相关文件）不受此设置的影响。 这些工具使用上次安装的语言版本。 以前安装的语言版本的工具将被覆盖，因为 Visual C++ 生成工具不使用附属 DLL 模型。

### <a name="see-also"></a>请参阅

- [安装语言包](../../install/install-visual-studio.md#step-6---install-language-packs-optional)
