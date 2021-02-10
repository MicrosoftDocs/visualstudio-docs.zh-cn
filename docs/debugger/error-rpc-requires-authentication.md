---
title: RPC 要求身份验证 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.rpc_requires_authentication
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 09901453fc602deaa509ceb15e4c571764d407a4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2021
ms.locfileid: "99871364"
---
# <a name="error-rpc-requires-authentication"></a>错误：RPC 要求身份验证
Visual Studio 调试器无法连接到远程计算机。 本地计算机上启用了阻止远程调试的 RPC 策略。

### <a name="to-correct-this-error"></a>更正此错误

1. 运行 `\`windir`\system32\regedt32.exe`

2. 找到并删除 `HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Windows NT\RPC\RestrictRemoteClients`。

3. 重新启动计算机以使注册表更改生效。

4. 如果问题仍然存在，请联系域管理员，咨询“计算机配置”>“管理模板”>“系统”>“远程过程调用”>“用于未验证的 RPC 客户端的限制”组策略设置方面的问题。