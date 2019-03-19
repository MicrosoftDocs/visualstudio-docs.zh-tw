---
title: IActiveScript::Clone | Microsoft Docs
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
ms.openlocfilehash: bec912596c792a67f65434062bc0d0ed11bd3fb9
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2019
ms.locfileid: "58149022"
---
# <a name="iactivescriptclone"></a>IActiveScript::Clone
複製目前指令碼引擎 （減去任何目前的執行狀態），傳回不已在目前的執行緒中的任何網站載入指令碼引擎。 這個新的指令碼引擎的屬性會與原始的指令碼引擎會在已轉換為初始化的狀態屬性相同。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT Clone(  
    IActiveScript **ppscript  // receives pointer to IActiveScript  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppscript`  
 [out]收到的指標變數的位址[IActiveScript](../../winscript/reference/iactivescript.md)複製指令碼引擎的介面。 主機必須建立的站台和呼叫[iactivescript:: Setscriptsite](../../winscript/reference/iactivescript-setscriptsite.md)有關新指令碼引擎之前，會處於初始化狀態的方法，因此，可使用。  
  
## <a name="return-value"></a>傳回值  
 會傳回下列值之一：  
  
|傳回值|意義|  
|------------------|-------------|  
|`S_OK`|成功。|  
|`E_NOTIMPL`|不支援這個方法。|  
|`E_POINTER`|指定了無效的指標。|  
|`E_UNEXPECTED`|不需要呼叫 （例如，指令碼引擎有尚未載入或初始化）。|  
  
## <a name="remarks"></a>備註  
 `IActiveScript::Clone`方式的最佳化`IPersist*::Save`， `CoCreateInstance`，和`IPersist*::Load`，因此新的指令碼引擎的狀態應該是相同的原始指令碼引擎狀態已儲存並載入至新的指令碼引擎。 具名項目會複製到複製的指令碼引擎，但特定的物件指標，每個項目會被遺忘，並且以取得[iactivescriptsite:: Getiteminfo](../../winscript/reference/iactivescriptsite-getiteminfo.md)方法。 這可讓相同的物件模型，要使用的每個執行緒的進入點 （apartment 模型）。  
  
 這個方法會用於多執行緒的伺服器主機可以執行多個相同的指令碼執行個體。 指令碼引擎可能會傳回`E_NOTIMPL`，在此情況下主應用程式時，可以藉由重複的持續性狀態，並建立與指令碼引擎的新執行個體達到相同的結果`IPersist*`介面。  
  
 可以從非基底執行緒呼叫這個方法，不會導致主機物件或非基底圖說[IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)介面。  
  
## <a name="see-also"></a>另請參閱  
 [IActiveScript](../../winscript/reference/iactivescript.md)