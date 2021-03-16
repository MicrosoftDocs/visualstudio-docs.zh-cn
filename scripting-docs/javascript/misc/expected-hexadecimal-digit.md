---
description: 你创建了不正确的 Unicode 转义序列。
title: 应为十六进制数字 |Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1023
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 67a86df7-49f9-43cb-99c6-99b1a427827a
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 107ce2dd4f9a65a0a04b8e2ec773367ffae4ce81
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2021
ms.locfileid: "103570422"
---
# <a name="expected-hexadecimal-digit"></a>应为十六进制数字
你创建了不正确的 Unicode 转义序列。 Unicode 转义序列以 \u 开头，后跟四个十六进制数字，不 (更多且不) 。 Unicode 十六进制数字只能包含0-9、大写字母、小写字母和小写字母 a-f。 下面的示例演示一个格式正确的 Unicode 转义序列。  
  
```JavaScript  
z = "\u1A5F";  
```  
  
### <a name="to-correct-this-error"></a>更正此错误  
  
- 请确保 Unicode 十六进制数字以 \u 开头，只包含数字0-9，大写字母 A-f，小写字母 a-f;和按四位数分组。  
  
    > [!NOTE]
    > 如果要在字符串中使用文本 \u，则使用两个反斜杠- (\\ \u) -一个用于对第一个反斜杠进行转义。  
  
## <a name="see-also"></a>请参阅  
 [数据类型](https://developer.mozilla.org/docs/Web/JavaScript/Data_structures)
