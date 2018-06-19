---
title: IActiveScript::Clone |Microsoft 文件
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 4b0b83bcf86bcc56701d11f22640df966334697b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24641588"
---
# <a name="iactivescriptclone"></a>IActiveScript::Clone
複製目前指令碼引擎 （減去任何目前的執行狀態），傳回不已在目前執行緒中的任何網站載入指令碼引擎。 這個新的指令碼引擎的屬性會與原始的指令碼引擎會在已轉換為初始化的狀態屬性相同。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT Clone(  
    IActiveScript **ppscript  // receives pointer to IActiveScript  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppscript`  
 [out]收到的指標變數的位址[IActiveScript](../../winscript/reference/iactivescript.md)複製指令碼引擎的介面。 主機必須建立網站和呼叫[IActiveScript::SetScriptSite](../../winscript/reference/iactivescript-setscriptsite.md)方法上的新指令碼引擎才會初始化狀態，因此，可使用。  
  
## <a name="return-value"></a>傳回值  
 會傳回下列值之一：  
  
|傳回值|意義|  
|------------------|-------------|  
|`S_OK`|成功。|  
|`E_NOTIMPL`|不支援這個方法。|  
|`E_POINTER`|指定了無效的指標。|  
|`E_UNEXPECTED`|不應該呼叫 （例如，指令碼引擎有尚未載入或初始化）。|  
  
## <a name="remarks"></a>備註  
 `IActiveScript::Clone`方法是最佳化的`IPersist*::Save`， `CoCreateInstance`，和`IPersist*::Load`，因此新的指令碼引擎的狀態應該是相同時，如果原始的指令碼引擎的狀態儲存和載入新的指令碼引擎。 具名項目會在複製的指令碼引擎中重複，但每個項目特定的物件指標會忘記，並取得與[IActiveScriptSite::GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md)方法。 這可讓相同的物件模型使用的每個執行緒的進入點 （apartment 模型）。  
  
 這個方法會用於可以執行多個相同的指令碼執行個體的多執行緒的伺服器主機。 指令碼引擎可能會傳回`E_NOTIMPL`，主應用程式在此情況下透過複製永續性狀態，並建立與指令碼引擎的新執行個體來達到相同的結果`IPersist*`介面。  
  
 可以從非基底執行緒呼叫這個方法，不會導致非基本圖說文字主機物件或[IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)介面。  
  
## <a name="see-also"></a>另請參閱  
 [IActiveScript](../../winscript/reference/iactivescript.md)