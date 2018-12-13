---
title: 错误： 站点使用 IP 地址 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.webdbg_siteusesipaddress
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b726902c57cc95b694f2ab7e656a444ed42a0ba9
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2018
ms.locfileid: "31470899"
---
# <a name="error-site-uses-ip-address"></a>错误：站点使用 IP 地址
调试器尝试自动附加到正在使用 IP 地址的 Web 应用程序时，会发生该错误。 如果你在 IIS 中更改 **网站标识** 到 **使用特定 IP 地址** 发生这种情况。  
  
 要使自动附加能够工作，需要创建具有特定 IP 地址而不只是计算机名称的项目。 否则，调试器会将计算机名称更改为 localhost，而这会导致无法将调试谓词发送到 IIS。  
  
### <a name="to-correct-this-error"></a>更正此错误  
  
1.  改用手动附加 (从调试菜单中，选择**附加到进程**)。  
  
     - 或 -  
  
2.  更改**IIS 网站标识**设置。  
  
## <a name="see-also"></a>请参阅  
 [调试 Web 应用程序：错误和疑难解答](../debugger/debugging-web-applications-errors-and-troubleshooting.md)