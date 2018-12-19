---
title: "在单步跟踪程序时保持焦点 | Microsoft Docs"
ms.custom: "seodec18"
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.stepping
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [C++], stepping
- focus, keeping
- stepping, focus
- windows, troubleshooting activation
ms.assetid: 11a30580-3a1a-4be8-a241-0abdc758302e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 509e169c7ede0d96882fa2c97eaf7b2c6eb78afb
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2018
ms.locfileid: "44280904"
---
# <a name="how-can-i-keep-focus-when-stepping-through-my-program"></a>如何在单步跟踪程序时保持焦点？
## <a name="description"></a>描述  
 我的程序存在窗口激活问题。用调试器单步跟踪程序时，因为程序不断失去焦点，所以妨碍了再现问题。 是否有方法可以避免该问题？  
  
## <a name="solution"></a>解决方案  
 如果有另一台计算机，请使用远程调试。 可以在远程计算机上运行您的程序，而在主机上运行调试器。 有关详细信息，请参阅[如何： 选择远程计算机](/previous-versions/visualstudio/visual-studio-2010/w8wtw2f3(v=vs.100))。  
  
## <a name="see-also"></a>请参阅  
 [调试本机代码常见问题解答](../debugger/debugging-native-code-faqs.md)   
 [附加到正在运行的进程](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [调试本机代码](../debugger/debugging-native-code.md)