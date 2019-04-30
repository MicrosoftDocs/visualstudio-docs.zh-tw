---
title: IActiveScriptAuthor::AddScriptlet | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.AddScriptlet
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::AddScriptlet
ms.assetid: 879a6651-f187-4934-b130-c1247549900b
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 64df7bd4c0d0dde303cdc15d7111688d14c7dc49
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62935454"
---
# <a name="iactivescriptauthoraddscriptlet"></a>IActiveScriptAuthor::AddScriptlet
將程式碼的程式碼片段加入做為子系的根層級`IScriptNode`物件。 在主機中，程式碼片段的完整的名稱被允許將只有兩個層級。  
  
## <a name="syntax"></a>語法  
  
```cpp
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
 [in]與 scriptlet 相關聯的預設名稱的位址。  
  
 `pszCode`  
 [in]Scriptlet 文字的位址。  
  
 `pszItemName`  
 [in]最上層的識別項的主應用程式中的完整程式碼片段名稱的緩衝區位址。  
  
 `pszSubItemName`  
 [in]第二個層級識別項的主應用程式中的完整程式碼片段名稱的緩衝區位址。 如果名稱有只有一個層級，請設為 NULL。  
  
 `pszEventName`  
 [in]包含程式碼片段的事件處理常式的事件名稱的緩衝區位址。  
  
 `pszDelimiter`  
 [in]End 的指令碼區塊分隔符號的位址。 當`pszCode`剖析文字資料流，從主應用程式通常會使用分隔符號 （例如兩個單引號），來偵測指令碼區塊的結尾。 如果分隔符號不會標記指令碼區塊的結尾，請設定此參數為 NULL。  
  
 `dwCookie`  
 [in]應用程式定義值，用來與主機物件產生關聯的程式碼片段。  
  
 `dwFlags`  
 [in]不使用。  
  
## <a name="return-value"></a>傳回值  
 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
  
## <a name="see-also"></a>另請參閱  
 [IActiveScriptAuthor 介面](../../winscript/reference/iactivescriptauthor-interface.md)