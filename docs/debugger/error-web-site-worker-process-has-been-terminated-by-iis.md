---
title: 错误： 网站辅助进程已被 IIS 终止 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.web_server_process_terminated
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
ms.openlocfilehash: 582cf1b5faf0cc62d85e17544aa03c4ede4ab0a8
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/23/2018
ms.locfileid: "49852838"
---
# <a name="error-web-site-worker-process-has-been-terminated-by-iis"></a>错误：网站辅助进程已被 IIS 终止
调试器已停止对网站执行代码。 这导致 Internet Information Services (IIS) 认为辅助进程已停止响应。 因此，IIS 终止了辅助进程。  
  
 若要继续调试，必须配置 IIS 以使辅助进程继续运行。 在低于 IIS 7 的 IIS 版本中，不会显示此错误消息。  
  
### <a name="to-configure-iis-7-to-allow-the-worker-process-to-continue"></a>配置 IIS 7 以使辅助进程继续运行  
  
1. 打开**管理工具**窗口。  
  
   1.  单击**启动**，然后选择**控制面板**。  
  
   2.  在**控制面板**中，选择**切换到经典视图**，如有必要，然后双击**管理工具**。  
  
2. 在**管理工具**窗口中，双击**Internet Information Services (IIS) Manager**。  
  
    IIS 管理器随即打开。  
  
3. 在**连接**窗格中，展开\<计算机名称 > 节点，如有必要。  
  
4. \<计算机名称 > 节点中，单击**应用程序池**。  
  
5. 在**应用程序池**列表中，右键单击运行的池中你的应用程序名称，然后单击**高级设置**。  
  
6. 在**高级设置**对话框中，找到**进程模型**部分，然后执行以下操作之一：  
  
   - 设置**启用 Ping**到**False**。  
  
   - 设置**Ping 最大响应时间**大于 90 秒的值。  
  
     设置**启用 Ping**到**False** IIS 停止检查辅助进程是否仍在运行，并使工作进程保持活动状态，直到您停止被调试的进程。 设置**Ping 最大响应时间**到较大的值使 IIS 继续监视辅助进程。  
  
7. 单击**确定**以关闭**高级设置**对话框。  
  
8. 关闭 IIS 管理器和**管理工具**窗口。  
  
## <a name="see-also"></a>请参阅  
 [远程调试错误和疑难解答](../debugger/remote-debugging-errors-and-troubleshooting.md)