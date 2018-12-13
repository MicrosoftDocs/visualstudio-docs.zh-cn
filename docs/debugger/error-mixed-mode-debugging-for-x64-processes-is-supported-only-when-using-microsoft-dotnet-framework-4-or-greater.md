---
title: 错误： 仅当使用 Microsoft .NET Framework 4 或更高版本时才支持对 x64 进程执行混合模式调试 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.interop_unsupported_x64
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: b1e7159c67ab104156f2dccd6d89413594ded33c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/23/2018
ms.locfileid: "49874405"
---
# <a name="error-mixed-mode-debugging-for-x64-processes-is-supported-only-when-using-microsoft-net-framework-4-or-greater"></a>错误：仅当使用 Microsoft .NET Framework 4 或更高版本时才支持对 x64 进程执行混合模式调试
若要调试 64 位进程中的混合本机代码和托管代码，你必须安装了 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 4 版。 低于 4 的 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 版本不支持对 64 位进程进行混合模式调试。  
  
### <a name="to-correct-this-error"></a>更正此错误  
  
- 执行以下步骤之一：  
  
  - 将 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 升级到 4 版。  
  
  - 生成 32 位版本的应用程序以进行调试。  
  
## <a name="see-also"></a>请参阅  
 [Remote Debugging](../debugger/remote-debugging.md)