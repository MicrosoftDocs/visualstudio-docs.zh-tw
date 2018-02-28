---
title: "IActiveScript::GetScriptDispatch |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IActiveScript.GetScriptDispatch
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_GetScriptDispatch
ms.assetid: 2092ccd4-1f4c-493a-b5b7-077a70ce95ca
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5b2f09934cf6d2bb28f7dae93d0bf49c8dc7437d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptgetscriptdispatch"></a>IActiveScript::GetScriptDispatch
擷取`IDispatch`介面的方法和屬性的目前執行的指令碼相關聯。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetScriptDispatch(  
    LPCOLESTR pstrItemName  // address of item name  
    IDispatch **ppdisp      // receives IDispatch pointer  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pstrItemName`  
 [in]包含的項目，呼叫端需要的相關聯的分派物件名稱的緩衝區位址。 如果這個參數是`NULL`，分派物件包含做為其成員的所有全域方法和屬性定義的指令碼。 透過`IDispatch`介面和相關聯`ITypeInfo`介面，主機可以叫用指令碼方法或檢視和修改指令碼變數。  
  
 `ppdisp`  
 [out]此變數會接收與指令碼的全域方法與屬性相關聯的物件指標的位址。 如果指令碼引擎不支援這類物件，`NULL`傳回。  
  
## <a name="return-value"></a>傳回值  
 會傳回下列值之一：  
  
|傳回值|意義|  
|------------------|-------------|  
|`S_OK`|成功。|  
|`E_INVALIDARG`|引數無效。|  
|`E_POINTER`|指定了無效的指標。|  
|`E_UNEXPECTED`|不應該呼叫 （例如，指令碼引擎有尚未載入或初始化）。|  
|`S_FALSE`|指令碼引擎不支援分派物件。`ppdisp`參數設定為 NULL。|  
  
## <a name="remarks"></a>備註  
 因為可以藉由呼叫加入方法和屬性[IActiveScriptParse](../../winscript/reference/iactivescriptparse.md)介面，`IDispatch`新方法和屬性，以動態方式可支援這個方法所傳回的介面。 同樣地，`IDispatch::GetTypeInfo`方法應傳回新的唯一`ITypeInfo`介面方法和屬性加入時。 不過請注意，語言引擎必須變更`IDispatch`介面的方式與不相容任何先前`ITypeInfo`介面傳回。 這表示，例如，永遠不會重複的 Dispid。  
  
## <a name="see-also"></a>另請參閱  
 [IActiveScript](../../winscript/reference/iactivescript.md)