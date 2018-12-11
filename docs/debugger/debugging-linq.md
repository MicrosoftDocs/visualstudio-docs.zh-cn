---
title: 调试 LINQ |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging, LINQ
- LINQ, viewing results in debugger
- LINQ, debugging
- LINQ, stepping
- LINQ, edit and continue
ms.assetid: dbae26cb-ac5f-4312-b474-b9f29714f4c6
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8511c3ac9efd79b712680bfe3f9d5611f3c5aa9c
ms.sourcegitcommit: bc43970c000f07c9cc2051f1264a9742943a9755
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/09/2018
ms.locfileid: "51349421"
---
# <a name="debugging-linq"></a>调试 LINQ
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 支持对语言集成查询 (LINQ) 代码进行调试，但是有一些限制。 大多数调试功能都对 LINQ 语句有效，其中包括单步执行、设置断点以及在调试器窗口中查看结果。 本主题介绍 LINQ 调试的主要限制。  
  
##  <a name="BKMK_ViewingLINQResults"></a> 查看 LINQ 结果  
 使用数据提示功能、“监视”窗口和“快速监视”对话框，可以查看 LINQ 语句的结果。 在使用源窗口时，可以将指针停放在源窗口中的某个查询上，这样会出现“数据提示”。 可以将一个 LINQ 变量复制并粘贴到“监视”窗口或“快速监视”对话框中。  
  
 在 LINQ 中，查询不会在创建或声明时进行计算，而只在使用时才进行计算。 因此，查询在计算之前没值。 有关查询创建和计算的完整说明，请参阅[LINQ 查询 (C#) 简介](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries)或[编写你的第一个 LINQ 查询](/dotnet/visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query)。  
  
 若要显示某个查询的结果，调试器必须计算该查询。 在调试器中查看 LINQ 查询结果时，这种隐式计算具有的某些影响，应当加以考虑：  
  
-   查询的每次计算都需要时间。 展开结果节点需要时间。 对于某些查询，反复计算可能导致性能显著下降。  
  
-   计算查询可能产生副作用，这些副作用表现为对数据的值或程序状态的更改。 不是所有查询都具有副作用。 若要确定查询是否可以安全计算而不具有副作用，必须理解实现查询的代码。  
  
##  <a name="BKMK_SteppingAndLinq"></a> 单步执行和 LINQ  
 调试 LINQ 代码时，单步执行具有一些你应知道的行为差异。  
  
### <a name="linq-to-sql"></a>LINQ to SQL  
 在 LINQ to SQL 查询中，谓词代码不受调试器控制。 因此，无法进入并单步执行谓词代码。 任何编译为表达式树的查询都会产生不受调试器控制的代码。  
  
### <a name="stepping-in-visual-basic"></a>Visual Basic 中的单步执行  
 在单步执行 Visual Basic 程序且调试器遇到查询声明时，调试器不会进入并单步执行该声明，而是将整个声明作为单个语句突出显示。 发生此行为的原因是查询直到调用时才进行计算。 有关详细信息，请参阅[在 Visual Basic 中的 LINQ 简介](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)。  
  
 如果单步执行下面的代码示例，则调试器会将查询声明或查询创建作为单个语句突出显示。  
  
```vb
Function MyFunction(ByVal x As Char)  
    Return True  
End Function  
  
Sub Main()  
    'Query creation  
    Dim x = From it In "faoaoeua" _  
            Where MyFunction(it) _  
            Select New With {.a = it}  
  
    ' Query execution  
    For Each cur In x  
        Console.WriteLine(cur.ToString())  
    Next  
End Sub  
```  
  
 当你再次单步执行时，调试器会突出显示 `For Each cur In x`。 在下一步中，调试器会进入并单步执行函数 `MyFunction`。 在单步执行 `MyFunction` 后，调试器跳回到 `Console.WriteLine(cur.ToSting())`。 调试器在任何时候都不会单步执行查询声明中的谓词代码，尽管调试器的确会计算该代码。  
  
### <a name="replacing-a-predicate-with-a-function-to-enable-stepping-visual-basic"></a>用函数替换谓词以启用单步执行 (Visual Basic)  
 如果必须单步执行谓词代码以便达到调试目的，则可以将谓词替换为对包含原始谓词代码的函数的调用。 例如，假定你具有下面的代码：  
  
```vb
Dim items() as integer ={1, 2, 3, 4, 5, 6, 7, 8, 9, 10}  
  
' Get the even numbers  
Dim query = From nextInt in items Where nextInt Mod 2 = 0 Select nextInt  
  
For each item in query  
      Console.WriteLine(item)  
Next  
```  
  
 可以将谓词代码移动至一个新函数，该函数称为 `IsEven`：  
  
```vb
Dim items () as integer ={1, 2, 3, 4, 5, 6, 7, 8, 9, 10}  
  
' Get the even numbers  
Dim query = From nextInt in items Where IsEven(nextInt) Select nextInt  
  
For each item in query  
      Console.WriteLine(item)  
Next  
...   
Function IsEven(item As =Integer) as Boolean  
      Return item Mod 2 = 0  
End Function  
```  
  
 修改后的查询在每次遍历 `IsEven` 时都会调用函数 `items`。 你可以使用调试器窗口来查看每个“item”是否满足指定条件，并且可以单步执行 `IsEven` 中的代码。 此示例中的谓词相当简单。 但是，如果必须调试一个更复杂的谓词，这种技术也会十分有用。  
  
##  <a name="BKMK_EditandContinueNotSupportedforLINQ"></a> 编辑并继续 LINQ 不支持  
 编辑并继续支持对 LINQ 查询与限制的更改。 有关详细信息，请参阅[EnC 受支持的更改](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits))
  
## <a name="see-also"></a>请参阅

- [SQL 调试](/previous-versions/visualstudio/visual-studio-2010/zefbf0t6\(v\=vs.100\))
- [管理调试器的异常](../debugger/managing-exceptions-with-the-debugger.md)
- [LINQ 查询简介 (C#)](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries)
- [Visual Basic 中的 LINQ 简介](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)
