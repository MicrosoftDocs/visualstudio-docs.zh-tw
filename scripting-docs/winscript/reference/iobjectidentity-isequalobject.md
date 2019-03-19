---
title: IObjectIdentity::IsEqualObject |Microsoft Docs
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
ms.openlocfilehash: c215a15a1239f07272079783366a1617c3a626e2
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2019
ms.locfileid: "58156030"
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
 [in]要與目前物件比較的物件的位址。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|物件相等。|  
|`S_FALSE`|物件不相等。|  
  
## <a name="remarks"></a>備註  
 實作`IsEqualObject`方法應傳回`S_OK`只有當物件是否相同。  
  
## <a name="see-also"></a>另請參閱  
 [IObjectIdentity 介面](../../winscript/reference/iobjectidentity-interface.md)