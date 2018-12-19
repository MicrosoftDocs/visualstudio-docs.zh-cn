---
title: "使用编辑并继续在中断模式下应用编辑 |Microsoft Docs"
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.variables.failededit
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Edit and Continue [Visual Basic], applying edits in break mode
- break mode, applying code changes
- Edit and Continue, applying edits in break mode
- editing, break mode
- coding, editing in break mode
- code, editing in break mode
ms.assetid: 1eef7498-6a1f-4fba-8146-510adc6375c9
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 263e4bf4505995a4c8eccbe7c33f59115412dda5
ms.sourcegitcommit: d462dd10746624ad139f1db04edd501e7737d51e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/29/2018
ms.locfileid: "50219505"
---
# <a name="how-to-apply-edits-in-break-mode-with-edit-and-continue"></a>如何：使用“编辑并继续”在中断模式下应用编辑
可以在中断模式下使用“编辑并继续”编辑代码，然后不必停止和重启调试器即可继续。  
  
有关使用编辑并继续调试时的限制，请参阅[支持的 (C#和 Visual Basic) 代码更改](../debugger/supported-code-changes-csharp.md)]
  
### <a name="to-edit-code-in-break-mode"></a>在中断模式下编辑代码  
  
1.  执行下列操作之一进入中断模式：  
  
    -   在代码中设置断点，然后从 **调试** 菜单中选择 **开始调试** ，然后等待应用程序命中断点。  
  
         或  
  
    -   开始调试，然后从 **调试** 菜单中依次 **全部中断** 。  
  
         或  
  
    -   异常发生时，从 **异常助手** 上选择 **启用编辑** 。  
  
2.  进行任何所需和受支持的代码更改。  
  
     有关详细信息，请参阅[支持的 (C#和 Visual Basic) 代码更改](../debugger/supported-code-changes-csharp.md)。  
  
    > [!NOTE]
    >  如果尝试进行“编辑并继续”所不允许的代码更改，你的编辑将被加上紫色波浪线，并且“任务列表”中会出现一项任务。 除非撤消非法的代码更改，否则将无法继续执行代码。  
  
3.  在 **调试** 菜单上，单击 **继续** 继续执行。  
  
     在你所做的编辑已并入项目并已应用的情况下，继续执行你的代码。  
  
## <a name="see-also"></a>请参阅  
 [支持 (C#和 Visual Basic) 代码更改](../debugger/supported-code-changes-csharp.md)   
 [编辑并继续 (Visual Basic)](../debugger/edit-and-continue-visual-basic.md)