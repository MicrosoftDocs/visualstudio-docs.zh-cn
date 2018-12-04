---
title: 调试源文件、通用属性，解决方案属性页对话框 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.options.FindSource
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
helpviewer_keywords:
- Debug Source Files property page
- debugging [Visual Studio], specifying source and symbol files
- source files, specifying in debugger
- debugger, source files
ms.assetid: 0af11464-eeb1-4d0b-87a6-0cc96779afb1
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 844d189b9dd11945f4257b1fc9dfbd3117ac5199
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2018
ms.locfileid: "31470759"
---
# <a name="debug-source-files-common-properties-solution-property-pages-dialog-box"></a>“解决方案属性页”对话框 ->“通用属性”->“调试源文件”
该属性页指定调试器调试解决方案时查找源文件的位置。  
  
 访问**调试源文件**属性页中，在解决方案中右键单击**解决方案资源管理器**，从快捷菜单中选择**属性**。 展开**通用属性**文件夹，然后单击**调试源文件**页。  
  
 **包含源代码的目录**  
 包含在调试器调试解决方案时搜索源文件的目录的列表。 还可搜索指定目录的子目录。  
  
 **不查找这些源文件**  
 输入不希望调试器读取的任何文件的名称。 如果调试器在以上指定的某个目录中找到这些文件之一，它将忽略该文件。 如果调试时出现 **查找源** 对话框，点击 **取消** ，正在搜索的文件被添加到此列表中，以使调试器不再继续搜索该文件。  
  
## <a name="see-also"></a>请参阅  
 [调试器安全](../debugger/debugger-security.md)   
 [调试器设置和准备](../debugger/debugger-settings-and-preparation.md)