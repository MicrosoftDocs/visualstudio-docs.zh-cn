---
title: 编辑并继续 (Visual Basic) |Microsoft 文档
ms.custom: ''
ms.date: 10/11/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Edit and Continue, 64-bit
- Edit and Continue [Visual Basic]
- debugging [Visual Basic], Edit and Continue
- Visual Basic, Edit and Continue
- 64-bit Edit and Continue
ms.assetid: 7e90f34f-e699-45ab-a4c9-a4b527c498c8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: aa3b8c287129c164d8c6984ac52375d6012fbd68
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2018
ms.locfileid: "31471039"
---
# <a name="edit-and-continue-visual-basic"></a>编辑并继续 (Visual Basic)
“编辑并继续”是当代码在中断模式时，可以更改代码 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 的一项调试功能。 在应用代码编辑后，可以继续执行新编辑过的代码并观察效果。  
  
 每次进入中断模式时都可以使用“编辑并继续”功能。 在中断模式下指令指针、 源窗口中的黄色箭头，指向方法或属性中下一步将被执行的语句。

 “编辑并继续”支持在调试会话期间，可能做出的大多数更改，但有某些例外。 有关详细信息，请参阅[支持的代码更改 （C# 和 Visual Basic）](../debugger/supported-code-changes-csharp.md)。   
  
 如果进行了未经授权的编辑，则所做更改会被加上紫色波浪下划线标记，并且会在任务列表中显示一个任务。 如果要继续使用“编辑并继续”功能，必须撤消未经授权的编辑。 在“编辑并继续”之外，可能允许执行某些未经授权的编辑。 如果要保留这种未经授权的编辑的结果，必须停止调试并重新启动应用程序。  
  
 编辑并继续支持适用于 Windows 10 UWP 应用和面向.NET Framework 4.6 的 x86 和 x64 应用中桌面或更高版本 （.NET Framework 是仅限桌面版本）。

 > [!NOTE]
 > 不受支持的应用程序和平台包括 ASP.NET 5、 Silverlight 5 和 Windows 8.1。
  
 在开始调试使用时不支持编辑并继续**附加到进程**。 为优化代码或混合不支持编辑并继续托管和本机代码。 有关详细信息，请参阅[支持的代码更改 (C# 和 Visual Basic](../debugger/supported-code-changes-csharp.md)。
  
 本节中各个主题提供的详细信息涉及：如何使用此功能，允许进行哪些类型的更改。  
  
## <a name="in-this-section"></a>本节内容  
 [如何：使用“编辑并继续”在中断模式下应用编辑](../debugger/how-to-apply-edits-in-break-mode-with-edit-and-continue.md)  
 解释如何在中断模式下应用代码编辑。  
  
 [受支持的代码更改 （C# 和 Visual Basic](../debugger/supported-code-changes-csharp.md)   
 描述了无法在 [!INCLUDE[vb_current_short](../debugger/includes/vb_current_short_md.md)]“编辑并继续”中执行的编辑的类型。  
  
## <a name="related-sections"></a>相关章节  
 [编辑并继续](../debugger/edit-and-continue.md)  
 提供“编辑并继续”主题的列表。