---
title: 模板策略和 "属性" 窗口 |Microsoft Docs
description: 了解如何使用模板策略设置属性的默认值、隐藏属性以及在属性窗口中添加属性。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window, template policy
ms.assetid: 1d8019d3-5e57-47ba-b358-526b0796a63b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 105a90699689ff6eab6ea5bdfa3d4037e700ecb5
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/05/2021
ms.locfileid: "97877710"
---
# <a name="template-policy-and-the-properties-window"></a>模板策略和属性窗口
当某个项目包含在企业模板项目中时，该企业模板项目可以强制实施策略。 模板策略成为一个约束系统，可用于设置属性的默认值、隐藏属性、添加属性等等。

 使用模板策略控制在 " **属性** " 窗口中显示的信息与实现不同 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> 。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> 在组件级别处理对象属性，而模板策略可用于在解决方案或项目级别约束对象属性。 换句话说

- 实现上的方法 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> ，以确定在 " **属性** " 窗口中显示的特定对象的内容

- 使用解决方案和项目级别的模板策略来确定以前指定的对象在 " **属性** " 窗口中显示的内容

  如果在 **解决方案资源管理器** 中选择指定类型的项目项，则在 "**属性**" 窗口中使用模板策略有选择地限制特定属性，这对于处理项目的开发团队的所有成员都非常有利。 例如，使用模板策略时，您可以为开发人员设置数据库中的所有连接字符串信息，并将连接字符串设置为只读。 通过这种方式，你可以提供一种简单的方法来确保每个开发人员都使用正确的数据访问路径。

## <a name="see-also"></a>另请参阅
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>
- [扩展属性](../../extensibility/internals/extending-properties.md)
