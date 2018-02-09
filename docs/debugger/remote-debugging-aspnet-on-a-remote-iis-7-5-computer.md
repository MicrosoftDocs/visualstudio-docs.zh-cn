---
title: "远程调试远程 IIS 计算机上的 ASP.NET |Microsoft 文档"
ms.custom: remotedebugging
ms.date: 07/26/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9cb339b5-3caf-4755-aad1-4a5da54b2a23
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: aspnet
ms.openlocfilehash: 6f11ec81c740a6930ce4eaef16d4e4e389aaca47
ms.sourcegitcommit: 65f85389047c5a1938b6d5243ccba8d4f14362ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2018
---
# <a name="remote-debug-aspnet-on-a-remote-iis-computer"></a>远程调试远程 IIS 计算机上的 ASP.NET
若要调试的 ASP.NET 应用程序部署到 IIS，安装和在计算机上运行远程工具其中部署您的应用程序，然后从 Visual Studio 附加到正在运行的应用。

![远程调试器组件](../debugger/media/remote-debugger-aspnet.png "Remote_debugger_components")

本指南说明如何设置和配置 Visual Studio 2017 ASP.NET MVC 4.5.2 应用程序，将其部署到 IIS 中，并从 Visual Studio 中附加远程调试器。 ASP.NET 核心执行远程调试，请参阅[在 IIS 的计算机上的远程调试 ASP.NET Core](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)。 对 Azure App Service，你可以轻松部署和调试上 IIS 使用的预配置实例[快照调试器](../debugger/debug-live-azure-applications.md)(.NET 4.6.1 所需) 或通过[将调试器附加服务器资源管理器](../debugger/remote-debugging-azure.md)。

这些过程已经过测试在这些服务器配置：
* Windows Server 2012 R2 和 IIS 8 （对于 Windows Server 2008 R2 中，服务器步骤会有所不同，）

## <a name="requirements"></a>需要

在从 Windows Server 2008 Service Pack 2 的 Windows Server 上支持远程调试器。 有关要求的完整列表，请参阅[要求](../debugger/remote-debugging.md#requirements_msvsmon)。

> [!NOTE]
> 不支持调试通过代理连接的两台计算机之间。 国家/地区中调试通过高延迟或低带宽连接，如拨号 Internet，或通过 Internet 不建议和可能失败也是非常慢。

## <a name="create-the-aspnet-452-application-on-the-visual-studio-computer"></a>创建 ASP.NET 4.5.2 Visual Studio 计算机上应用程序
  
1. 创建新的 MVC ASP.NET 应用程序。 (**文件 > 新建 > 项目**，然后选择 * * Visual C# > Web > ASP.NET Web 应用程序。 在 **ASP.NET 4.5.2** 模板部分中，选择“MVC” 。 请确保**启用 Docker 支持**未选中，**身份验证**设置为**无身份验证**。 将项目**MyASPApp**。)

2. 打开 HomeController.cs 文件，并在 `About()` 方法中设置断点。

## <a name="bkmk_configureIIS"></a>安装和 Windows Server 上配置 IIS

[!INCLUDE [remote-debugger-install-iis-role](../debugger/includes/remote-debugger-install-iis-role.md)]

## <a name="update-browser-security-settings-on-windows-server"></a>更新 Windows Server 上的浏览器安全设置

具体取决于你的安全设置，则可能会节省你时候将以下受信任的站点添加到你的浏览器，以便你可以轻松地下载本教程中所述的软件。 可能需要这些站点的访问：

- microsoft.com
- go.microsoft.com
- download.microsoft.com
- visualstudio.com

如果你使用的 Internet Explorer，则可以通过转到添加受信任的站点**Internet 选项 > 安全 > 受信任的站点 > 站点**。 这些步骤是不同的其他浏览器。 （如果需要从 my.visualstudio.com 下载较旧版本的远程调试器，某些其他受信任的站点所需登录。）

当你下载的软件时，可能会收到请求授予加载各种 web 站点脚本和资源的权限。 在大多数情况下，这些其他资源不需要安装软件。

## <a name="BKMK_deploy_asp_net"></a>在 Windows Server 上安装 ASP.NET 4.5

如果你想要在 IIS 上安装 ASP.NET 的更多详细的信息，请参阅[IIS 8.0 使用 ASP.NET 3.5 和 ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45)。

1. 使用 Web 平台安装程序 (WebPI) 安装 ASP.NET 4.5 (从 Windows Server 2012 R2 中的服务器节点中，选择**获取新的 Web 平台组件**然后搜索 ASP.NET)

    ![RemoteDBG_IIS_AspNet_45](../debugger/media/remotedbg_iis_aspnet_45.png "RemoteDBG_IIS_AspNet_45")

    > [!NOTE]
    > 如果你使用的 Windows Server 2008 R2，安装 ASP.NET 4 而不使用此命令：

     **C:\Windows\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe -ir**

2. 重新启动系统 (或执行**net 停止已 /y**跟**net 启动 w3svc**从命令提示符以拾取到系统路径的更改)。

## <a name="BKMK_install_webdeploy"></a>（可选）安装 Web 部署 Windows Server 上的 3.6

[!INCLUDE [remote-debugger-install-web-deploy](../debugger/includes/remote-debugger-install-web-deploy.md)]

## <a name="BKMK_deploy_asp_net"></a>在 Windows Server 计算机上配置 ASP.NET 网站

1. 打开 Windows 资源管理器并创建一个新的文件夹， **C:\Publish**，稍后将部署 ASP.NET 项目。

2. 打开**Internet Information Services (IIS) 管理器**。 (在服务器管理器的左窗格中，选择**IIS**。 右键单击服务器并选择**Internet Information Services (IIS) Manager**。)

3. 下**连接**在左窗格中，转到**站点**。

4. 选择**Default Web Site**，选择**基本设置**，并设置**物理路径**到**C:\Publish**。

5. 右键单击“默认网站”  节点，然后选择“添加应用程序” 。

6. 设置**别名**字段**MyASPApp**，接受默认应用程序池 (**DefaultAppPool**)，并设置**物理路径**到**C:\Publish**。

7. 下**连接**，选择**应用程序池**。 打开**DefaultAppPool**和将应用程序池字段设置为**ASP.NET v4.0** （ASP.NET 4.5 不是应用程序池的一个选项）。

8. 选择在 IIS 管理器站点后，选择**编辑权限**，并确保该 IUSR、 IIS_IUSRS 或配置应用程序池为授权的用户使用读取和执行权限的用户。 如果任何这些用户是否存在，将 IUSR 添加为具有读取和执行权限的用户。

## <a name="bkmk_webdeploy"></a>（可选）发布和使用 Web 部署从 Visual Studio 部署应用

[!INCLUDE [remote-debugger-deploy-app-web-deploy](../debugger/includes/remote-debugger-deploy-app-web-deploy.md)]

此外，你可能需要阅读部分上[疑难解答端口](#bkmk_openports)。

## <a name="optional-publish-and-deploy-the-app-by-publishing-to-a-local-folder-from-visual-studio"></a>（可选）发布和部署应用程序发布到本地文件夹从 Visual Studio

你可以发布和使用文件系统或其他工具部署应用。

1. (ASP.NET 4.5.2)请确保 web.config 文件列出的.NET framework 的正确版本。  例如，如果面向的 ASP.NET 4.5.2，请确保在 web.config 中列出此版本中的一种。
  
    ```xml
    <system.web>
      <compilation debug="true" targetFramework="4.5.2" />
      <httpRuntime targetFramework="4.5.2" />
      <httpModules>
        <add name="ApplicationInsightsWebTracking" type="Microsoft.ApplicationInsights.Web.ApplicationInsightsHttpModule, Microsoft.AI.Web" />
      </httpModules>
    </system.web>
  
    ```

    例如，版本应为 4.0，如果你安装 ASP.NET 4 而不是 4.5.2。

[!INCLUDE [remote-debugger-deploy-app-local](../debugger/includes/remote-debugger-deploy-app-local.md)]

## <a name="BKMK_msvsmon"></a>下载并在 Windows Server 上安装远程工具

在本教程中，我们将使用 Visual Studio 2017。

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

> [!TIP]
> 在某些情况下，它可以从文件共享运行远程调试器方式效率最高。 有关详细信息，请参阅[从文件共享运行远程调试器](../debugger/remote-debugging.md#fileshare_msvsmon)。
  
## <a name="BKMK_setup"></a>设置 Windows Server 上的远程调试器

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> 如果你需要添加其他用户的权限更改身份验证模式中，或者远程调试器端口号，请参阅[配置远程调试器](../debugger/remote-debugging.md#configure_msvsmon)。

有关运行远程调试器作为服务的信息，请参阅[远程调试器作为服务运行](../debugger/remote-debugging.md#bkmk_configureService)。

## <a name="BKMK_attach"></a> 从 Visual Studio 计算机附加到 ASP.NET 应用程序

1. 在 Visual Studio 计算机上打开**MyASPApp**解决方案。
2. 在 Visual Studio 中，单击**调试 > 附加到进程**（Ctrl + Alt + P）。

    > [!TIP]
    > 在 Visual Studio 2017 年，你可以重新附加到你以前通过使用附加到的相同进程**调试 > 重新附加到进程...**(Shift+Alt+P). 

3. 将限定符字段设置为**\<远程计算机名称 >: 4022**。
4. 单击**刷新**。
    “可用进程”  窗口中将显示某些进程。

    如果看不到任何进程，请尝试使用的 IP 地址而不 （端口是必需的） 远程计算机名称。 你可以使用`ipconfig`若要获取的 IPv4 地址的命令行中。

5. 勾选“显示所有用户的进程”  。
6. 键入要快速查找的进程名称的首字母**w3wp.exe**为 ASP.NET 4.5。

    ![RemoteDBG_AttachToProcess](../debugger/media/remotedbg_attachtoprocess.png "RemoteDBG_AttachToProcess")

7. 单击**附加**

8. 打开远程计算机的网站。 在浏览器中，转到**http://\<远程计算机名称 >**。
    
    将显示 ASP.NET 网页。
9. 在运行的 ASP.NET 应用程序，单击链接到**有关**页。

    应在 Visual Studio 中命中断点。

## <a name="bkmk_openports"></a>疑难解答： 打开 Windows Server 上的所需的端口

在大多数系统中，打开 ASP.NET 和远程调试器的安装所需的端口。 但是，你可能需要验证的端口打开。

> [!NOTE]
> 在 Azure VM，则必须打开端口通过[网络安全组](/azure/virtual-machines/virtual-machines-windows-hero-role#open-port-80)。 

所需的端口：

- 80-所需的 IIS
- 8172-（可选） 所需的 Web 部署来部署 Visual Studio 中的应用
- 4022-所需的 Visual Studio 2017 从远程调试 (请参阅[远程调试器端口分配](../debugger/remote-debugger-port-assignments.md)有关详细信息。
- UDP 3702-（可选） 发现端口可用于在**查找**按钮时将附加到 Visual Studio 中的远程调试器。

1. 若要打开 Windows 服务器上的端口，请打开**启动**菜单中，搜索**高级安全 Windows 防火墙**。

2. 然后选择**入站规则 > 新规则 > 端口**。 选择**下一步**并在列表视图**特定本地端口**，输入端口号，单击**下一步**，然后**允许连接**，单击下一步，和将名称添加 (**IIS**， **Web 部署**，或**msvsmon**) 为入站规则。

    如果你想配置 Windows 防火墙的详细信息，请参阅[配置 Windows 防火墙以进行远程调试](../debugger/configure-the-windows-firewall-for-remote-debugging.md)。

3. 创建对其他所需端口的其他规则。