---
title: "ISimpleConnectionPoint::Advise |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: ISimpleConnectionPoint.Advise
apilocation: pdm.dll
helpviewer_keywords: ISimpleConnectionPoint::Advise
ms.assetid: 59ded60d-b938-4110-aca3-e69ba234ca9a
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7ec43d135401386a3f54f2c047040897f038ba19
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="isimpleconnectionpointadvise"></a>ISimpleConnectionPoint::Advise
建立簡單的連接點物件與用戶端接收器之間的連接。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT Advise(  
   IDispatch*  pdisp,  
   DWORD*      pdwCookie  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pdisp`  
 [in]指標`IDispatch`介面在用戶端上的通知接收。 用戶端接收器接收連出呼叫從簡單的連接點。  
  
 `pdwCookie`  
 [out]傳回的權杖可唯一識別這個連接的指標。 呼叫端會使用此 token 稍後要傳遞至刪除連接`ISimpleConnectionPoint::Unadvise`方法。 如果未成功建立連接，這個值會是零。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|說明|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 這個方法會建立簡單的連接點物件與用戶端接收器之間的連線。  
  
## <a name="see-also"></a>另請參閱  
 [ISimpleConnectionPoint 介面](../../winscript/reference/isimpleconnectionpoint-interface.md)   
 [ISimpleConnectionPoint::Unadvise](../../winscript/reference/isimpleconnectionpoint-unadvise.md)