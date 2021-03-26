---
title: 旧版语言服务中的自动格式设置 |Microsoft Docs
description: 了解旧版语言服务中的自动格式设置，当你开始键入已知的代码构造时，它会自动插入代码片段。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, automatic formatting
ms.assetid: c210fc94-77bd-4694-b312-045087d8a549
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a08a56a6820917b3a954c162b1875430875c7585
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/25/2021
ms.locfileid: "105086269"
---
# <a name="automatic-formatting-in-a-legacy-language-service"></a>旧版语言服务中的自动格式设置
对于自动格式设置，当用户开始键入已知的代码构造时，语言服务会自动插入代码片段。

## <a name="automatic-formatting-behavior"></a>自动设置格式行为
 例如，当你键入 *if* 时，语言服务会自动插入匹配的大括号，或者，如果按 enter 键，则语言服务会将新行上的插入点强制转换为相应的缩进级别，具体取决于上面的行是否打开了新的作用域。

 用于其他语言服务的命令筛选器也可用于自动格式设置。 还可以通过调用突出显示匹配的大括号 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A> 。

## <a name="see-also"></a>另请参阅
- [开发旧版语言服务](../../extensibility/internals/developing-a-legacy-language-service.md)
