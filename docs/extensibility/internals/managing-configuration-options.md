---
title: 管理配置选项 |Microsoft Docs
description: 了解如何在 Visual Studio 中管理项目和解决方案配置设置，以控制项目的生成、打包、部署和运行方式。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- configuration options
ms.assetid: 596c28ee-f48d-4252-a5c4-f730c43a39e6
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 565f73b9809f3f18fe6828a19860a46b14ff07e9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2021
ms.locfileid: "99839462"
---
# <a name="managing-configuration-options"></a>管理配置选项
当你创建新的项目类型时，你必须管理项目和解决方案配置设置，这些设置确定如何生成、打包、部署和运行你的项目。 以下主题讨论项目和解决方案配置。

## <a name="in-this-section"></a>本节内容
- [概述](../../extensibility/internals/configuration-options-overview.md)

 描述中的项目如何 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 支持多个配置。

- [属性页](../../extensibility/internals/property-pages.md)

 说明用户可以使用属性页查看和更改项目配置依赖属性和独立属性。

- [解决方案配置](../../extensibility/internals/solution-configuration.md)

 提供有关解决方案配置中存储的内容的信息，以及解决方案配置如何定向 **启动** 和 **生成** 命令的行为。

- [项目配置对象](../../extensibility/internals/project-configuration-object.md)

 说明项目配置对象如何管理向 UI 显示的配置信息。

- [用于生成的项目配置](../../extensibility/internals/project-configuration-for-building.md)

 说明如何通过 " **解决方案配置** " 对话框管理特定解决方案的解决方案配置列表。

- [用于管理部署的项目配置](../../extensibility/internals/project-configuration-for-managing-deployment.md)

 定义部署的行为，并通过两种方式 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 支持支持部署的项目。

- [用于输出的项目配置](../../extensibility/internals/project-configuration-for-output.md)

 介绍每个配置可以支持的生成过程，以及可使输出项可用的接口和方法。

## <a name="related-sections"></a>相关章节
- [项目类型](../../extensibility/internals/project-types.md)

 提供项目概述，作为集成开发环境的基本构建基块 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (IDE) 。 向说明项目如何控制生成和编译代码的其他主题提供了链接。
