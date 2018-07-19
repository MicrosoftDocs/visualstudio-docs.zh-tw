---
title: 報告攔截函式 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.hooks
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- hooks, report
- _CrtDbgReport function
- debugger, report hook functions
- memory allocation, debug heap
- debugging [C++], hook functions
- _CrtSetReportHook function
- report hook functions
ms.assetid: 1854bca7-d7eb-4502-89bf-b1ee64cb50ef
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 093b7732f78f7257a2e58812ca2697496d65682f
ms.sourcegitcommit: 0bf2aff6abe485e3fe940f5344a62a885ad7f44e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37056478"
---
# <a name="report-hook-functions"></a>報告攔截函式
報告攔截函式，使用安裝[_CrtSetReportHook](/cpp/c-runtime-library/reference/crtsetreporthook)，每次都會呼叫[_CrtDbgReport](/cpp/c-runtime-library/reference/crtdbgreport-crtdbgreportw)會產生偵錯報表。 除此之外，您可以使用它來篩選報告以專注於特定類型的配置。 報告攔截函式應該有像下列的原型：  
  
```cpp
int YourReportHook(int nRptType, char *szMsg, int *retVal);  
```  
  
 將指標傳遞給 **_CrtSetReportHook**別的 **_CRT_REPORT_HOOK**、 CRTDBG 中所定義。H:  
  
```cpp
typedef int (__cdecl *_CRT_REPORT_HOOK)(int, char *, int *);  
```  
  
 當執行階段程式庫呼叫攔截函式， *nRptType*引數包含報告的分類 (**_CRT_WARN**， **_CRT_ERROR**，或 **_CRT_ASSERT**)， *szMsg*包含完全組裝的報告訊息字串、 指標和*retVal*指定是否`_CrtDbgReport`應繼續正常執行之後產生報表] 或 [啟動偵錯工具。 (A *retVal*值為零會繼續執行，值為 1 會啟動偵錯工具。)  
  
 如果攔截處理的訊息完全，而沒有進一步回報是必要，它應該傳回 **，則為 TRUE**。 如果它傳回**假**，`_CrtDbgReport`通常會報告訊息。  
  
## <a name="see-also"></a>另請參閱  
 [撰寫偵錯攔截函式](../debugger/debug-hook-function-writing.md)   
 [crt_dbg2 範例](http://msdn.microsoft.com/en-us/21e1346a-6a17-4f57-b275-c76813089167)
