---
title: 步骤 8：添加验证玩家是否获胜的方法
description: 了解如何添加一种方法来确定玩家是否获胜。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: 6e317f6e-ba4c-4306-8924-300b0c2f65c6
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 931e39a4f3cf87fe2d147d90f2111c9a9db3faeb
ms.sourcegitcommit: 6d88913a8b5a9e5eda01d3f95205b4d138f440f8
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/13/2021
ms.locfileid: "107296997"
---
# <a name="step-8-add-a-method-to-verify-whether-the-player-won"></a>步骤 8：添加验证玩家是否获胜的方法
你已创建了一个有趣的游戏，但需要添加其他项来完成制作。 该游戏应当在玩家获胜时结束，因此您需要添加 `CheckForWinner()` 方法以验证玩家是否获胜。

## <a name="to-add-a-method-to-verify-whether-the-player-won"></a>添加方法以验证玩家是否获胜

1. 在你的代码底部，`timer1_Tick()` 事件处理程序下方添加一个 `CheckForWinner()` 方法，如以下代码所示。

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step8/cs/form1.cs" id="Snippet10":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step8/vb/form1.vb" id="Snippet10":::

      > [!IMPORTANT]
      > 使用此页右上角的编程语言控件查看 C# 代码片段或 Visual Basic 代码片段。<br><br>![Docs.Microsoft.com 的编程语言控件](../ide/media/docs-programming-language-control.png)     

     该方法使用 C# 中的另一个 `foreach` 循环或Visual Basic 中的 `For Each` 循环以执行 <xref:System.Windows.Forms.TableLayoutPanel> 中的每个标签。 它使用相等运算符（C# 中的 `==` 和 Visual Basic 中的 `=`）检查每个标签的图标颜色，以验证它是否与背景匹配。 如果颜色匹配，图标将保持不可见，玩家还没有匹配所有剩余的图标。 在这种情况下，程序使用 `return` 语句跳过其余方法。 如果循环遍历所有标签而不执行 `return` 语句，则意味着窗体上的所有图标均已匹配。 该程序将显示一个恭喜玩家获胜的 MessageBox，然后调用窗体的 `Close()` 方法来结束游戏。

2. 接下来，让标签的 <xref:System.Windows.Forms.Control.Click> 事件处理程序调用新的 `CheckForWinner()` 方法。 请确保程序在显示玩家选择的第二个图标后立即检查是否有赢家。 查找设置第二个选中图标颜色的行，然后在其后直接调用 `CheckForWinner()` 方法，如以下代码所示。

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step8/cs/form1.cs" id="Snippet11":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step8/vb/form1.vb" id="Snippet11":::

3. 保存并运行程序。 玩游戏并匹配所有图标。 当你获胜时，程序将显示一个祝贺 MessageBox（如以下屏幕截图所示），然后关闭该框。

     ![具有 MessageBox 的匹配游戏](../ide/media/express_tut4step8.png)<br/>
*具有 MessageBox 的匹配游戏

## <a name="to-continue-or-review"></a>继续或查看

- 要转到下一个教程步骤，请参阅[步骤 9：尝试其他功能](../ide/step-9-try-other-features.md)。

- 要返回到上一个教程步骤，请参阅[步骤 7：保持对可见](../ide/step-7-keep-pairs-visible.md)。
