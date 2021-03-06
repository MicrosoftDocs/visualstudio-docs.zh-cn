---
title: 图像形状的属性
description: 了解图像形状以及如何使用图像形状指定域类在生成的设计器中的显示方式。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.selectimagedialog
- vs.dsltools.dsldesigner.imageshape
helpviewer_keywords:
- Domain-Specific Language, image shape
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 98198b1197de6f5fda6a05a5bae58378a323f718
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/19/2021
ms.locfileid: "112390550"
---
# <a name="properties-of-image-shapes"></a>图像形状的属性

可以使用图像形状指定域类在生成的设计器中的显示方式。 将 类的 属性设置为预定义的图像 `Image` 文件，以定义图像形状。 支持以下格式：

- .gif

- .jpg

- .jpeg

- .bmp

- .wmf

- .emf

- .png

默认情况下，设计器资源文件（如图像文件）位于 **Dsl** **项目的 Resources** 文件夹中。

有关详细信息，请参阅 [How to Define a Domain-Specific Language](../modeling/how-to-define-a-domain-specific-language.md)。 有关如何使用这些属性的信息，请参阅自定义和扩展Domain-Specific [语言](../modeling/customizing-and-extending-a-domain-specific-language.md)。

图像形状具有下表中列出的属性。

|属性|描述|默认|
|-|-|-|
|填充颜色|此形状的填充颜色。|White|
|填充渐变模式|此形状的填充渐变模式。|横向|
|具有默认连接点|如果 `True` 为 ，则形状将使用生成的设计器中的上、下、左和右连接点。|False|
|轮廓颜色|此形状的轮廓颜色。|黑色|
|大纲短划线样式|此形状的轮廓短划线样式 (Solid、Dash、Dot、DashDot、DashDotDot 或自定义) 。|单色|
|轮廓粗细|此形状的轮廓粗细。|0.03125|
|文本颜色|用于与此形状关联的文本修饰器的颜色。|黑色|
|访问修饰符|geometry 形状的访问修饰符 (公共或内部) 。|公用|
|自定义特性|用于向从此形状生成的源代码类添加属性。|\<none>|
|生成双派生|如果 `True` 为 ，则基类和分部 (类都支持通过重写) 将生成自定义。 有关详细信息，请参阅 [重写和扩展生成的类](../modeling/overriding-and-extending-the-generated-classes.md)。|False|
|具有自定义构造函数|如果 `True` 为 ，将在源代码中提供自定义构造函数。 有关详细信息，请参阅 [重写和扩展生成的类](../modeling/overriding-and-extending-the-generated-classes.md)。|False|
|继承修饰符|描述从图像形状生成的源代码类的继承类型 (`none` `abstract` 或 `sealed`) 。|无|
|基础图像形状|此形状的基类。|（无）|
|名称|此形状的名称。|当前名称|
|命名空间|此形状所附属的命名空间。|当前命名空间|
|工具提示类型|定义工具提示的位置 (固定、变量或无) 。 如果固定，则属性的值用作工具提示;如果为变量，则 `Fixed Tooltip Text` 工具提示在自定义代码中定义。|无|
|说明|与此形状关联的非正式说明。|\<none>|
|初始高度|此形状的初始高度（英寸）。|1|
|初始宽度|此形状的初始宽度（英寸）。|1.5|
|公开了填充颜色作为属性<br /><br /> 公开填充渐变模式<br /><br /> 将轮廓颜色公开为属性<br /><br /> 公开轮廓短划线样式作为属性<br /><br /> 公开轮廓粗细属性<br /><br /> 公开文本颜色|如果 `True` 为 ，则用户可以设置形状的已说明属性。 若要设置此选项，请右键单击形状定义，然后单击"**添加公开"。**|False|
|描述|用于记录生成的设计器。|\<none>|
|显示名称|将在此形状的生成设计器中显示的名称。|\<none>|
|修复了工具提示文本|用于固定工具提示的文本。|\<none>|
|帮助关键字|用于索引此元素的 F1 帮助的 关键字。|\<none>|
|映像|用于此形状的图像文件的路径。|\<none>|

## <a name="see-also"></a>另请参阅

- [域特定语言工具术语表](/previous-versions/bb126564(v=vs.100))