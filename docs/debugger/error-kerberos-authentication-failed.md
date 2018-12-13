---
title: '错误: Kerberos 身份验证失败 | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.callback_kerberos_auth_failed
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0cf34885ee715a5685e4c2ced8b5a116e5c33e8d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/23/2018
ms.locfileid: "49857642"
---
# <a name="error-kerberos-authentication-failed"></a>错误：Kerberos 身份验证失败
当尝试进行远程调试时，可能会收到以下错误消息：  
  
```cmd
Error: The Visual Studio Remote Debugger on the target computer cannot connect back to this computer. Kerberos authentication failed.  
```  
  
 当 Visual Studio 远程调试监视器在“本地系统”帐户或“网络服务”帐户下运行时，会发生此错误。 在其中任何一个帐户下，远程调试器都必须建立 Kerberos 身份验证连接，以便向 Visual Studio 调试器主机提供反馈。  
  
 Kerberos 身份验证在下列条件下不可用：  
  
- 目标计算机或调试器主机位于工作组中，而不是位于域中  
  
   \- 或 -  
  
- 域控制器上已禁用 Kerberos。  
  
  如果 Kerberos 身份验证不可用，请更改用于运行 Visual Studio 远程调试监视器的帐户。 有关过程，请参阅[错误： 目标计算机上的 Visual Studio 远程调试器服务无法重新连接到此计算机](../debugger/error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer.md)。  
  
  如果这两台计算机都连接到同一域，而您仍然收到此消息，请验证目标计算机上的 DNS 是否正确解析了调试器主机的名称。 请参见下面的步骤。  
  
### <a name="to-verify-that-dns-on-the-target-computer-is-correctly-resolving-the-debugger-host-computer-name"></a>验证目标计算机上的 DNS 是否正确解析了调试器主机名称  
  
1.  在目标计算机上打开**启动**菜单，依次指向**附件**，然后单击**命令提示符下**。  
  
2.  在**命令提示符下**窗口中，键入：  
  
    ```cmd
    ping <debugger_host_computer_name>  
    ```  
  
3.  `ping` 响应的第一行显示了 DNS 为指定计算机返回的完整计算机名称和 IP 地址。  
  
4.  调试器主机计算机上，打开**命令提示符**窗口，并运行`ipconfig`。  
  
5.  比较 IP 地址值。  
  
## <a name="see-also"></a>请参阅  
 [远程调试错误和故障排除](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Remote Debugging](../debugger/remote-debugging.md)
