---
title: 条件编译已关闭 |Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1030
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 59a030b0-a6c6-47f2-b90e-c0ed204d5116
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 91e32971013d2dfcf0ee2dc901d84681522c7e89
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/09/2020
ms.locfileid: "91861651"
---
# <a name="conditional-compilation-is-turned-off"></a>条件编译已关闭
您尝试在不先打开的条件编译的情况下使用条件编译变量。 启用条件编译会告诉 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 编译器将以 @ 开头的标识符解释为条件编译变量。 为此，可通过在语句开头使用条件代码来执行此操作：  
  
```js
/*@cc_on @*/  
```  
  
### <a name="to-correct-this-error"></a>更正此错误  
  
- 在条件代码的开头添加以下语句：  
  
    ```JavaScript  
    /*@cc_on @*/  
    ```  
  
## <a name="see-also"></a>请参阅  
 [条件编译](/previous-versions/windows/internet-explorer/ie-developer/scripting-articles/121hztk3(v=vs.84))   
 [条件编译变量](/previous-versions/windows/internet-explorer/ie-developer/scripting-articles/s59bkzce(v=vs.84))   
 [@cc_on 损益](https://developer.mozilla.org/docs/Archive/Web/JavaScript/Microsoft_Extensions/at-cc-on)   
 [@if 损益](https://developer.mozilla.org/docs/Archive/Web/JavaScript/Microsoft_Extensions/at-if)   
 [@set 损益](https://developer.mozilla.org/docs/Archive/Web/JavaScript/Microsoft_Extensions/at-set)