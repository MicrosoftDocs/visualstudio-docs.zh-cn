---
title: 如何：使用 Built-In 可着色项 |Microsoft Docs
description: 了解如何在 Visual Studio 集成开发环境中使用内置可着色项 (IDE) 用于你的语言服务。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- colorable items
- language services, built-in colorable items
ms.assetid: 5e5f3436-6bad-4fd2-8823-6a30353ba648
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 253c108fe83eaf44f945f546bd64dd6529de1dd6
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/25/2021
ms.locfileid: "105086074"
---
# <a name="how-to-use-built-in-colorable-items"></a>如何：使用内置可着色项
使用内置的可着色项之前，必须首先向集成开发环境发出信号， (IDE) 不提供自己的自定义可着色项，在本例中为 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> 对象。 为此，可设置语言服务的注册表项。

## <a name="to-use-built-in-colorable-items"></a>使用内置的可着色项

1. 在 **HKEY_LOCAL_MACHINE\VisualStudio\\<X. Y> \languages\language Services \\<语言名称 \>**，其中 \<X.Y> 是版本的， [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] \<Language Name> 是语言名称，创建名为 **RequestStockColors** 的 DWORD 注册表项值。

2. 将 **RequestStockColors** 注册表项值设置为 *1*。

    在创建注册表项后，colorizer 的 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> 方法可以使用枚举的成员 <xref:Microsoft.VisualStudio.TextManager.Interop.DEFAULTITEMS> 来填充颜色特性的数组以供编辑器使用。

   > [!NOTE]
   > 如果提供自定义可着色项，请不要设置此注册表项。 有关详细信息，请参阅 [自定义可着色项](../../extensibility/internals/custom-colorable-items.md)。

## <a name="see-also"></a>另请参阅
- [自定义编辑器中的语法着色](../../extensibility/syntax-coloring-in-custom-editors.md)
- [旧版语言服务中的语法着色](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)
- [实现语法着色](../../extensibility/internals/implementing-syntax-coloring.md)
- [自定义可着色项](../../extensibility/internals/custom-colorable-items.md)
- [注册旧版语言服务](../../extensibility/internals/registering-a-legacy-language-service2.md)
