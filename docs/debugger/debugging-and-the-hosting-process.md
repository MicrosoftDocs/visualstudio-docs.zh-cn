---
title: 调试和托管进程 |Microsoft Docs
ms.custom: ''
ms.date: 08/01/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], hosting process
- hosting process
ms.assetid: d0f0b9a6-2a6e-463d-b6ea-9518ee727933
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 59ef28f5724c12fd9897adbaa9125bafe26beb60
ms.sourcegitcommit: 0cf1e63b6e0e6a0130668278489b21a6e5038084
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/02/2018
ms.locfileid: "39468255"
---
# <a name="debugging-and-the-hosting-process"></a>调试和托管进程
Visual Studio 托管进程提高了调试器性能，并启用了新的调试器功能，如部分信任调试和设计时表达式求值。 如果需要，你可以禁用托管进程。 以下部分描述用托管进程和不用托管进程进行调试的一些差异。

> [!NOTE]
> 在 Visual Studio 2017 中，不再需要使用托管进程进行调试的选项，并且已删除了该项。 有关详细信息，请参阅[调试： Visual Studio 2017 旨在加速您最不喜欢的工作](https://vslive.com/Blogs/News-and-Tips/2017/02/Debugging-Visual-Studio-2017-aims-to-speed-up-your-least-favorite-job.aspx)。

## <a name="partial-trust-debugging-and-click-once-security"></a>部分信任调试和 Click-Once 安全
 部分信任调试需要托管进程。 如果禁用托管进程，部分信任调试将不工作，即使在 **“项目属性”** 的 **“安全”** 页上启用了部分信任安全。 有关详细信息，请参阅[如何： 调试部分信任应用程序](../debugger/how-to-debug-a-partial-trust-application.md)。

## <a name="design-time-expression-evaluation"></a>设计时表达式求值
 设计时表达式始终使用托管进程。 如果在 **“项目属性”** 中禁用托管进程，则禁用了类库项目的设计时表达式求值。 对于其他项目类型，不禁用设计时表达式计算。 相反，Visual Studio 启动实际可执行文件，并将它用于不用托管进程的设计时求值。 这种差异可能产生不同的结果。

## <a name="appdomaincurrentdomainfriendlyname-differences"></a>AppDomain.CurrentDomain.FriendlyName 差异
 `AppDomain.CurrentDomain.FriendlyName` 依据是否启用托管进程返回不同的结果。 如果在启用托管进程时调用 `AppDomain.CurrentDomain.FriendlyName` ，它将返回 *app_name*`.vhost.exe`。 如果在启用托管进程时调用它，它将返回 *app_name*`.exe`。

## <a name="assemblygetcallingassemblyfullname-differences"></a>Assembly.GetCallingAssembly().FullName 差异
 `Assembly.GetCallingAssembly().FullName` 依据是否启用托管进程返回不同的结果。 如果在启用托管进程时调用 `Assembly.GetCallingAssembly().FullName` ，它将返回 `mscorlib`。 如果禁用托管进程时调用 `Assembly.GetCallingAssembly().FullName` ，它将返回该应用程序名。

## <a name="see-also"></a>请参阅

- [如何：调试部分信任的应用程序](../debugger/how-to-debug-a-partial-trust-application.md)