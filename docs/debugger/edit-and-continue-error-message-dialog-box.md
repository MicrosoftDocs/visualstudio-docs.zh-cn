---
title: 编辑并继续错误消息对话框 |Microsoft Docs
ms.custom: ''
ms.date: 06/22/2018
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.ENC.SupportedButNotAvaiable
- vs.debug.ENC.CannotEditWhileException
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Edit and Continue Error Message dialog box
ms.assetid: f98c91c0-447a-4533-85b6-87170a0dc4c3
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5fd4fe31996a75c4b743f3dac12e7b945c912506
ms.sourcegitcommit: c5e72875206b8c5737c29d5b1ec7b86eec747303
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/17/2018
ms.locfileid: "49382787"
---
# <a name="edit-and-continue-error-message"></a>编辑并继续的错误消息 

在调试支持 **编辑并继续** 的代码语言时，将出现 **编辑并继续** 错误消息框，但是 **编辑并继续** 对您所做的代码更改不可用。该错误消息提供了更详细的说明。 若要响应该对话框，选择 **确定** 按钮以关闭对话框并取消编辑尝试。  

此错误消息的可能原因包括：  

-   尝试编辑 SQL Server 代码。
-   尝试编辑优化的代码。 您可能需要从发布版本切换到调试版本。
-   尝试编辑代码时它正在运行，而不是在调试器中暂停时。 请尝试[设置断点](../debugger/using-breakpoints.md)，和编辑代码时暂停。
-   尝试启用仅非托管调试时编辑托管的代码。 编辑并继续不适用于[混合模式调试](../debugger/how-to-debug-in-mixed-mode.md)。
-   进行代码更改，不支持编辑并继续的编程语言。 详细信息，请参阅文章[支持中的代码更改C# ](supported-code-changes-csharp.md)，[不受支持的 Visual Basic 编辑并继续中的编辑](unsupported-edits-in-visual-basic-edit-and-continue.md)，并[支持 c + + 代码更改](supported-code-changes-cpp.md).
-   尝试在你所附，而不是启动从调试的应用中编辑代码**调试**菜单。  
-   尝试在灾难恢复进行调试时编辑代码。Watson 转储。  
-   尝试编辑代码后会发生未处理的异常，并选择**展开调用堆栈上未经处理的异常**未选中。  
-   尝试调试嵌入式运行时应用程序时编辑代码。
-   尝试编辑托管的代码使用.NET Framework 版本 4.5.1 之前以 64 位应用程序为目标。 若要使用编辑并继续为.NET Framework 4.5.1 之前，请将目标设置为**x86**中**\<项目名称 >** > **属性** > **编译**选项卡上，**高级编译器**设置。  
-   尝试编辑在调试过程中修改和重新加载的程序集的代码。  
-   尝试编辑尚未加载的程序集中的代码。  
-   开始调试旧版本的应用程序，因为最新版本具有生成错误。
  
有关详细信息，请参见:
- [C + + 编辑并继续博客文章](https://blogs.msdn.microsoft.com/vcblog/2016/07/01/c-edit-and-continue-in-visual-studio-2015-update-3/)  
- [支持代码更改 （c + +）](../debugger/supported-code-changes-cpp.md)
- [编辑并继续](../debugger/edit-and-continue.md)