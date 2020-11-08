---
title: 导入或导出安装配置
titleSuffix: ''
description: 了解如何将安装配置导出到 .vsconfig 文件用于与他人共享，以及如何将其导入进行克隆。
ms.date: 05/18/2019
ms.topic: how-to
f1_keywords:
- vs.about
helpviewer_keywords:
- import installation configuration
- export installation configuration
- install Visual Studio
- Visual Studio installer
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 4dcad21ce0a77e18bed0b077f731a509916e9e63
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/02/2020
ms.locfileid: "85418816"
---
# <a name="import-or-export-installation-configurations"></a>导入或导出安装配置

可以使用安装配置文件在组织中配置 Visual Studio。 若要执行此操作，只需使用 Visual Studio 安装程序将工作负载和组件信息导出到 .vsconfig 文件。 然后便可将配置导入到新安装或现有安装中，并与他人共享。

操作方法如下。

::: moniker range="vs-2017"

> [!NOTE]
> 此功能仅在 Visual Studio 2017 版本 15.9 及更高版本中可用。

::: moniker-end

## <a name="export-a-configuration"></a>导出配置

可以选择从以前安装的 Visual Studio 实例或当前正在安装的 Visual Studio 实例中导出安装配置文件。

1. 打开 Visual Studio 安装程序。

1. 在产品卡中，选择“更多”  按钮，然后选择“导出配置”  。

   ![从 Visual Studio 安装程序的产品卡中导出配置](../install/media/vs-2019/vs-installer-export-config.png)

1. 浏览到或键入要保存 .vsconfig 文件的位置，然后选择“查看详细信息”  。

   ![从 Visual Studio 安装程序中导出配置](../install/media/vs-2019/export-configuration-confirmation.png)

1. 确保已有所需的工作负载和组件，然后选择“导出”  。

## <a name="import-a-configuration"></a>导入配置

当你准备好导入安装配置文件时，请执行以下步骤。

1. 打开 Visual Studio 安装程序。

1. 在产品卡中，选择“更多”  按钮，然后选择“导入配置”  。

1. 找到要导入的 .vsconfig 文件，然后选择“查看详细信息”  。

1. 确保已有所需的工作负载和组件，然后选择“关闭”  。

::: moniker range="vs-2019"

## <a name="automatically-install-missing-components"></a>自动安装缺少的组件

 Visual Studio 2019 新增功能：将 .vsconfig 文件保存到解决方案根目录并打开解决方案时，Visual Studio 会自动检测缺少哪些组件并提示你安装它们。

![解决方案资源管理器建议安装其他组件](../install/media/vs-2019/solution-explorer-config-file.png)

还可以直接从解决方案资源管理器中生成 .vsconfig 文件。

1. 右键单击解决方案文件。

1. 选择“添加”>“安装配置文件”   。

1. 确认要保存 .vsconfig 文件的位置，然后选择“查看详细信息”  。

1. 确保已有所需的工作负载和组件，然后选择“导出”  。

::: moniker-end

> [!NOTE]
> 有关详细信息，请参阅[使用 .vsconfig 在组织中配置 Visual Studio](https://devblogs.microsoft.com/setup/configure-visual-studio-across-your-organization-with-vsconfig/) 博客文章。

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>请参阅

* [创建 Visual Studio 的网络安装](create-a-network-installation-of-visual-studio.md)
* [更新基于网络的 Visual Studio 安装](update-a-network-installation-of-visual-studio.md)
* [控制 Visual Studio 部署的更新](controlling-updates-to-visual-studio-deployments.md)
* [为企业部署设置默认值](set-defaults-for-enterprise-deployments.md)
