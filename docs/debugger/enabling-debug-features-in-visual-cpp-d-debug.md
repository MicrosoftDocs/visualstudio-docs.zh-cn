---
title:  在 Visual C++ 中启用调试功能 (-D_DEBUG) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- /D_DEBUG compiler option [C++]
- debugging [C++], enabling debug features
- debugging [MFC], enabling debug features
- assertions, enabling debug features
- D_DEBUG compiler option
- MFC libraries, debug version
- debug builds, MFC
- _DEBUG macro
ms.assetid: 276e2254-7274-435e-ba4d-67fcef4f33bc
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 772467caf74a381fc2ef5cc74e8e31bf2ff0503c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/23/2018
ms.locfileid: "49949612"
---
# <a name="enabling-debug-features-in-visual-c-ddebug"></a>在 Visual C++ 中启用调试功能 (/D_DEBUG)
在[!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)]中，调试功能，如当符号重新编译程序时，启用断言 **_DEBUG**定义。 您可以定义 **_DEBUG**中两种方式之一：  
  
- 指定 **#define _DEBUG**在源代码中或  
  
- 指定 **/D_DEBUG**编译器选项。 (如果在使用向导，Visual Studio 中创建你的项目 **/D_DEBUG**调试配置中自动定义。)  
  
  当 **_DEBUG**是定义，则编译器将编译包围的代码的部分 **#ifdef _DEBUG**和`#endif`。  
  
  MFC 程序的调试配置必须与 MFC 库的调试版本链接。 MFC 标头文件确定要链接的 MFC 库的正确版本根据已定义，如符号 **_DEBUG**并 **_UNICODE**。 有关详细信息，请参阅[MFC 库版本](/cpp/mfc/mfc-library-versions)。  
  
## <a name="see-also"></a>请参阅  
 [调试本机代码](../debugger/debugging-native-code.md)   
 [C++ 调试配置的项目设置](../debugger/project-settings-for-a-cpp-debug-configuration.md)