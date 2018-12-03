---
title: CRT 调试技术 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- c.runtime.debugging
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [CRT]
- CRT, debugging
- debugging [C++], CRT debug support
ms.assetid: 9be561f6-14a8-44ff-925d-d911d5b8e6ff
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 890dec4a47a4dd49fa75521aaad068d331652a92
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2018
ms.locfileid: "31458422"
---
# <a name="crt-debugging-techniques"></a>CRT 调试技术
如果调试使用 C 运行库的程序，这些调试技术可能会有用。  
  
## <a name="in-this-section"></a>本节内容  
 [CRT 调试库使用](../debugger/crt-debug-library-use.md)  
 描述由 C 运行库提供的调试支持并提供有关访问这些工具的说明。  
  
 [用于报告的宏](../debugger/macros-for-reporting.md)  
 相关信息提供 **_RPTn**和 **_RPTFn**宏 （在 CRTDBG 中定义。H)，它们取代了的`printf`语句进行调试。  
  
 [堆分配函数的调试版本](../debugger/debug-versions-of-heap-allocation-functions.md)  
 讨论堆分配函数的特殊“Debug”版本，包括：CRT 如何映射调用、显式调用它们的好处、如何避免转换、跟踪客户端块中单独的分配类型和不调用 _DEBUG 的结果。  
  
 [CRT 调试堆详细信息](../debugger/crt-debug-heap-details.md)  
 提供指向某些主题的链接，这些主题包括内存管理和调试堆，调试堆上的块类型，如何使用调试堆，堆状态报告函数，以及跟踪堆分配请求等。  
  
 [编写调试挂钩函数](../debugger/debug-hook-function-writing.md)  
 列出指向客户端块挂钩函数、分配挂钩函数、分配挂钩和 CRT 内存分配以及报告挂钩函数的链接。  
  
 [使用 CRT 库查找内存泄漏](../debugger/finding-memory-leaks-using-the-crt-library.md)  
 介绍有关使用调试器和 C 运行库检测和隔离内存泄漏的方法。  
  
## <a name="related-sections"></a>相关章节  
 [调试本机代码](../debugger/debugging-native-code.md)  
 讨论 C 和 C++ 应用程序的一些常见调试问题和技术。  
  
 [调试器安全](../debugger/debugger-security.md)  
 提供更为安全的调试的建议。