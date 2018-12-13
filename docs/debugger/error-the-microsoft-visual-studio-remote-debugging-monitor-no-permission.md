---
title: 错误： Microsoft Visual Studio 远程调试监视器在远程计算机上没有连接到此计算机的权限 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.debug.error.access_denied_oncallback
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- remote debugging, Windows version error
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4bb71667da94027d3170a372a9a570e5e1eea4ba
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/23/2018
ms.locfileid: "49854164"
---
# <a name="error-the-microsoft-visual-studio-remote-debugging-monitor-on-the-remote-computer-does-not-have-permission-to-connect-to-this-computer"></a>错误: 远程计算机上的 Microsoft Visual Studio 远程调试监视器没有连接到此计算机的权限。
当本地计算机上尝试运行的 Visual Studio 远程调试监视器 (msvsmon) 不具有帐户时，会发生此错误。  
  
### <a name="to-fix-this-problem"></a>修复此问题  
  
- 将一个用户帐户添加到 Visual Studio 调试器主机，该帐户与在远程计算机上运行 msvsmon 的用户帐户具有相同的名称和密码。  
  
   \- 或 -  
  
- 以具有调用本地计算机权限的用户身份运行 msvsmon。 这意味着该用户必须是 msvsmon 计算机上的域用户或管理员。 您可以指定该用户帐户以两种方式中的任一种来运行 msvsmon：  
  
  - 右击 msvsmon 图标并选择快捷菜单上的 **运行方式**  
  
    \- 或 -  
  
  - 在命令提示符处，运行 `runas.exe`。  
  
## <a name="see-also"></a>请参阅  
 [远程调试错误和故障排除](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [远程调试](../debugger/remote-debugging.md)