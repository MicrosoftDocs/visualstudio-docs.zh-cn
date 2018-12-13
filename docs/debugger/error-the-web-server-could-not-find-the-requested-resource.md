---
title: 错误： Web 服务器未能找到请求的资源 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: troubleshooting
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
ms.openlocfilehash: 8769c84237d877f02b7c9d3d02c6391f9e955ff3
ms.sourcegitcommit: 40b6438b5acd7e59337a382c39ec711b9e99cc8a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/11/2018
ms.locfileid: "49100973"
---
# <a name="error-the-web-server-could-not-find-the-requested-resource"></a>错误：Web 服务器未能找到请求的资源
为了安全起见，IIS 已返回通用错误。  

一个可能的原因是服务器的安全配置。 IIS 6.0 和早期版本使用名为 URLScan 的外接程序来筛选出可疑请求和格式不正确的请求。 IIS 7.0 具有用于实现同一目的的内置请求筛选。 在这两种情况下，过度限制性请求筛选可防止 Visual Studio 调试服务器。  

此错误的另一个可能的原因是未启动 IIS W3SVC 服务。 检查，此服务是否已启动 （灰色） 在服务窗口中 (*services.msc*)。

此错误有大量可能原因。 几个最常见的原因包括：文件系统中的 IIS 安装或配置、网站配置或权限有问题。 您可以尝试使用浏览器访问资源。 根据 IIS 的配置方式，可能需要在服务器上使用本地浏览器或检查 IIS 错误日志以获取详细的错误消息。  
  
 有关排除 IIS 问题的详细信息，请参阅[IIS 管理和管理](/iis/manage/provisioning-and-managing-iis/iis-management-and-administration)。  
  
## <a name="see-also"></a>请参阅  
 [错误：Web 服务器已被锁定，并阻止 DEBUG 谓词](../debugger/error-the-web-server-has-been-locked-down-and-is-blocking-the-debug-verb.md)