---
title: 调试 64 位应用程序 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], 64-bit
- 64-bit debugging
ms.assetid: db648e5f-6375-4e2d-aa98-eb7261958927
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 28a7625729989252a29ab1d0f65feec010e9e65f
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2018
ms.locfileid: "44284076"
---
# <a name="debug-64-bit-applications"></a>调试 64 位应用程序
您可以调试运行于本地计算机或远程计算机上的 64 位应用程序。  
  
 若要调试在远程计算机上运行的 64 位应用程序，请参阅 [远程调试](../debugger/remote-debugging.md)。  
  
 若要在本地调试 64 位应用程序，Visual Studio 将使用 64 位辅助进程 (msvsmon.exe) 执行不能在 32 位 Visual Studio 进程内执行的低级别操作。  
  
 使用 .NET Framework 3.5 或更早版本的 64 位进程不支持混合模式调试。  
  
## <a name="debug-a-64-bit-application"></a>调试 64 位应用程序  
 若要尝试调试 64 位应用程序：  
  
1.  创建一个 Visual Studio 解决方案，例如 C# 控制台应用程序。  
  
2.  使用配置管理器将配置设置为 64 位。 有关详细信息，请参阅 [如何：配置项目以面向目标平台](../ide/how-to-configure-projects-to-target-platforms.md)。  
  
3.  此时将启动 64 位版本的远程调试器 (msvsmon.exe)。 只要使用的解决方案 64 位配置为打开状态，它就会运行。  
  
4.  开始调试。 你应该具有与 32 位配置相同的体验。 如果出现错误，请参阅下面的“疑难解答”一节。  
  
## <a name="troubleshooting-64-bit-debugging"></a>64 位调试疑难解答  
 可能会遇到错误:"64 位调试操作比预期长。" 在这种情况下，则说明 Visual Studio 已向 64 位版本的 msvsmon.exe 发送请求，返回该请求的结果花费了较长的时间。  
  
 出现此错误的主要原因有两个：  
  
-   你的计算机上所安装的网络安全软件导致网络堆栈不可靠，并且该网络安全软件已删除通过 localhost 的数据包。 请尝试禁用全部的网络安全软件，然后查看该问题是否解决。 如果问题解决，那么请发送报告给你的网络安全软件供应商，说明该软件正在干扰 localhost 通信。  
  
-   你正遇到挂起或 Visual Studio 性能问题。 如果该问题定期发生，你可收集 Visual Studio (devenv.exe) 和辅助进程 (msvsmon.exe) 的转储并将其发送给 Microsoft。 有关报告问题的详细信息，请参阅 [How to Report a Problem with Visual Studio](../ide/How-to-Report-a-Problem-with-Visual-Studio-2017.md)。
  
## <a name="see-also"></a>请参阅  
 [64 位应用程序](https://docs.microsoft.com/dotnet/framework/64-bit-apps)   
 [配置 64 位的程序](/cpp/build/configuring-programs-for-64-bit-visual-cpp)   
 [Visual Studio IDE 64 位支持](../ide/visual-studio-ide-64-bit-support.md)   
 [使用转储文件](../debugger/using-dump-files.md)   
 [远程调试](../debugger/remote-debugging.md)