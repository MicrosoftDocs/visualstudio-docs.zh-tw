---
title: IActiveScript：： GetScriptDispatch |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.GetScriptDispatch
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_GetScriptDispatch
ms.assetid: 2092ccd4-1f4c-493a-b5b7-077a70ce95ca
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ba53f2eccde18bd5b2d9c609ea680b50cb7261c9
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575753"
---
# <a name="iactivescriptgetscriptdispatch"></a>IActiveScript::GetScriptDispatch
針對與目前執行之腳本相關聯的方法和屬性，抓取 `IDispatch` 介面。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetScriptDispatch(  
    LPCOLESTR pstrItemName  // address of item name  
    IDispatch **ppdisp      // receives IDispatch pointer  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pstrItemName`  
 在緩衝區的位址，其中包含呼叫端需要相關聯分派物件的專案名稱。 如果這個參數是 `NULL`，分派物件會包含該腳本所定義的所有全域方法和屬性（property）做為其成員。 透過 `IDispatch` 介面和相關聯的 `ITypeInfo` 介面，主機可以叫用腳本方法或 view 和 modify 腳本變數。  
  
 `ppdisp`  
 脫銷此變數的位址，會接收與腳本的全域方法和屬性相關聯之物件的指標。 如果腳本引擎不支援這類物件，則會傳回 `NULL`。  
  
## <a name="return-value"></a>傳回值  
 傳回下列其中一個值：  
  
|傳回值|意義|  
|------------------|-------------|  
|`S_OK`|成功。|  
|`E_INVALIDARG`|引數無效。|  
|`E_POINTER`|指定了不正確指標。|  
|`E_UNEXPECTED`|不需要呼叫（例如，腳本引擎尚未載入或初始化）。|  
|`S_FALSE`|腳本引擎不支援分派物件;`ppdisp` 參數設定為 Null。|  
  
## <a name="remarks"></a>備註  
 因為方法和屬性可以藉由呼叫[IActiveScriptParse](../../winscript/reference/iactivescriptparse.md)介面來加入，所以這個方法所傳回的 `IDispatch` 介面可以動態支援新的方法和屬性。 同樣地，當新增方法和屬性時，`IDispatch::GetTypeInfo` 方法應該會傳回新的唯一 `ITypeInfo` 介面。 不過要注意的是，語言引擎不能變更 `IDispatch` 介面，方法與傳回的任何先前 `ITypeInfo` 介面不相容。 例如，這表示不會重複使用 Dispid。  
  
## <a name="see-also"></a>請參閱  
 [IActiveScript](../../winscript/reference/iactivescript.md)