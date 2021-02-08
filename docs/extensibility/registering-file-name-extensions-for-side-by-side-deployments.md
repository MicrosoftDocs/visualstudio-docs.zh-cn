---
title: 为并行 Ide 注册文件扩展名
description: 了解如何为并行部署注册文件扩展名，这允许用户在适当版本的 Visual Studio 中打开文件。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- file extensions, registering for side-by-side
ms.assetid: 9ab046a2-147d-4167-aa14-7d661b1eaaa5
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a457a3848917eff3d3722a8e72f0b0b720c0b43b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2021
ms.locfileid: "99836990"
---
# <a name="register-file-name-extensions-for-side-by-side-deployments"></a>为并行部署注册文件扩展名
对于在并行环境中部署的 Vspackage，必须注册文件扩展名，以便将文件与正确版本的相关联 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 。 如果你使用特定于版本的文件扩展名，则注册使用户能够在适当版本的中打开你的项目和项目项文件 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 。

## <a name="in-this-section"></a>本节内容
- [关于文件扩展名](../extensibility/about-file-name-extensions.md) 讨论文件扩展名的注册方式。

- [指定文件扩展名的文件处理程序](../extensibility/specifying-file-handlers-for-file-name-extensions.md) 提供有关如何注册可打开、编辑等特定文件扩展名的应用程序的信息。

- [注册文件扩展名的谓词](../extensibility/registering-verbs-for-file-name-extensions.md) 讨论如何注册谓词。

- [管理并行文件关联](../extensibility/managing-side-by-side-file-associations.md) 讨论如何处理并行安装，其中应调用的特定版本 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 来打开文件。

## <a name="related-sections"></a>相关章节
- [支持多个版本的 Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md) 描述 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 在开发和向最终用户部署过程中与 VSPackage 的多个版本相关的问题。
