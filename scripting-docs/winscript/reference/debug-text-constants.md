---
title: DEBUG_TEXT 常數 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 5dde10c3-7040-46b1-a328-959c6ce5cd9f
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2342555c4ee92b403aa01cc0ca15bb805f2b002e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62955246"
---
# <a name="debugtext-constants"></a>DEBUG_TEXT 的常數
使用期間[IDebugExpressionContext::ParseLanguageText](../../winscript/reference/idebugexpressioncontext-parselanguagetext.md)。  
  
## <a name="syntax"></a>語法  
  
```cpp
typedef DWORD DEBUG_TEXT;  
```  
  
## <a name="constants"></a>常數  
  
|常數|值|描述|  
|--------------|-----------|-----------------|  
|DWORD DEBUG_TEXT_ISEXPRESSION|0x00000001|指出文字是運算式而不是陳述式。 這個旗標可能會影響某些語言中剖析之文字的方式。|  
|DEBUG_TEXT_RETURNVALUE|0x00000002|是否可傳回的值，它將會使用呼叫端。|  
|DEBUG_TEXT_NOSIDEEFFECTS|0x00000004|不允許副作用。 如果設定此旗標，則運算式的評估應該變更任何執行階段狀態。|  
|DEBUG_TEXT_ALLOWBREAKPOINTS|0x00000008|允許文字的評估期間的中斷點。 如果未設定此旗標，將會在文字的評估期間忽略中斷點。|  
|DEBUG_TEXT_ALLOWERRORREPORT|0x00000010|允許文字的評估期間的錯誤報表。 如果未設定此旗標，則錯誤將不會報告主機在評估期間。|  
|DEBUG_TEXT_EVALUATETOCODECONTEXT|0x00000020|指出運算式可評估為程式碼內容，而不是執行本身的運算式。|  
  
## <a name="see-also"></a>另請參閱  
 [動態指令碼偵錯工具的常數、列舉和結構](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)