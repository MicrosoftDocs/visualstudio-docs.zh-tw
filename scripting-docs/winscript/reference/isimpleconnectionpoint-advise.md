---
title: ISimpleConnectionPoint::Advise |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ISimpleConnectionPoint.Advise
apilocation:
- pdm.dll
helpviewer_keywords:
- ISimpleConnectionPoint::Advise
ms.assetid: 59ded60d-b938-4110-aca3-e69ba234ca9a
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b3c0ea37e6fabb051458a11c4838061126bd98bf
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2019
ms.locfileid: "54091737"
---
# <a name="isimpleconnectionpointadvise"></a>ISimpleConnectionPoint::Advise
建立簡單的連接點物件與用戶端接收之間的連線。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT Advise(  
   IDispatch*  pdisp,  
   DWORD*      pdwCookie  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pdisp`  
 [in]指標`IDispatch`介面在用戶端上的通知接收。 用戶端接收會收到傳出呼叫，從簡單的連接點。  
  
 `pdwCookie`  
 [out]傳回的權杖，可唯一識別此連線的指標。 呼叫端會使用此權杖稍後若要刪除連接傳遞至`ISimpleConnectionPoint::Unadvise`方法。 如果未成功建立連線，這個值會是零。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 這個方法會建立簡單的連接點物件與用戶端接收器之間的連線。  
  
## <a name="see-also"></a>另請參閱  
 [ISimpleConnectionPoint 介面](../../winscript/reference/isimpleconnectionpoint-interface.md)   
 [ISimpleConnectionPoint::Unadvise](../../winscript/reference/isimpleconnectionpoint-unadvise.md)