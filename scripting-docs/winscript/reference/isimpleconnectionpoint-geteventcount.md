---
title: "ISimpleConnectionPoint::GetEventCount |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: ISimpleConnectionPoint.GetEventCount
apilocation: pdm.dll
helpviewer_keywords: ISimpleConnectionPoint::GetEventCount
ms.assetid: f1527d5b-6076-4536-8e59-e55da741ef39
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 523748112d99f000d2eb88a7a64c88b60d5ea44f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="isimpleconnectionpointgeteventcount"></a>ISimpleConnectionPoint::GetEventCount
傳回此介面上公開的事件數目。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetEventCount(  
   ULONG*  pulCount  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pulCount`  
 [out]這個介面計數上公開的事件數目。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|說明|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 這個方法會傳回此介面上公開的事件數目。  
  
## <a name="see-also"></a>另請參閱  
 [ISimpleConnectionPoint 介面](../../winscript/reference/isimpleconnectionpoint-interface.md)