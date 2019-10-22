---
title: IActiveScriptDebug：： GetScriptletTextAttributes |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptDebug.GetScriptletTextAttributes
apilocation:
- jscript.dll
helpviewer_keywords:
- IActiveScriptDebug::GetScriptletTextAttributes
ms.assetid: b3990d86-5fdf-4c9f-9678-3f4b808c7ca8
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6a5dd9e219e51b001659225636396fe45ac815b9
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572805"
---
# <a name="iactivescriptdebuggetscriptlettextattributes"></a>IActiveScriptDebug::GetScriptletTextAttributes
傳回任意程式碼片段的文字屬性。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetScriptletTextAttributes(  
   LPCOLESTR          pstrCode,  
   ULONG              uNumCodeChars,  
   LPCOLESTR          pstrDelimiter,  
   DWORD              dwFlags,  
   SOURCE_TEXT_ATTR*  pattr  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pstrCode`  
 在程式碼片段文字。 這個字串不需要以 null 結束。  
  
 `uNumCodeChars`  
 在程式碼片段文字中的字元數。  
  
 `pstrDelimiter`  
 在程式碼片段後端分隔符號的位址。 從文字的資料流程剖析 `pstrCode` 時，主機通常會使用分隔符號，例如兩個單引號（' '）來偵測程式碼片段的結尾。 這個參數會指定主機所使用的分隔符號，讓腳本引擎提供一些條件式基本前置處理（例如，使用兩個單引號來取代單引號 [']，做為分隔符號）。 腳本引擎使用此資訊的確切方式，取決於腳本引擎。 如果主機未使用分隔符號來標示程式碼片段的結尾，請將此參數設為 Null。  
  
 `dwFlags`  
 在與程式碼片段相關聯的旗標。 可以是這些值的組合：  
  
|常數|值|描述|  
|--------------|-----------|-----------------|  
|GETATTRTYPE_DEPSCAN|0x0001|表示應該分別使用 SOURCETEXT_ATTR_IDENTIFIER 和 SOURCETEXT_ATTR_MEMBERLOOKUP 旗標來識別識別碼和點運算子。|  
|GETATTRFLAG_THIS|0x0100|表示應該使用 SOURCETEXT_ATTR_THIS 旗標來識別目前物件的識別碼。|  
|GETATTRFLAG_HUMANTEXT|0x8000|表示應該使用 SOURCETEXT_ATTR_HUMANTEXT 旗標來識別字串內容和註解文字。|  
  
 `pattr`  
 [in、out]包含傳回屬性的緩衝區。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 執行 `IDebugDocumentText` 介面的智慧型主機可以使用這個方法，將呼叫委派給 `IDebugDocumentText::GetText` 方法。  
  
 提供這個呼叫的原因是程式碼片段傾向于運算式，而且可能會有與腳本區塊不同的語法。 如果它們具有相同的語法，則此方法的執行會與 `GetScriptTextAttributes` 方法的實作為相同。  
  
## <a name="see-also"></a>請參閱  
 [IActiveScriptDebug 介面](../../winscript/reference/iactivescriptdebug-interface.md)   
 [IActiveScriptDebug：： GetScriptTextAttributes](../../winscript/reference/iactivescriptdebug-getscripttextattributes.md)    
 [IDebugDocumentText 介面](../../winscript/reference/idebugdocumenttext-interface.md)   
 [IDebugDocumentText：： GetText](../../winscript/reference/idebugdocumenttext-gettext.md)    
 [SOURCE_TEXT_ATTR 列舉](../../winscript/reference/source-text-attr-enumeration.md)