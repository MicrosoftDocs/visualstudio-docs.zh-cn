---
title: "在低带宽或不可靠的网络环境中安装 | Microsoft Docs"
description: "介绍了 Visual Studio 安装程序在不可靠的网络条件下的运行方式，以及如何在开始安装前下载安装文件。"
ms.date: 04/14/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 44DB1998-68CD-4560-870A-EE5B993DCF6E
author: timsneath
ms.author: tims
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: 85576806818a6ed289c2f660f87b5c419016c600
ms.openlocfilehash: 9dbe70bce6c246416df64de304b06cd211320f2a
ms.contentlocale: zh-cn
ms.lasthandoff: 05/10/2017

---

# <a name="install-visual-studio-2017-on-low-bandwidth-or-unreliable-network-environments"></a>在低带宽或不可靠的网络环境中安装 Visual Studio 2017
我们精心设计了新的 Visual Studio 2017 安装程序，它非常适合在各种网络和计算机条件下安装 Visual Studio。

- 由于安装 Visual Studio 所需的文件发布在全球传送网络上，因此我们可以从本地服务器为你获取这些文件；
- 在安装过程中，我们会尝试三种不同的下载技术（WebClient、BITS 和 WinInet），以最大限度地减少对防病毒和代理软件的干扰；
- 基于工作负载的新模型的推出意味着，需要安装的内容比旧版 Visual Studio 少。

因此，建议尝试使用新的 Web 安装程序，使用体验一定会让你感到满意。 不过，如果要确保在开始安装 Visual Studio 前已成功下载安装文件，我们已为你提供了相应对策。 开始安装前，可以使用命令行创建所需文件的本地缓存。

操作方法如下。

## <a name="download-the-visual-studio-bootstrapper"></a>下载 Visual Studio 引导程序
首先，下载选定 Visual Studio 版本的 Visual Studio 引导程序。

安装程序文件（具体而言是引导程序文件）将是下列项之一，或与之类似。

| 版本                    | 文件                                                                    |
|----------------------------|-------------------------------------------------------------------------|
| Visual Studio 社区    | [vs_community.exe](https://aka.ms/vs/15/release/vs_community.exe)       |
| Visual Studio Professional | [vs_professional.exe](https://aka.ms/vs/15/release/vs_professional.exe) |
| Visual Studio Enterprise   | [vs_enterprise.exe](https://aka.ms/vs/15/release/vs_enterprise.exe)     |

## <a name="create-a-local-install-cache"></a>创建本地安装缓存
若要创建本地布局，请打开命令提示符，然后运行以下示例中的一个命令。 下面的示例假定已下载 Visual Studio Community 引导程序：请根据你的版本相应调整命令。

- 对于 .NET Web 和.NET 桌面开发，请运行：
  ```
  vs_community.exe --layout c:\vs2017layout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional --lang en-US
  ```
- 对于 .NET 桌面和 Office 开发，请运行：
  ```
  vs_community.exe --layout c:\vs2017layout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.Office --includeOptional --lang en-US
  ```
- 对于 C++ 桌面开发，请运行：
  ```
  vs_community.exe --layout c:\vs2017layout --add Microsoft.VisualStudio.Workload.NativeDesktop --includeRecommended --lang en-US
  ```

- 若要创建包含所有功能的完整本地布局（耗时将很长，因为我们提供的功能_非常多_！），请运行：
  ```
  vs_community.exe --layout c:\vs2017layout --lang en-US
  ```

如果要安装非英语语言，请从此页底部的列表中将 `en-US` 更改为相应的区域设置。 请使用此[可用组件和工作负载列表](workload-and-component-ids.md)，根据需要进一步自定义安装缓存。

## <a name="install-from-the-local-cache"></a>从本地缓存安装
当你从本地安装缓存运行时，我们将使用其中每个文件的本地版本。 不过，如果你在安装过程中选择的组件不在缓存中，我们将尝试从 Internet 下载。

为了确保只安装已下载的文件，请使用在创建布局缓存时所用的相同命令行选项。 例如，如果使用以下命令创建了布局缓存：

```
vs_community.exe --layout c:\vs2017layout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional --lang en-US
```

请使用以下命令运行安装布局：

```
c:\vs2017layout\vs_community.exe --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional
```

## <a name="list-of-language-locales"></a>语言区域设置列表
| **语言-区域设置** | **语言** |
| ----------------------- | --------------- |  
| cs-CZ | 捷克语 |
| de-DE | 德语 |
| en-US | 英语 |
| es-ES | 西班牙语 |
| fr-FR | 法语 |
| it-IT | 意大利语 |
| ja-JP | 日语 |
| ko-KR | 朝鲜语 |
| pl-PL | 波兰语 |
| pt-BR | 葡萄牙语 - 巴西 |
| ru-RU | 俄语 |
| tr-TR | 土耳其语 |
| zh-CN | 中文 - 简体 |
| zh-TW | 中文 - 繁体 |

## <a name="see-also"></a>另请参阅
* [安装 Visual Studio](install-visual-studio.md)
* [Visual Studio 管理员指南](visual-studio-administrator-guide.md)
* [使用命令行参数安装 Visual Studio](use-command-line-parameters-to-install-visual-studio.md)

