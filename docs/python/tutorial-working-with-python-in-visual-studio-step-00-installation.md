---
title: Visual Studio 中的 Python 教程步骤 0，安装
titleSuffix: ''
description: 在 Visual Studio 中使用 Python 的核心教程的第 0 步（安装前提条件）。
ms.date: 01/28/2019
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 96c067d4c55a5df4d9343e60360142466e8f218f
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/20/2020
ms.locfileid: "62431275"
---
# <a name="install-python-support-in-visual-studio"></a>在 Visual Studio 中安装 Python 支持

> [!Note]
> 目前仅在 Visual Studio for Windows 中提供 Python 支持；在 Mac 和 Linux 上，可通过 [Visual Studio Code](https://code.visualstudio.com/docs/python/python-tutorial) 获取 Python 支持。

1. 下载并运行适用于 Windows 的最新 Visual Studio 安装程序（版本 15.2 及更高版本提供 Python 支持）。 如果已安装 Visual Studio，请运行 Visual Studio 安装程序，并转到步骤 2。

    > [!div class="nextstepaction"]
    > [安装 Visual Studio Community](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Community&rel=15&rid=34347&utm_source=docs&utm_medium=clickbutton&utm_campaign=python_gettingstarted)

    >[!Tip]
    > Community Edition 适用于个体开发者、课堂学习、学术研究和开放源代码开发。 对于其他用途，请安装 [Visual Studio Professional](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Professional&rel=15&rid=34347&utm_source=docs&utm_medium=clickbutton&utm_campaign=python_gettingstarted) 或 [Visual Studio Enterprise](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Enterprise&rel=15&rid=34347&utm_source=docs&utm_medium=clickbutton&utm_campaign=python_gettingstarted)。

1. 安装程序提供工作负载列表，即一组用于特定开发领域的相关选项。 对于 Python，请选择 **Python 开发** 工作负载，然后选择“安装”：

    ![Visual Studio 安装程序中的 Python 开发工作负载](media/installation-python-workload.png)

1. 若要快速测试 Python 支持，请启动 Visual Studio，按 Alt+I 打开 Python 交互窗口，然后输入 `2+2`。 如果看不到输出 `4`，请重新检查步骤。

    ![通过交互窗口测试 Python](media/installation-interactive-test.png)

## <a name="next-step"></a>下一步

> [!div class="nextstepaction"]
> [步骤 1：创建 Python 项目](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)

## <a name="see-also"></a>另请参阅

- [手动标识现有的 Python 解释器](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment)
- [在 Visual Studio 2015 及更早版本中安装 Python 支持](installing-python-support-in-visual-studio.md)
- [安装位置](installing-python-support-in-visual-studio.md#install-locations)
