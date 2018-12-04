---
title: DebugBreak 和 __debugbreak |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- DebugBreak
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [C++], DebugBreak function
- DebugBreak function
- breakpoints, DebugBreak function
ms.assetid: 9787c795-df94-4f48-bc8d-3bf899b67421
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a5eda428410733bf72174676f5a2303a7f625aa7
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2018
ms.locfileid: "31470468"
---
# <a name="debugbreak-and-debugbreak"></a>DebugBreak 和 __debugbreak
你可以在代码内部的任何位置调用 DebugBreak Win32 函数或[__debugbreak](/cpp/intrinsics/debugbreak)。 `DebugBreak` 和 `__debugbreak` 具有与在该位置设置断点相同的效果。  
  
 由于 `DebugBreak` 是对系统函数的调用，因此必须安装系统调试符号，以确保中断后显示正确的调用堆栈信息。 否则，调试器可能在显示一条调用堆栈信息后就停止显示。 如果使用 `__debugbreak`，则不需要符号。  
  
## <a name="see-also"></a>请参阅  
 [编译器内部函数](/cpp/intrinsics/compiler-intrinsics)   
 [调试器安全](../debugger/debugger-security.md)   
 [调试本机代码](../debugger/debugging-native-code.md)   
 [指定符号 (.pdb) 和源文件](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)