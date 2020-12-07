---
title: 步骤 7：添加乘法和除法问题
description: 了解如何添加乘法题和除法题。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: e638959e-f6a4-4eb4-b2e9-f63b7855cf8f
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 84dc1df79392aeefe331746c52d2fbe8dbb91e8e
ms.sourcegitcommit: df6ba39a62eae387e29f89388be9e3ee5ceff69c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/02/2020
ms.locfileid: "96479493"
---
# <a name="step-7-add-multiplication-and-division-problems"></a>步骤 7：添加乘法和除法问题

在本教程的第 7 部分中，您将添加乘法和除法题，但首先要考虑如何做出这种更改。 考虑与存储值相关的初始步骤。

> [!NOTE]
> 本主题是基本编码概念教程系列中的一部分。 有关本教程的概述，请参阅[教程 2：创建计时数学测验](../ide/tutorial-2-create-a-timed-math-quiz.md)。

## <a name="to-add-multiplication-and-division-problems"></a>添加乘法和除法问题

1. 再向窗体添加四个整型变量。

     [!code-vb[VbExpressTutorial3Step7#15](../ide/codesnippet/VisualBasic/step-7-add-multiplication-and-division-problems_1.vb)]
     [!code-csharp[VbExpressTutorial3Step7#15](../ide/codesnippet/CSharp/step-7-add-multiplication-and-division-problems_1.cs)]

     [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

2. 与前面的操作一样，修改 `StartTheQuiz()` 方法，以便为乘法和除法题填入随机数。

     [!code-vb[VbExpressTutorial3Step7#16](../ide/codesnippet/VisualBasic/step-7-add-multiplication-and-division-problems_2.vb)]
     [!code-csharp[VbExpressTutorial3Step7#16](../ide/codesnippet/CSharp/step-7-add-multiplication-and-division-problems_2.cs)]

3. 修改 `CheckTheAnswer()` 方法，使之同样检查乘法和除法题。

     [!code-vb[VbExpressTutorial3Step7#17](../ide/codesnippet/VisualBasic/step-7-add-multiplication-and-division-problems_3.vb)]
     [!code-csharp[VbExpressTutorial3Step7#17](../ide/codesnippet/CSharp/step-7-add-multiplication-and-division-problems_3.cs)]

     由于使用键盘无法方便地输入乘号 (×) 和除号 (÷)，因此 C# 和 Visual Basic 接受用星号 (*) 代替乘号，用斜线 (/) 代替除号。

4. 更改计时器 <xref:System.Windows.Forms.Timer.Tick> 事件处理程序的最后部分，使其在时间用完时填入正确答案。

     [!code-vb[VbExpressTutorial3Step7#23](../ide/codesnippet/VisualBasic/step-7-add-multiplication-and-division-problems_4.vb)]
     [!code-csharp[VbExpressTutorial3Step7#23](../ide/codesnippet/CSharp/step-7-add-multiplication-and-division-problems_4.cs)]

5. 保存并运行程序。

     如下图所示，测验对象必须回答四个问题才能完成测验。

     ![包含四道题的数学测验](../ide/media/express_finishedquiz.png)<br/>
*包含四道题的数学测验

## <a name="to-continue-or-review"></a>继续或查看

- 要转到下一个教程步骤，请参阅[步骤 8：自定义测验](../ide/step-8-customize-the-quiz.md)。

- 若要返回上一个教程步骤，请参阅[步骤 6：添加减法问题](../ide/step-6-add-a-subtraction-problem.md)。
