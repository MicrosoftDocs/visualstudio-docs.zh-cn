---
title: 为 CD 安装启用自动启动 |Microsoft Docs
description: 了解如何在通过可移动媒体（如 cd-rom 或 DVD-ROM）部署 ClickOnce 应用程序时启用自动启动。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, AutoStart
- ClickOnce deployment, installation on CD or DVD
- deploying applications [ClickOnce], installation on CD or DVD
ms.assetid: caaec619-900c-4790-90e3-8c91f5347635
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b157df8666223e72a1e36d58505a5c087b0351bf
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2021
ms.locfileid: "99900677"
---
# <a name="how-to-enable-autostart-for-cd-installations"></a>如何：为 CD 安装启用自动启动
当 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 通过可移动媒体（如 cd-rom 或 dvd-rom）来部署应用程序时，可以启用， `AutoStart` 以便在 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 插入媒体时自动启动应用程序。

 `AutoStart`可以在 "**项目设计器**" 的 "**发布**" 页上启用。

### <a name="to-enable-autostart"></a>启用自动启动

1. 在 **解决方案资源管理器** 中选择一个项目后，在 " **项目** " 菜单上单击 " **属性**"。

2. 单击 **“发布”** 选项卡。

3. 单击“选项”  按钮。

     此时将显示 " **发布选项** " 对话框。

4. 单击“部署”。

5. 选中 " **对于 cd 安装，插入 cd 时将自动启动安装程序** " 复选框。

     发布应用程序时，会将 *自动运行的 .inf* 文件复制到发布位置。

## <a name="see-also"></a>另请参阅
- [发布 ClickOnce 应用程序](../deployment/publishing-clickonce-applications.md)
- [如何：使用发布向导发布 ClickOnce 应用程序](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)