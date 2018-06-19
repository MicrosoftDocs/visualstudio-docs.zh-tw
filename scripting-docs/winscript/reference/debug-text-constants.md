---
title: DEBUG_TEXT 的常數 |Microsoft 文件
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 5dde10c3-7040-46b1-a328-959c6ce5cd9f
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5126a9efefaab611cd27d2104c40918f8dc7c7e3
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24641058"
---
# <a name="debugtext-constants"></a>DEBUG_TEXT 的常數
期間使用[IDebugExpressionContext::ParseLanguageText](../../winscript/reference/idebugexpressioncontext-parselanguagetext.md)。  
  
## <a name="syntax"></a>語法  
  
```  
typedef DWORD DEBUG_TEXT;  
```  
  
## <a name="constants"></a>常數  
  
|常數|值|描述|  
|--------------|-----------|-----------------|  
|DWORD DEBUG_TEXT_ISEXPRESSION|0x00000001|指出文字是運算式而不是陳述式。 這個旗標可能會影響某些語言中剖析文字的方式。|  
|DEBUG_TEXT_RETURNVALUE|0x00000002|如果傳回值使用時，它將供呼叫端。|  
|DEBUG_TEXT_NOSIDEEFFECTS|0x00000004|不允許副作用。 如果設定此旗標，則運算式評估應該變更任何執行階段狀態。|  
|DEBUG_TEXT_ALLOWBREAKPOINTS|0x00000008|允許文字的評估期間的中斷點。 如果未設定此旗標，中斷點將會忽略文字的評估期間。|  
|DEBUG_TEXT_ALLOWERRORREPORT|0x00000010|允許文字的評估期間的錯誤報告。 如果未設定此旗標，然後錯誤將不會報告主機在評估期間。|  
|DEBUG_TEXT_EVALUATETOCODECONTEXT|0x00000020|指出運算式是評估成程式碼內容，而不是執行本身的運算式。|  
  
## <a name="see-also"></a>另請參閱  
 [動態指令碼偵錯工具的常數、列舉和結構](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)