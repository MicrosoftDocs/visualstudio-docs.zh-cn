---
title: "LocationType |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: LocationType enumeration
ms.assetid: d3e1eedc-bfd3-4c91-881b-d69565138d0f
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 3f59f33ef51eee099a8dfe5bbc5c822f217f8cd2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/22/2017
---
# <a name="locationtype"></a>LocationType
指示在符号中包含的位置信息的类型。  
  
## <a name="syntax"></a>语法  
  
```C++  
enum LocationType {   
   LocIsNull,  
   LocIsStatic,  
   LocIsTLS,  
   LocIsRegRel,  
   LocIsThisRel,  
   LocIsEnregistered,  
   LocIsBitField,  
   LocIsSlot,  
   LocIsIlRel,  
   LocInMetaData,  
   LocIsConstant,  
   LocTypeMax  
};  
```  
  
## <a name="elements"></a>元素  
 `LocIsNull`  
 位置信息不可用。  
  
 `LocIsStatic`  
 位置是静态的。  
  
 `LocIsTLS`  
 位置是在线程本地存储。  
  
 `LocIsRegRel`  
 位置是注册相对。  
  
 `LocIsThisRel`  
 位置是`this`-相对。  
  
 `LocIsEnregistered`  
 位置是在寄存器中。  
  
 `LocIsBitField`  
 位置是中的位字段。  
  
 `LocIsSlot`  
 位置是 Microsoft 中间语言 (MSIL) 槽。  
  
 `LocIsIlRel`  
 位置是 MSIL 相对。  
  
 `LocInMetaData`  
 位置是在元数据中。  
  
 `LocIsConstant`  
 位置是一个常量值。  
  
 `LocTypeMax`  
 此枚举中的位置类型的数目。  
  
## <a name="remarks"></a>备注  
 属性可供[IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)接口取决于图像文件中的符号的位置。 有关详细信息，请参阅[符号位置](../../debugger/debug-interface-access/symbol-locations.md)。  
  
 此枚举中的值返回通过调用[idiasymbol:: Get_locationtype](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)方法。  
  
## <a name="requirements"></a>需要  
 标头： cvconst.h  
  
## <a name="see-also"></a>请参阅  
 [枚举和结构](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Idiasymbol:: Get_locationtype](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)   
 [符号位置](../../debugger/debug-interface-access/symbol-locations.md)