---
title: 错误： web 服务器配置不正确 |Microsoft 文档
ms.custom: ''
ms.date: 09/20/2017
ms.technology: vs-ide-debug
ms.topic: troubleshooting
f1_keywords:
- vs.debug.remote.projnotconfigured
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c9ff79148af491ee27aeae20b66b4d7b742bef6b
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2018
ms.locfileid: "31471848"
---
# <a name="error-the-web-server-is-not-configured-correctly"></a>错误：Web 服务器配置不正确

在谈论完解决此问题的详情后，在再次尝试调试前，可能还需要重置 IIS。 你可以通过打开管理员命令提示符并键入`iisreset` 执行该操作。

执行以下步骤来解决此问题：

1. 如果服务器上托管的 web 应用配置为发布版本，重发布为调试版本，重新发布并验证 web.config 文件包含`debug=true`编译元素中。 重置 IIS，然后重试。

    例如，如果您将发布配置文件用于发布版本，将其更改为调试并重新发布。 否则，调试属性将设置为`false`发布时。

2. (IIS)验证物理路径正确。 在 IIS 中，找到此设置在**基本设置 > 物理路径**(或**高级设置**在较旧版本的 IIS)。

    如果 web 应用程序已复制到不同的计算机、 手动重命名或移动，可能不正确的物理路径。 重置 IIS，然后重试。

3. 如果你正使用 Visual Studio 进行本地调试，请验证已选中的属性中正确的服务器。 (打开**属性 > Web > 服务器**或**属性 > 调试**具体取决于你的项目类型。 对于 Web 窗体项目，打开**属性页 > 启动选项 > 服务器**)。

    如果你使用如 IIS 外部 （自定义） 服务器，则该 URL 必须是正确的。 否则，请选择 IIS Express，然后重试。

4. (IIS)请确保服务器上安装了 ASP.NET 的正确版本。

    ASP.NET 在 IIS 上和 Visual Studio 项目中的不匹配的版本可能会导致此问题。 你可能需要在 web.config 中设置的 framework 版本。若要在 IIS 上安装 ASP.NET，请使用[Web 平台安装程序 (WebPI)](https://www.microsoft.com/web/downloads/platform.aspx)。 另请参阅[IIS 8.0 使用 ASP.NET 3.5 和 ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45)或为 ASP.NET Core[使用 IIS 的 Windows 上的主机](https://docs.asp.net/en/latest/publishing/iis.html)。
  
4. 如果`maxConnection`在 IIS 中的限制值太小，而你有过多连接，则可能需要[增加连接限制](/iis/configuration/system.applicationhost/sites/sitedefaults/limits)。
  
## <a name="see-also"></a>请参阅  
 [远程调试远程 IIS 计算机上的 ASP.NET](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)   
 [调试 Web 应用程序：错误和疑难解答](../debugger/debugging-web-applications-errors-and-troubleshooting.md)