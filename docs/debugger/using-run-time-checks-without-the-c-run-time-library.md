---
title: 使用執行階段檢查時不使用 C 執行階段程式庫 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.runtime
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- run-time errors, error checks
- CRT, run-time checks
- debugger, native run-time checks
- run-time errors, run-time checks
- run-time checks, /RTC option
- debugging [Visual Studio], run-time routines
ms.assetid: 30ed90f3-9323-4784-80a4-937449eb54f6
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a4fb9f61242490b30e1b89132f4e79fbb56d48de
ms.sourcegitcommit: 0bf2aff6abe485e3fe940f5344a62a885ad7f44e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37056012"
---
# <a name="using-run-time-checks-without-the-c-run-time-library"></a>不使用 C 語言執行階段程式庫進行執行階段檢查
如果您連結您的程式不使用 C 執行階段程式庫，請使用 **/NODEFAULTLIB**，並想要使用執行階段檢查，您必須連結 runtmchk.lib。  
  
 `_RTC_Initialize` 將為執行階段檢查初始化您的程式。 如果沒有連結 C 語言執行階段程式庫，您就必須在呼叫 `_RTC_Initialize` 之前，檢查程式是否由執行階段錯誤檢查進行編譯，如下所示：  
  
```cpp
#ifdef __MSVC_RUNTIME_CHECKS  
    _RTC_Initialize();  
#endif  
```  
  
 如果沒有連結 C 語言執行階段程式庫，您也必須定義名為 `_CRT_RTC_INITW` 的函式。 `_CRT_RTC_INITW` 會將您的使用者定義函式安裝成預設的錯誤報告函式，如下所示：  
  
```cpp
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
  
 您可以在安裝好預設錯誤報告函式之後，使用 `_RTC_SetErrorFuncW` 安裝其他錯誤報告函式。 如需詳細資訊，請參閱 < [_RTC_SetErrorFuncW](/cpp/c-runtime-library/reference/rtc-seterrorfuncw)。  
  
## <a name="see-also"></a>另請參閱  
 [如何：使用原生執行階段檢查](../debugger/how-to-use-native-run-time-checks.md)
