---
title: 尝试联系远程计算机时出现 DCOM 错误。 拒绝访问。 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.remote.dcom_access_denied
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- remote debugging, DCOM error
- remote DCOM access denied error
- DCOM, access errors
ms.assetid: 9d7dfc1b-9fe0-4f54-9c50-9c0e0f8358c5
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 193c93e7c29d3ea9fa13c08c9d77e4e88026d814
ms.sourcegitcommit: 97204b85caadbcf14baeb6738710e287a196673e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "49900509"
---
# <a name="a-dcom-error-occurred-trying-to-contact-the-remote-computer-access-is-denied"></a>尝试联系远程计算机时出现 DCOM 错误。 拒绝访问。
 如下情景远程调试时，通过 DCOM 将本地和远程计算机进行通信：  
  
- 调试器设置为**本机兼容模式**或**托管兼容模式**签入**工具 > 选项 > 调试**页  
  
- 调试的是托管 C++ (C++/CLI) 代码。  
  
- 在 Visual Studio 2013 中，当**启用本机编辑并继续**签入**工具 > 选项 > 调试**页  
  
- 某些第三方调试方案  
  
  当 Visual Studio 进程无法通过 DCOM 针对远程调试器进程验证自己的身份（或提供的凭据被视为不足）时，将出现此错误。 以下一个或多个解决方法可解决此问题：  
  
- 关闭“本机兼容模式”   和“托管兼容模式” 。  
  
- 在 Visual Studio 2013 中，关闭“启用本机编辑并继续” 。  
  
- 重新启动这两台计算机。  
  
- 如果远程调试要求输入凭据，则选中该选项以保存凭据。  
  
## <a name="see-also"></a>请参阅  
 [远程调试错误和故障排除](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [远程调试](../debugger/remote-debugging.md)