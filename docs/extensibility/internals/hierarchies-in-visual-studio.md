---
title: Visual Studio 中的层次结构 |Microsoft Docs
description: 了解 Visual Studio 集成开发环境中的项目层次结构 (IDE) 包含项目项及其关联的属性。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- hierarchies, Visual Studio IDE
- IDE, hierarchies
ms.assetid: 0a029a7c-79fd-4b54-bd63-bd0f21aa8d30
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d3fe1487e082907958c1cf8a36f1653efb97c9de
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/25/2021
ms.locfileid: "105056618"
---
# <a name="hierarchies-in-visual-studio"></a>Visual Studio 中的层次结构
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]集成开发环境 (IDE) 将项目显示为 *层次结构*。 在 IDE 中，层次结构是节点的树，其中每个节点都有一组关联的属性。 *项目层次结构* 是一个容器，用于保存项目的项、项的关系以及项的关联属性和命令。

 在中 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ，可以使用层次结构接口管理项目层次结构 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> 。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>接口将从项目项调用的命令重定向到适当的层次结构窗口，而不是标准命令处理程序。

## <a name="project-hierarchies"></a>项目层次结构
 每个项目层次结构都包含您可以查看和编辑的项。 这些项因项目类型而异。 例如，数据库项目可能包含存储过程、数据库视图和数据库表。 另一方面，一种编程语言项目将可能包括用于位图和对话框的源文件和资源文件。 层次结构可以嵌套，这为你在创建项目层次结构时提供了一些灵活性。

 当你创建新的项目类型时，项目类型会控制可在其中进行编辑的整套项。 但是，项目可以包含它们不支持编辑的项。 例如，Visual C++ 项目可以包含 HTML 文件，即使 Visual C++ 不提供 HTML 文件类型的任何自定义编辑器。

 层次结构管理它们所包含的项的暂留。 层次结构的实现必须控制影响层次结构内项的持久性的任何特殊属性。 例如，如果项表示存储库中的对象而不是文件，则层次结构实现必须控制这些对象的持久性。 IDE 本身指示层次结构保存项，以符合用户输入，但 IDE 不会控制保存这些项所需的任何操作。 相反，项目处于控件中。

 当用户在编辑器中打开某一项时，将选择控制该项的层次结构，并成为活动层次结构。 所选层次结构确定可对该项执行操作的命令集。 以这种方式跟踪用户焦点使层次结构能够反映用户的当前上下文。

## <a name="see-also"></a>另请参阅
- [项目类型](../../extensibility/internals/project-types.md)
- [IDE 中的选择和货币](../../extensibility/internals/selection-and-currency-in-the-ide.md)
- [VSSDK 示例](https://github.com/Microsoft/VSSDK-Extensibility-Samples)
