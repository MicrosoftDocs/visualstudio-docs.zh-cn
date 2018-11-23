---
title: COM 服务器和容器调试 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.com
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- ActiveX control container debugging [Visual Studio]
- debugging ActiveX controls
- COM servers, debugging
- ActiveX controls, debugging
- COM [Visual Studio], debugging
ms.assetid: b7ce8696-ebb8-4354-a767-f76b8ada4ac1
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5b4c23d362a930f28ccb1a097de44a936e55cacf
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2018
ms.locfileid: "31458172"
---
# <a name="com-server-and-container-debugging"></a>调试 COM 服务器和容器
COM 应用程序执行若干不直接受程序员控制的任务。 DLL 间的通信、对象的使用计数和剪贴板操作只是可能遇到意外行为的少数几个情况。 发生这种情况时，第一步应是追踪问题的根源。  
  
 在容器和服务器中Visual Studio 调试器支持逐过程和逐语句。 这包括逐过程步过远程过程调用 (RPC) 的能力。  
  
##  <a name="BKMK_COMServerandContainerintheSameSolution"></a> 调试 COM 服务器和同一解决方案中的容器  
 可以使用同一解决方案中的两个项目来调试 COM 服务器和容器。 在每个项目和调试中设置适当的断点。 当容器对服务器进行调用而遇到断点时，容器将一直等到服务器代码返回（即等到完成调试）。  
  
 调试 COM 容器类似于调试标准程序。 一个不同的情况是当调试生成回调事件时（如在容器应用程序上拖动数据）。 这种情况下，必须在回调函数中设置断点。  
  
##  <a name="BKMK_ServerApplicationWithoutContainerInformation"></a> 调试没有容器信息的服务器应用程序  
 如果没有或不想使用容器应用程序的调试信息，那么开始调试服务器应用程序可分三步进行：  
  
1.  像对待普通的应用程序一样开始调试服务器。  
  
2.  按需要设置断点。  
  
3.  启动容器应用程序。  
  
##  <a name="BKMK_DebuggingaServerandDomainIsolationSDIApplication"></a> 调试服务器和域隔离 (SDI) 应用程序  
 如果你正在调试的 SDI 服务器应用程序，你必须指定`/Embedding`或`/Automation`中**命令行自变量**中的属性*项目*属性页对话框中，C/c + +，C# 中，或Visual Basic 项目。  
  
 使用这些命令行自变量，调试器可以像从容器中启动服务器应用程序一样启动它。 从程序管理器或文件管理器启动容器将导致容器使用在调试器中启动的服务器实例。  
  
 访问*项目*属性页对话框中，右键单击解决方案资源管理器中的项目，然后从快捷菜单选择属性。 若要找到“命令行自变量”属性，请展开“配置属性”类别并单击“调试”页。  
  
## <a name="see-also"></a>请参阅  
 [调试 COM 和 ActiveX](../debugger/com-and-activex-debugging.md)