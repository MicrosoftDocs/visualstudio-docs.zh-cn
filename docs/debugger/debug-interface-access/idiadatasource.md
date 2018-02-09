---
title: "IDiaDataSource |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaDataSource interface
ms.assetid: 6260ac76-4f9d-4144-ba22-32f8620b32c2
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 51a277d9ff1bf190aa87d7c4e9d8d852f8c38323
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/22/2017
---
# <a name="idiadatasource"></a>IDiaDataSource
启动的调试符号的源的访问。  
  
## <a name="syntax"></a>语法  
  
```  
IDiaDataSource : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Vtable 顺序中的方法  
 下表显示的方法`IDiaDataSource`。  
  
|方法|描述|  
|------------|-----------------|  
|[IDiaDataSource::get_lastError](../../debugger/debug-interface-access/idiadatasource-get-lasterror.md)|检索最后一个的加载错误的文件名称。|  
|[IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)|将打开并准备作为调试数据源的程序数据库 (.pdb) 文件。|  
|[IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)|将打开，并验证程序数据库 (.pdb) 文件与提供; 的签名信息匹配准备调试数据源的.pdb 文件。|  
|[IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)|将打开并准备与.exe/.dll 文件相关联的调试数据。|  
|[IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)|准备存储在内存中数据流通过访问程序数据库 (.pdb) 文件的调试数据。|  
|[IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md)|将打开一个可用于查询符号会话。|  
  
## <a name="remarks"></a>备注  
 对的一种负载方法的调用`IDiaDataSource`接口打开符号源。 成功调用[idiadatasource:: Opensession](../../debugger/debug-interface-access/idiadatasource-opensession.md)方法返回[IDiaSession](../../debugger/debug-interface-access/idiasession.md)支持查询数据源的接口。 如果负载方法返回与文件相关的错误则[idiadatasource:: Get_lasterror](../../debugger/debug-interface-access/idiadatasource-get-lasterror.md)方法返回值包含与错误关联的文件名称。  
  
## <a name="notes-for-callers"></a>调用方的说明  
 此接口通过调用获取`CoCreateInstance`函数与类标识符`CLSID_DiaSource`和的接口 ID `IID_IDiaDataSource`。 该示例演示如何获取此接口。  
  
## <a name="example"></a>示例  
  
```C++  
  
      IDiaDataSource* pSource;  
HRESULT hr = CoCreateInstance(CLSID_DiaSource,  
                              NULL,  
                              CLSCTX_INPROC_SERVER,  
                              IID_IDiaDataSource,  
                              (void**) &pSource);  
if (FAILED(hr))  
{  
    // Report error and exit  
}  
```  
  
## <a name="requirements"></a>需要  
 标头： Dia2.h  
  
 库： diaguids.lib  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>请参阅  
 [接口（调试接口访问 SDK）](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)