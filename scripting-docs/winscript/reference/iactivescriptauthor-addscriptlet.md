---
title: "IActiveScriptAuthor::AddScriptlet |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IActiveScriptAuthor.AddScriptlet
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::AddScriptlet
ms.assetid: 879a6651-f187-4934-b130-c1247549900b
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b21f906a73a313bf775683ba63738adb25af0007
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptauthoraddscriptlet"></a>IActiveScriptAuthor::AddScriptlet
將程式碼的程式碼片段加入做為子系的根層級`IScriptNode`物件。 在主機中的程式碼片段的完整限定的名稱可包含只有兩個層級。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT AddScriptlet(  
   LPCOLESTR pszDefaultName,  
   LPCOLESTR pszCode,  
   LPCOLESTR pszItemName,  
   LPCOLESTR pszSubItemName,  
   LPCOLESTR pszEventName,  
   LPCOLESTR pszDelimiter,  
   DWORD dwCookie,  
   DWORD dwFlags  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pszDefaultName`  
 [in]使用程式碼片段相關聯的預設名稱的位址。  
  
 `pszCode`  
 [in]程式碼片段文字的位址。  
  
 `pszItemName`  
 [in]在主機中的完整程式碼片段名稱的最上層的識別項的緩衝區位址。  
  
 `pszSubItemName`  
 [in]在主機中的完整程式碼片段名稱的第二個層級識別碼緩衝區位址。 如果只有一個層級名稱，請設為 NULL。  
  
 `pszEventName`  
 [in]包含程式碼片段的事件處理常式的事件名稱的緩衝區位址。  
  
 `pszDelimiter`  
 [in]結束的指令碼區塊分隔符號的位址。 當`pszCode`剖析文字資料流，從主應用程式通常使用分隔符號 （例如兩個單引號），來偵測指令碼區塊的結尾。 此參數設為 NULL，如果分隔符號不會將標示指令碼區塊的結尾。  
  
 `dwCookie`  
 [in]應用程式定義值，用來與主機物件產生關聯的程式碼片段。  
  
 `dwFlags`  
 [in]未使用。  
  
## <a name="return-value"></a>傳回值  
 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|說明|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
  
## <a name="see-also"></a>另請參閱  
 [IActiveScriptAuthor 介面](../../winscript/reference/iactivescriptauthor-interface.md)