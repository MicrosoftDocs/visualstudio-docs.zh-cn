---
title: "常量 （调试接口访问 SDK） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- constants, DIA SDK
- DIA SDK, constants
ms.assetid: aca4ec77-bc08-4cdd-a6ce-8d4a28ea5ea3
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 8241190650bf395e1e4e2467b4862119cd2b10dc
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/22/2017
---
# <a name="constants-debug-interface-access-sdk"></a>常量（调试接口访问 SDK）
这些字符串常量可以用于标识程序调试数据库 (PDB) 文件通过 DIA SDK 的各个部分。  
  
## <a name="constants"></a>常量  
 以下被声明为 C/c + + 宏。  
  
|宏|“值”|  
|-----------|-----------|  
|`DiaTable_Symbols`|L"符号"|  
|`DiaTable_Sections`|L"部分"|  
|`DiaTable_SrcFiles`|L"SourceFiles"|  
|`DiaTable_LineNums`|L"LineNumbers"|  
|`DiaTable_SegMap`|L"SegmentMap"|  
|`DiaTable_Dbg`|L"Dbg"|  
|`DiaTable_InjSrc`|L"InjectedSource"|  
|`DiaTable_FrameData`|L"FrameData"|  
  
## <a name="example"></a>示例  
 下面是一个示例使用这些符号之一：  
  
```C++  
HRESULT GetSymbolTable(IDiaEnumTables *pEnumTables, IDiaTable **pTable)  
{  
    HRESULT hr;  
    VARIANT var;  
    var.vt      = VT_BSTR;  
    var.bstrVal = SysAllocString( DiaTable_Symbols );  
    hr = pEnumTables->Item( var, pTable );  
    return(hr);  
}  
```  
  
## <a name="requirements"></a>需要  
 标头： dia2.h  
  
## <a name="see-also"></a>请参阅  
 [引用](../../debugger/debug-interface-access/debug-interface-access-sdk-reference.md)   
 [枚举和结构](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [接口 （调试接口访问 SDK）](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaEnumTables::Item](../../debugger/debug-interface-access/idiaenumtables-item.md)