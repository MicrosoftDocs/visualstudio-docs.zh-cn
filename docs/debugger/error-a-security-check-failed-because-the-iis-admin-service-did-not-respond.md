---
description: 当 IIS 管理服务没有响应时，会发生此错误。
title: 安全检查失败，因为 IIS 管理服务没有响应 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.iis_not_responding
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 42c0a5a1a1fdb3a997f46a6933df9c8681fe0498
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2021
ms.locfileid: "102147077"
---
# <a name="error-a-security-check-failed-because-the-iis-admin-service-did-not-respond"></a>错误：安全检查失败，因为 IIS 管理服务没有响应
当 IIS 管理服务没有响应时，会发生此错误。 这通常表示 IIS 的安装有问题。 首先，请使用“管理工具”中的“服务”工具验证该服务是否正在运行 。

### <a name="to-correct-this-error"></a>更正此错误

- 使用“添加或删除程序”控制面板重新安装 IIS。

- \- 或 -

- 使用控制面板中的 “添加/删除程序” 从计算机中删除 IIS。 如果已移除 IIS，但是仍存在问题，请检查注册表，并确保下面的项不再存在：

    `HKEY_CLASSES_ROOT\CLSID\{A9E69610-B80D-11D0-B9B9-00A0C922E750}`

     \- 或 -

- 使用“管理工具”控制面板禁用 IIS 管理服务。 这将在您的计算机上禁用 IIS。

     执行这三个步骤中的任一步骤后，重新启动计算机。

     有关其他信息，请参见 IIS 文档。

## <a name="see-also"></a>请参阅
- [调试 Web 应用程序：错误和疑难解答](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
