---
title: 浏览存储以上传数据
description: 了解如何在远程计算机或 Azure 文件共享上访问所有存储，以上传数据或下载模型和日志。
ms.custom: SEO-VS-2020
author: jillre
ms.author: jillfra
manager: jmartens
monikerRange: vs-2017
ms.date: 11/13/2017
ms.topic: how-to
ms.workload:
- multiple
ms.openlocfilehash: c32fc5f4ceeb090c8c602b01078fd446249f33eb
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2021
ms.locfileid: "99841414"
---
# <a name="browse-storage-to-upload-data-or-download-models-and-logs"></a>浏览存储以上传数据或下载模型和日志

可以在远程计算机或 Azure 文件共享上访问所有存储，以上传数据或下载模型和日志。 或者，如果要访问特定作业的日志和作业输出，也可以在作业浏览器中执行相同的操作。

## <a name="to-access-all-data-on-the-remote-machine-or-file-share"></a>访问远程计算器或文件共享上的所有数据

1. 打开“服务器资源管理器”。
2. 展开远程计算机或 Batch AI 计算上下文。
3. 右键单击“存储”；然后单击“浏览” 。

    ![服务器资源管理器的屏幕截图，其中展开了“远程计算机”文件夹。 文件夹树中突出显示了“存储”，并且上下文菜单中已选中“浏览”。](media/manage-storage/browse-storage.png)

## <a name="to-access-job-specific-data-on-the-remote-machine-or-file-share"></a>在远程计算机或文件共享上访问作业特定数据

1. 打开 [“作业历史记录”](job-details.md)
2. 选择作业。
3. 单击“工作文件夹”，或单击 StdOut/Stderr 快速访问这些重要的日志文件 。

    ![服务器资源管理器中“作业浏览器”窗口的屏幕截图。 train_mnist 作业处于选中状态，并且在“作业详细信息”下选中了“工作文件夹”链接。](media/manage-storage/job-workingfolder.png)
