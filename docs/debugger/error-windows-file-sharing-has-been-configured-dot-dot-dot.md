---
title: 错误： Windows 文件共享已配置...|Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.remote_credentials_prohibited
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 591b051cb6164f4c8d260be3de29833154c96255
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2018
ms.locfileid: "31472784"
---
# <a name="error-windows-file-sharing-has-been-configured"></a>错误：已配置 Windows 文件共享...
已配置 Windows 文件共享，因此您将使用另一不同的用户名连接到远程计算机。 这与远程调试不兼容  
  
 当前文件共享配置设置为使用另一用户名连接到远程计算机。 在这种情况下不能进行远程调试。  
  
 若要更正此错误，请使用其他帐户名登录到计算机上，或是更改文件共享以使用要用来进行调试的帐户名。  
  
 如果要使用此用户名连接到远程计算机，则必须首先从远程计算机断开连接。  
  
### <a name="to-correct-this-error"></a>更正此错误  
  
1.  使用其他帐户名登录到本地计算机（要从其进行调试的计算机）上。  
  
     - 或 -  
  
     . 中断与远程计算机的连接，然后重新配置文件共享，以便使用您的帐户名称连接至其他计算机：  
  
    1.  在**开始**菜单中，指向**附件**，然后单击**命令提示符**。  
  
    2.  在 Windows 命令提示符中，键入：  
  
         `net use /delete computer_name`  
  
    3.  使用 Windows 帮助中介绍的任一方法更改文件共享设置。