---
title: CRT 调试堆详细信息 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debug heap, accessing
- heap functions
- _CRTDBG_CHECK_ALWAYS_DF macro
- _CrtMemDumpStatistics function
- debugging [C++], debug heap
- _CRT_BLOCK macro
- DBGINT.H file
- _CrtMemDumpAllObjectsSince function
- _crtBreakAlloc global variable
- _CrtMemState function
- _CLIENT_BLOCK macro
- _FREE_BLOCK block
- _CrtMemBlockHeader function
- heap state reporting functions
- _CRTDBG_ALLOC_MEM_DF macro
- _CrtSetBreakAlloc function
- memory blocks, allocation types on debug heap
- debugging [C++], CRT debug support
- debug heap, tracking heap allocation requests
- memory allocation, debug heap
- _NORMAL_BLOCK block
- crtBreakAlloc global variable
- _CrtDoForAllClientObjects function
- new operator, using debug heap from C++
- _CrtSetDumpClient function
- debugging [CRT], heap-related problems
- debug heap, solving memory allocation problems
- _CrtMemCheckpoint function
- debug builds, linking to debug heap
- _IGNORE_BLOCK block
- _crtDbgFlag function
- client blocks, specifying subtypes
- memory leaks, tracking
- _CrtSetDbgFlag function
- nBlockUse method
- memory leaks, CRT debug library functions
- _CRTDBG_DELAY_FREE_MEM_DF macro
- allocation request numbers
- _CRTDBG_LEAK_CHECK_DF macro
- debug heap
- memory, debugging
- _CrtReportBlockType function
- _CrtDumpMemoryLeaks function
- _CrtCheckMemory function
- debug heap, CRT
- memory blocks, free
- _BLOCK_TYPE macro
- debug heap, memory blocks
- heap allocation, debug
- debugging memory leaks
- _BLOCK_SUBTYPE macro
- debug heap, using from C++
- _CrtMemDifference function
- heap allocation, tracking requests
- debugging [Visual Studio], debug heap
- delete operator, using debug heap from C++
- blocks, types of on the debug heap
- _CRTDBG_CHECK_CRT_DF macro
- debug heap, reporting functions
ms.assetid: bf78ace6-28e4-4a04-97c6-39e0cdd00ba4
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: df3dbcd36bdb72bdd76972ff03a295ba9310f8f7
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/23/2018
ms.locfileid: "49897077"
---
# <a name="crt-debug-heap-details"></a>CRT 调试堆详细信息
本主题详细描述了 CRT 调试堆。  
  
##  <a name="BKMK_Contents"></a> 内容  
 [利用调试堆查找缓冲区溢出](#BKMK_Find_buffer_overruns_with_debug_heap)  
  
 [调试堆上的块类型](#BKMK_Types_of_blocks_on_the_debug_heap)  
  
 [检查堆完整性和内存泄漏](#BKMK_Check_for_heap_integrity_and_memory_leaks)  
  
 [配置调试堆](#BKMK_Configure_the_debug_heap)  
  
 [new、 delete 和 _client_block 中 c + + 调试堆](#BKMK_new__delete__and__CLIENT_BLOCKs_in_the_C___debug_heap)  
  
 [堆状态报告函数](#BKMK_Heap_State_Reporting_Functions)  
  
 [跟踪堆分配请求](#BKMK_Track_Heap_Allocation_Requests)  
  
##  <a name="BKMK_Find_buffer_overruns_with_debug_heap"></a> 利用调试堆查找缓冲区溢出  
 覆盖已分配缓冲区的末尾以及内存泄漏，是两种程序员最常遇到又棘手的问题（未能在不再需要某些分配后将其释放）。 调试堆提供功能强大的工具来解决这类内存分配问题。  
  
 堆函数的“Debug”版本调用“Release”版本中使用的标准版本或基版本。 当请求内存块时，调试堆管理器从基堆分配略大于所请求块的内存块，并返回指向该块中属于您的部分的指针。 例如，假定应用程序包含调用：`malloc( 10 )`。 在发布版本中， [malloc](/cpp/c-runtime-library/reference/malloc)将调用基堆分配例程以请求分配 10 个字节。 在调试版本中，但是，`malloc`将调用[_malloc_dbg](/cpp/c-runtime-library/reference/malloc-dbg)，随后就其可以调用基堆分配例程，以请求分配 10 个字节加上大约 36 个字节的额外内存。 调试堆中产生的所有内存块，在单个链接列表中连接起来，按照分配时间排序。  
  
 调试堆例程分配的附加内存的用途为：存储簿记信息，存储将调试内存块链接在一起的指针，以及形成数据两侧的小缓冲区（用于捕捉已分配区域的覆盖）。  
  
 当前，用于存储调试堆的簿记信息块的头结构在 DBGINT.H 头文件中声明如下：  
  
```cpp
typedef struct _CrtMemBlockHeader  
{  
// Pointer to the block allocated just before this one:  
    struct _CrtMemBlockHeader *pBlockHeaderNext;  
// Pointer to the block allocated just after this one:  
    struct _CrtMemBlockHeader *pBlockHeaderPrev;  
    char *szFileName;    // File name  
    int nLine;           // Line number  
    size_t nDataSize;    // Size of user block  
    int nBlockUse;       // Type of block  
    long lRequest;       // Allocation number  
// Buffer just before (lower than) the user's memory:  
    unsigned char gap[nNoMansLandSize];  
} _CrtMemBlockHeader;  
  
/* In an actual memory block in the debug heap,  
 * this structure is followed by:  
 *   unsigned char data[nDataSize];  
 *   unsigned char anotherGap[nNoMansLandSize];  
 */  
```  
  
 `NoMansLand`块的用户数据区域两侧的缓冲区目前大小为 4 个字节，使用调试堆例程验证用户的内存块，限制的已知的字节值填充。 调试堆同样用已知值填充新的内存块。 如果选择在堆的链接列表中保留已释放块（如下文所述），则这些已释放块也用已知值填充。 当前，所用的实际字节值如下所示：  
  
 NoMansLand (0xFD)  
 应用程序用当前用 0xFD 填充内存两侧的“NoMansLand”缓冲区。  
  
 已释放块 (0xDD)  
 设置 `_CRTDBG_DELAY_FREE_MEM_DF` 标志后，调试堆的链接列表中保留未使用的已释放块当前用 0xDD 填充。  
  
 新对象 (0xCD)  
 分配新对象时，这些对象用 0xCD 填充。  
  
 ![返回页首](../debugger/media/pcs_backtotop.png "PCS_BackToTop")  
  
 ![返回页首](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [目录](#BKMK_Contents)  
  
##  <a name="BKMK_Types_of_blocks_on_the_debug_heap"></a> 调试堆上的块类型  

 调试堆中的每个内存块都分配以五种分配类型之一。 出于泄漏检测和状态报告目的对这些类型进行不同地跟踪和报告。 可以指定块的类型，方法是使用类似于直接调用调试堆分配函数之一来分配[_malloc_dbg](/cpp/c-runtime-library/reference/malloc-dbg)。 调试堆中内存块的五种类型 (在中设置**nBlockUse**的成员 **_CrtMemBlockHeader**结构) 如下所示：  
  
 **_NORMAL_BLOCK**  
 调用[malloc](/cpp/c-runtime-library/reference/malloc)或[calloc](/cpp/c-runtime-library/reference/calloc)创建普通块。 如果你想要使用普通的块，而不需要对客户端块，您可能想要定义[_CRTDBG_MAP_ALLOC](/cpp/c-runtime-library/crtdbg-map-alloc)，这将导致所有堆分配调用映射到其调试版本中的调试等效项。 这将允许将关于每个分配调用的文件名和行号信息存储到对应的块头中。  
  
 `_CRT_BLOCK`  
 由许多运行库函数内部分配的内存块被标记为 CRT 块，以便可以单独处理这些块。 结果，泄漏检测和其他操作不需要受这些块影响。 分配永不可以分配、重新分配或释放任何 CRT 类型的块。  
  
 `_CLIENT_BLOCK`  
 出于调试目的，应用程序可以专门跟踪一组给定的分配，方法是使用对调试堆函数的显式调用将它们作为该类型的内存块进行分配。 MFC 中，例如，分配所有**Cobject**作为客户端块; 其他应用程序可能会使不同的内存对象在客户端块中。 还可以指定“客户端”块的子类型以获得更大的跟踪粒度。 若要指定“客户端”块子类型，请将该数字向左移 16 位，并将它与 `OR` 进行 `_CLIENT_BLOCK` 运算。 例如：  
  
```cpp
#define MYSUBTYPE 4  
freedbg(pbData, _CLIENT_BLOCK|(MYSUBTYPE<<16));  
```  
  
 可以使用安装客户端提供的挂钩函数，以转储存储在客户端块中的对象[_CrtSetDumpClient](/cpp/c-runtime-library/reference/crtsetdumpclient)，然后将每当调试函数转储客户端块时调用。 此外， [_CrtDoForAllClientObjects](/cpp/c-runtime-library/reference/crtdoforallclientobjects)可用于调用应用程序在调试堆中的每个客户端块所提供的给定的函数。  
  
 **_FREE_BLOCK**  
 通常，所释放的块将从列表中移除。 为了检查并未仍在向已释放的内存写入数据，或为了模拟内存不足情况，可以选择在链接列表上保留已释放块，将其标记为“可用”，并用已知字节值（当前为 0xDD）填充。  
  
 **_IGNORE_BLOCK**  
 有可能在一段时间内关闭调试堆操作。 在该时间段内，内存块保留在列表上，但被标记为“忽略”块。  
  
 若要确定的类型和给定的块的子类型，请使用函数[_CrtReportBlockType](/cpp/c-runtime-library/reference/crtreportblocktype)和宏 **_BLOCK_TYPE**并 **_BLOCK_SUBTYPE**。 宏的定义（在 crtdbg.h 中）如下所示：  
  
```cpp
#define _BLOCK_TYPE(block)          (block & 0xFFFF)  
#define _BLOCK_SUBTYPE(block)       (block >> 16 & 0xFFFF)  
```  
  
 ![返回页首](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [目录](#BKMK_Contents)  
  
##  <a name="BKMK_Check_for_heap_integrity_and_memory_leaks"></a> 检查堆完整性和内存泄漏  
 许多调试堆功能必须从代码内访问。 下一节描述其中一些功能以及如何使用这些功能。  
  
 `_CrtCheckMemory`  
 可以使用调用[_CrtCheckMemory](/cpp/c-runtime-library/reference/crtcheckmemory)，例如，若要查看任何时候堆的完整性。 该函数检查堆中的每个内存块，验证内存块头信息有效，并确认尚未修改缓冲区。  
  
 `_CrtSetDbgFlag`  
 您可以控制如何将跟踪调试堆的分配使用的内部标志[_crtDbgFlag](/cpp/c-runtime-library/crtdbgflag)，这可以读取和使用设置[_CrtSetDbgFlag](/cpp/c-runtime-library/reference/crtsetdbgflag)函数。 通过更改该标志，可以指示调试堆在程序退出时检查内存泄漏，并报告检测到的所有泄漏。 类似地，可以指定不将已释放的内存块从链接列表移除，以模拟内存不足情况。 当检查堆时，将完全检查这些已释放的块，以确保它们未受打扰。  
  
 **_CrtDbgFlag**标志包含下列位域：  
  
|位域|默认<br /><br /> 值|描述|  
|---------------|-----------------------|-----------------|  
|**_CRTDBG_ALLOC_MEM_DF**|On|打开调试分配。 当该位为 off，分配仍链接在一起，但它们的块类型是 **_IGNORE_BLOCK**。|  
|**_CRTDBG_DELAY_FREE_MEM_DF**|Off|防止实际释放内存，与模拟内存不足情况相同。 当该位为 on 时，已释放的块保留在调试堆的链接列表，但标记为 **_FREE_BLOCK** ，并用特殊字节值。|  
|**_CRTDBG_CHECK_ALWAYS_DF**|Off|将导致 **_CrtCheckMemory**每个分配和解除分配时要调用。 这将减慢执行，但可快速捕捉错误。|  
|**_CRTDBG_CHECK_CRT_DF**|Off|导致块标记为类型 **_CRT_BLOCK**要包含在泄漏检测和状态差异操作中。 当该位为 off 时，在这些操作期间将忽略由运行库内部使用的内存。|  
|**_CRTDBG_LEAK_CHECK_DF**|Off|会导致泄漏检查要执行在程序退出时通过调用 **_CrtDumpMemoryLeaks**。 如果应用程序未能释放其所分配的所有内存，将生成错误报告。|  
  
 ![返回页首](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [目录](#BKMK_Contents)  
  
##  <a name="BKMK_Configure_the_debug_heap"></a> 配置调试堆  
 对于堆函数（例如 `malloc`、`free`、`calloc`、`realloc`、`new` 和 `delete`）的所有调用均解析为这些函数在调试堆中运行的调试版本。 当释放内存块时，调试堆自动检查已分配区域两侧的缓冲区的完整性，如果发生覆盖，将发出错误报告。  
  
 **若要使用调试堆**  
  
- 用 C 运行库的调试版本链接应用程序的调试版本。  
  
  **若要更改一个或多个 _crtDbgFlag 位域并创建标志的新状态**  
  
1. 在 `_CrtSetDbgFlag` 参数设置为 `newFlag` 的情况下调用 `_CRTDBG_REPORT_FLAG`（以获取当前的 `_crtDbgFlag` 状态），并在一个临时变量中存储返回值。  
  
2. 打开的任何位`OR`-ing (按位&#124;符号) 带相应位屏蔽 （在应用程序代码中由清单常量显示） 的临时变量。  
  
3. 通过对带有相应位屏蔽的 `AND`（按位 ~ 符号）的变量进行 `NOT`-ing（按位 & 符号）运算关闭其他位。  
  
4. 在 `_CrtSetDbgFlag` 参数设置为临时变量中存储的值的情况下调用 `newFlag`，以创建 `_crtDbgFlag` 的新状态。  
  
   例如，下列代码行打开自动泄漏检测，关闭检查 `_CRT_BLOCK` 类型的块：  
  
```cpp
// Get current flag  
int tmpFlag = _CrtSetDbgFlag( _CRTDBG_REPORT_FLAG );  
  
// Turn on leak-checking bit.  
tmpFlag |= _CRTDBG_LEAK_CHECK_DF;  
  
// Turn off CRT block checking bit.  
tmpFlag &= ~_CRTDBG_CHECK_CRT_DF;  
  
// Set flag to the new value.  
_CrtSetDbgFlag( tmpFlag );  
```  
  
 ![返回页首](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [目录](#BKMK_Contents)  
  
##  <a name="BKMK_new__delete__and__CLIENT_BLOCKs_in_the_C___debug_heap"></a> new、 delete 和 _client_block 中 c + + 调试堆  
 C 运行库的调试版本包含 C++ `new` 和 `delete` 运算符的调试版本。 如果使用 `_CLIENT_BLOCK` 分配类型，则必须直接调用 `new` 运算符的调试版本，或者创建可在调试模式中替换 `new` 运算符的宏，如下面的示例所示：  
  
```cpp
/* MyDbgNew.h  
 Defines global operator new to allocate from  
 client blocks  
*/  
  
#ifdef _DEBUG  
   #define DEBUG_CLIENTBLOCK   new( _CLIENT_BLOCK, __FILE__, __LINE__)  
#else  
   #define DEBUG_CLIENTBLOCK  
#endif // _DEBUG  
  
/* MyApp.cpp  
        Use a default workspace for a Console Application to  
 *      build a Debug version of this code  
*/  
  
#include "crtdbg.h"  
#include "mydbgnew.h"  
  
#ifdef _DEBUG  
#define new DEBUG_CLIENTBLOCK  
#endif  
  
int main( )   {  
    char *p1;  
    p1 =  new char[40];  
    _CrtMemDumpAllObjectsSince( NULL );  
}  
```  
  
 `delete` 运算符的“Debug”版本可用于所有块类型，并且编译“Release”版本时程序中不需要任何更改。  
  
 ![返回页首](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [目录](#BKMK_Contents)  
  
##  <a name="BKMK_Heap_State_Reporting_Functions"></a> 堆状态报告函数  
 **_CrtMemState**  
  
 若要捕获给定时刻堆状态的摘要快照，请使用 CRTDBG.H 中定义的 _CrtMemState 结构：  
  
```cpp
typedef struct _CrtMemState  
{  
    // Pointer to the most recently allocated block:  
    struct _CrtMemBlockHeader * pBlockHeader;  
    // A counter for each of the 5 types of block:  
    size_t lCounts[_MAX_BLOCKS];  
    // Total bytes allocated in each block type:  
    size_t lSizes[_MAX_BLOCKS];  
    // The most bytes allocated at a time up to now:  
    size_t lHighWaterCount;  
    // The total bytes allocated at present:  
    size_t lTotalCount;  
} _CrtMemState;  
```  
  
 该结构保存指向调试堆的链接列表中的第一个（最近分配的）块的指针。 然后，它在两个数组中记录列表中每种类型的内存块（_NORMAL_BLOCK、`_CLIENT_BLOCK`、_FREE_BLOCK 等等）的个数，以及每种类型的块中分配的字节数。 最后，它记录到该点为止堆中总共分配的最大字节数以及当前分配的字节数。  
  
 **其他 CRT 报告函数**  
  
 下列函数报告堆的状态和内容，并使用这些信息帮助检测内存泄漏及其他问题：  
  
|函数|描述|  
|--------------|-----------------|  
|[_CrtMemCheckpoint](/cpp/c-runtime-library/reference/crtmemcheckpoint)|将保存在堆的快照 **_CrtMemState**应用程序所提供的结构。|  
|[_CrtMemDifference](/cpp/c-runtime-library/reference/crtmemdifference)|比较两个内存状态结构，在第三个状态结构中保存二者之间的差异，如果两个状态不同，则返回 TRUE。|  
|[_CrtMemDumpStatistics](/cpp/c-runtime-library/reference/crtmemdumpstatistics)|转储给定 **_CrtMemState**结构。 该结构可能包含给定时刻调试堆状态的快照或两个快照之间的差异。|  
|[_CrtMemDumpAllObjectsSince](/cpp/c-runtime-library/reference/crtmemdumpallobjectssince)|转储有关在堆的给定快照之后，或是从执行开始时起，分配的所有对象的信息。 每次它转储 **_CLIENT_BLOCK**块中，它调用应用程序，所提供的挂钩函数，如果已使用安装其中一个 **_CrtSetDumpClient**。|  
|[_CrtDumpMemoryLeaks](/cpp/c-runtime-library/reference/crtdumpmemoryleaks)|确定自程序开始执行以来是否发生过内存泄漏，如果发生过，则转储所有已分配对象。 每次 **_CrtDumpMemoryLeaks**转储 **_CLIENT_BLOCK**块中，它调用应用程序，所提供的挂钩函数，如果已使用安装一个 **_CrtSetDumpClient**.|  
  
 ![返回页首](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [目录](#BKMK_Contents)  
  
##  <a name="BKMK_Track_Heap_Allocation_Requests"></a> 跟踪堆分配请求  
 尽管查明在其中执行断言或报告宏的源文件名和行号对于定位问题原因常常很有用，对于堆分配函数却可能不是这样。 虽然可在应用程序的逻辑树中的许多适当点插入宏，但分配经常隐藏在特殊例程中，该例程会在很多不同时刻从很多不同位置进行调用。 问题通常并不在于如何确定哪行代码进行了错误分配，而在于如何确定该行代码进行的上千次分配中的哪一次是错误分配以及原因。  
  
 **唯一分配请求编号和 _crtBreakAlloc**  
  
 标识发生错误的特定堆分配调用的最简单方法是利用与调试堆中的每个块关联的唯一分配请求编号。 当其中一个转储函数报告有关一个块的信息时，该分配请求编号将括在大括号中 (例如，"{36}")。  
  
 一旦您知道某个错误分配块的分配请求编号，您可以将该编号传递给[_CrtSetBreakAlloc](/cpp/c-runtime-library/reference/crtsetbreakalloc)创建断点。 执行将恰在分配该块以前中断，您可以向回追踪以确定哪个例程执行了错误调用。 若要避免重新编译，可以完成相同的事情在调试器中设置 **_crtBreakAlloc**到感兴趣的分配请求编号。  
  
 **创建分配例程的调试版本**  
  
 稍微复杂一些，方法是创建类似于您自己分配例程的调试版本 **_dbg**新版[堆分配函数](../debugger/debug-versions-of-heap-allocation-functions.md)。 然后，可以将源文件和行号自变量传递给基础堆分配例程，并能立即看到错误分配的出处。  
  
 例如，假定您的应用程序包含与下面类似的常用例程：  
  
```cpp
int addNewRecord(struct RecStruct * prevRecord,  
                 int recType, int recAccess)  
{  
    // ...code omitted through actual allocation...   
    if ((newRec = malloc(recSize)) == NULL)  
    // ... rest of routine omitted too ...   
}  
```  
  
 在头文件中，可以添加如下代码：  
  
```cpp
#ifdef _DEBUG  
#define  addNewRecord(p, t, a) \  
            addNewRecord(p, t, a, __FILE__, __LINE__)  
#endif  
```  
  
 接下来，可以如下更改记录创建例程中的分配：  
  
```cpp
int addNewRecord(struct RecStruct *prevRecord,  
                int recType, int recAccess  
#ifdef _DEBUG  
               , const char *srcFile, int srcLine  
#endif  
    )  
{  
    /* ... code omitted through actual allocation ... */  
    if ((newRec = _malloc_dbg(recSize, _NORMAL_BLOCK,  
            srcFile, scrLine)) == NULL)  
    /* ... rest of routine omitted too ... */  
}  
```  
  
 在其中调用 `addNewRecord` 的源文件名和行号将存储在产生的每个块中（这些块是在调试堆中分配的），并将在检查该块时进行报告。  
  
 ![返回页首](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [目录](#BKMK_Contents)  
  
## <a name="see-also"></a>请参阅  
 [调试本机代码](../debugger/debugging-native-code.md)
