---
title: "远程调试在 IIS 和 Azure 上的 ASP.NET Core |Microsoft 文档"
ms.custom: remotedebugging
ms.date: 08/14/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a6c04b53-d1b9-4552-a8fd-3ed6f4902ce6
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- aspnet
- dotnetcore
- azure
ms.openlocfilehash: 22b7724a6eee2c31de1bf64f12a040e042972e96
ms.sourcegitcommit: 65f85389047c5a1938b6d5243ccba8d4f14362ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2018
---
# <a name="remote-debug-aspnet-core-on-iis-in-azure-in-visual-studio-2017"></a>在 Visual Studio 2017 在 Azure 中的 IIS 上的远程调试 ASP.NET 核心

本指南说明如何设置和配置 Visual Studio 2017 ASP.NET Core 应用，将其部署到 IIS 使用 Azure，并从 Visual Studio 中附加远程调试器。

在 Azure 上的远程调试的推荐的方式取决于你的方案：

* 若要调试在 Azure App Service 上的 ASP.NET 核心，请参阅[调试 Azure 应用程序使用快照调试器](../debugger/debug-live-azure-applications.md)。 这是建议的方法。
* 若要调试 ASP.NET Core 上使用更加传统的调试功能的 Azure App Service，请按照本主题中的步骤 (请参阅明[在 Azure App Service 上进行远程调试](#remote_debug_azure_app_service))。

    在此方案中，你必须部署到 Azure 从 Visual Studio 应用但不是需要手动安装或配置 IIS 或远程调试器 （这些组件使用虚线表示），如下面的插图中所示。

    ![远程调试器组件](../debugger/media/remote-debugger-azure-app-service.png "Remote_debugger_components")

* 若要调试在 Azure VM 上的 IIS，请按照本主题中的步骤 (请参阅明[在 Azure VM 上进行远程调试](#remote_debug_azure_vm))。 此选项，可以使用自定义的配置的 IIS，但更复杂的安装和部署步骤。

    对于 Azure VM，必须部署到 Azure 从 Visual Studio 应用，你还需要手动安装 IIS 角色和远程调试器下, 图中所示。

    ![远程调试器组件](../debugger/media/remote-debugger-azure-vm.png "Remote_debugger_components")

* 若要调试在 Azure Service Fabric 上的 ASP.NET 核心，请参阅[调试远程 Service Fabric 应用程序](/azure/service-fabric/service-fabric-debugging-your-application#debug-a-remote-service-fabric-application)。

> [!WARNING]
> 请务必删除时已完成本教程中的步骤创建 Azure 资源。 这样可以避免产生不必要的费用。


### <a name="requirements"></a>需要

不支持调试通过代理连接的两台计算机之间。 国家/地区中调试通过高延迟或低带宽连接，如拨号 Internet，或通过 Internet 不建议和可能失败也是非常慢。 有关要求的完整列表，请参阅[要求](../debugger/remote-debugging.md#requirements_msvsmon)。

## <a name="create-the-aspnet-core-application-on-the-visual-studio-2017-computer"></a>在 Visual Studio 2017 计算机上创建 ASP.NET Core 应用程序 

1. 创建新的 ASP.NET Core 应用程序。 (选择**文件 > 新建 > 项目**，然后选择**Visual C# > Web > ASP.NET 核心 Web 应用程序**)。

    在**ASP.NET Core**模板部分中，选择**Web 应用程序**。

2. 请确保**ASP.NET 核心 2.0**选中，则，**启用 Docker 支持**是**不**选且**身份验证**设置为**无身份验证**。

3. 将项目**MyASPApp**单击**确定**创建新的解决方案。

4. 打开 About.cshtml.cs 文件和中设置断点`OnGet`方法 (在以前的模板，打开 HomeController.cs 而是和中设置断点`About()`方法)。

## <a name="remote_debug_azure_app_service"></a>在 Azure App Service 上的远程调试 ASP.NET 核心

从 Visual Studio 中，可以快速发布和调试你的应用的完全设置的 IIS 实例。 但是，预设的 IIS 配置，并且你无法自定义它。 有关详细说明，请参阅[ASP.NET 核心 web 应用部署到 Azure 中使用 Visual Studio](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs)。 (如果需要自定义 IIS 的功能，请尝试调试[Azure VM](#BKMK_azure_vm)。) 

#### <a name="to-deploy-the-app-and-remote-debug-using-server-explorer"></a>若要部署应用程序，并使用服务器资源管理器进行远程调试

1. 在 Visual Studio 中，右键单击项目节点并选择**发布**。

2. 选择**Microsoft Azure App Service**从**发布**对话框中，选择**新建**，并按照提示来发布。

    有关详细说明，请参阅[ASP.NET 核心 web 应用部署到 Azure 中使用 Visual Studio](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs)。

3. 打开**服务器资源管理器**(**视图** > **服务器资源管理器**)，在 App Service 实例上右键单击，然后选择**附加调试器**.

4. 在运行的 ASP.NET 应用程序，单击链接到**有关**页。

    应在 Visual Studio 中命中断点。

    就这么简单！ 本主题中的步骤的其余部分适用于 Azure VM 上的远程调试。

## <a name="remote_debug_azure_vm"></a>在 Azure VM 上的远程调试 ASP.NET 核心

你可以创建一个 Azure VM 的 Windows 服务器，然后安装和配置 IIS 和其他所需的软件组件。 这比将部署到 Azure App Service 的更多时间，并要求你按照本教程中的剩余步骤。

首先，按照中所述的所有步骤[安装和运行的 IIS](/azure/virtual-machines/virtual-machines-windows-hero-role)。

网络安全组中打开端口 80 时，还为远程调试器打开端口 4022。 这样一来，无需以后将其打开。

### <a name="update-browser-security-settings-on-windows-server"></a>更新 Windows Server 上的浏览器安全设置

具体取决于浏览器安全设置，则可能会节省你时候将以下受信任的站点添加到你的浏览器，以便你可以轻松地下载本教程中所述的软件。 可能需要这些站点的访问：

- microsoft.com
- go.microsoft.com
- download.microsoft.com
- visualstudio.com

如果你使用的 Internet Explorer，则可以通过转到添加受信任的站点**Internet 选项 > 安全 > 受信任的站点 > 站点**。 这些步骤是不同的其他浏览器。 （如果需要从 my.visualstudio.com 下载较旧版本的远程调试器，某些其他受信任的站点所需登录。）

当你下载的软件时，可能会收到请求授予加载各种 web 站点脚本和资源的权限。 在大多数情况下，这些其他资源不需要安装软件。

### <a name="install-aspnet-core-on-windows-server"></a>在 Windows Server 上安装 ASP.NET 核心

1. 安装[.NET 核心 Windows 服务器承载](https://aka.ms/dotnetcore-2-windowshosting)主机系统上的软件包。 捆绑包将安装.NET Core 运行时，.NET 核心库和 ASP.NET 核心模块。 有关更多深入说明，请参阅[发布到 IIS](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration)。

    > [!NOTE]
    > 如果系统没有连接到 Internet，获取并安装 *[Microsoft Visual c + + 2015年可再发行组件](https://www.microsoft.com/download/details.aspx?id=53840)*之前安装.NET 核心 Windows 服务器承载捆绑。

3. 重新启动系统 (或执行**net 停止已 /y**跟**net 启动 w3svc**从命令提示符以拾取到系统路径的更改)。

### <a name="BKMK_install_webdeploy"></a>（可选）安装 Web 部署 Windows Server 上的 3.6

[!INCLUDE [remote-debugger-install-web-deploy](../debugger/includes/remote-debugger-install-web-deploy.md)]

### <a name="BKMK_deploy_asp_net"></a>在 Windows Server 计算机上配置 ASP.NET 网站

1. 打开“Internet 信息服务(IIS)管理器”  并转到“站点” 。

2. 右键单击“默认网站”  节点，然后选择“添加应用程序” 。

3. 设置**别名**字段**MyASPApp**和应用程序池字段**无托管代码**。 设置**物理路径**到**C:\Publish** （将在其中你更高版本部署 ASP.NET 项目）。

4. 选择在 IIS 管理器站点后，选择**编辑权限**，并确保该 IUSR、 IIS_IUSRS 或配置应用程序池为授权的用户使用读取和执行权限的用户。

    如果你看不到具有权限的这些用户之一，请完成步骤将 IUSR 添加为具有读取和执行权限的用户。

### <a name="bkmk_webdeploy"></a>（可选）发布和使用 Web 部署从 Visual Studio 部署应用

如果你安装 Web 部署使用 Web 平台安装程序，你可以部署该应用程序直接从 Visual Studio。

1. 使用提升的权限启动 Visual Studio 并重新打开项目。

    这可能需要使用 Web Deploy 部署应用。

2. 在“解决方案资源管理器” 中，右键单击项目节点并选择“发布” 。

3. 有关**选择发布目标**，选择**Microsoft Azure 虚拟机**单击**发布**。

    ![RemoteDBG_Publish_IISl](../debugger/media/remotedbg_azure_vm_profile.png "RemoteDBG_Publish_IIS")

4. 在对话框中，选择前面创建的 Azure VM。

4. 输入你的 Azure VM 和 IIS 设置的更正配置参数。

    ![RemoteDBG_Publish_WebDeployl](../debugger/media/remotedbg_iis_webdeploy_config.png "RemoteDBG_Publish_WebDeploy")

    如果主机名不能解决当你尝试验证下一步中的步骤**服务器**文本框中，请尝试 IP 地址。 请确保使用在端口 80**服务器**文本框中，并确保端口 80 是在防火墙中打开。

6. 单击**下一步**，选择**调试**配置，然后选择**删除目标位置的其他文件**下**文件发布**选项。

5. 单击**Prev**，然后选择**验证**。 如果连接安装验证，你可以尝试发布。

6. 单击**发布**发布该应用程序。

    输出选项卡将显示是否发布已成功，以及你的浏览器将打开应用程序。

    如果你收到一提的是 Web 部署错误，重新检查 Web 部署安装步骤，请确保[正确的端口已打开](#bkmk_openports)在服务器上。

    如果应用程序已成功部署，但不能正常运行，重新检查 IIS 和 Visual Studio 项目，将使用相同版本的 ASP.NET。 如果，它不是问题，可能有您的 IIS 配置或你的 Web 站点配置的问题。 在 Windows Server 中，打开从 IIS 的网站的更具体的错误消息，然后重新检查之前的步骤。

### <a name="optional-publish-and-deploy-the-app-by-publishing-to-a-local-folder-from-visual-studio"></a>（可选）发布和部署应用程序发布到本地文件夹从 Visual Studio

如果你不使用 Web 部署，必须发布，并使用文件系统或其他工具部署应用。 你可以首先创建包使用文件系统中，然后手动部署包或使用 PowerShell、 RoboCopy 或 XCopy 等其他工具。 在此部分中，我们假定你正在手动复制包，如果你不使用 Web 部署。

[!INCLUDE [remote-debugger-deploy-app-local](../debugger/includes/remote-debugger-deploy-app-local.md)]

### <a name="BKMK_msvsmon"></a>下载并在 Windows Server 上安装远程工具

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]
  
### <a name="BKMK_setup"></a>设置 Windows Server 上的远程调试器

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> 如果你需要添加其他用户的权限更改身份验证模式中，或者远程调试器端口号，请参阅[配置远程调试器](../debugger/remote-debugging.md#configure_msvsmon)。

### <a name="BKMK_attach"></a> 从 Visual Studio 计算机附加到 ASP.NET 应用程序

1. 在 Visual Studio 计算机上打开**MyASPApp**解决方案。
2. 在 Visual Studio 中，单击**调试 > 附加到进程**（Ctrl + Alt + P）。

    > [!TIP]
    > 在 Visual Studio 2017 年，你可以重新附加到你以前通过使用附加到的相同进程**调试 > 重新附加到进程...**(Shift+Alt+P). 

3. 将限定符字段设置为**\<远程计算机名称 >: 4022**。
4. 单击**刷新**。
    “可用进程”  窗口中将显示某些进程。

    如果看不到任何进程，请尝试使用的 IP 地址而不 （端口是必需的） 远程计算机名称。 你可以使用`ipconfig`若要获取的 IPv4 地址的命令行中。

    如果你想要使用**查找**按钮，你可能需要为[打开 UDP 端口 3702](#bkmk_openports)服务器上。

5. 勾选“显示所有用户的进程”  。
6. 键入要快速查找的进程名称的首字母**dotnet.exe** （适用于 ASP.NET Core)。
    >注意： 对于 ASP.NET Core 应用程序，以前的进程名称是 dnx.exe。

    ![RemoteDBG_AttachToProcess](../debugger/media/remotedbg_attachtoprocess_aspnetcore.png "RemoteDBG_AttachToProcess")

7. 单击 **“附加”**。

8. 打开远程计算机的网站。 在浏览器中，转到**http://\<远程计算机名称 >**。
    
    将显示 ASP.NET 网页。
9. 在运行的 ASP.NET 应用程序，单击链接到**有关**页。

    应在 Visual Studio 中命中断点。

### <a name="bkmk_openports"></a>疑难解答： 打开 Windows Server 上的所需的端口

在大多数系统中，打开 ASP.NET 和远程调试器的安装所需的端口。 但是，如果你正在排查部署问题，并且该应用程序承载在防火墙后面，你可能需要验证打开了正确的端口。

在 Azure VM，则必须打开端口通过[网络安全组](/azure/virtual-machines/virtual-machines-windows-hero-role#open-port-80)。 

所需的端口：

- 80-所需的 IIS
- 4022-所需的 Visual Studio 2017 从远程调试 (请参阅[远程调试器端口分配](../debugger/remote-debugger-port-assignments.md)有关详细信息)。
- UDP 3702-（可选） 发现端口可用于在**查找**按钮时将附加到 Visual Studio 中的远程调试器。

此外，应已 ASP.NET 安装可打开这些端口：
- 8172-（可选） 所需的 Web 部署来部署 Visual Studio 中的应用

