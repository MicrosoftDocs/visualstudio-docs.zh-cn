---
title: "如何： 调试自我托管的 WCF 服务 |Microsoft Docs"
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
- debugging, WCF
- WCF, self-hosted service
- WCF, debugging
ms.assetid: 288922be-ba3f-411e-af50-bba39c9529cc
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 255ca0f7d472060d110135536d76de99dc46a18e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/23/2018
ms.locfileid: "49872117"
---
# <a name="how-to-debug-a-self-hosted-wcf-service"></a>如何：调试自我托管的 WCF 服务
一个*自我托管服务（self-hosted service）* 的 WCF 服务是不会在 IIS 中运行，比如 WCF 服务主机（Host）或[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]开发服务器。 调试自我托管（self-hosted）的 WCF ，最简单的方法是在 **调试** 菜单上选择 **启动调试** 时，配置[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 以启动客户端和服务器。  
  
 如果 WCF 服务在内部自我托管（self-hosting），或者进程不能以这种方式启动，如 NT 服务，不能使用此方法。 做为代替方案，可以执行以下操作：  
  
-   手动将调试器附加到宿主（hosting）进程。 有关详细信息，请参阅[附加到正在运行的进程](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)。  
  
     — 或 —  
  
-   开始调试客户端，并随后单步执行对服务的调用。 这要求你在 app.config 文件中启用调试。 有关详细信息[WCF 调试的限制](../debugger/limitations-on-wcf-debugging.md)。  
  
### <a name="to-start-both-client-and-host-from-visual-studio"></a>若要从 Visual Studio 启动客户端和主机（host）  
  
1. 创建[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]包含客户端和服务器项目的解决方案。  
  
2. 将解决方案配置为在你选择时启动客户端和服务器进程**启动**上**调试**菜单。  
  
   1.  在中**解决方案资源管理器**，右键单击解决方案名称。  
  
   2.  单击**设置启动项目**。  
  
   3.  在中**解决方案\<名称 > 属性**对话框中，选择**多个启动项目**。  
  
   4.  在中**多个启动项目**网格中的，对应于服务器项目中，在行上单击**操作**，然后选择**启动**。  
  
   5.  在与客户端项目相对应的行中，单击**操作**，然后选择**启动**。  
  
   6.  单击 **“确定”**。  
  
## <a name="see-also"></a>请参阅  
 [调试 WCF 服务](../debugger/debugging-wcf-services.md)   
 [WCF 调试的限制](../debugger/limitations-on-wcf-debugging.md)   
 [如何：单步执行 WCF 服务](../debugger/how-to-step-into-wcf-services.md)