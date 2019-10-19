---
title: IDebugDocumentHost：： GetScriptTextAttributes |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHost.GetScriptTextAttributes
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugDocumentHost::GetScriptTextAttributes
ms.assetid: fe459d0d-937f-4176-be81-99d5cca121a1
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3b18f4f49fa157b78e4f1fd6c7766e929890a6c6
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72569211"
---
# <a name="idebugdocumenthostgetscripttextattributes"></a>IDebugDocumentHost::GetScriptTextAttributes
傳回檔文字區塊的文字屬性。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetScriptTextAttributes(  
   LPCOLESTR          pstrCode,  
   ULONG              uNumCodeChars,  
   LPCOLESTR          pstrDelimiter,  
   DWORD              dwFlags,  
   SOURCE_TEXT_ATTR*  pattr  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pstrCode`  
 在腳本區塊文字。 這個字串不需要以 null 結束。  
  
 `uNumCodeChars`  
 在腳本區塊文字中的字元數。  
  
 `pstrDelimiter`  
 在結束腳本區塊分隔符號的位址。 從文字的資料流程剖析 `pstrCode` 時，主機通常會使用分隔符號，例如兩個單引號（' '）來偵測腳本區塊的結尾。 這個參數會指定主機所使用的分隔符號，讓腳本引擎提供一些條件式基本前置處理（例如，使用兩個單引號來取代單引號 [']，做為分隔符號）。 腳本引擎使用此資訊的確切方式，取決於腳本引擎。 如果主機未使用分隔符號來標示腳本區塊的結尾，請將此參數設為 Null。  
  
 `dwFlags`  
 在與腳本區塊相關聯的旗標。 可以是這些值的組合：  
  
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
|`E_NOTIMPL`|主機只會使用預設屬性。|  
  
## <a name="remarks"></a>備註  
 這個方法會傳回檔文字任意區塊的文字屬性。 主機可以接受 `E_NOTIMPL`，在此情況下會使用預設屬性。  
  
## <a name="see-also"></a>請參閱  
 [IDebugDocumentHost 介面](../../winscript/reference/idebugdocumenthost-interface.md)   
 [SOURCE_TEXT_ATTR 列舉](../../winscript/reference/source-text-attr-enumeration.md)