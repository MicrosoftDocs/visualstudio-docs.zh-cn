---
title: "在调试器外部运行程序时，发生调试访问冲突 | Microsoft Docs"
ms.custom: "seodec18"
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.access
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- access violation debugging
- debugging [Visual Studio], access violations
ms.assetid: 780a298a-132e-4245-8370-8c82ca27c6c1
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 47941b2d98029c6466451fb947e31e71d14e6c57
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2018
ms.locfileid: "31473005"
---
# <a name="how-can-i-debug-access-violations-when-running-my-program-outside-the-debugger"></a>在调试器外部运行程序时，如何处理调试访问冲突？

## <a name="problem-description"></a>问题描述  
 我的程序在 Visual Studio 环境中运行良好，但在 Windows 操作系统中独立运行时发生访问冲突。 如何通过调试处理该问题？  
  
## <a name="solution"></a>解决方案  
 设置[实时调试](../debugger/just-in-time-debugging-in-visual-studio.md)选项并运行独立程序，直到发生访问冲突。 然后，在**访问冲突**对话框中，你可以单击**取消**以启动调试器。  
  
## <a name="see-also"></a>请参阅  
 [调试本机代码常见问题](../debugger/debugging-native-code-faqs.md)   
 [调试本机代码](../debugger/debugging-native-code.md)