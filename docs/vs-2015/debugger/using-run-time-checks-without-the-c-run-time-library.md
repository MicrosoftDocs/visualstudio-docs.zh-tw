---
title: 使用執行階段檢查時不使用 C 執行階段程式庫 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.runtime
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- run-time errors, error checks
- CRT, run-time checks
- debugger, native run-time checks
- run-time errors, run-time checks
- run-time checks, /RTC option
- debugging [Visual Studio], run-time routines
ms.assetid: 30ed90f3-9323-4784-80a4-937449eb54f6
caps.latest.revision: 20
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7f5d9c56cfde6e87c0f9bd92289597e77bfea875
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58930318"
---
# <a name="using-run-time-checks-without-the-c-run-time-library"></a>不使用 C 語言執行階段程式庫進行執行階段檢查
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

如果您連結您的程式不使用 C 執行階段程式庫，請使用 **/NODEFAULTLIB**，並想要使用執行階段檢查，您必須連結 runtmchk.lib。  
  
 `_RTC_Initialize` 將為執行階段檢查初始化您的程式。 如果沒有連結 C 語言執行階段程式庫，您就必須在呼叫 `_RTC_Initialize` 之前，檢查程式是否由執行階段錯誤檢查進行編譯，如下所示：  
  
```  
#ifdef __MSVC_RUNTIME_CHECKS  
    _RTC_Initialize();  
#endif  
```  
  
 如果沒有連結 C 語言執行階段程式庫，您也必須定義名為 `_CRT_RTC_INITW` 的函式。 `_CRT_RTC_INITW` 會將您的使用者定義函式安裝成預設的錯誤報告函式，如下所示：  
  
```  
// C version:  
_RTC_error_fnW __cdecl _CRT_RTC_INITW(  
        void *res0, void **res1, int res2, int res3, int res4)  
{  
    // set the error handler.  
    return &MyErrorFunc;   
}  
  
// C++ version:  
extern "C" _RTC_error_fnW __cdecl _CRT_RTC_INITW(  
       void *res0, void **res1, int res2, int res3, int res4)  
{  
    // set the error handler:  
    return &MyErrorFunc;  
}  
```  
  
 您可以在安裝好預設錯誤報告函式之後，使用 `_RTC_SetErrorFuncW` 安裝其他錯誤報告函式。 如需詳細資訊，請參閱 [_RTC_SetErrorFuncW](http://msdn.microsoft.com/library/b3e0d71f-1bd3-4c37-9ede-2f638eb3c81a)。  
  
## <a name="see-also"></a>另請參閱  
 [如何：使用原生執行階段檢查](../debugger/how-to-use-native-run-time-checks.md)
