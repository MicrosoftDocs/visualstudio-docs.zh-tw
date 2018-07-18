---
title: IActiveScriptAuthor::GetScriptletTextAttributes |Microsoft 文件
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: b01fba7d0e8eb80fed51b1ff0ebd3a8816bacb01
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24645688"
---
# <a name="iactivescriptauthorgetscriptlettextattributes"></a>IActiveScriptAuthor::GetScriptletTextAttributes
傳回的文字屬性的程式碼片段。  
  
## <a name="syntax"></a>語法  
  
```  
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
 [在 size_is (`cch`)] 的程式碼片段文字。 這個字串並沒有以 null 結尾。  
  
 `cch`  
 [in]所使用的大小`pszCode`和`pattr`參數。  
  
 `pszDelimiter`  
 [in]結尾的程式碼片段分隔符號的位址。 當`pszCode`剖析文字資料流，從主應用程式通常使用分隔符號 （例如兩個單引號），來偵測程式碼片段的結尾。 如果沒有分隔符號用來識別程式碼片段的結尾，請設定此參數為 NULL。  
  
 `dwFlags`  
 [in]相關聯的程式碼片段文字屬性的旗標。 可以是下列值的組合。  
  
|常數|值|描述|  
|--------------|-----------|-----------------|  
|GETATTRTYPE_DEPSCAN|0x0001|識別具有 SOURCETEXT_ATTR_IDENTIFIER 屬性的識別項，並找出有 SOURCETEXT_ATTR_MEMBERLOOKUP 屬性的點運算子。|  
|GETATTRFLAG_THIS|0x0100|識別具有 SOURCETEXT_ATTR_THIS 屬性的目前物件。|  
|GETATTRFLAG_HUMANTEXT|0x8000|識別具有 SOURCETEXT_ATTR_HUMANTEXT 屬性的字串內容和註解文字。|  
  
 `pattr`  
 [in、 out size_is (`cch`)] 的程式碼片段的程式碼的色彩資訊。  
  
## <a name="return-value"></a>傳回值  
 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|說明|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
  
## <a name="see-also"></a>另請參閱  
 [IActiveScriptAuthor 介面](../../winscript/reference/iactivescriptauthor-interface.md)   
 [IActiveScriptAuthor::GetScriptTextAttributes](../../winscript/reference/iactivescriptauthor-getscripttextattributes.md)   
 [SOURCE_TEXT_ATTR 列舉](../../winscript/reference/source-text-attr-enumeration.md)