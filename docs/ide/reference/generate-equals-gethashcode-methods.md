---
title: 生成 C# Equals 和 GetHashCode 方法重写
description: 了解如何使用“快速操作和重构”菜单生成 Equals 和 GetHashCode 方法。
ms.custom: SEO-VS-2020
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: f6f7ec74af21ef62079a3fef18dd39544e7b42aa
ms.sourcegitcommit: 2cf87f79762906ccaa133a7645aa4c77a0bed7da
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2020
ms.locfileid: "96617508"
---
# <a name="generate-equals-and-gethashcode-method-overrides-in-visual-studio"></a>在 Visual Studio 中生成 C# Equals 和 GetHashCode 方法重写

此代码生成适用于：

- C#

功能：让你生成 Equals 和 GetHashCode 方法。

适用情况：当具备的类型应按一个或多个字段进行比较，而不是按内存中的对象位置进行比较时，生成这些重写。

操作原因：

- 如果实现值类型，则应考虑重写 Equals 方法，针对 Equals 方法在 ValueType 上的默认实现提升相关性能。

- 在实现引用类型时，如果类型看起来像基类型（如点、字符串和 BigNumber 等），请考虑重写 Equals 方法。

- 重写 GetHashCode 方法，使类型能在哈希表中正常工作。 了解有关[相等运算符](/dotnet/standard/design-guidelines/equality-operators)的更多指南。

## <a name="how-to"></a>操作说明

1. 将游标放在类型声明的行上。

   ![突出显示的代码](media/overrides-highlight-cs.png)

   > [!TIP]
   > 请勿双击选择类型名称，否则菜单选项将不可用。 只需将游标置于行上的某处。

1. 接下来，执行以下操作之一：

   - 按“Ctrl”+ **。** 触发“快速操作和重构”菜单。

   - 右键单击并选择“快速操作和重构”菜单。

   - 单击 ![左边缘中](../media/screwdriver-icon.png) 显示的螺丝刀图标。

   ![生成重写预览](media/overrides-preview-cs.png)

1. 从下拉菜单中选择“生成 Equals(object)”或“生成 Equals 和 GetHashCode”。

1. 在“选取成员”对话框中，选择要为其生成方法的成员：

    ![生成重写对话框](media/overrides-dialog-cs.png)

    > [!TIP]
    > 也可以通过使用对话框底部附近的复选框，选择从此对话框中生成运算符。

   将使用默认实现生成 `Equals` 和 `GetHashCode` 方法。

   ![生成方法结果](media/overrides-result-cs.png)

## <a name="see-also"></a>请参阅

- [代码生成](../code-generation-in-visual-studio.md)
- [预览更改](../../ide/preview-changes.md)
