---
title: 如何：在元素上设置 CLR 特性
description: 了解如何添加任何继承自 System.object 类的属性。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.dsltools.EditAttributesDialog
helpviewer_keywords:
- Domain-Specific Language, custom attrributes
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b11a6bd4a04bdb469cdf5c2fe2d7b78e0c0fe29a
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/19/2021
ms.locfileid: "112387328"
---
# <a name="how-to-set-clr-attributes-on-an-element"></a>如何：在元素上设置 CLR 特性
自定义属性是可以添加到域元素、形状、连接符和关系图中的特殊属性。 可以添加从类继承的任何属性 `System.Attribute` 。

### <a name="to-add-a-custom-attribute"></a>添加自定义属性

1. 在 " **DSL 资源管理器**" 中，选择要向其添加自定义属性的元素。

2. 在 " **属性** " 窗口中，在 " **自定义属性** " 属性旁边，单击 "浏览 (**...** ") 图标。

     此时将打开 " **编辑属性** " 对话框。

3. 在 " **名称** " 列中，单击 **\<add attribute>** 并键入属性的名称。 按 Enter。

4. 属性名称下面的行显示括号。 在此行上，键入属性的参数类型 (例如， `string`) ，然后按 enter。

5. 在 " **名称属性** " 列中，键入适当的名称，例如 `MyString` 。

6. 单击 **“确定”** 。

     " **自定义属性** " 属性现在按以下格式显示属性：

     `[`*AttributeName* `(`*ParameterName* `=`*类型*`)]`

## <a name="see-also"></a>另请参阅

- [域特定语言工具术语表](/previous-versions/bb126564(v=vs.100))