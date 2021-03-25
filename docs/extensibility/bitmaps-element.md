---
title: 位图元素 |Microsoft Docs
description: Bitmap 元素对一个或多个位图元素进行分组。 本文包含一个位图元素示例。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Bitmaps
- Bitmaps element (VSCT XML schema)
ms.assetid: 74652e1b-fcfa-421b-aa9f-fbc081d3b476
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: cc17162c8d66df99eefe721589863ee4221c8602
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/25/2021
ms.locfileid: "105068201"
---
# <a name="bitmaps-element"></a>位图元素
组 [位图元素](../extensibility/bitmap-element.md) 元素。

## <a name="syntax"></a>语法

```
<Bitmaps>
  <Bitmap>... </Bitmap>
  <Bitmap>... </Bitmap>
</Bitmaps>
```

## <a name="attributes-and-elements"></a>特性和元素
 下列各节描述了特性、子元素和父元素。

### <a name="attributes"></a>特性

|属性|说明|
|---------------|-----------------|
|条件|可选。 请参阅 [条件特性](../extensibility/vsct-xml-schema-conditional-attributes.md)。|

### <a name="child-elements"></a>子元素

|元素|说明|
|-------------|-----------------|
|[位图元素](../extensibility/bitmaps-element.md)|组位图元素。|
|[Bitmap 元素](../extensibility/bitmap-element.md)|定义位图。|

### <a name="parent-elements"></a>父元素

|元素|说明|
|-------------|-----------------|
|[Commands 元素](../extensibility/commands-element.md)|表示 VSPackage 工具栏上命令的集合。|

## <a name="example"></a>示例

```
<Bitmaps>
  <Bitmap guid="guidWidgetIcons" href="WidgetToolbarIcons_32.bmp" />
  <Bitmap guid="guidWidgetIcons2" resID="IDBMP_WIDGETICONS"
    usedList="1, 2, 3, 4"/>
</Bitmaps>
```

## <a name="see-also"></a>另请参阅
- [Vspackage 如何添加用户界面元素](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [命令、菜单和工具栏](../extensibility/internals/commands-menus-and-toolbars.md)
