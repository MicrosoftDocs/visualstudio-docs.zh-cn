---
title: 使用CRT 调试库 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- c.debug.runtime
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- /DEBUG linker option [C++]
- crtdbg.h file
- debug library
- MDd compiler option [C++]
- libraries, CRT debug library
- MTd compiler option [C++]
- LDd compiler function [C++]
- /MTd compiler option [C++]
- /MDd compiler option [C++]
- debugging [CRT], CRT debug library
- DEBUG linker option [C++]
- /LDd compiler function [C++]
ms.assetid: 464de16b-4215-4787-9bfa-921aaff9d9f4
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5e550a5fa705f3c85b3464046cd3c92d96bc47ca
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2018
ms.locfileid: "31467951"
---
# <a name="crt-debug-library-use"></a>CRT 调试库使用
C 运行库提供广泛的调试支持。 若要使用 CRT 调试库之一，你必须与链接[/DEBUG](/cpp/build/reference/debug-generate-debug-info)和使用进行编译 **/MDd**， **/MTd**，或 **/LDd**。  
  
## <a name="remarks"></a>备注  
 CRT 调试的主要定义和宏可在 CRTDBG.h 头文件中找到。  
  
 CRT 调试库中的函数在编译时带有调试信息 ([/Z7、 /Zd、 /Zi、 /ZI （调试信息格式）](/cpp/build/reference/z7-zi-zi-debug-information-format))，而且不进行优化。 某些函数包含断言以验证传递给它们的参数，并且提供源代码。 使用此类源代码，可以单步执行 CRT 函数，以确认这些函数按预期方式工作并检查错误的参数或内存状态。 （某些 CRT 技术是专有技术，不提供用于异常处理、浮点和少数其他例程的源代码。）  
  
 安装 Visual C++ 时，可以选择在硬盘上安装 C 运行库源代码。 如果不安装源代码，将需要 CD-ROM 才能单步执行 CRT 函数。  
  
 你可以使用的各种运行时库的详细信息，请参阅[C 运行时库](/cpp/c-runtime-library/crt-library-features)。  
  
## <a name="see-also"></a>请参阅  
 [CRT 调试技术](../debugger/crt-debugging-techniques.md)   
 [/MD、/MT、/LD（使用运行时库）](/cpp/build/reference/md-mt-ld-use-run-time-library)