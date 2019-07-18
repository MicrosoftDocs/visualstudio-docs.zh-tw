---
title: 報告攔截函式 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.hooks
dev_langs:
- FSharp
- VB
- CSharp
- C++
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
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0a492a1db8b65cad74d02cec0f43bf0c81461730
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65687502"
---
# <a name="report-hook-functions"></a>報告攔截函式
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

報告攔截函式，使用 [_CrtSetReportHook](https://msdn.microsoft.com/library/1ae7c64f-8c84-4797-9574-b59f00f7a509) 安裝，會在每次 [_CrtDbgReport](https://msdn.microsoft.com/library/6e581fb6-f7fb-4716-9432-f0145d639ecc) 產生偵錯報告時呼叫。 除此之外，您可以使用它來篩選報告以專注於特定類型的配置。 報告攔截函式應該有像下列的原型：  
  
```  
int YourReportHook(int nRptType, char *szMsg, int *retVal);  
```  
  
 將指標傳遞給 **_CrtSetReportHook**別的 **_CRT_REPORT_HOOK**、 CRTDBG 中所定義。H:  
  
```  
typedef int (__cdecl *_CRT_REPORT_HOOK)(int, char *, int *);  
```  
  
 當執行階段程式庫呼叫攔截函式時，*nRptType* 引數包含報告的分類 (**_CRT_WARN**、**_CRT_ERROR** 或 **_CRT_ASSERT**)，*szMsg* 包含完整重組報告訊息字串的指標，而 *retVal* 指定 `_CrtDbgReport` 是否應該在產生報告或啟動偵錯工具繼續照常執行。 (*retVal* 值為零時會繼續執行，值為 1 時會啟動偵錯工具。)  
  
 如果攔截能完整處理該訊息，而不需要進一步的報告，應該就會傳回 **TRUE**。 如果傳回的是 **FALSE`_CrtDbgReport`，** 會以一般方式報告訊息。  
  
## <a name="see-also"></a>另請參閱  
 [撰寫偵錯攔截函式](../debugger/debug-hook-function-writing.md)   
 [crt_dbg2 範例](https://msdn.microsoft.com/21e1346a-6a17-4f57-b275-c76813089167)
