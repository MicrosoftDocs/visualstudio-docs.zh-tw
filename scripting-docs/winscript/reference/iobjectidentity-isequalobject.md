---
title: IObjectIdentity::IsEqualObject |Microsoft 文件
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 52e386055e458568f8d4076a37489b7b2397f399
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24728598"
---
# <a name="iobjectidentityisequalobject"></a>IObjectIdentity::IsEqualObject
判斷物件是否等於目前的物件。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT IsEqualObject(  
  IUnknown*punk  
);  
```  
  
#### <a name="parameters"></a>參數  
 `punk`  
 [in]若要與目前物件比較的物件的位址。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|說明|  
|-----------|-----------------|  
|`S_OK`|物件相等。|  
|`S_FALSE`|物件不相等。|  
  
## <a name="remarks"></a>備註  
 實作`IsEqualObject`方法應傳回`S_OK`只当物件相同。  
  
## <a name="see-also"></a>另請參閱  
 [IObjectIdentity 介面](../../winscript/reference/iobjectidentity-interface.md)