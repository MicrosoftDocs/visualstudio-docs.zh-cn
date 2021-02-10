---
title: 支持的 Roslyn 包版本映射
description: 本文介绍了不同版本的 Visual Studio 支持 (Roslyn) 包版本的 .NET 编译器平台。
ms.custom: SEO-VS-2020
ms.date: 04/29/2019
ms.topic: reference
helpviewer_keywords:
- roslyn package versions
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f76a8dcdbb644fe456c62fca7de6fb7afe96d556
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2021
ms.locfileid: "99935881"
---
# <a name="net-compiler-platform-package-version-reference"></a>.NET 编译器平台包版本引用

下表显示了不同版本的 Visual Studio 支持 [ (Roslyn 的 .net 编译器平台) 包](https://www.nuget.org/packages/Microsoft.Net.Compilers/) 版本。

例如，若要确保自定义分析器适用于所有版本的 Visual Studio 2017，它应面向版本2.0 （Microsoft.Net）。

| Roslyn 包版本 | 支持的最低 Visual Studio 版本 |
| - | - |
| 3.x | Visual Studio 2019 |
| 2.10.0 | Visual Studio 2017 版本 15.9 |
| 2.9.0 | Visual Studio 2017 版本 15.8 |
| 2.8.2 | Visual Studio 2017 15.7 版 |
| 2.7.0 | Visual Studio 2017 版本 15.6 |
| 2.6.1 | Visual Studio 2017 版本 15.5 |
| 2.4.0 | Visual Studio 2017 版本 15.4 |
| 2.3.2 | Visual Studio 2017 版本 15.3 |
| 2.2.0 | Visual Studio 2017 版本 15.2 |
| 2.1.0 | Visual Studio 2017 版本 15.1 |
| 2.0.0 | Visual Studio 2017 RTM |
| 1.3.2 | Visual Studio 2015 update 3 |
| 1.2.2 | Visual Studio 2015 update 2 |
| 1.1.1 | Visual Studio 2015 update 1 |
| 1.0.1 | Visual Studio 2015 RTM |

> [!TIP]
> 对于受支持的最低 Visual Studio 版本为 Visual Studio 2017 版本的 Roslyn 包，还支持所有版本的 Visual Studio 2019，因为它们会在以后提供。

## <a name="see-also"></a>另请参阅

- [.NET 编译器平台 SDK](/dotnet/csharp/roslyn-sdk/)
- [Roslyn 分析器入门](getting-started-with-roslyn-analyzers.md)
