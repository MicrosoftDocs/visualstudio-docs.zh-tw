---
title: 報告巨集 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 84b5e72b15d085e29823fb8c8e116a153ff550e8
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49224376"
---
# <a name="macros-for-reporting"></a>報告巨集
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以使用 **_RPTn**，並 **_RPTFn** CRTDBG 中定義的巨集。H，來取代使用`printf`陳述式中的偵錯。 這些巨集會自動地消失在您的發行組建 **_DEBUG**未定義，因此不需要括住在 **#ifdef**s。  
  
|巨集|描述|  
|-----------|-----------------|  
|**_RPT0**， **_RPT1**， **_RPT2**， **_RPT3**， **_RPT4**|輸出訊息字串和零至四個引數。 從 _rpt1 到 **_RPT4**，訊息字串做為引數的 printf 樣式格式字串。|  
|**_RPTF0**， **_RPTF1**， **，_RPTF2**， **_RPTF4**|與相同 **_RPTn** ，但是這些巨集也會輸出巨集所在位置的檔案名稱和行號。|  
  
 參考下列範例：  
  
```  
#ifdef _DEBUG  
    if ( someVar > MAX_SOMEVAR )  
        printf( "OVERFLOW! In NameOfThisFunc( ),  
               someVar=%d, otherVar=%d.\n",  
               someVar, otherVar );  
#endif  
```  
  
 此程式碼輸出的值`someVar`並`otherVar`要**stdout**。 您可以使用下列的 `_RPTF2` 呼叫來報告這些相同的值，此外，還有檔名和行號：  
  
```  
if (someVar > MAX_SOMEVAR) _RPTF2(_CRT_WARN, "In NameOfThisFunc( ), someVar= %d, otherVar= %d\n", someVar, otherVar );  
```  
  
 如果您發現特定應用程式需要的偵錯報告是 C 執行階段程式庫提供的巨集所沒有的，您可以撰寫特別設計的巨集來符合您自己的需要。 在其中一個標頭檔，例如，您可以包含像是下列內容以定義巨集呼叫的程式碼**ALERT_IF2**:  
  
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
  
 若要一次呼叫**ALERT_IF2**無法執行的所有函式**printf**本主題開頭的程式碼：  
  
```  
ALERT_IF2(someVar > MAX_SOMEVAR, "OVERFLOW! In NameOfThisFunc( ),   
someVar=%d, otherVar=%d.\n", someVar, otherVar );  
```  
  
 因為自訂巨集可以很容易地變更為報告較多或較少資訊至不同的目的端 (取決於哪一種比較方便)，當您的偵錯需求不同時，這種方法特別有用。  
  
## <a name="see-also"></a>另請參閱  
 [CRT 偵錯技術](../debugger/crt-debugging-techniques.md)



