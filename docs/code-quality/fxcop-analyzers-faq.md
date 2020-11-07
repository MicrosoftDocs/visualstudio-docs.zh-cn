---
title: FxCop 代码分析和 FxCop 分析器
ms.date: 09/06/2018
description: 了解 Visual Studio 中的旧 FxCop 和 FxCop 分析器之间的差异。 请参阅有关如何使用这些分析器的问题的解答。
ms.custom: SEO-VS-2020
ms.topic: conceptual
helpviewer_keywords:
- code analysis FAQ
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 0e6768ad7f1ee87f75592c736b03bf6fd64e28c2
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/07/2020
ms.locfileid: "94348953"
---
# <a name="frequently-asked-questions-about-fxcop-and-fxcop-analyzers"></a>有关 FxCop 和 FxCop 分析器的常见问题解答

理解旧版 FxCop 和 FxCop 分析器之间的差异可能有点令人困惑。 本文旨在解决你可能遇到的一些问题。

## <a name="whats-the-difference-between-legacy-fxcop-and-fxcop-analyzers"></a>旧版 FxCop 和 FxCop 分析器之间有什么区别？

旧版 FxCop 在已编译的程序集上运行生成后分析。 它作为单独的可执行文件运行，名为 FxCopCmd.exe。 FxCopCmd.exe 加载已编译的程序集，运行代码分析，然后报告结果（或“诊断”）。

FxCop 分析器基于 .NET Compiler Platform（“Roslyn”）。 [将它们安装 NuGet 包](install-fxcop-analyzers.md#nuget-package)，该包为项目或解决方案所引用。 FxCop 分析器在编译器执行期间运行基于源代码的分析。 FxCop 分析器托管在编译器进程（csc.exe 或 vbc.exe）中，并在生成项目时运行分析。 报告分析器结果以及编译器结果。

> [!NOTE]
> 还可[将 FxCop 分析器安装为 Visual Studio 扩展](install-fxcop-analyzers.md#vsix)。 在这种情况下，当你在代码编辑器中键入时分析器将执行，但它们不会在生成时执行。 若要将 FxCop 分析器作为持续集成 (CI) 的一部分运行，请将它们安装为 NuGet 包。

## <a name="does-the-run-code-analysis-command-run-fxcop-analyzers"></a>“运行代码分析”命令是否运行 FxCop 分析器？

在 Visual Studio 2019 16.5 版本之前，当你选择 " **分析**  >  **运行代码分析** " 时，它会执行旧式分析。 启动 Visual Studio 2019 16.5， **运行代码分析** 菜单选项执行所选项目或解决方案的基于 Roslyn 的分析器。 如果已安装基于 Roslyn 的 FxCop 分析器，则这些分析器也将执行。 有关详细信息，请参阅 [如何：手动运行托管代码的代码分析](how-to-run-code-analysis-manually-for-managed-code.md)。

## <a name="does-the-runcodeanalysis-msbuild-project-property-run-analyzers"></a>RunCodeAnalysis msbuild 项目属性是否运行分析器？

否。 项目文件（例如 .csproj）中的 RunCodeAnalysis 属性仅用于执行旧版 FxCop。 它将运行调用 FxCopCmd.exe 的生成后 msbuild 任务。

## <a name="so-how-do-i-run-fxcop-analyzers-then"></a>那么我该如何运行 FxCop 分析器呢？

要运行 FxCop 分析器，首先请为它们[安装 NuGet 包](install-fxcop-analyzers.md)。 然后在 Visual Studio 中或使用 msbuild 生成项目或解决方案。 FxCop 分析器生成的警告和错误将显示在“错误列表”或命令窗口中。

## <a name="i-get-warning-ca0507-even-after-ive-installed-the-fxcop-analyzers-nuget-package"></a>即使在安装了 FxCop 分析器 NuGet 包之后，我仍会收到 CA0507 警告

如果已安装了 FxCop 分析器但继续获取警告 CA0507 **"运行代码分析" 已弃用（在生成过程中运行** ），则可能需要将 [项目文件](../ide/solutions-and-projects-in-visual-studio.md#project-file)中的 **RunCodeAnalysis** msbuild 属性设置为 **false** 。 否则，将在每次生成后执行旧式分析。

```xml
<RunCodeAnalysis>false</RunCodeAnalysis>
```

## <a name="which-rules-have-been-ported-to-fxcop-analyzers"></a>哪些规则已移植到 FxCop 分析器？

有关哪些旧分析规则已移植到 [FxCop 分析器](install-fxcop-analyzers.md)的信息，请参阅 [fxcop 规则端口状态](fxcop-rule-port-status.md)。

## <a name="code-analysis-warnings-are-treated-as-errors"></a>代码分析警告被视为错误

如果你的项目使用 "生成" 选项将警告视为错误，则 FxCop 分析器警告可能会显示为错误。 若要防止代码分析警告被视为错误，请按照 [代码分析常见问题解答](../code-quality/analyzers-faq.md#treat-warnings-as-errors)中的步骤进行操作。

## <a name="see-also"></a>请参阅

- [.NET Compiler Platform 分析器概述](roslyn-analyzers-overview.md)
- [迁移到 FxCop 分析器](migrate-from-legacy-analysis-to-fxcop-analyzers.md)
- [安装 FxCop 分析器](install-fxcop-analyzers.md)
