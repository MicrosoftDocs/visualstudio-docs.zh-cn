---
title: 命令标志元素|Microsoft Docs
description: Command 标志元素修改其父元素。 查看其父元素和子元素。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- CommandFlag element (VSCT XML schema)
- VSCT XML schema elements, CommandFlag
ms.assetid: 5ef63399-d2db-4dc1-97ce-be1bd4ef4e39
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6356fd02c8045aee9dc48ebc9d30a346159080bb
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902028"
---
# <a name="command-flag-eelement"></a>命令标志 Eelement
修改其父元素。

## <a name="syntax"></a>语法

```
<CommandFlag>DynamicVisibility</CommandFlag>
```

## <a name="attributes-and-elements"></a>特性和元素
 以下部分介绍有效的元素值。

### <a name="attributes"></a>特性
 无。

### <a name="child-elements"></a>子元素

|值|描述|
|-----------|-----------------|
|AllowParams|指示用户在键入命令的规范名称时，可以在"命令"窗口中输入命令参数。<br /><br /> 适用于： `Button`|
|AlwaysCreate|即使菜单没有组或按钮，也创建菜单。<br /><br /> 适用于： `Menu`|
|CaseSensitive|用户条目区分大小写。<br /><br /> 适用于： `Combo`|
|CommandWellOnly|如果命令未显示在顶级菜单上，并且想要使其可用于其他 shell 自定义（例如，用于将命令绑定到键盘快捷方式），请应用此标志。 安装 VSPackage 后，可以通过打开"选项"对话框，然后编辑"键盘环境"类别下的命令位置来 **自定义这些** 命令。 此标志不影响快捷菜单、工具栏、菜单控制器或子菜单上的放置。<br /><br /> 对 有效 `Button` ：、 `Combo`|
|DefaultDisabled|默认情况下，如果未加载实现该命令的 VSPackage 或尚未调用 方法， `QueryStatus` 则禁用该命令。<br /><br /> 对 有效 `Button` ：、 `Combo`|
|DefaultDocked|默认停靠。 此设置不再应用于工具栏，因为它们始终停靠。|
|DefaultInvisible|默认情况下，如果未加载实现该命令的 VSPackage 或尚未调用 方法，则该命令 `QueryStatus` 不可见。<br /><br /> 建议将其与 标志 `DynamicVisibility` 结合使用。<br /><br /> 有效范围 `Button` `Combo` ：、、 `Menu`|
|DontCache|开发环境不会缓存 `QueryStatus` 此命令的 方法结果。<br /><br /> 对于菜单，这会告知菜单控制器不要缓存其菜单项的文本。 当菜单包含动态项或具有动态文本的项时，请使用此标志。<br /><br /> 对 有效 `Button` ：、 `Menu`|
|DynamicItemStart|指示动态列表的开头。 这使环境能够通过连续调用列表项上的 方法来生成列表，直到OLECMDERR_E_UNSUPPORTED `QueryStatus` 标志。 这适用于 MRU 列表和窗口 (最近) 等项。<br /><br /> 适用于： `Button`|
|DynamicVisibility|可以通过 方法或 部分中包含的上下文 GUID 更改命令 `QueryStatus` 的 `VisibilityConstraints` 可见性。<br /><br /> 适用于显示在菜单和工具窗口工具栏上的命令，但不包括在主窗口上显示的顶级工具栏上的命令。 当从 方法返回顶级工具栏OLECMDF_INVISIBLE项时，可以禁用但不隐藏 `QueryStatus` 这些项。 可以隐藏工具窗口工具栏上显示的工具栏命令。<br /><br /> 在菜单上，此标志还指示当其所有成员都隐藏时，它应自动隐藏。 此标志通常分配给子菜单，因为顶级菜单已具有此行为。<br /><br /> 此标志应与 标志 `DefaultInvisible` 结合使用。<br /><br /> 有效范围 `Button` `Combo` ：、、 `Menu`|
|FilterKeys|请参阅组合元素 下的"筛选 [密钥"主题](../extensibility/combo-element.md)。<br /><br /> 适用于： `Combo`|
|FixMenuController|如果此命令定位在菜单控制器上，则该命令始终为默认值;也就是说，每当选择菜单控制器按钮本身时，都会选择命令。 如果菜单控制器设置了 标志，则菜单控制器还会从具有 标志的命令 `TextIsAnchorCommand` 中采用 `FixMenuController` 其文本。<br /><br /> 菜单控制器上只有一个命令应具有 `FixMenuController` 标志。 如果标记了多个命令，则菜单中的最后一个命令将成为默认命令。<br /><br /> 适用于： `Button`|
|IconAndText|在菜单和工具栏上显示图标和文本。<br /><br /> 有效范围 `Button` `Combo` ：、、 `Menu`|
|NoAutoComplete|自动完成功能已禁用。<br /><br /> 适用于： `Combo`|
|NoButtonCustomize|不允许用户自定义此按钮。<br /><br /> 对 有效 `Button` ：、 `Combo`|
|NoKeyCustomize|不要启用键盘自定义。<br /><br /> 对 有效 `Button` ：、 `Combo`|
|NoShowOnMenuController|如果此命令定位在菜单控制器上，则该命令不会出现在下拉列表中。<br /><br /> 适用于： `Button`|
|NotInTBList|不会出现在可用工具栏列表中。 这仅适用于工具栏菜单类型。<br /><br /> 适用于： `Menu`|
|NoToolbarClose|用户无法关闭工具栏。 这仅适用于工具栏菜单类型。<br /><br /> 适用于： `Menu`|
|Pict|只显示工具栏上的图标，但只显示菜单上的文本。 如果未指定图标，则工具栏上将显示可单击的空白区域。<br /><br /> 适用于： `Button`|
|PostExec|使命令成为非阻塞命令。 开发环境会延迟执行，直到所有预处理查询完成。<br /><br /> 适用于： `Button`|
|RouteToDocs|命令将路由到活动文档。<br /><br /> 适用于： `Button`|
|StretchHorizontally|设置此标志后，宽度将变为组合框的最小宽度，如果工具栏上有空间，则组合框会拉伸以填充可用空间。 这种情况仅在工具栏水平停靠时才会发生，而工具栏上只有一个组合框可以使用标志 (除了第一个组合框外，) 忽略标志。<br /><br /> 适用于： `Combo`|
|TextChanges|命令或菜单文本可在运行时通过方法进行更改 `QueryStatus` 。<br /><br /> 适用于： `Button` 、 `Menu`|
|TextChangesButton|适用于： `Button`|
|TextIsAnchorCommand|对于菜单控制器，菜单文本是从默认 (定位点) 命令获取的。 定位符命令是最后一个选定或锁定的命令。 如果未设置此标志，则菜单控制器使用其自己的 `MenuText` 字段。 然而，单击菜单控制器仍将从该控制器启用最后一个选定的命令。<br /><br /> 建议将此标志与标志结合起来 `TextChanges` 。<br /><br /> 此标志仅适用于 MenuController 或 MenuControllerLatched 类型的菜单。<br /><br /> 适用于： `Menu`|
|TextMenuCtrlUseMenu|使用 `MenuText` 菜单控制器上的字段。 默认字段是 `ButtonText` 。<br /><br /> 适用于： `Button`|
|TextMenuUseButton|将 `ButtonText` 字段用于菜单。 如果已指定，则默认值为 `MenuText` 。<br /><br /> 适用于： `Button`|
|TextOnly|仅显示工具栏或菜单上的文本，但不显示图标（即使指定了图标）。<br /><br /> 适用于： `Button`|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[按钮元素](../extensibility/buttons-element.md)|为 [Button 元素](../extensibility/button-element.md) 元素提供组。|
|[菜单元素](../extensibility/menus-element.md)|定义 VSPackage 实现的所有菜单。|

## <a name="see-also"></a>另请参阅
- [Visual Studio 命令表 (。.Vsct) 文件](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
