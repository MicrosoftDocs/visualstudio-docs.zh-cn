---
title: CreateExpInstance 实用程序 |Microsoft Docs
description: 了解允许您创建、重置或删除 Visual Studio 的实验实例的 CreateExpInstance 实用程序。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- experimental builds
- experimental hive
- experimental instance
- createexpinstance
- createexpinst
ms.assetid: 03779774-9401-49ae-997c-0c3ab25ed0d5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d0010c4a98d0ea50ec7feb2f7a379f3c84bc3d53
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/25/2021
ms.locfileid: "105056982"
---
# <a name="createexpinstance-utility"></a>CreateExpInstance 实用程序
使用 **CreateExpInstance** 实用工具可以创建、重置或删除 Visual Studio 的实验实例。 您可以使用实验实例来调试和测试 Visual Studio 扩展，而无需更改基础产品。

## <a name="syntax"></a>语法

```
CreateExpInstance.exe [/Create | /Reset | /Clean] /VSInstance=VsInstance /RootSuffix=Suffix
```

## <a name="parameters"></a>参数
 **/Create** 创建实验实例。

 **/Reset** 删除实验实例，然后创建一个新实例。

 **/Clean** 删除实验实例。

 **/VSInstance** 包含要复制的基本 Visual Studio 实例的目录的名称。

 **/RootSuffix** 要追加到实验实例目录的名称的后缀。

## <a name="remarks"></a>备注
 当你使用 Visual Studio 扩展时，可以按 F5 打开默认实验实例，并安装当前扩展。 如果没有可用的实验实例，Visual Studio 会创建一个具有默认设置的。

 实验实例的默认位置取决于 Visual Studio 版本号。 例如，对于 Visual Studio 2015，此位置是 *%localappdata%\Microsoft\VisualStudio\14.0Exp \\*。 目录位置中的所有文件都被视为该实例的一部分。 Visual Studio 不会加载任何其他实验实例，除非将目录名称更改为默认位置。

 Visual Studio 在打开实验实例时不会访问系统注册表。 这不同于早期版本的 Visual Studio，后者使用试验版的注册表配置单元。

 **CreateExpInstance** 实用程序将替换 **VsRegEx** 实用程序。

 下面的示例重置 Visual Studio 的默认实验实例：

 **CreateExpInstance.exe/Reset/VSInstance = 14.0/RootSuffix = Exp**

## <a name="see-also"></a>另请参阅
- [VSPackages](../../extensibility/internals/vspackages.md)
