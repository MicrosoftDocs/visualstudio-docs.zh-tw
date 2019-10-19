---
title: IScriptNode：： CreateChildHandler |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptNode.CreateChildHandler
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptNode::CreateChildHandler
ms.assetid: 4ce5eb10-1a3f-43b0-a4b7-599a397ed3a2
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9e024bb7d6a81b35994edddfe9e71666b0ee8df0
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573593"
---
# <a name="iscriptnodecreatechildhandler"></a>IScriptNode::CreateChildHandler
加入程式碼片段做為 `IScriptNode` 的子實例。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT CreateChildHandler(  
   LPCOLESTR          pszDefaultName,  
   LPCOLESTR          *prgpszNames,  
   ULONG              cpszNames,  
   LPCOLESTR          pszEvent,  
   LPCOLESTR          pszDelimiter,  
   ITypeInfo*         ptiSignature,  
   ULONG              iMethodSignature,  
   ULONG              isn,  
   DWORD              dwCookie,  
   IScriptEntry       **ppse  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pszDefaultName`  
 在要與程式碼片段建立關聯的預設名稱位址。  
  
 `prgpszNames`  
 [in，size_is （`cpszNames`）]主機上完整名稱的識別碼清單。  
  
 `cpszNames`  
 在@No__t_0 參數中的識別碼數目。  
  
 `pszEvent`  
 在識別與程式碼片段相關聯之事件名稱的緩衝區位址。  
  
 `pszDelimiter`  
 在結束腳本區塊分隔符號的位址。 對於剖析，主機通常會使用分隔符號（例如兩個單引號）來偵測腳本區塊的結尾。  
  
 分隔符號可讓腳本撰寫引擎進行前置處理。 例如，引擎可能會使用兩個單引號來取代單引號，以作為分隔符號。 引擎會決定分隔符號的使用方式。  
  
 如果未使用分隔符號來識別腳本區塊的結尾，則設為 Null。  
  
 `ptiSignature`  
 在函式物件的類型資訊。  
  
 `iMethodSignature`  
 在@No__t_0 參數中的函式索引。  
  
 `isn`  
 在父系中子系的索引。  
  
 `dwCookie`  
 在應用程式定義的值，用來將專案與主物件產生關聯。  
  
 `ppse`  
 脫銷接收子實例之 `IScriptEntry` 介面指標的變數位址。  
  
## <a name="return-value"></a>傳回值  
 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 程式碼片段會指定事件處理常式。 這個方法會建立程式碼片段（如果它是由代表網頁的 `IScriptNode` 物件所呼叫）。 如果其他介面呼叫這個方法，則不會成功。  
  
## <a name="see-also"></a>請參閱  
 [IScriptNode 介面](../../winscript/reference/iscriptnode-interface.md)   
 [IScriptEntry 介面](../../winscript/reference/iscriptentry-interface.md)