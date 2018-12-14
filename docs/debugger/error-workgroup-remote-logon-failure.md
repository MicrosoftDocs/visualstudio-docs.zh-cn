---
title: 错误： 工作组远程登录失败 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.workgroup_remote_logon_failure
dev_langs:
- CSharp
- VB
- FSharp
- JScript
- C++
helpviewer_keywords:
- logon failure, remote debugging
- remote debugging, logon failure
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 60cee4e6bdb4ebab925325695eb9ad6813929879
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2018
ms.locfileid: "31481991"
---
# <a name="error-workgroup-remote-logon-failure"></a>错误：工作组远程登录失败
此错误显示如下：  
  
 登录失败: 未知的用户名或密码不正确  
  
 **原因**  
  
 当在工作组上的计算机进行调试，并尝试连接到远程计算机时可能发生此错误。 可能的原因包括：  
  
-   远程计算机上没有匹配用户名和密码的帐户。  
  
-   Visual Studio 计算机和远程计算机都在工作组上，远程计算机默认设置**本地安全策略** 时，可能发生此错误。 默认**本地安全策略**设置**仅来宾-本地用户以来宾身份验证**。 若要在此设置上调试，必须在远程计算机上更改设置**经典-本地用户以自己的身份验证**。  
  
> [!NOTE]
>  你必须是管理员才能执行以下任务。  
  
### <a name="to-open-the-local-security-policy-window"></a>打开“本地安全策略”窗口  
  
1.  在 Microsoft 管理控制台管理单元中启动 **secpol.msc** 。 在 Windows 搜索、Windows“运行”框中或命令提示符处键入 secpol.msc。  
  
### <a name="to-add-user-rights-assignments"></a>添加用户权限分配  
  
1.  打开**本地安全策略**窗口。  
  
2.  展开**本地策略**文件夹。  
  
3.  单击**用户权限分配**。  
  
4.  在**策略**列中，双击**调试程序**查看**本地安全策略设置**对话框中当前本地组策略分配。  
  
     ![本地安全策略用户权限](../debugger/media/dbg_err_localsecuritypolicy_userrightsdebugprograms.png "DBG_ERR_LocalSecurityPolicy_UserRightsDebugPrograms")  
  
5.  若要添加新用户，请单击**添加用户或组**按钮。  
  
### <a name="to-change-the-sharing-and-security-model"></a>更改“共享和安全模型”  
  
1.  打开**本地安全策略**窗口。  
  
2.  展开**本地策略**文件夹。  
  
3.  单击**安全选项**。  
  
4.  在**策略**列中，双击**网络访问： 本地帐户的共享和安全模型**。  
  
5.  在**网络访问： 本地帐户的共享和安全模型**对话框中，更改值为 **经典-本地用户以自己的身份验证** 然后单击**应用**按钮。  
  
     ![本地安全策略安全选项](../debugger/media/dbg_err_localsecuritypolicy_securityoptions_networkaccess.png "DBG_ERR_LocalSecurityPolicy_SecurityOptions_NetworkAccess")  
  
## <a name="see-also"></a>请参阅  
 [远程调试错误和疑难解答](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [远程调试](../debugger/remote-debugging.md)