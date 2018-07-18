---
title: ISimpleConnectionPoint::DescribeEvents |Microsoft 文件
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 42dab9558d46eae0fbb640c60264a79877708321
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24734018"
---
# <a name="isimpleconnectionpointdescribeevents"></a>ISimpleConnectionPoint::DescribeEvents
在指定範圍的事件中傳回的 DISPID 和每個事件的名稱。  
  
## <a name="syntax"></a>語法  
  
```  
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
 [in]要擷取的第一個事件的索引。  
  
 `cEvents`  
 [in]要擷取的事件數目。  
  
 `prgid`  
 [out]事件的 DISPID 值的陣列。  
  
 `prgbstr`  
 [out]事件名稱的陣列。  
  
 `pcEventsFetched`  
 [out]實際讀取的事件數目。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|說明|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
|`S_FALSE`|要求比可用的其他事件。 無法使用的事件會表示 DISPID_NULL 與 null 的 BSTR。|  
|`E_INVALIDARG`|無法擷取任何項目。|  
  
## <a name="remarks"></a>備註  
 這個方法傳回的 DISPID 和每個事件的名稱在指定範圍的事件。  
  
## <a name="see-also"></a>另請參閱  
 [ISimpleConnectionPoint 介面](../../winscript/reference/isimpleconnectionpoint-interface.md)