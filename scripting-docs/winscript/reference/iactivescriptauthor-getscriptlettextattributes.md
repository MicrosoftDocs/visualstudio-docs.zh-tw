---
title: IActiveScriptAuthor：： GetScriptletTextAttributes |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.GetScriptletTextAttributes
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::GetScriptletTextAttributes
ms.assetid: 082edfce-6c5b-4e5e-b942-31b423a4fa1d
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4cd0090b9ade47ad37acf6d285ec7f072f1ea5af
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576175"
---
# <a name="iactivescriptauthorgetscriptlettextattributes"></a>IActiveScriptAuthor::GetScriptletTextAttributes
傳回程式碼片段的文字屬性。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetScriptletTextAttributes(  
   LPCOLESTR pszCode,  
   ULONG cch,  
   LPCOLESTR pszDelimiter,  
   DWORD dwFlags,  
   SOURCE_TEXT_ATTR *pattr  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pszCode`  
 [in、size_is （`cch`）]程式碼片段文字。 這個字串不一定要終止 null。  
  
 `cch`  
 在`pszCode` 和 `pattr` 參數所使用的大小。  
  
 `pszDelimiter`  
 在程式碼片段後端分隔符號的位址。 從文字的資料流程剖析 `pszCode` 時，主機通常會使用分隔符號（例如兩個單引號）來偵測程式碼片段的結尾。 如果沒有使用分隔符號來識別程式碼片段的結尾，請將此參數設定為 Null。  
  
 `dwFlags`  
 在與程式碼片段的文字屬性相關聯的旗標。 可以是下列值的組合。  
  
|常數|值|描述|  
|--------------|-----------|-----------------|  
|GETATTRTYPE_DEPSCAN|0x0001|識別具有 SOURCETEXT_ATTR_IDENTIFIER 屬性的識別碼，並識別具有 SOURCETEXT_ATTR_MEMBERLOOKUP 屬性的點運算子。|  
|GETATTRFLAG_THIS|0x0100|識別具有 SOURCETEXT_ATTR_THIS 屬性的目前物件。|  
|GETATTRFLAG_HUMANTEXT|0x8000|識別具有 SOURCETEXT_ATTR_HUMANTEXT 屬性的字串內容和註解文字。|  
  
 `pattr`  
 [in、out、size_is （`cch`）]程式碼片段程式碼的色彩資訊。  
  
## <a name="return-value"></a>傳回值  
 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
  
## <a name="see-also"></a>另請參閱  
 [IActiveScriptAuthor 介面](../../winscript/reference/iactivescriptauthor-interface.md)   
 [IActiveScriptAuthor：： GetScriptTextAttributes](../../winscript/reference/iactivescriptauthor-getscripttextattributes.md)   
 [SOURCE_TEXT_ATTR 列舉](../../winscript/reference/source-text-attr-enumeration.md)