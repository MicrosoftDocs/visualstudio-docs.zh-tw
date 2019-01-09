---
title: IActiveScriptAuthor::GetScriptletTextAttributes |Microsoft Docs
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
ms.openlocfilehash: 0973b2943ed76a7baa231a287476b237cd45e257
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2019
ms.locfileid: "54095455"
---
# <a name="iactivescriptauthorgetscriptlettextattributes"></a>IActiveScriptAuthor::GetScriptletTextAttributes
傳回的文字屬性的程式碼片段。  
  
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
 [在 size_is (`cch`)] 的程式碼片段文字。 以 null 結尾沒有這個字串。  
  
 `cch`  
 [in]所使用的大小`pszCode`和`pattr`參數。  
  
 `pszDelimiter`  
 [in]結束的程式碼片段分隔符號的位址。 當`pszCode`剖析文字資料流，從主應用程式通常會使用分隔符號 （例如兩個單引號），偵測 scriptlet 結尾。 如果沒有分隔符號用來識別 scriptlet 結尾，請設定此參數為 NULL。  
  
 `dwFlags`  
 [in]相關聯的程式碼片段的文字屬性的旗標。 可以是下列值的組合。  
  
|常數|值|描述|  
|--------------|-----------|-----------------|  
|GETATTRTYPE_DEPSCAN|0x0001|識別具有 SOURCETEXT_ATTR_IDENTIFIER 屬性的識別項，並找出具有 SOURCETEXT_ATTR_MEMBERLOOKUP 屬性的點運算子。|  
|GETATTRFLAG_THIS|0x0100|識別目前具有 SOURCETEXT_ATTR_THIS 屬性的物件。|  
|GETATTRFLAG_HUMANTEXT|0x8000|識別具有 SOURCETEXT_ATTR_HUMANTEXT 屬性的字串內容和註解文字。|  
  
 `pattr`  
 [in、 out size_is (`cch`)] 的程式碼片段的程式碼的色彩資訊。  
  
## <a name="return-value"></a>傳回值  
 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
  
## <a name="see-also"></a>另請參閱  
 [IActiveScriptAuthor 介面](../../winscript/reference/iactivescriptauthor-interface.md)   
 [IActiveScriptAuthor::GetScriptTextAttributes](../../winscript/reference/iactivescriptauthor-getscripttextattributes.md)   
 [SOURCE_TEXT_ATTR 列舉](../../winscript/reference/source-text-attr-enumeration.md)