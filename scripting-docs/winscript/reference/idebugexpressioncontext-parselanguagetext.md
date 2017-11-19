---
title: "IDebugExpressionContext::ParseLanguageText |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugExpressionContext.ParseLanguageText
apilocation: jscript.dll
helpviewer_keywords: IDebugExpressionContext::ParseLanguageText
ms.assetid: 650cb016-7d80-4011-b264-780f871a3466
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e455768b7d38096c64ab61f2b36aeba871ddf0bc
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="idebugexpressioncontextparselanguagetext"></a>IDebugExpressionContext::ParseLanguageText
建立指定文字的偵錯運算式。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT ParseLanguageText(  
   LPCOLESTR           pstrCode,  
   UINT                nRadix,  
   LPCOLESTR           pstrDelimiter,  
   DWORD               dwFlags,  
   IDebugExpression**  ppe  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pstrCode`  
 [in]提供運算式或陳述式的文字。  
  
 `nRadix`  
 [in]若要使用的基數。  
  
 `pstrDelimiter`  
 [in]結束的指令碼區塊分隔符號。 當`pstrCode`剖析文字資料流，從主應用程式通常會使用分隔符號，例如兩個單引號 （'），來偵測指令碼區塊的結尾。 這個參數會指定使用主機，允許以提供一些條件的基本前置處理指令碼引擎的分隔符號 （例如，取代單引號 ['] 具有兩個單引號做為分隔符號使用）。 方式 （和 if） 這項資訊取決於指令碼引擎的指令碼引擎使用。 這個參數設定為`NULL`若主機未使用的分隔符號來標示指令碼區塊的結尾。  
  
 `dwFlags`  
 [in]下列偵錯文字旗標的組合：  
  
|常數|值|描述|  
|--------------|-----------|-----------------|  
|DEBUG_TEXT_ISEXPRESSION|0x00000001|指出文字是運算式而不是陳述式。 這個旗標可能會影響某些語言中剖析文字的方式。|  
|DEBUG_TEXT_RETURNVALUE|0x00000002|如果傳回值使用時，它將供呼叫端。|  
|DEBUG_TEXT_NOSIDEEFFECTS|0x00000004|不允許副作用。 如果設定此旗標，則運算式評估應該變更任何執行階段狀態。|  
|DEBUG_TEXT_ALLOWBREAKPOINTS|0x00000008|允許文字的評估期間的中斷點。 如果未設定此旗標，則中斷點會忽略文字的評估期間。|  
|DEBUG_TEXT_ALLOWERRORREPORT|0x00000010|允許文字的評估期間的錯誤報告。 如果未設定此旗標然後錯誤不會報告主機在評估期間。|  
|DEBUG_TEXT_EVALUATETOCODECONTEXT|0x00000020|指出運算式是評估成程式碼內容，而不是執行本身的運算式|  
  
 `ppe`  
 [out]傳回指定文字的偵錯運算式。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|說明|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 這個方法會建立指定文字的偵錯運算式。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugExpressionContext 介面](../../winscript/reference/idebugexpressioncontext-interface.md)