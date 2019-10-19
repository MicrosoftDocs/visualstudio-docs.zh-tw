---
title: IDebugExpressionCoNtext：:P arseLanguageText |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugExpressionContext.ParseLanguageText
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugExpressionContext::ParseLanguageText
ms.assetid: 650cb016-7d80-4011-b264-780f871a3466
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0493adde76e029088b637be3c6aaf02c55caaace
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573162"
---
# <a name="idebugexpressioncontextparselanguagetext"></a>IDebugExpressionContext::ParseLanguageText
建立指定之文字的 debug 運算式。  
  
## <a name="syntax"></a>語法  
  
```cpp
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
 在提供運算式或語句的文字。  
  
 `nRadix`  
 在要使用的基數。  
  
 `pstrDelimiter`  
 在腳本區塊的結尾分隔符號。 從文字的資料流程剖析 `pstrCode` 時，主機通常會使用分隔符號，例如兩個單引號（' '）來偵測腳本區塊的結尾。 這個參數會指定主機所使用的分隔符號，讓腳本引擎提供一些條件式基本前置處理（例如，使用兩個單引號來取代單引號 [']，做為分隔符號）。 腳本引擎使用此資訊的確切方式，取決於腳本引擎。 如果主機未使用分隔符號來標示腳本區塊的結尾，請將此參數設定為 `NULL`。  
  
 `dwFlags`  
 在下列 debug 文字旗標的組合：  
  
|常數|值|描述|  
|--------------|-----------|-----------------|  
|DEBUG_TEXT_ISEXPRESSION|0x00000001|表示文字是運算式，而不是語句。 此旗標可能會影響某些語言剖析文字的方式。|  
|DEBUG_TEXT_RETURNVALUE|0x00000002|如果傳回值可供使用，則呼叫端將會使用它。|  
|DEBUG_TEXT_NOSIDEEFFECTS|0x00000004|不允許副作用。 如果設定此旗標，運算式的評估應該不會變更執行時間狀態。|  
|DEBUG_TEXT_ALLOWBREAKPOINTS|0x00000008|允許在評估文字期間執行中斷點。 如果未設定此旗標，則會在評估文字期間忽略中斷點。|  
|DEBUG_TEXT_ALLOWERRORREPORT|0x00000010|在評估文字期間允許錯誤報表。 如果未設定此旗標，則不會在評估期間向主機回報錯誤。|  
|DEBUG_TEXT_EVALUATETOCODECONTEXT|0x00000020|指出運算式要評估為程式碼內容，而不是執行運算式本身|  
  
 `ppe`  
 脫銷傳回指定之文字的 debug 運算式。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 這個方法會建立指定文字的 debug 運算式。  
  
## <a name="see-also"></a>請參閱  
 [IDebugExpressionContext 介面](../../winscript/reference/idebugexpressioncontext-interface.md)