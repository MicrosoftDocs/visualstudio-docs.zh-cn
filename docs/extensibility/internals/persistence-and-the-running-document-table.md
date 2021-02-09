---
title: 持久性和正在运行的文档表 |Microsoft Docs
description: 了解项目如何在正在运行的文档表中协调文档的打开、保存和重命名，从而在 Visual Studio IDE 中跟踪文档状态。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- persistence, managing
- IVsPersistHierarchyItem interface, implementing
- architecture, persistence
- running document table (RDT), architecture
ms.assetid: 27117eae-6c58-4189-a61a-1397a43b5ecf
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6070cba3e24f16da0bf5619fc979e0d4471971c0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2021
ms.locfileid: "99895435"
---
# <a name="persistence-and-the-running-document-table"></a>持久性和正在运行的文档表
在 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE 中，项目完全负责管理其项目项的持久性，它们使用服务实现 <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable> 。 文档是 Visual Studio 环境中持久性的基本单元。 项目使用正在运行的文档表来协调文档的开始、保存和重命名 (RDT) ，这是跟踪所有打开文档状态的资源。

## <a name="managing-persistence"></a>管理持久性
 项目通过实现接口控制环境的持久性服务 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem> 。 虽然环境不会直接要求文档保持自身，但会要求所属项目 (或层次结构) 保存文档。 这样，项目就可以将其项目项数据保存到本地文件、远程文件、数据库、存储库或其他介质中。

 全局环境会保留 RDT。 环境维护 RDT 中所有打开的窗口和文档的条目，这使得它们可以接收特殊通知，如解决方案关闭时。 此外，RDT 使环境可以在 **解决方案资源管理器** 中跟踪其相应节点。 RDT 针对每个打开的持久对象维护一条记录，其中包括项目文件和项目项文档。

## <a name="see-also"></a>另请参阅
- [运行文档表](../../extensibility/internals/running-document-table.md)
- [IDE 中的选择和货币](../../extensibility/internals/selection-and-currency-in-the-ide.md)
