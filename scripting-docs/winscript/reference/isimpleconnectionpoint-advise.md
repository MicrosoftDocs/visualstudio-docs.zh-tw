---
title: ISimpleConnectionPoint：： Advise |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: d7d08d4774dffbfd840c674b15abe82bedb37e5f
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571834"
---
# <a name="isimpleconnectionpointadvise"></a>ISimpleConnectionPoint::Advise
建立簡單連接點物件與用戶端接收之間的連接。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT Advise(  
   IDispatch*  pdisp,  
   DWORD*      pdwCookie  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pdisp`  
 在用戶端的建議接收上 `IDispatch` 介面的指標。 用戶端的接收會接收來自簡單連接點的撥出電話。  
  
 `pdwCookie`  
 脫銷可唯一識別此連接之傳回 token 的指標。 呼叫者稍後會使用此權杖來刪除連接，方法是將它傳遞給 `ISimpleConnectionPoint::Unadvise` 方法。 如果連接未成功建立，此值會是零。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 這個方法會建立簡單連接點物件與用戶端接收之間的連接。  
  
## <a name="see-also"></a>另請參閱  
 [ISimpleConnectionPoint 介面](../../winscript/reference/isimpleconnectionpoint-interface.md)   
 [ISimpleConnectionPoint::Unadvise](../../winscript/reference/isimpleconnectionpoint-unadvise.md)