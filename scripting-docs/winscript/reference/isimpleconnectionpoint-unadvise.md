---
title: ISimpleConnectionPoint：： Unadvise |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ISimpleConnectionPoint.Unadvise
apilocation:
- pdm.dll
helpviewer_keywords:
- ISimpleConnectionPoint::Unadvise
ms.assetid: eae06a58-ed42-4839-aad4-14420b15343f
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e00c172fd33eb0ccf27aaf28e0e2f692c1a353ab
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571758"
---
# <a name="isimpleconnectionpointunadvise"></a>ISimpleConnectionPoint::Unadvise
終止先前透過 `ISimpleConnectionPoint::Advise` 建立的諮詢連接。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT Unadvise(  
   DWORD  dwCookie  
);  
```  
  
#### <a name="parameters"></a>參數  
 `dwCookie`  
 在要終止之連接的 Token，如同從 `ISimpleConnectionPoint::Advise` 傳回。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 當諮詢連接終止時，連接點會在 `ISimpleConnectionPoint::Advise` 方法期間，針對連接所儲存的指標呼叫 `Release` 方法。 當連接點呼叫諮詢接收的 `QueryInterface` 時，該呼叫會反轉 `ISimpleConnectionPoint::Advise` 期間所執行的 `AddRef`。  
  
## <a name="see-also"></a>請參閱  
 [ISimpleConnectionPoint 介面](../../winscript/reference/isimpleconnectionpoint-interface.md)