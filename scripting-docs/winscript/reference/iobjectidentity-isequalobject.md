---
title: IObjectIdentity：： IsEqualObject |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IObjectIdentity.IsEqualObject
apilocation:
- scrobj.dll
helpviewer_keywords:
- IsEqualObject method
ms.assetid: 78c5c5c2-d299-4036-986c-7c1d87cbe7cd
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 636dfa07b1fc94dfec2273220aa4101f5cd085b1
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571470"
---
# <a name="iobjectidentityisequalobject"></a>IObjectIdentity::IsEqualObject
判斷物件是否等於目前的物件。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT IsEqualObject(  
  IUnknown*punk  
);  
```  
  
#### <a name="parameters"></a>參數  
 `punk`  
 在要與目前物件比較之物件的位址。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|物件相等。|  
|`S_FALSE`|物件不相等。|  
  
## <a name="remarks"></a>備註  
 只有在物件完全相同時，`IsEqualObject` 方法的執行才會傳回 `S_OK`。  
  
## <a name="see-also"></a>請參閱  
 [IObjectIdentity 介面](../../winscript/reference/iobjectidentity-interface.md)