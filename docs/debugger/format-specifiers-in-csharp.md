---
title: 调试器中(C#)格式说明符 |Microsoft Docs
ms.custom: ''
ms.date: "11/21/2018"
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- expressions [C#], formatting values
- variables [debugger], watch variable symbols
- symbols, watch variable formatting
- QuickWatch dialog box, using format specifiers
- specifiers, watch variable format
- QuickWatch dialog box, format specifiers in C#
- specifiers
- watch variable symbols
- Watch window, format specifiers in C#
- format specifiers, debugger
- debugger, format specifiers recognized by
ms.assetid: 345c8589-5f36-4d34-a58c-e56271687dd6
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 0e8605671d1c245826ce6d699e91795fcd7ee32e
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/25/2018
ms.locfileid: "36756855"
---
# <a name="format-specifiers-in-c-in-the-visual-studio-debugger"></a>在 Visual Studio 调试器中的（C#）格式说明符
你可以使用格式说明符更改在 **监视** 窗口中显示值的格式。 此外可以在 **即时** 窗口、**命令**窗口、[跟踪点](../debugger/using-breakpoints.md#BKMK_Print_to_the_Output_window_with_tracepoints)、源窗口中使用格式说明符。 如果你在暂停在表达式上，在这些窗口结果将以已指定的格式显示[DataTip](../debugger/view-data-values-in-data-tips-in-the-code-editor.md) 。  
  
 若要使用格式说明符，在适当的说明符和逗号后输入一个变量表达式。  
  
## <a name="using-format-specifiers"></a>设置格式说明符  
我们使用以下代码：  
  
```csharp  
{  
        int my_var1 = 0x0065;  
        int my_var2 = 0x0066;  
        int my_var3 = 0x0067;  
}  
```  
  
 在调试时，添加`my_var1`变量到 **监视** 窗口，**调试 > Windows > 观看 > 监视 1**。然后，右键单击该变量，选择**十六进制显示**。 现在 **监视**  窗口将显示它包含值 0x0065。 若要看到该值表示为十进制整数而不是十六进制整数，请在**名称** 列的变量名之后添加十进制格式说明符 **, d** 。 **值**列现在显示十进制值 **101**。  
  
 ![WatchFormatCSharp](../debugger/media/watchformatcsharp.png "WatchFormatCSharp")  
  
## <a name="format-specifiers"></a>格式说明符  
 下表显示 Visual Studio 调试器中的 C# 格式说明符。  
  
|说明符|格式|原始监视值|显示|  
|---------------|------------|--------------------------|--------------|  
|ac|表达式的强制计算。 当关闭属性的隐式计算和隐式函数调用时，这是很有用的。|消息"隐式函数计算处于关闭状态的用户"|\<value>|  
|d|十进制整数|0x0065|101|  
|dynamic|使用“动态”视图显示指定对象|显示对象的所有成员，包括动态视图|仅显示动态视图|  
|h|十六进制整数|61541|0x0000F065|  
|nq|不带引号的字符串|"My String"|My String|  
|nse|指定行为，不格式。 使用"无副作用"的表达式的计算结果。 如果表达式不能解释和才可以解析 （如函数调用） 评估，您将看到错误。|不可用|不可用|
|隐藏|显示所有公共成员和非公共成员|显示公共成员|显示所有成员|  
|raw|以项在原始项节点中的显示格式来显示项。 只对代理对象有效。|字典\<T >|字典中的原始视图\<T >|  
|results|与实现 IEnumerable 或 IEnumerable 的类型的变量一起使用\<T >，通常在查询表达式的结果。 仅显示包含查询结果的成员。|显示所有成员。|显示满足查询条件的成员。|  
  
## <a name="see-also"></a>请参阅  
 [监视窗口和快速监视窗口](../debugger/watch-and-quickwatch-windows.md)   
 [“自动”和“局部变量”窗口](../debugger/autos-and-locals-windows.md)
