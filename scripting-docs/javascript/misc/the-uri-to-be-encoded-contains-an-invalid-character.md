---
title: 要编码的 URI 包含无效字符 |Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5024
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: a3f0fdbb-8d4b-41ae-a396-43dfc9483760
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 310db785041de0beb0ebbba0cdd9b7c356397bc4
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/09/2020
ms.locfileid: "91862384"
---
# <a name="the-uri-to-be-encoded-contains-an-invalid-character"></a>要编码的 URI 包含无效字符
您尝试将字符串编码为 URI (统一资源标识符) ，但它包含无效字符。 尽管大多数字符在要转换为 Uri 的字符串内有效，但某些 Unicode 字符序列是非法的。  
  
### <a name="to-correct-this-error"></a>更正此错误  
  
- 确保要编码的字符串只包含有效的 Unicode 序列。 完整的 URI 由一个组件和分隔符序列组成。 尖括号中的名称表示组件，"："、"/"、";" 和 "？" 是用作分隔符的保留字符。 一般形式为：  
  
    ```JavaScript  
    <Scheme>:<first>/<second>;<third>?<fourth>  
    ```  
  
## <a name="see-also"></a>请参阅  
 [encodeURI 函数](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/encodeuri)   
 [encodeURIComponent 函数](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/encodeuricomponent)