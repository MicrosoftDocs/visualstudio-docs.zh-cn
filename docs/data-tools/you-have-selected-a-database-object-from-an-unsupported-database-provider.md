---
title: 不受支持的提供程序中的对象
description: 您选择了不受支持的数据库提供程序的数据库对象。 ) 消息查看有关此 Visual Studio (O/R 设计器的信息。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: c0f1298e-31aa-471e-ae19-1bafffd2ae40
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: c3ccd477882382962efcc2f87c5dc99f59c14be1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2021
ms.locfileid: "99858041"
---
# <a name="you-have-selected-a-database-object-from-an-unsupported-database-provider"></a>您从不支持的数据库提供程序选择了数据库对象

**O/R 设计器** 仅支持 SQL Server () 的 .NET Framework 数据提供程序 <xref:System.Data.SqlClient> 。 虽然可以单击“确定”并继续使用来自不支持的数据库提供程序的对象，但在运行时可能遇到意外行为。

> [!NOTE]
> 仅支持使用用于 SQL Server 的 .NET Framework 数据提供程序的数据连接。

## <a name="options"></a>选项

- 单击“确定”，继续设计映射到使用不受支持数据库提供程序的连接的实体类。 使用不支持的数据库提供程序时，可能遇到意外行为。

- 单击 " **取消** " 以停止此操作。 创建或使用用于 SQL Server 的 .NET Framework 提供程序的其他数据连接。

## <a name="see-also"></a>另请参阅

- [Visual Studio 中的 LINQ to SQL 工具](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
