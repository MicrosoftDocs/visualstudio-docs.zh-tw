---
title: IActiveScriptDebug::GetScriptletTextAttributes |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 757c56750ee54e7de50f245b8b643cc5983f3149
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2019
ms.locfileid: "54097548"
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
 [in]程式碼片段文字。 這個字串不需要終止的 null。  
  
 `uNumCodeChars`  
 [in]在程式碼片段文字中的字元數。  
  
 `pstrDelimiter`  
 [in]結束的程式碼片段分隔符號的位址。 當`pstrCode`剖析文字資料流，從主應用程式通常會使用分隔符號，例如兩個單引號 （'），偵測 scriptlet 結尾。 這個參數指定主應用程式使用，允許以提供一些條件式的基本前置處理指令碼引擎的分隔符號 （比方說，取代兩個單引號以做為分隔符號使用的單引號 [']）。 究竟要如何 （以及是否） 這項資訊會取決於指令碼引擎的指令碼引擎使用。 如果主機未使用分隔符號來標示程式碼片段的結尾，請設定此參數為 NULL。  
  
 `dwFlags`  
 [in]與 scriptlet 相關的旗標。 可以是下列值的組合：  
  
|常數|值|描述|  
|--------------|-----------|-----------------|  
|GETATTRTYPE_DEPSCAN|0x0001|表示識別項和點運算子應該識別 SOURCETEXT_ATTR_IDENTIFIER 和 SOURCETEXT_ATTR_MEMBERLOOKUP 旗標，以分別。|  
|GETATTRFLAG_THIS|0x0100|表示目前物件的識別碼都應該識別 SOURCETEXT_ATTR_THIS 旗標。|  
|GETATTRFLAG_HUMANTEXT|0x8000|表示字串內容和註解文字應該識別 SOURCETEXT_ATTR_HUMANTEXT 旗標。|  
  
 `pattr`  
 [in、 out]包含傳回的屬性的緩衝區。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 實作智慧主機`IDebugDocumentText`介面可以使用這個方法將委派呼叫`IDebugDocumentText::GetText`方法。  
  
 提供此呼叫，因為程式碼片段通常為運算式，而且可能會有不同的語法比指令碼區塊。 如果它們有相同的語法，此方法的實作將會完全相同的實作`GetScriptTextAttributes`方法。  
  
## <a name="see-also"></a>另請參閱  
 [IActiveScriptDebug 介面](../../winscript/reference/iactivescriptdebug-interface.md)   
 [IActiveScriptDebug::GetScriptTextAttributes](../../winscript/reference/iactivescriptdebug-getscripttextattributes.md)   
 [IDebugDocumentText 介面](../../winscript/reference/idebugdocumenttext-interface.md)   
 [IDebugDocumentText::GetText](../../winscript/reference/idebugdocumenttext-gettext.md)   
 [SOURCE_TEXT_ATTR 列舉](../../winscript/reference/source-text-attr-enumeration.md)