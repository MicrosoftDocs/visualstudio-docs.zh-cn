---
title: 配置 Windows 防火墙以进行远程调试 |Microsoft Docs
ms.custom: ''
ms.date: 10/31/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 66e3230a-d195-4473-bbce-8ca198516014
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d4e4ccc09d8919260b1634fd02790c1bf5b10636
ms.sourcegitcommit: 1df0ae74af03bcf0244129a29fd6bd605efc9f61
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/01/2018
ms.locfileid: "50750931"
---
# <a name="configure-windows-firewall-for-remote-debugging"></a>配置 Windows 防火墙以进行远程调试

Windows防火墙保护电脑网络安全，进行远程调试时防火墙必须配置为允许。 在安装或启动时，Visual Studio 和远程调试工具尝试打开正确的防火墙端口，但可能还需要打开端口或手动允许应用程序。 

本主题介绍如何在Windows 10、8/8.1 和 7， 以及Windows Server 2012 R2、 2012年和 2008 R2上设置Windows 防火墙，进行远程调试。Visual Studio 和远程计算机无需运行相同的操作系统。 例如，运行Visual Studio 的计算机可以使用 Windows 10 ，远程计算机可以运行 Windows Server 2012 R2。      
  
>[!NOTE]
>在不同操作系统上和较旧版本的 Windows上，有关配置 Windows 防火墙的说明略有不同。 Windows 8/8.1、 Windows 10 和 Windows Server 2012 设置使用单词*应用程序*，而 Windows 7 和 Windows Server 2008 使用单词*程序*。  

## <a name="configure-ports-for-remote-debugging"></a>配置用于远程调试的端口  

Visual Studio 和远程调试器在安装或启动期间尝试打开正确的端口。 但是，在某些情况下，如使用第三方防火墙时，你可能需要手动打开端口。 

**若要打开的端口：**
  
1. 在 Windows 中**开始**菜单中，搜索并打开**高级安全 Windows 防火墙**。 在 Windows 10 中，为**具有高级安全性的 Windows Defender 防火墙**。
   
1. 对于新的打开端口，选择**入站规则**，然后选择**新规则**。 对于传出的规则，请选择**出站规则**相反。

1. 在中**新建入站规则向导**，选择**端口**，然后选择**下一步**。 
   
1. 选择任一**TCP**或**UDP**，取决于下表中的端口号。
   
1. 下**特定本地端口**，从下表中，输入端口号，然后选择**下一步**。
   
1. 选择**允许连接**，然后选择**下一步**。
   
1. 选择一个或多个网络类型，若要启用，包括远程连接的网络类型，然后选择**下一步**。
   
1. 添加规则的名称 (例如， **msvsmon**， **IIS**，或**Web 部署**)，然后选择**完成**。

   新规则应出现和中选定**入站规则**或**出站规则**列表。

### <a name="ports-on-the-remote-computer-that-enable-remote-debugging"></a>在远程计算机上启用远程调试端口

对于远程调试，必须在远程计算机上打开以下端口：

|**端口**|**传入/传出**|**协议**|**说明**|   
|-|-|-|-|
|4022|传入|TCP|VS 2017。 每个 Visual Studio 版本端口号码递增 2。 有关详细信息，请参阅[Visual Studio 远程调试器端口分配](../debugger/remote-debugger-port-assignments.md)。|  
|4023|传入|TCP|VS 2017。 每个 Visual Studio 版本端口号码递增 2。 此端口是仅用于64 位版本的远程调试器远程调试 32 位进程。 有关详细信息，请参阅[Visual Studio 远程调试器端口分配](../debugger/remote-debugger-port-assignments.md)。| 
|3702|传出|UDP|（可选）必须远程调试器搜索。|    
  
如果选择**使用托管兼容模式**下**工具** > **选项** > **调试**，打开这些附加远程调试器端口。 调试器托管兼容模式，使旧、 Visual Studio 2010 版本的调试器。 

|**端口**|**传入/传出**|**协议**|**说明**|  
|-|-|-|-|  
|135, 139, 445|传出|TCP|必须的。|  
|137, 138|传出|UDP|必须的。|  

如果您的域策略要求通过 IPSec 进行网络通信，则必须打开 Visual Studio 和远程计算机上的其他端口。 若要调试远程 IIS web 服务器上，打开远程计算机上的端口 80。

|**端口**|**传入/传出**|**协议**|**说明**|  
|-|-|-|-|  
|500, 4500|传出|UDP|如果你的域策略需要通过 IPSec 进行网络通信，则需要。|  
|80|传出|TCP|所需的 web 服务器调试。|

若要允许特定应用程序通过 Windows 防火墙，请参阅[配置Windows 防火墙以进行远程调试](#configure-remote-debugging-through-windows-firewall)。 

## <a name="configure-remote-debugging-through-windows-firewall"></a>配置 Windows 防火墙以进行远程调试

可以在远程计算机上安装远程调试工具，或从共享文件夹运行它们。 在任一情况下，必须正确配置远程计算机防火墙。 

在远程计算机上远程调试工具将位于：  
  
*\<Visual Studio 安装目录\>\\Common7\\IDE\\远程调试器\\\<x86*， *x64*，或*Appx*\> 
  
### <a name="allow-and-configure-the-remote-debugger-through-windows-firewall"></a>Windows 在防火墙中设置允许远程调试器通过
  
1. 在 Windows 中**开始**菜单中，搜索并打开**Windows 防火墙**，或**Windows Defender 防火墙**。 
  
1. 选择**允许通过 Windows 防火墙的应用程序**。  
  
1.  如果**远程调试器**或**Visual Studio 远程调试器**未显示在**允许的应用程序和功能**，选择**更改设置**，然后选择**允许另一个应用**。 

1.  如果远程调试器应用程序仍未列出在**将应用添加**对话框中，选择**浏览**，并导航到 *\<Visual Studio 安装目录\>\\Common7\\IDE\\远程调试器\\\<x86*， *x64*，或*Appx* \>具体取决于您的应用程序的适当体系结构。 选择*msvsmon.exe*，然后选择**添加**。  
    
1.  在中**应用程序**列表中，选择**远程调试器**刚添加的。 选择**网络类型**，然后选择一个或多个网络类型，包括远程连接的网络类型。 
    
1.  选择**外**，然后选择**确定**。

## <a name="troubleshooting"></a>远程调试连接进行故障排除
  
如果远程调试器不能附加到您的应用程序，请确保远程调试的防火墙端口，协议、 网络类型和应用程序设置是否都正确。 

- 在 Windows 中**开始**菜单中，搜索并打开**Windows 防火墙**，然后选择**允许的应用程序通过 Windows 防火墙**。 请确保**远程调试器**或**Visual Studio 远程调试器**将出现在**允许的应用程序和功能**列出了与所选的复选框和正确的网络类型选择。 如果不是，[添加正确的应用和设置](#configure-remote-debugging-through-windows-firewall)。
  
- 在 Windows 中**开始**菜单中，搜索并打开**高级安全 Windows 防火墙**。 请确保**远程调试器**或**Visual Studio 远程调试器**下将显示**入站规则**(和 （可选），**出站规则**)使用一个绿色的复选标记图标，和的所有设置都均正确。 
  
  - 若要查看或更改规则设置，请右键单击**远程调试器**应用程序在列表中，选择**属性**。 使用**属性**选项卡来启用或禁用规则，或更改端口号、 协议或网络类型。 
  - 如果规则列表中看不到远程调试器应用[添加并配置了正确的端口](#configure-ports-for-remote-debugging)。 

## <a name="see-also"></a>请参阅  
[远程调试](../debugger/remote-debugging.md)

[Visual Studio 远程调试器端口分配](../debugger/remote-debugger-port-assignments.md)
