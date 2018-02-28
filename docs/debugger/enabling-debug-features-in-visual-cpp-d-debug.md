---
title: "啟用偵錯 Visual c + + 功能 (-/d_debug) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0f1067ee5b60b8a8a402c9612357f2d83b6da138
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="enabling-debug-features-in-visual-c-ddebug"></a>啟用 Visual C++ 的偵錯功能 (/D_DEBUG)
在[!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)]，偵錯功能，當您編譯您的程式使用的符號時，會啟用判斷提示之類**_DEBUG**定義。 您可以定義**_DEBUG**中有兩種：  
  
-   指定**#define _DEBUG**您在原始程式碼中，或  
  
-   指定**/D_DEBUG**編譯器選項。 (如果您在 Visual Studio 中使用精靈，建立您的專案**/D_DEBUG**在偵錯組態會自動定義。)  
  
 當**_DEBUG**是定義，編譯器會編譯包圍的程式碼區段**#ifdef _DEBUG**和`#endif`。  
  
 MFC 程式的偵錯組態必須與 MFC 程式庫的偵錯版本連結。 MFC 標頭檔會決定要連結的 MFC 程式庫的正確版本根據定義，例如符號**_DEBUG**和**_UNICODE**。 如需詳細資訊，請參閱[MFC 程式庫版本](/cpp/mfc/mfc-library-versions)。  
  
## <a name="see-also"></a>請參閱  
 [偵錯機器碼](../debugger/debugging-native-code.md)   
 [C++ 偵錯組態的專案設定](../debugger/project-settings-for-a-cpp-debug-configuration.md)