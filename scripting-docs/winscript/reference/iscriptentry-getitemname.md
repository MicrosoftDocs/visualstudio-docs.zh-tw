---
title: IScriptEntry：： GetItemName |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptEntry.GetItemName
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptEntry::GetItemName
ms.assetid: 8f2562f1-8231-4a39-ad79-074f9ec3d403
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dcd1b83fa6d22fafc2123645f1f252fa1325f7f1
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575456"
---
# <a name="iscriptentrygetitemname"></a>IScriptEntry::GetItemName
傳回識別 `IScriptEntry` 物件的專案名稱。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetItemName(  
   BSTR               *pbstr  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pbstr`  
 脫銷包含專案名稱之緩衝區的位址。 主機會使用專案名稱來識別該專案。  
  
## <a name="return-value"></a>傳回值  
 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 針對 `IScriptScriptlet` 物件，您可以使用[IActiveScriptAuthor：： AddScriptlet](../../winscript/reference/iactivescriptauthor-addscriptlet.md)來設定專案名稱。 針對其他介面，您可以使用[IScriptEntry：： SetItemName](../../winscript/reference/iscriptentry-setitemname.md)來設定專案名稱。  
  
## <a name="see-also"></a>請參閱  
 [IScriptEntry 介面](../../winscript/reference/iscriptentry-interface.md)