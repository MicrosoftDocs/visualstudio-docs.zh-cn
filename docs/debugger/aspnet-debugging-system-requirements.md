---
title: ASP.NET 调试： 系统要求 |Microsoft Docs
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
- debugging ASP.NET Web applications, system requirements
- debugging ASP.NET Web applications, security requirements
ms.assetid: 7810b9b2-debf-4271-8fc7-1df031123255
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: 71b6cbc3f523b8f21b21b0e69b1d6e45e23acb0c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/23/2018
ms.locfileid: "49915342"
---
# <a name="aspnet-debugging-system-requirements"></a>ASP.NET 调试：系统要求
本主题描述了 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 调试方案的软件和安全性要求：  
  
- 本地调试：其中， [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 和 Web 应用程序在同一台计算机上运行。 此方案有两种版本：  
  
  - [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 代码驻留在文件系统中。  
  
  - [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 代码驻留在 IIS 网站中。  
  
- 远程调试：其中， [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 在客户端计算机上运行，并对在远程服务器计算机上运行的 Web 应用程序进行调试。  
  
## <a name="security-requirements"></a>安全性要求  
 对于远程调试，本地和远程计算机必须位于域设置或工作组设置上。  
  
 若要调试[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]（宿主应用程序池） 的工作进程，您必须有权调试该进程。 默认情况下[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]低于 IIS 6.0 的应用程序运行**ASPNET**用户。 在 IIS 6.0 和 IIS 7.0 中默认帐户是**网络服务**。 如果辅助进程作为 **“ASPNET”** 或 **“NETWORK SERVICE”** 运行，则您必须具有管理员权限才能对它进行调试。

 > [!IMPORTANT]
 > 从 Windows Server 2008 R2 开始，我们建议使用[ApplicationPoolIdentity](/iis/manage/configuring-security/application-pool-identities)作为为每个应用程序池标识。
  
 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 辅助进程的名称根据调试方案和 IIS 版本的不同而不同。 有关详细信息，请参阅 [如何: 找到ASP.NET进程名称](../debugger/how-to-find-the-name-of-the-aspnet-process.md)。  
  
 可以通过编辑运行 IIS 服务器上的 machine.config 文件，来更改运行 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 辅助进程的用户帐户。 实现此目的的最佳方式是使用 **“Internet 信息服务(IIS)管理器”**。 有关详细信息，请参阅[如何： 在用户帐户之上运行辅助进程](../debugger/how-to-run-the-worker-process-under-a-user-account.md)。  
  
 如果将 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 辅助进程更改为在您自己的用户帐户下运行，则您不必是运行 IIS 服务器上的管理员。  
  
> [!CAUTION]
>  在将 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 辅助进程更改为使用其他帐户运行之前，应考虑如果 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 辅助进程在使用该帐户运行时，受到黑客攻击后，将可能出现哪些后果。 ASPNET 和 NETWORK SERVICE 用户帐户以最低的权限运行，从而降低了进程受到攻击时可能造成的损坏程度。 如果必须将 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 辅助进程更改为使用具有较高权限的帐户运行，则会增大受损的可能性。  
  
## <a name="see-also"></a>请参阅  
 [调试 ASP.NET 应用程序](../debugger/how-to-enable-debugging-for-aspnet-applications.md)   
 [如何：在用户帐户下运行辅助进程](../debugger/how-to-run-the-worker-process-under-a-user-account.md)