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
ms.openlocfilehash: facbdc1258b3fca72a239d9d5cc41772cf577f13
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577375"
---
# <a name="debug_text-constants"></a>DEBUG_TEXT 的常數
在 IDebugExpressionCoNtext 期間使用[：:P arselanguagetext](../../winscript/reference/idebugexpressioncontext-parselanguagetext.md)。  
  
## <a name="syntax"></a>語法  
  
```cpp
typedef DWORD DEBUG_TEXT;  
```  
  
## <a name="constants"></a>常數  
  
|常數|值|描述|  
|--------------|-----------|-----------------|  
|DWORD DEBUG_TEXT_ISEXPRESSION|0x00000001|表示文字是運算式，而不是語句。 此旗標可能會影響某些語言剖析文字的方式。|  
|DEBUG_TEXT_RETURNVALUE|0x00000002|如果傳回值可供使用，則呼叫端將會使用它。|  
|DEBUG_TEXT_NOSIDEEFFECTS|0x00000004|不允許副作用。 如果設定此旗標，運算式的評估應該不會變更執行時間狀態。|  
|DEBUG_TEXT_ALLOWBREAKPOINTS|0x00000008|允許在評估文字期間執行中斷點。 如果未設定此旗標，則會在評估文字期間忽略中斷點。|  
|DEBUG_TEXT_ALLOWERRORREPORT|0x00000010|在評估文字期間允許錯誤報表。 如果未設定此旗標，則在評估期間將不會向主機回報錯誤。|  
|DEBUG_TEXT_EVALUATETOCODECONTEXT|0x00000020|指出運算式要評估為程式碼內容，而不是執行運算式本身。|  
  
## <a name="see-also"></a>請參閱  
 [動態指令碼偵錯工具的常數、列舉和結構](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)