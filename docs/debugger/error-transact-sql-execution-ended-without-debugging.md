---
title: 错误： TRANSACT-SQL 执行结束，而不进行调试 |Microsoft Docs
ms.custom: ''
ms.date: 11/08/2018
ms.technology: vs-ide-debug
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.sqlde_sql_executed_but_not_debugged
dev_langs:
- CSharp
- VB
- FSharp
- C++
- SQL
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0efb83f6b6cbebc255f6f47c30e3934d74de7870
ms.sourcegitcommit: bc43970c000f07c9cc2051f1264a9742943a9755
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/09/2018
ms.locfileid: "51348995"
---
# <a name="error-transact-sql-execution-ended-without-debugging"></a>错误：Transact-SQL 执行未经调试便已结束

当你尝试调试 TRANSACT-SQL 或 SQLCLR 程序，调试器未从 SQL Server 接收调试消息时，将发生此错误。  
  
此问题可能是由于网络问题或 SQL 服务器上的问题，但最可能的原因是权限问题。  
  
这涉及到两种帐户：  
  
- 应用程序帐户是 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 运行时所用的用户帐户。  
  
- 连接帐户是用于建立到 SQL Server 的连接的标识。 此帐户并不一定像的连接使用 SQL 身份验证运行 Visual Studio 的标识相同。  
  
  SQL 调试要求应用程序帐户必须与连接帐户匹配或者是 sysadmin。  
  
  如果使用的类似于 sa 的 SQL 帐户名称，应用程序帐户必须是设置在 SQL Server 上为系统管理员。 默认情况下，SQL server 运行的计算机上的管理员是 SQL Server 系统管理员。  
  
  若要纠正此错误，可能需要：  
  
  - 验证权限设置。 有关详细信息，请参阅[如何： 设置 SQL Server 调试权限](https://msdn.microsoft.com/84e088d0-0409-41d4-841b-f5d4b0fda414)。  
  
  - 如果设置正确，请确保 SQL 调试也正确。  
  
  - 请咨询网络或数据库管理员。  
  
## <a name="see-also"></a>请参阅

- [设置 SQL 调试](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/s4sszxst(v=vs.100))
- [如何： 设置 SQL Server 权限以进行调试](https://msdn.microsoft.com/84e088d0-0409-41d4-841b-f5d4b0fda414)
- [调试器设置和准备](../debugger/debugger-settings-and-preparation.md)
- [Remote Debugging](../debugger/remote-debugging.md)