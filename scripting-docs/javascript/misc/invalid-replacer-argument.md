---
description: 尝试使用无效的参数调用 json.stringify 的情况。
title: 无效的替换器参数 |Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5035
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 4727186f-facd-4aa6-9447-bbefbae83f07
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 95a73d6fcbcf1350eece52e2cd58693646617a28
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2021
ms.locfileid: "103570890"
---
# <a name="invalid-replacer-argument"></a>无效的替换器参数
尝试使用无效的 `JSON.stringify` 自变量进行调用。 `replacer`参数必须是函数或数组。  
  
### <a name="to-correct-this-error"></a>更正此错误  
  
- 将 `replacer` 自变量更改为函数或数组。  
  
## <a name="example"></a>示例  
 此示例中的代码导致运行时错误 `memberfilter` ，因为是对象而不是函数或数组。  
  
```JavaScript  
var contact = new Object();  
contact.firstname = "Jesper";  
contact.surname = "Aaberg";  
contact.phone = ["555-0100", "555-0120"];  
  
var memberfilter = new Object();  
  
// This line will cause a runtime error.  
var jsontext = JSON.stringify(contact, memberfilter, "\t");  
```  
  
## <a name="see-also"></a>请参阅  
 [JSON 对象](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/JSON)   
 [JSON。 parse 函数](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/JSON/parse)   
 [JavaScript 运行时错误](/microsoft-edge/devtools-guide/console/error-and-status-codes#javascript-run-time-errors)
