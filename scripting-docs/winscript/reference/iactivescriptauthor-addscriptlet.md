---
title: IActiveScriptAuthor：： AddScriptlet |Microsoft Docs
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
ms.openlocfilehash: 3a349a848f282e6b3a228c7b17009e0261801be5
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577978"
---
# <a name="iactivescriptauthoraddscriptlet"></a>IActiveScriptAuthor::AddScriptlet
加入程式碼程式碼片段做為根層級 `IScriptNode` 物件的子系。 在主機中，程式碼片段的完整名稱只允許有兩個層級。  
  
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
 在要與程式碼片段建立關聯的預設名稱位址。  
  
 `pszCode`  
 在程式碼片段文字的位址。  
  
 `pszItemName`  
 在主機中完整程式碼片段名稱的最上層識別碼的緩衝區位址。  
  
 `pszSubItemName`  
 在主機中完整程式碼片段名稱的第二層識別碼的緩衝區位址。 如果名稱只有一個層級，則設定為 Null。  
  
 `pszEventName`  
 在緩衝區的位址，其中包含程式碼片段為事件處理常式的事件名稱。  
  
 `pszDelimiter`  
 在結束腳本區塊分隔符號的位址。 從文字的資料流程剖析 `pszCode` 時，主機通常會使用分隔符號（例如兩個單引號）來偵測腳本區塊的結尾。 如果分隔符號不會標示腳本區塊的結尾，請將此參數設定為 Null。  
  
 `dwCookie`  
 在應用程式定義的值，用來將程式碼片段與主機物件產生關聯。  
  
 `dwFlags`  
 在未使用。  
  
## <a name="return-value"></a>傳回值  
 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
  
## <a name="see-also"></a>請參閱  
 [IActiveScriptAuthor 介面](../../winscript/reference/iactivescriptauthor-interface.md)