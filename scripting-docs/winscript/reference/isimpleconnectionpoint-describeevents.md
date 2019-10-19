---
title: ISimpleConnectionPoint：:D escribeEvents |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ISimpleConnectionPoint.DescribeEvents
apilocation:
- pdm.dll
helpviewer_keywords:
- ISimpleConnectionPoint::DescribeEvents
ms.assetid: 659ea05f-d41e-424a-bb38-df7672b2d135
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b5000689d588fe3f63ec5408893187bba8d13d63
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571815"
---
# <a name="isimpleconnectionpointdescribeevents"></a>ISimpleConnectionPoint::DescribeEvents
傳回指定的事件範圍內，每個事件的 DISPID 和名稱。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT DescribeEvents(  
   ULONG    iEvent,  
   ULONG    cEvents,  
   DISPID*  prgid,  
   BSTR*    prgbstr,  
   ULONG*   pcEventsFetched  
);  
```  
  
#### <a name="parameters"></a>參數  
 `iEvent`  
 在要取出之第一個事件的索引。  
  
 `cEvents`  
 在要取出的事件數目。  
  
 `prgid`  
 脫銷事件 DISPID 值的陣列。  
  
 `prgbstr`  
 脫銷事件名稱的陣列。  
  
 `pcEventsFetched`  
 脫銷所提取的實際事件數目。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
|`S_FALSE`|要求的事件數超過可用的數目。 無法使用的事件會以 DISPID_Null 和 Null BSTR 來表示。|  
|`E_INVALIDARG`|無法提取任何元素。|  
  
## <a name="remarks"></a>備註  
 這個方法會針對指定範圍內的事件，傳回每個事件的 DISPID 和名稱。  
  
## <a name="see-also"></a>請參閱  
 [ISimpleConnectionPoint 介面](../../winscript/reference/isimpleconnectionpoint-interface.md)