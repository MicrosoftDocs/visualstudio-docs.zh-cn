---
title: Group 元素 |Microsoft Docs
description: Group 元素定义 VSPackage 命令组。 本文介绍特性、子元素和父元素。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Groups
- Groups element (VSCT XML schema)
ms.assetid: 69faee18-cbf4-470a-b952-c1919c583df8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: daf0115161963448d47cb6721c92d0f9ffe623a0
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/25/2021
ms.locfileid: "105057580"
---
# <a name="group-element"></a>Group 元素
定义 VSPackage 命令组。

## <a name="syntax"></a>语法

```xml
<Group guid="guidMyCommandSet" id="MyGroup" priority="0x101">
  <Parent>... </Parent>
</Group>
```

## <a name="attributes-and-elements"></a>特性和元素
 下列各节描述了特性、子元素和父元素。

### <a name="attributes"></a>特性

|属性|说明|
|---------------|-----------------|
|GUID|必需。 GUID/ID 命令标识符的 GUID。|
|id|必需。 GUID/ID 命令标识符的 ID。|
|priority|可选。 一个指定优先级的数值。|
|天气条件|可选。 请参阅 [条件特性](../extensibility/vsct-xml-schema-conditional-attributes.md)。|

### <a name="child-elements"></a>子元素

|元素|说明|
|-------------|-----------------|
|Parent|可选。 按钮的父元素。|
|批注|可选注释。|

### <a name="parent-elements"></a>父元素

|元素|说明|
|-------------|-----------------|
|[Groups 元素](../extensibility/groups-element.md)|包含定义 VSPackage 的命令组的项。|

## <a name="example"></a>示例

```xml
<Group guid="cmdSetGuidWidgetCommands" id="groupIDFileEdit">
  <Parent guid="guidSHLMainMenu" id="IDM_VS_TOOL_MAINMENU"/>
</Group>
```

## <a name="see-also"></a>另请参阅
- [Visual Studio 命令表 ( .vsct) 文件](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
