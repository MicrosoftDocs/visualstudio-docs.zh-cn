---
title: "分配挂钩函数和 C 运行时内存分配 |Microsoft Docs"
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.hooks
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [C++], hook functions
- memory allocation, troubleshooting allocation hooks
- allocation hooks
- hooks, allocation
ms.assetid: cc34ee96-3d91-41bd-a019-aa3759139e7e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7e4c631b72ae9b12f77daf2ddd49919651c0b3e5
ms.sourcegitcommit: 80f9daba96ff76ad7e228eb8716df3abfd115bc3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/03/2018
ms.locfileid: "37433095"
---
# <a name="allocation-hooks-and-c-run-time-memory-allocations"></a>分配挂钩函数和 C 运行时内存分配
在分配挂钩函数时，一个非常重要的限制是，它们必须显式忽略`_CRT_BLOCK`块。 这些块是C运行时库函数，内部进行内存分配的，如果它们调用任何C运行时库函数，就会分配内部内存。 可通过将如下代码，放到分配挂钩函数开始处，来忽略`_CRT_BLOCK`块：  
  
```cpp
if ( nBlockUse == _CRT_BLOCK )  
    return( TRUE );  
```  
  
 如果您的分配挂钩不忽略`_CRT_BLOCK`块，那么在挂钩函数中调用任何 C 运行时库函数，可以使用程序进入无限循环。 例如，`printf` 执行内部分配。 如果挂钩代码调用`printf`，则产生的内存分配，将导致您的再次调用挂钩函数，于是将再次调用**printf**，依此类推，直到堆栈溢出。 如果需要报告 `_CRT_BLOCK` 分配内存操作，回避该限制的一种方法是，使用 Windows API 函数而不是 C 运行时函数来进行格式化和输出。 因为 Windows Api 不使用 C 运行库堆，所以它们不会使您的分配挂钩陷入无穷循环。  
  
 如果您检查运行时库源文件，您将看到默认的分配挂钩函数，**CrtDefaultAllocHook** (只是简单的返回**TRUE**)，位于其自身的单独的源文件DBGHOOK.C。 如果希望在应用程序中的**main**函数之前，运行时代码执行内存分配时，分配挂钩函数挂钩被调用，您可以放置你自己的默认函数，代替[_CrtSetAllocHook](/cpp/c-runtime-library/reference/crtsetallochook)。  
  
## <a name="see-also"></a>请参阅  
 [编写调试挂钩函数](../debugger/debug-hook-function-writing.md)   
