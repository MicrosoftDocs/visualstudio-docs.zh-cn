---
title: 将变量声明移动到引用附近
description: 了解如何使用“快速操作和重构”菜单来移动变量声明，使其更接近其用法。
ms.custom: SEO-VS-2020
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: ce731da61c0c119869c1c1b85a87ebe44fabf273
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2021
ms.locfileid: "99927920"
---
# <a name="move-declaration-near-reference-refactoring"></a>将变量声明移动到引用附近

此重构适用于：

- C#

- Visual Basic

功能：将变量声明移至靠近其用法的位置。

时机：具有可存在于较窄范围中的变量声明时。

原因：可以将其保留不变，但这可能会导致可读性问题或信息隐藏。 可以进行重构，以提高可读性。

## <a name="how-to"></a>操作说明

1. 将光标置于变量声明中。

1. 接下来，执行以下操作之一：

   - **键盘**
      - 按“Ctrl”+ **。** 触发“快速操作和重构”菜单，然后从“预览”弹出窗口中选择“移动声明至引用附近”。
   - **鼠标**
      - 右键单击代码，选择“快速操作和重构”菜单，然后从“预览”弹出窗口中选择“移动声明至引用附近”。

1. 对更改感到满意时，按 Enter 或单击菜单中的修复，即可提交所做的更改。

例如：

```csharp
// Before
int x;
if (condition)
{
    x = 1;
    Console.WriteLine(x);
}

// Move declaration near reference

// After
if (condition)
{
    int x = 1;
    Console.WriteLine(x);
}
```

## <a name="see-also"></a>另请参阅

- [重构](../refactoring-in-visual-studio.md)
- [预览更改](../../ide/preview-changes.md)
