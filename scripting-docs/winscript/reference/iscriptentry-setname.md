---
title: IScriptEntry：： SetName |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptEntry.SetName
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptEntry::SetName
ms.assetid: dfa33450-87d7-4c8e-bfd8-0cc2d6542a0e
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d9dfa27c6c8c58c0ee1599e17e1da5b5f424e416
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575359"
---
# <a name="iscriptentrysetname"></a>IScriptEntry::SetName
針對代表單一物件（例如函式）的專案，設定物件的名稱。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT SetName(  
   LPCOLESTR          psz  
);  
```  
  
#### <a name="parameters"></a>參數  
 `psz`  
 在@No__t_0 物件的新名稱。  
  
## <a name="return-value"></a>傳回值  
 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
  
## <a name="see-also"></a>請參閱  
 [IScriptEntry 介面](../../winscript/reference/iscriptentry-interface.md)   
 [IScriptEntry::GetName](../../winscript/reference/iscriptentry-getname.md)