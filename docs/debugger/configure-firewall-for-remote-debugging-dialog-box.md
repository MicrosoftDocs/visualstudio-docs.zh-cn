---
title: “为远程调试配置防火墙”对话框 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.firewallconfiguration
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- Configure Firewall for Remote Debugging dialog box
- remote debugging, configuring firewalls
- firewalls, configuring for remote debugging
ms.assetid: 5dff3393-fdeb-4129-a2f6-31f653107a82
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 982e677639cec6a98ae3aafe3d0ae624df588ccd
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2018
ms.locfileid: "31459644"
---
# <a name="configure-firewall-for-remote-debugging-dialog-box"></a>“为远程调试配置防火墙”对话框
当 Windows 防火墙阻止调试器在网络上接收信息时，会出现此对话框。 若要继续进行远程调试，您必须在防火墙上打开一个入口以使调试器能够接收信息。  
  
> [!CAUTION]
>  如果在防火墙上打开一个入口，可能会使计算机暴露在防火墙应该阻止的安全威胁之下。 在 Visual Studio 2015 中，打开一个入口进行远程调试将取消阻止端口 4020 和 4021。 在其他版本的 Visual Studio 中，将使用其他端口号。 有关详细信息，请参阅[远程调试器端口分配](../debugger/remote-debugger-port-assignments.md)。 此外，它还允许调试器打开其他端口。 有关详细信息，请参阅[配置 Windows 防火墙以进行远程调试](../debugger/configure-the-windows-firewall-for-remote-debugging.md)。  
  
## <a name="uielement-list"></a>UIElement 列表  
 **取消远程调试**  
 取消尝试远程调试。 计算机的安全设置保持不变。  
  
 **取消阻止从本地网络 （子网） 上的计算机进行远程调试**  
 启用本地子网中的计算机的远程调试。 这可能会将安全漏洞暴露给本地子网上的计算机，但是防火墙将继续阻止来自子网外的信息。  
  
 **取消阻止从任何计算机的远程调试**  
 启用网络上任何位置的计算机的远程调试。 此设置是最不安全的。  
  
## <a name="see-also"></a>请参阅  
 [调试器安全](../debugger/debugger-security.md)   
 [远程调试](../debugger/remote-debugging.md)  
 [调试用户界面参考](../debugger/debugging-user-interface-reference.md)