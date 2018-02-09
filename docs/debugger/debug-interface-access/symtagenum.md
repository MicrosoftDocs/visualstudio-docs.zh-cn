---
title: "SymTagEnum |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: SymTagEnum enumeration
ms.assetid: 528a50cf-e13d-46ec-a98c-323d5d047de9
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 9165059991e4b961fc995b96a0c285f28a1587b4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/22/2017
---
# <a name="symtagenum"></a>SymTagEnum
指定符号的类型。  
  
## <a name="syntax"></a>语法  
  
```C++  
enum SymTagEnum {   
   SymTagNull,  
   SymTagExe,  
   SymTagCompiland,  
   SymTagCompilandDetails,  
   SymTagCompilandEnv,  
   SymTagFunction,  
   SymTagBlock,  
   SymTagData,  
   SymTagAnnotation,  
   SymTagLabel,  
   SymTagPublicSymbol,  
   SymTagUDT,  
   SymTagEnum,  
   SymTagFunctionType,  
   SymTagPointerType,  
   SymTagArrayType,   
   SymTagBaseType,   
   SymTagTypedef,   
   SymTagBaseClass,  
   SymTagFriend,  
   SymTagFunctionArgType,   
   SymTagFuncDebugStart,   
   SymTagFuncDebugEnd,  
   SymTagUsingNamespace,   
   SymTagVTableShape,  
   SymTagVTable,  
   SymTagCustom,  
   SymTagThunk,  
   SymTagCustomType,  
   SymTagManagedType,  
   SymTagDimension,  
   SymTagCallSite,  
   SymTagInlineSite,  
   SymTagBaseInterface,  
   SymTagVectorType,  
   SymTagMatrixType,  
   SymTagHLSLType  
};  
```  
  
## <a name="elements"></a>元素  
 `SymTagNull`  
 指示符号具有任何类型。  
  
 `SymTagExe`  
 指示符号是.exe 文件。 只有一个`SymTagExe`每符号存储区的符号。 它用作全局作用域，并不具有词法父级。  
  
 `SymTagCompiland`  
 指示每个编译单位组件的符号存储区的编译单位符号。 对于本机应用程序，`SymTagCompiland`符号对应对象文件链接到的映像。 对于某些类型的 Microsoft 中间语言 (MSIL) 映像，是一个编译单位，每个类。  
  
 `SymTagCompilandDetails`  
 指示该符号包含编译单位的扩展的属性。 检索这些属性可能需要加载编译单位符号。  
  
 `SymTagCompilandEnv`  
 指示符号为环境字符串为编译单位定义。  
  
 `SymTagFunction`  
 指示符号是一个函数。  
  
 `SymTagBlock`  
 指示符号是嵌套的块。  
  
 `SymTagData`  
 指示符号数据。  
  
 `SymTagAnnotation`  
 指示符号针对的代码批注。 此符号的子级是连续的数据字符串 (`SymTagData`， `LocIsConstant`， `DataIsConstant`)。 大多数客户端忽略此符号。  
  
 `SymTagLabel`  
 指示符号是一个标签。  
  
 `SymTagPublicSymbol`  
 指示符号是公共符号。 对于本机应用程序，此符号是链接映像时遇到 COFF 外部符号。  
  
 `SymTagUDT`  
 指示该符号为用户定义类型 （结构、 类或联合）。  
  
 `SymTagEnum`  
 指示符号是一个枚举。  
  
 `SymTagFunctionType`  
 指示符号是函数签名类型。  
  
 `SymTagPointerType`  
 指示符号是指针类型。  
  
 `SymTagArrayType`  
 指示符号是一个数组类型。  
  
 `SymTagBaseType`  
 指示符号是基类型。  
  
 `SymTagTypedef`  
 指示该符号`typedef`，即，另一种类型的别名。  
  
 `SymTagBaseClass`  
 指示符号是用户定义类型的基类。  
  
 `SymTagFriend`  
 指示符号是用户定义类型的友元。  
  
 `SymTagFunctionArgType`  
 指示符号是一个函数参数。  
  
 `SymTagFuncDebugStart`  
 指示符号是函数的序言代码的结束位置。  
  
 `SymTagFuncDebugEnd`  
 指示符号是函数的尾声代码的开始位置。  
  
 `SymTagUsingNamespace`  
 指示符号是当前作用域中处于活动状态的命名空间名称。  
  
 `SymTagVTableShape`  
 指示符号是虚拟表说明。  
  
 `SymTagVTable`  
 指示了符号是一个虚拟表指针。  
  
 `SymTagCustom`  
 表示符号是一个自定义的符号，无法解释 DIA.  
  
 `SymTagThunk`  
 指示符号是一个 thunk，用于 16 和 32 位代码之间的共享数据。  
  
 `SymTagCustomType`  
 表示符号自定义编译器符号。  
  
 `SymTagManagedType`  
 指示符号是在元数据中。  
  
 `SymTagDimension`  
 指示符号是 FORTRAN 多维数组。  
  
 `SymTagCallSite`  
 指示符号表示调用站点。  
  
 `SymTagInlineSite`  
 指示符号表示内联站点。  
  
 `SymTagBaseInterface`  
 指示符号是一个基接口。  
  
 `SymTagVectorType`  
 指示符号是矢量类型。  
  
 `SymTagMatrixType`  
 指示该符号为矩阵类型。  
  
 `SymTagHLSLType`  
 指示符号为高级别着色器语言类型。  
  
## <a name="remarks"></a>备注  
 调试文件中的所有符号都有一个识别的标记，它指定符号的类型。  
  
 此枚举中的值返回通过调用[idiasymbol:: Get_symtag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)方法。  
  
 此枚举中的值将传递到以下的方法，以限制对特定符号类型的搜索作用域中：  
  
-   [IDiaSession::findSymbolByAddr](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)  
  
-   [IDiaSession::findSymbolByRVA](../../debugger/debug-interface-access/idiasession-findsymbolbyrva.md)  
  
-   [IDiaSession::findSymbolByRVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)  
  
-   [IDiaSession::findSymbolByToken](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)  
  
-   [IDiaSession::findSymbolByVA](../../debugger/debug-interface-access/idiasession-findsymbolbyva.md)  
  
-   [IDiaSession::findSymbolByVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)  
  
-   [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)  
  
-   [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)  
  
## <a name="requirements"></a>需要  
 标头： cvconst.h  
  
## <a name="see-also"></a>请参阅  
 [枚举和结构](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [符号类型的词法层次结构](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)   
 [Idiasession:: Findsymbolbyaddr](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)   
 [Idiasession:: Findsymbolbyrva](../../debugger/debug-interface-access/idiasession-findsymbolbyrva.md)   
 [Idiasession:: Findsymbolbyrvaex](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)   
 [Idiasession:: Findsymbolbytoken](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)   
 [Idiasession:: Findsymbolbyva](../../debugger/debug-interface-access/idiasession-findsymbolbyva.md)   
 [Idiasession:: Findsymbolbyvaex](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)   
 [Idiasession:: Findchildren](../../debugger/debug-interface-access/idiasession-findchildren.md)   
 [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)