---
title: IScriptEntry：： SetItemName |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptEntry.SetItemName
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptEntry::SetItemName
ms.assetid: 9551a7ec-38f8-466a-9722-09367763f380
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7ba226704f5b064c86b52c1b349650d509b2b549
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575362"
---
# <a name="iscriptentrysetitemname"></a>IScriptEntry::SetItemName
設定識別 `IScriptEntry` 物件的專案名稱。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT SetItemName(  
   LPCOLESTR          psz  
);  
```  
  
#### <a name="parameters"></a>參數  
 `psz`  
 在包含專案名稱之緩衝區的位址。 主機會使用專案名稱來識別該專案。  
  
## <a name="return-value"></a>傳回值  
 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
|`E_FAIL`|方法未成功。|  
  
## <a name="remarks"></a>備註  
 若為 `IScriptEntry` 物件，這個方法會傳回 `S_OK`。  
  
 若為 `IScriptScriptlet` 物件（衍生自 `IScriptEntry`），這個方法會傳回 `E_FAIL`。 針對 `IScriptScriptlet` 物件，專案名稱是由[IActiveScriptAuthor：： AddScriptlet](../../winscript/reference/iactivescriptauthor-addscriptlet.md)所設定，而且無法變更。  
  
## <a name="see-also"></a>另請參閱  
 [IScriptEntry 介面](../../winscript/reference/iscriptentry-interface.md)   
 [IScriptEntry::GetItemName](../../winscript/reference/iscriptentry-getitemname.md)