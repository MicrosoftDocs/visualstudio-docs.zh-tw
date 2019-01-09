---
title: 'Iactivescript:: Getscriptdispatch |Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 2a18d6781ca2b7820686b317ad0be5da425ade1f
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2019
ms.locfileid: "54097678"
---
# <a name="iactivescriptgetscriptdispatch"></a>IActiveScript::GetScriptDispatch
擷取`IDispatch`介面的方法和目前執行的指令碼相關聯的屬性。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetScriptDispatch(  
    LPCOLESTR pstrItemName  // address of item name  
    IDispatch **ppdisp      // receives IDispatch pointer  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pstrItemName`  
 [in]包含的項目，呼叫端需要相關聯的分派物件名稱的緩衝區位址。 如果這個參數是`NULL`，分派物件包含做為其成員的所有全域方法和屬性定義的指令碼。 透過`IDispatch`介面和相關聯`ITypeInfo`介面，主機可以叫用指令碼方法或檢視和修改指令碼變數。  
  
 `ppdisp`  
 [out]此變數會接收指令碼的全域方法與屬性相關聯物件的指標位址。 如果指令碼引擎不支援這類物件，`NULL`會傳回。  
  
## <a name="return-value"></a>傳回值  
 會傳回下列值之一：  
  
|傳回值|意義|  
|------------------|-------------|  
|`S_OK`|成功。|  
|`E_INVALIDARG`|引數無效。|  
|`E_POINTER`|指定了無效的指標。|  
|`E_UNEXPECTED`|不需要呼叫 （例如，指令碼引擎有尚未載入或初始化）。|  
|`S_FALSE`|指令碼引擎不支援的分派物件;`ppdisp`參數設為 NULL。|  
  
## <a name="remarks"></a>備註  
 藉由呼叫，則可以加入方法和屬性，因此[IActiveScriptParse](../../winscript/reference/iactivescriptparse.md)介面，`IDispatch`新方法和屬性，以動態方式可支援這個方法所傳回的介面。 同樣地，`IDispatch::GetTypeInfo`方法應傳回的新唯一`ITypeInfo`介面加入方法和屬性時。 不過請注意，語言引擎必須變更`IDispatch`介面的方式不使用任何先前`ITypeInfo`傳回的介面。 這表示，例如，Dispid 會永遠不會重複使用。  
  
## <a name="see-also"></a>另請參閱  
 [IActiveScript](../../winscript/reference/iactivescript.md)