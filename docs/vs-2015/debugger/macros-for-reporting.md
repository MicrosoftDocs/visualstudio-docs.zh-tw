---
title: 適用于報表的宏 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.macros
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- macros, CRT reporting macros
- macros, debugging with
- _RPTFn macro
- CRT, reporting macros
- debugging [CRT], reporting macros
- _RPTn macro
ms.assetid: f2085314-a3a8-4caf-a5a4-2af9ad5aad05
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e4aee33d571f95e24a359fa2bc7e12ae8d64eae0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "62431624"
---
# <a name="macros-for-reporting"></a>報告巨集
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以使用 CRTDBG.H 裡中定義的 **_RPTn**和 **_RPTFn** 宏。H，取代語句的使用以 `printf` 進行調試。 當 **_DEBUG** 未定義時，這些宏會自動在您的發行組建中消失，因此不需要將它們放在 **#ifdef**s 中。  
  
|巨集|描述|  
|-----------|-----------------|  
|**_RPT0**、**_RPT1**、**_RPT2**、**_RPT3**、**_RPT4**|輸出訊息字串和零至四個引數。 從 _RPT1 到 **_RPT4**，訊息字串作為引數的 printf 樣式格式字串。|  
|**_RPTF0**、 **_RPTF1**、 **_RPTF2**、 **_RPTF4**|與 **_RPTn** 相同，但是這些宏也會輸出宏所在的檔案名和行號。|  
  
 請考慮下列範例：  
  
```  
#ifdef _DEBUG  
    if ( someVar > MAX_SOMEVAR )  
        printf( "OVERFLOW! In NameOfThisFunc( ),  
               someVar=%d, otherVar=%d.\n",  
               someVar, otherVar );  
#endif  
```  
  
 這段程式碼會將 `someVar` 和 `otherVar` 的值輸出至 **stdout**。 您可以使用下列的 `_RPTF2` 呼叫來報告這些相同的值，此外，還有檔名和行號：  
  
```  
if (someVar > MAX_SOMEVAR) _RPTF2(_CRT_WARN, "In NameOfThisFunc( ), someVar= %d, otherVar= %d\n", someVar, otherVar );  
```  
  
 如果您發現特定應用程式需要的偵錯報告是 C 執行階段程式庫提供的巨集所沒有的，您可以撰寫特別設計的巨集來符合您自己的需要。 例如，您可以在其中一個標頭檔案中，包含如下的程式碼，來定義名為 **ALERT_IF2** 的巨集：  
  
```  
#ifndef _DEBUG                  /* For RELEASE builds */  
#define  ALERT_IF2(expr, msg, arg1, arg2)  do {} while (0)  
#else                           /* For DEBUG builds   */  
#define  ALERT_IF2(expr, msg, arg1, arg2) \  
    do { \  
        if ((expr) && \  
            (1 == _CrtDbgReport(_CRT_ERROR, \  
                __FILE__, __LINE__, msg, arg1, arg2))) \  
            _CrtDbgBreak( ); \  
    } while (0)  
#endif  
```  
  
 **ALERT_IF2**的一個呼叫可在本主題開頭執行**printf**程式碼的所有功能：  
  
```  
ALERT_IF2(someVar > MAX_SOMEVAR, "OVERFLOW! In NameOfThisFunc( ),   
someVar=%d, otherVar=%d.\n", someVar, otherVar );  
```  
  
 因為自訂巨集可以很容易地變更為報告較多或較少資訊至不同的目的端 (取決於哪一種比較方便)，當您的偵錯需求不同時，這種方法特別有用。  
  
## <a name="see-also"></a>另請參閱  
 [CRT 偵錯技術](../debugger/crt-debugging-techniques.md)
