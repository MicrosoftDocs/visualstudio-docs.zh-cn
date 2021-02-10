---
title: 指定要启动的二进制文件 | Microsoft Docs
description: 了解如何在“<Target> 属性页”对话框中输入信息来分析二进制文件，如 DLL。
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.performance.property.itemlaunch
helpviewer_keywords:
- profiling tools, launching
- performance tools, launching
- performance sessions, launching
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 575a55ae654ada9774abed510d66b94e4ce9d271
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2021
ms.locfileid: "99899535"
---
# <a name="how-to-specify-the-binary-to-start"></a>如何：指定要启动的二进制文件

若要分析二进制文件（如 DLL），必须在“\<Target> 属性页”对话框中输入信息。 这些信息指示 DLL 项目查找调用应用程序的位置。

1. 在“性能资源管理器”中，右键单击目标二进制文件，然后单击“属性”。

2. 在“属性页”对话框中单击“启动”属性 。

3. 选中“重写项目属性”复选框。

4. 在“要启动的可执行文件”文本框中，指定文件的位置。

5. 在“参数”文本框中，指定启动应用程序所需的参数。

6. 在“工作目录”文本框中，指定目录的位置。

7. 单击 **“确定”** 。

## <a name="see-also"></a>请参阅

[配置性能会话](../profiling/configuring-performance-sessions.md)
