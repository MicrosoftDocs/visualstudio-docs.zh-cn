---
title: CommandPlacement 元素 |Microsoft Docs
description: CommandPlacement 元素允许在多个组或菜单中包含按钮、组和菜单。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- CommandPlacements element (VSCT XML schema)
- VSCT XML schema elements, CommandPlacements
ms.assetid: 2cbd7ac8-c55a-43d8-a26d-713b3d790016
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 69be89fb2773be9de632b8059cf217303daaede7
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901989"
---
# <a name="commandplacement-element"></a>CommandPlacement 元素
CommandPlacement 元素允许在多个组或菜单中包含按钮、组和菜单。 使用 CommandPlacement 元素时，无需完全重新定义这些项即可修改用户界面的外观。

 有关详细信息，请参阅 [创建可重用的按钮组](../extensibility/creating-reusable-groups-of-buttons.md)。

## <a name="syntax"></a>语法

```
<CommandPlacement guid="guidMyCommandSet" id="MyCommand" priority="0x001" >
  <Parent>... </Parent>
</CommandPlacement>
```

## <a name="attributes-and-elements"></a>特性和元素
 下列各节描述了特性、子元素和父元素。

### <a name="attributes"></a>特性

|属性|描述|
|---------------|-----------------|
|GUID|必需。 在 [符号元素](../extensibility/symbols-element.md)中定义的命令集的 guid。|
|id|必需。 要放置的菜单、组或命令的 id，如中所定义 `Symbols Element` 。|
|priority|必需。 确定项在其父元素中的可视位置。|
|条件|可选。 请参阅 [条件 Aattributes](../extensibility/vsct-xml-schema-conditional-attributes.md)。|

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|Parent|必需。 承载要放置的项的菜单或组。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[CommandPlacements 元素](../extensibility/commandplacements-element.md)|指定 CommandPlacements 和 CommandPlacement 元素的组。|

## <a name="example"></a>示例

```
<CommandPlacements>
  <CommandPlacement guid="guidWidgetPackage" id="cmdidInsertOptions"
    priority="0x0300">
    <Parent guid="cmdGuidWidgetCommands" id="menuIDEditWidget"/>
  </CommandPlacement>
</CommandPlacements>
```

## <a name="see-also"></a>另请参阅
- [CommandPlacements 元素](../extensibility/commandplacements-element.md)
- [Visual Studio 命令表 ( .vsct) 文件](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
