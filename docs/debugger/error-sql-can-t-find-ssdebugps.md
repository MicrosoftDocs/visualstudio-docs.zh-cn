---
title: 错误： SQL 找不到 Ssdebugps |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.sqlde_cant_find_ssdebugps
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
ms.openlocfilehash: 1498a287bdb474751dfaa5b4b23c30bc302544e7
ms.sourcegitcommit: 0bf2aff6abe485e3fe940f5344a62a885ad7f44e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2018
ms.locfileid: "37058251"
---
# <a name="error-sql-can39t-find-ssdebugps"></a>错误： SQL 找不到 Ssdebugps

SSDEBUGPS.dll 为 SQL Server Debugging Host 组件。

此错误在尝试开始调试时发生，指示指定的文件在 [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)] 计算机上不存在。 可能的原因是从未运行远程调试安装，或是由于某种原因删除了此文件。

若要解决此错误的两种方式： 通过重新运行远程调试安装，并通过复制文件拖放到[!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)]机。

若要重新运行远程调试安装，请按照的说明[远程调试](../debugger/remote-debugging.md)。

如果可以找到 ssdebugps.dll 的某个副本，可以将其拖到复制[!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)]机。 如果存在，该文件会位于目录 \Program Files\ Common Files\Microsoft Shared\SQL Debugging 中。 你可能会发现它在另一台[!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)]计算机，或已安装 Visual Studio 2005 的计算机上。

若要将 SSDEBUGPS.dll 复制到 SQL Server 2005 计算机上：

1. 将文件复制到具有相同名称和路径的目录上[!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)]机。

2. 通过打开注册**命令提示符下**，并运行以下命令：

    ```cmd
    regsrv32 ssdebugps.dll
    ```
