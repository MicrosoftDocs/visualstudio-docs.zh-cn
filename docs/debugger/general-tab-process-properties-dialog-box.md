---
title: 常规选项卡，进程属性对话框 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: reference
helpviewer_keywords:
- Process properties for Windows NT
ms.assetid: 86f4d61d-a594-4aac-8960-c5279b4a10fd
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3dcefc8be643c74349102261725c4879c0e161cd
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2018
ms.locfileid: "31471695"
---
# <a name="general-tab-process-properties-dialog-box"></a>常规选项卡，进程属性对话框
使用**常规**选项卡以找出有关特定的进程的详细信息。 若要显示[进程属性对话框](../debugger/process-properties-dialog-box.md)，移动焦点到[进程视图](../debugger/processes-view.md)窗口。 在树中，选择任何进程节点，然后从**视图**菜单选择**属性**。  
  
 以下设置可在**常规**选项卡中获得：  
  
|条目|描述|  
|-----------|-----------------|  
|**模块名**|模块的名称。|  
|**进程 ID**|此进程的唯一 ID。 进程 ID 号会重复使用，以便它们仅针对该进程的生存期的标识过程。 运行程序时创建的进程对象类型。 在进程中的所有线程共享相同的地址空间，并有权访问相同的数据。|  
|**优先级基数**|此进程当前基本优先级。 进程中的线程可以引发和降低其自己的基本优先级相对于进程的基本优先级。|  
|**线程**|此过程中处于活动状态的线程数。|  
|**CPU 时间**|在此过程，并且其线程上花费的总 CPU 时间。 用户时间加上 Privileged 的 Time 等于。|  
|**用户的时间**|此进程的线程正在执行代码在用户模式下在非空闲线程所用累计运行时间。 子系统，如窗口管理器和图形引擎一样，应用程序在用户模式中执行。|  
|**Privileged 的 Time**|总运行时间此进程已运行在特权模式下在非空闲线程中。 服务层、 高级管理人员例程和内核在特权模式下中执行。 图形适配器和打印机以外的大多数设备的设备驱动程序还执行在特权模式下。 除了 Privileged Time 其他子系统进程对 Windows 应用程序执行某些工作可能会出现。|  
|**运行时间**|总运行时间此进程已运行。|