---
title: 错误： 目标进程已退出，代码&#39;代码&#39;对函数求值时&#39;函数&#39;|Microsoft Docs
ms.custom: ''
ms.date: 4/06/2018
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.process_exit_during_func_eval
ms.technology: vs-ide-debug
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 98923757912d1f4619cc79c8f946aabaa531ac05
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/23/2018
ms.locfileid: "49936259"
---
# <a name="error-the-target-process-exited-with-code-39code39-while-evaluating-the-function-39function39"></a>错误： 目标进程已退出，代码&#39;代码&#39;对函数求值时&#39;函数&#39;

完整的消息文本： 计算函数 function 时，目标进程已退出，代码为 code。

若要更加轻松地检查.NET 对象的状态，调试器会自动强制调试的进程运行其他代码 (通常是属性 getter 方法和`ToString`函数)。 在大多数情况下，这些函数已成功完成或引发可由调试器捕获的异常。 但是，在某些情况下，由于异常跨越内核边界、需要用户消息循环或不可恢复，因此无法捕获异常。 作为结果、 属性 getter 或执行代码的 ToString 方法，或者显式终止进程 (例如，调用`ExitProcess()`) 或引发未经处理的异常不能被捕获 (例如， `StackOverflowException`) 将终止调试的进程并结束调试会话。 如果遇到此错误消息，此问题发生。
 
对于此问题的一个常见原因是，调试器将计算调用自身的属性，这可能会导致堆栈溢出异常。 无法恢复堆栈溢出异常，目标进程将终止。
 
## <a name="to-correct-this-error"></a>更正此错误
 
此问题有两个可能的解决方案。
 
### <a name="solution-1-prevent-the-debugger-from-calling-the-getter-property-or-tostring-method"></a>解决方法 #1： 防止调试器调用 getter 属性或 ToString 方法 

错误消息将告知调试器尝试调用函数的名称。 使用此函数的名称，你可以尝试从**即时**窗口重新计算该函数。 调试时，从**即时**窗口求值时，因为 **自动/局部变量/监视** 窗口与隐式求值与不同，调试器将在未经处理的异常处中断。

如果可以修改此函数，可以阻止调试器调用 getter 属性或`ToString`方法。 请尝试以下方法之一：
 
* 将方法更改为其他类型的代码 getter 属性或 ToString 方法和问题将会消失。
    或
* (有关`ToString`) 给类型类型定义 `DebuggerDisplay` 特性（attribute），调试器将计算 `ToString` 之外的值。
    或
* （适用于 getter属性)给属性定义 `[System.Diagnostics.DebuggerBrowsable(DebuggerBrowsableState.Never)]` 特性（attribute）。如果需要保持属性 API 的兼容性，这很有用，但这里应该使用一个方法。

如果您不能修改此方法，您可以在备用的指令处中断目标进程，然后重试求值。
 
### <a name="solution-2-disable-all-implicit-evaluation"></a>解决方案 2： 禁用所有隐式求值
 
如果先前的解决方案未解决此问题，请转到**工具** > **选项**，并取消选中该设置**调试** >  **常规** > **启用属性求值和其他隐式函数调用**。 这将会禁用大多数隐式函数求值，然后应解决的问题。



  
