---
title: "BasicType |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: BasicType enumeration
ms.assetid: 19ae53ba-cd6e-47b6-9f94-27ae663ce955
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 302e935c1b9f772735612e731503f84ccc3e468f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/22/2017
---
# <a name="basictype"></a>BasicType
指定符号的基本类型。  
  
## <a name="syntax"></a>语法  
  
```C++  
enum BasicType {   
   btNoType   = 0,  
   btVoid     = 1,  
   btChar     = 2,  
   btWChar    = 3,  
   btInt      = 6,  
   btUInt     = 7,  
   btFloat    = 8,  
   btBCD      = 9,  
   btBool     = 10,  
   btLong     = 13,  
   btULong    = 14,  
   btCurrency = 25,  
   btDate     = 26,  
   btVariant  = 27,  
   btComplex  = 28,  
   btBit      = 29,  
   btBSTR     = 30,  
   btHresult  = 31  
};  
```  
  
## <a name="elements"></a>元素  
 btNoType  
 未不指定任何基本类型。  
  
 btVoid  
 基本类型是`void`。  
  
 btChar  
 基本类型是`char`（C/c + + 类型）。  
  
 btWChar  
 基本类型是宽 (Unicode) 字符 (`WCHAR`)。  
  
 btInt  
 基本类型是`signed int`（C/c + + 类型）。  
  
 btUInt  
 基本类型是`unsigned int`（C/c + + 类型）。  
  
 btFloat  
 基本类型是一个浮点数 (`FLOAT`)。  
  
 btBCD  
 为二进制编码 （十进制） 基本类型 (`BCD`)。  
  
 btBool  
 基本类型为布尔值 (`BOOL`)。  
  
 btLong  
 基本类型是`long int`（C/c + + 类型）。  
  
 btULong  
 基本类型是`unsigned long int`（C/c + + 类型）。  
  
 btCurrency  
 基本类型是货币。  
  
 btDate  
 基本类型是日期/时间 (`DATE`)。  
  
 btVariant  
 基本类型是变量类型结构 (`VARIANT`)。  
  
 btComplex  
 基本类型是一个复杂的数字。  
  
 btBit  
 基本类型是一个位。  
  
 btBSTR  
 基本类型为基本或二进制字符串 (`BSTR`)。  
  
 btHresult  
 基本类型是`HRESULT`。  
  
## <a name="remarks"></a>备注  
 此枚举中的值由[idiasymbol:: Get_basetype](../../debugger/debug-interface-access/idiasymbol-get-basetype.md)方法。  
  
## <a name="requirements"></a>需要  
 标头： cvconst.h  
  
## <a name="see-also"></a>请参阅  
 [枚举和结构](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [Idiasymbol:: Get_basetype](../../debugger/debug-interface-access/idiasymbol-get-basetype.md)   
 [IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)