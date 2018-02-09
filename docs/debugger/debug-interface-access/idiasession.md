---
title: "IDiaSession |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaSession interface
ms.assetid: 69dab9bf-2c68-4f70-9678-3b50fba3e6fa
caps.latest.revision: "19"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: f3939ab86cd9f0948a2be44756b9ed94d143ecc8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/22/2017
---
# <a name="idiasession"></a>IDiaSession
为调试符号提供查询上下文。  
  
## <a name="syntax"></a>语法  
  
```  
IDiaSession : IUnknown  
```  
  
## <a name="methods"></a>方法  
 下表显示的方法`IDiaSession`。  
  
|方法|描述|  
|------------|-----------------|  
|[IDiaSession::get_loadAddress](../../debugger/debug-interface-access/idiasession-get-loadaddress.md)|检索对应于此符号存储区中的符号的可执行文件的负载地址。 这是相同的值传递到`put_loadAddress`方法。|  
|[IDiaSession::put_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md)|在此符号存储区中将对应的可执行文件的负载地址设置为符号。 **注意：**很重要时，可以调用此方法`IDiaSession`对象，并开始使用该对象之前。|  
|[IDiaSession::get_globalScope](../../debugger/debug-interface-access/idiasession-get-globalscope.md)|检索到全局作用域的引用。|  
|[IDiaSession::getEnumTables](../../debugger/debug-interface-access/idiasession-getenumtables.md)|检索包含在符号存储区中的所有表的枚举数。|  
|[IDiaSession::getSymbolsByAddr](../../debugger/debug-interface-access/idiasession-getsymbolsbyaddr.md)|检索所有命名符号静态位置的枚举数。|  
|[IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)|检索指定的父标识符的所有匹配的名称和符号类型的子级。|  
|[IDiaSession::findSymbolByAddr](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)|检索指定的符号类型包含，或接近指定的地址。|  
|[IDiaSession::findSymbolByRVA](../../debugger/debug-interface-access/idiasession-findsymbolbyrva.md)|检索指定的符号类型包含，或接近指定的相对虚拟地址 (RVA)。|  
|[IDiaSession::findSymbolByVA](../../debugger/debug-interface-access/idiasession-findsymbolbyva.md)|检索指定的符号类型包含，或接近指定的虚拟地址 (VA)。|  
|[IDiaSession::findSymbolByToken](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)|检索包含指定元数据标记的符号。|  
|[IDiaSession::symsAreEquiv](../../debugger/debug-interface-access/idiasession-symsareequiv.md)|检查以确定两个符号是否等效。|  
|[IDiaSession::symbolById](../../debugger/debug-interface-access/idiasession-symbolbyid.md)|检索由其唯一标识符的符号。|  
|[IDiaSession::findSymbolByRVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)|检索包含，或与具有指定的相对虚拟地址和偏移量最接近指定的符号类型。|  
|[IDiaSession::findSymbolByVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)|检索包含，或与具有指定的虚拟地址和偏移量最接近指定的符号类型。|  
|[IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)|检索由编译单位和名称的源文件。|  
|[IDiaSession::findFileById](../../debugger/debug-interface-access/idiasession-findfilebyid.md)|通过源文件标识符来检索源文件。|  
|[IDiaSession::findLines](../../debugger/debug-interface-access/idiasession-findlines.md)|检索指定的编译单位和源文件标识符中的行号。|  
|[IDiaSession::findLinesByAddr](../../debugger/debug-interface-access/idiasession-findlinesbyaddr.md)|检索包含指定的地址的行中指定的编译单位。|  
|[IDiaSession::findLinesByRVA](../../debugger/debug-interface-access/idiasession-findlinesbyrva.md)|检索包含指定的相对虚拟地址的行中指定的编译单位。|  
|[IDiaSession::findLinesByVA](../../debugger/debug-interface-access/idiasession-findlinesbyva.md)|查找指定的地址范围中包含行的行号信息。|  
|[IDiaSession::findLinesByLinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)|检索由源文件和行号指定编译单位中的行。|  
|[IDiaSession::findInjectedSource](../../debugger/debug-interface-access/idiasession-findinjectedsource.md)|检索已放入属性提供程序由符号存储区或其他组件的编译过程的源。|  
|[IDiaSession::getEnumDebugStreams](../../debugger/debug-interface-access/idiasession-getenumdebugstreams.md)|检索一个枚举的调试数据流的序列。|  
|[IDiaSession::findInlineFramesByAddr](../../debugger/debug-interface-access/idiasession-findinlineframesbyaddr.md)|检索一个枚举，允许客户端用于循环访问所有给定的地址上的嵌入式框架。|  
|[IDiaSession::findInlineFramesByRVA](../../debugger/debug-interface-access/idiasession-findinlineframesbyrva.md)|检索一个枚举，允许客户端用于循环访问所有上指定的相对虚拟地址 (RVA) 的嵌入式框架。|  
|[IDiaSession::findInlineFramesByVA](../../debugger/debug-interface-access/idiasession-findinlineframesbyva.md)|检索一个枚举，允许客户端用于循环访问所有上指定的虚拟地址 (VA) 的嵌入式框架。|  
|[IDiaSession::findInlineeLines](../../debugger/debug-interface-access/idiasession-findinlineelines.md)|检索一个枚举，允许客户端循环访问的行号信息的所有函数的内联，直接或间接地，由指定的父符号。|  
|[IDiaSession::findInlineeLinesByAddr](../../debugger/debug-interface-access/idiasession-findinlineelinesbyaddr.md)|检索一个枚举，允许客户端循环访问的行号信息的所有函数的内联，直接或间接地，由指定的父符号和都包含在指定的地址范围。|  
|[IDiaSession::findInlineeLinesByRVA](../../debugger/debug-interface-access/idiasession-findinlineelinesbyrva.md)|检索一个枚举，允许客户端循环访问的行号信息的所有函数的内联，直接或间接地，由指定的父符号和都包含在指定的相对虚拟地址 (RVA)。|  
|[IDiaSession::findInlineeLinesByVA](../../debugger/debug-interface-access/idiasession-findinlineelinesbyva.md)|检索一个枚举，允许客户端循环访问的行号信息的所有函数的内联，直接或间接地，由指定的父符号和都包含在指定的虚拟地址 (VA)。|  
|[IDiaSession::findInlineeLinesByLinenum](../../debugger/debug-interface-access/idiasession-findinlineelinesbylinenum.md)|检索一个枚举，允许客户端遍历所有函数内联，直接或间接中指定的源文件和行号的行号信息。|  
|[IDiaSession::findInlineesByName](../../debugger/debug-interface-access/idiasession-findinlineesbyname.md)|检索一个枚举，允许客户端循环访问与指定的名称匹配的所有内联函数的行号信息。|  
|[IDiaSession::findSymbolsForAcceleratorPointerTag](../../debugger/debug-interface-access/idiasession-findsymbolsforacceleratorpointertag.md)|父快捷键存根 （stub） 函数中返回符号的变量的指定的标记值对应于的枚举。|  
|[IDiaSession::findSymbolsByRVAForAcceleratorPointerTag](../../debugger/debug-interface-access/idiasession-findsymbolsbyrvaforacceleratorpointertag.md)|给定相应的标记值，则此方法将返回在指定的相对虚拟地址处的指定的父快捷键存根 （stub） 函数中包含的符号的枚举。|  
|[IDiaSession::findAcceleratorInlineesByName](../../debugger/debug-interface-access/idiasession-findacceleratorinlineesbyname.md)|返回与指定的内联函数名称对应的嵌入式框架的符号的枚举。|  
|[IDiaSession::findAcceleratorInlineesByLinenum](../../debugger/debug-interface-access/idiasession-findacceleratorinlineesbylinenum.md)|返回到指定的源位置的符号对应的嵌入式框架枚举。|  
  
## <a name="remarks"></a>备注  
 务必要调用[idiasession:: Put_loadaddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md)方法之后创建`IDiaSession`对象-和值传递给`put_loadAddress`方法必须为非零-符号的任何虚拟地址 (VA) 的属性可访问。 负载地址来自于任何程序加载正在调试的可执行文件。 例如，你可以调用 Win32 函数`GetModuleInformation`用于检索负载地址的可执行文件，给出的可执行文件句柄。  
  
## <a name="example"></a>示例  
 此示例演示如何获取`IDiaSession`作为 DIA SDK 的常规初始化的一部分的接口。  
  
```C++  
CComPtr<IDiaDataSource> pSource;  
ComPtr<IDiaSession> psession;  
  
void InitializeDIA(const char *szFilename)  
{  
    HRESULT hr = CoCreateInstance( CLSID_DiaSource,  
                                   NULL,  
                                   CLSCTX_INPROC_SERVER,  
                                   __uuidof( IDiaDataSource ),  
                                  (void **) &pSource);  
    if (FAILED(hr))  
    {  
        Fatal("Could not CoCreate CLSID_DiaSource. Register msdia80.dll." );  
    }  
    wchar_t wszFilename[ _MAX_PATH ];  
    mbstowcs( wszFilename,  
              szFilename,  
              sizeof( wszFilename )/sizeof( wszFilename[0] ) );  
    if ( FAILED( pSource->loadDataFromPdb( wszFilename ) ) )  
    {  
        if ( FAILED( pSource->loadDataForExe( wszFilename, NULL, NULL ) ) )  
        {  
            Fatal( "loadDataFromPdb/Exe" );  
        }  
    }  
    if ( FAILED( pSource->openSession( &psession ) ) )  
    {  
        Fatal( "openSession" );  
    }  
}  
```  
  
## <a name="requirements"></a>需要  
 标头： Dia2.h  
  
 库： diaguids.lib  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>请参阅  
 [接口 （调试接口访问 SDK）](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [概述](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)   
 [Exe](../../debugger/debug-interface-access/exe.md)   
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)   
 [Idiadatasource:: Opensession](../../debugger/debug-interface-access/idiadatasource-opensession.md)   
 [Idiasymbol:: Findchildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)   
 [查询 .Pdb 文件](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)