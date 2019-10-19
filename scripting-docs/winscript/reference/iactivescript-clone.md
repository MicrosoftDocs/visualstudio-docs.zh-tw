---
title: IActiveScript：： Clone |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.Clone
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_Clone
ms.assetid: aa000b2a-7085-448d-a422-f7adac7851cb
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fbaad29cb31af26a0f26a1c679a900192fc77041
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575791"
---
# <a name="iactivescriptclone"></a>IActiveScript::Clone
複製目前的腳本引擎（減去任何目前的執行狀態），並傳回在目前線程中沒有任何網站的已載入腳本引擎。 這個新腳本引擎的屬性會與原始腳本引擎在轉換回初始化狀態時所處的屬性相同。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT Clone(  
    IActiveScript **ppscript  // receives pointer to IActiveScript  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppscript`  
 脫銷接收復制的腳本引擎之[IActiveScript](../../winscript/reference/iactivescript.md)介面指標的變數位址。 主機必須先建立網站，並在新的腳本引擎上呼叫[IActiveScript：： SetScriptSite](../../winscript/reference/iactivescript-setscriptsite.md)方法，才會處於已初始化的狀態，因此可供使用。  
  
## <a name="return-value"></a>傳回值  
 傳回下列其中一個值：  
  
|傳回值|意義|  
|------------------|-------------|  
|`S_OK`|成功。|  
|`E_NOTIMPL`|不支援這個方法。|  
|`E_POINTER`|指定了不正確指標。|  
|`E_UNEXPECTED`|不需要呼叫（例如，腳本引擎尚未載入或初始化）。|  
  
## <a name="remarks"></a>備註  
 @No__t_0 方法是 `IPersist*::Save`、`CoCreateInstance` 和 `IPersist*::Load` 的優化，因此新腳本引擎的狀態應該與原始腳本引擎的狀態已儲存並載入至新的腳本引擎相同。 在複製的腳本引擎中，命名專案是重複的，但每個專案的特定物件指標會被忘記，並使用[IActiveScriptSite：： GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md)方法來取得。 這可讓您使用具有每個執行緒進入點（一個單元模型）的相同物件模型。  
  
 這個方法用於多執行緒伺服器主機，可以執行相同腳本的多個實例。 腳本引擎可能會傳回 `E_NOTIMPL`，在這種情況下，主機可以藉由複製持續性狀態，並使用 `IPersist*` 介面建立新的腳本引擎實例，來達到相同的結果。  
  
 這個方法可以從非基底線程呼叫，而不會產生非基底的標注來裝載物件或[IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)介面。  
  
## <a name="see-also"></a>請參閱  
 [IActiveScript](../../winscript/reference/iactivescript.md)