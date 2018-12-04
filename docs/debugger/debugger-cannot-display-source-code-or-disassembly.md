---
title: 调试器不能显示源代码或反汇编 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- disassembly code, errors
ms.assetid: 112d3ea3-fdd2-4bce-92b4-167a76258934
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 313a0e9e5727d776eaeb13f1c4cef8cf3d8d3bb9
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2018
ms.locfileid: "31472693"
---
# <a name="debugger-cannot-display-source-code-or-disassembly"></a>调试器不能显示源代码或反汇编
此错误显示如下：  
  
 代码在当前位置停止执行，但调试器不能显示当前位置的源代码或反汇编。  
  
 该错误信息可能由于许多原因而发生：  
  
-   可能断点的地方没有对应的源代码，同时当前调试的语言不支持反汇编。 打开**断点**窗口，找到所需断点，并将其删除。  
  
-   如果正在调试脚本，则可能在程序中没有线程时命中了某个断点。 从**调试**菜单中选择**步入**或**继续**继续进行调试。  
  
-   出于安全考虑，调试器当前调试的程序，可能禁止读取堆栈、线程和其他上下文信息。 如果正在调试 Web 应用程序，且没有访问虚拟内存的正确权限，这种情况最可能发生。 将虚拟目录的安全性设置为 Anonymous 并再次尝试。  
  
## <a name="see-also"></a>请参阅  
 [在 Visual Studio 中调试](../debugger/index.md)[调试器功能教程](../debugger/debugger-feature-tour.md)   
 [查看调试器中的数据](../debugger/viewing-data-in-the-debugger.md)