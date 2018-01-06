---
title: "報告攔截函式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.hooks
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
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 958c33c623830af509185b3d35ef8a8b5956aaae
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="report-hook-functions"></a>報告攔截函式
報告攔截函式，使用安裝[_CrtSetReportHook](/cpp/c-runtime-library/reference/crtsetreporthook)，每次呼叫[_CrtDbgReport](/cpp/c-runtime-library/reference/crtdbgreport-crtdbgreportw)會產生偵錯報表。 除此之外，您可以使用它來篩選報告以專注於特定類型的配置。 報告攔截函式應該有像下列的原型：  
  
```  
int YourReportHook(int nRptType, char *szMsg, int *retVal);  
```  
  
 您傳遞給指標**_CrtSetReportHook**的型別**_CRT_REPORT_HOOK**、 CRTDBG 中所定義。H:  
  
```  
typedef int (__cdecl *_CRT_REPORT_HOOK)(int, char *, int *);  
```  
  
 當執行階段程式庫呼叫攔截函式， *nRptType*引數包含報表的類別目錄 (**_CRT_WARN**， **_CRT_ERROR**，或**_CRT_ASSERT**)， *szMsg*包含完全組裝的報告訊息字串、 指標和*retVal*指定是否`_CrtDbgReport`應繼續正常執行之後產生的報表或開始偵錯工具。 (A *retVal*值為零會繼續執行，值為 1 時會啟動偵錯工具。)  
  
 如果攔截處理問題中的訊息完全，而無須任何進一步的報告，它應該傳回**TRUE**。 如果它傳回**FALSE**，`_CrtDbgReport`通常會報告訊息。  
  
## <a name="see-also"></a>請參閱  
 [偵錯攔截函式寫入](../debugger/debug-hook-function-writing.md)   
 [crt_dbg2 範例](http://msdn.microsoft.com/en-us/21e1346a-6a17-4f57-b275-c76813089167)