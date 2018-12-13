---
title: 错误：远程计算机上的 Microsoft Visual Studio 远程调试监视器正以其他用户身份运行 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: troubleshooting
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- -anyuser option
- anyuser option
- Remote Debugging Monitor
- remote debugging, Remote Debugging Monitor
- msvsmon.exe
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e2bdc731b65a8d451b6882914e8bed1abca2139b
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2018
ms.locfileid: "31482017"
---
# <a name="error-the-microsoft-visual-studio-remote-debugging-monitor-on-the-remote-computer-is-running-as-a-different-user"></a>错误：远程计算机上的 Microsoft Visual Studio 远程调试监视器正以其他用户身份运行
当尝试执行远程调试时，您可能会收到如下错误信息：  
  
 远程计算机上的“Microsoft Visual Studio 远程调试监视器”正在以其他用户身份运行。  
  
## <a name="cause"></a>原因  
 当您正在“无身份验证”模式下进行调试时，启动 msvsmon 的用户不是运行 Visual Studio 的用户时，会出现此消息。  
  
## <a name="solution"></a>解决方案  
 最安全也是最好的解决方案是，以与运行 Visual Studio 相同的用户帐户运行远程调试监视器 (msvsmon.exe)。 如果无法做到这一点，你可以在远程调试监视器中选择**选项**对话框，使用其他用户帐户运行远程调试监视器**允许任何用户进行调试**。  
  
> [!CAUTION]
>  授予其他用户进行连接的权限可能会导致意外地连接到错误的远程调试会话。 在**无身份验证**模式中调试不安全，应谨慎使用。
  
## <a name="see-also"></a>请参阅  
 [远程调试错误和疑难解答](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [远程调试](../debugger/remote-debugging.md)