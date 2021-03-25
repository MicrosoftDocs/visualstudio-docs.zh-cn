---
title: 连接到团队资源管理器中的项目
description: 了解如何使用 Visual Studio 中的团队资源管理器，与团队成员一起开发和管理项目。
ms.custom: SEO-VS-2020
ms.date: 11/17/2020
ms.topic: conceptual
ms.author: tglee
author: TerryGLee
ms.manager: jillfra
ms.openlocfilehash: 58603b72128af1c6dd9caae93f92c435f0851ada
ms.sourcegitcommit: 3fc099cdc484344c781f597581f299729c6bfb10
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/19/2021
ms.locfileid: "104672990"
---
# <a name="connect-to-projects-in-team-explorer"></a>连接到团队资源管理器中的项目

::: moniker range="vs-2017"

使用“团队资源管理器”工具窗口与其他团队成员协调代码工作，以开发项目，并管理分配给你、你的团队或项目的工作。 团队资源管理器将 Visual Studio 连接到 Git 和 GitHub 存储库、Team Foundation 版本控制 (TFVC) 存储库以及 [Azure DevOps Services](/azure/devops/user-guide/what-is-azure-devops-services) 或本地 [Azure DevOps Server](/azure/devops/index-all)（以前称为 TFS）上托管的项目。 你可管理源代码、工作项和生成。

::: moniker-end

::: moniker range="vs-2019"

可以使用“团队资源管理器”工具窗口与其他团队成员协调代码工作，以开发项目，并管理分配给你、你的团队或项目的工作。

> [!IMPORTANT]
> 在最新发布的 Visual Studio 2019 [版本 16.8](/visualstudio/releases/2019/release-notes/) 中，现在默认为启用新的 Git 版本控制体验。 不过，如果更希望继续使用团队资源管理器，则转到“工具” > “选项” > “环境” > “预览功能”，然后切换“新的 Git 用户体验”复选框。 有关详细信息，请参阅 [Visual Studio 中的 Git 体验](git-with-visual-studio.md)页面。

团队资源管理器将 Visual Studio 连接到 Git 和 GitHub 存储库、Team Foundation 版本控制 (TFVC) 存储库以及 [Azure DevOps Services](/azure/devops/user-guide/what-is-azure-devops-services) 或本地 [Azure DevOps Server](/azure/devops/index-all)（以前称为 TFS）上托管的项目。 你可管理源代码、工作项和生成。

::: moniker-end

![Visual Studio 中的团队资源管理器主页](media/team-explorer/team-explorer.png "Visual Studio 中的团队资源管理器主页。")

::: moniker range="vs-2017"

> [!TIP]
> 如果打开 Visual Studio 但未显示团队资源管理器，请从菜单栏中选择“视图” > “团队资源管理器”将其打开，或者通过按“Ctrl+\”和“Ctrl+M”      。

::: moniker-end

## <a name="connect-to-a-project-or-repository"></a>连接到项目或存储库

连接到“连接”页上的项目或存储库。

![团队资源管理器中的“连接”页](media/team-explorer/connect.png "Visual Studio 中的团队资源管理器“连接”页面")

要连接到项目：

1. 选择“管理连接”图标，打开“连接”页 。

   ![团队资源管理器中的“管理连接”按钮](media/team-explorer/manage-connections.png "Visual Studio 中的团队资源管理器“管理连接”按钮。")

1. 在“连接”页上，选择“管理连接” > “连接到项目”  。

   ![连接到团队资源管理器中的项目](media/team-explorer/connect-project.png "Visual Studio 中的团队资源管理器“连接到项目”页面。")

> [!TIP]
> 如果要打开存储库中的项目，请参阅[打开存储库中的项目](../get-started/tutorial-open-project-from-repo.md)。 如果要创建新项目或将用户添加到项目，请参阅[创建项目 (Azure DevOps)](/azure/devops/organizations/projects/create-project) 和[将用户添加到项目或团队 (Azure DevOps)](/azure/devops/organizations/security/add-users-team-project)。

## <a name="see-also"></a>请参阅

- [并行比较 Git 和团队资源管理器](git-team-explorer-feature-comparison.md)
- [Visual Studio 中的 Git 新体验](git-with-visual-studio.md)
- [教程：打开存储库中的项目](../get-started/tutorial-open-project-from-repo.md)
- [团队资源管理器参考](reference/team-explorer-reference.md)
- [连接到项目 (Azure DevOps)](/azure/devops/organizations/projects/connect-to-projects)
- [排查项目连接问题](/azure/devops/user-guide/troubleshoot-connection?view=azure-devops&preserve-view=true)
