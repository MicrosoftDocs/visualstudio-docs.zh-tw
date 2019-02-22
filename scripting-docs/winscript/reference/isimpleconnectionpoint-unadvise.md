---
title: ISimpleConnectionPoint::Unadvise |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 83fdf8f6a6e9378d328a9df61b1561a1ae747ae8
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2019
ms.locfileid: "54089257"
---
# <a name="isimpleconnectionpointunadvise"></a>ISimpleConnectionPoint::Unadvise
終止透過先前建立的諮詢連接`ISimpleConnectionPoint::Advise`。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT Unadvise(  
   DWORD  dwCookie  
);  
```  
  
#### <a name="parameters"></a>參數  
 `dwCookie`  
 [in]連線終止，從傳回的語彙基元`ISimpleConnectionPoint::Advise`。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 連接的諮詢連接終止時，點呼叫`Release`期間連線方法所儲存的指標上`ISimpleConnectionPoint::Advise`方法。 呼叫反轉`AddRef`期間，執行`ISimpleConnectionPoint::Advise`的連接點時呼叫的通知接收`QueryInterface`。  
  
## <a name="see-also"></a>另請參閱  
 [ISimpleConnectionPoint 介面](../../winscript/reference/isimpleconnectionpoint-interface.md)