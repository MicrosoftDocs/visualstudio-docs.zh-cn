---
title: Vspackage 中的命令传送 |Microsoft Docs
description: 了解 Vspackage 中的命令路由，以及如何根据在 Visual Studio 中执行这些命令的上下文来路由命令。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, routing
- command routing, Visual Studio SDK
ms.assetid: a9c7f9ae-3594-4557-a314-8cf76f5f8772
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d05612f9d15c3670411a7901157570fbb3e315a3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2021
ms.locfileid: "99939989"
---
# <a name="command-routing-in-vspackages"></a>Vspackage 中的命令传送
命令 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 根据执行它的上下文进行路由。 它从初始上下文到全局上下文的外部路由。

## <a name="in-this-section"></a>本节内容
- [命令传送算法](../../extensibility/internals/command-routing-algorithm.md)

 描述命令路由解决方案的顺序。

- [命令可用性](../../extensibility/internals/command-availability.md)

 讨论命令路由。

- [使用互操作程序集的命令和菜单](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)

 讨论托管代码与 COM 之间路由命令的注意事项。

## <a name="related-sections"></a>相关章节
- [选择上下文对象](../../extensibility/internals/selection-context-objects.md)

 讨论如何在窗口上确定用户的选择上下文焦点的模型。

- [命令、菜单和工具栏](../../extensibility/internals/commands-menus-and-toolbars.md)

 说明如何创建包含菜单、工具栏和命令组合框的 UI。
