---
title: IRemoteDebugApplication：： QueryAlive |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplication.QueryAlive
apilocation:
- pdm.dll
helpviewer_keywords:
- IRemoteDebugApplication::QueryAlive
ms.assetid: 08e49d3b-6fb3-4438-960e-f05395ba9b17
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3edc4fc007a2372c429b0bbece394cb1c30a2770
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577467"
---
# <a name="iremotedebugapplicationqueryalive"></a>IRemoteDebugApplication::QueryAlive
指出應用程式是否有回應。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT QueryAlive();  
```  
  
#### <a name="parameters"></a>參數  
 這個方法不接受任何參數。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 這個方法會指出應用程式是否有回應。 這個方法的實作為應該一律會傳回 `S_OK`。  
  
 如果應用程式進程意外終止，COM 會從封送處理 proxy 傳回錯誤，以呼叫此方法。  
  
## <a name="see-also"></a>請參閱  
 [IRemoteDebugApplication 介面](../../winscript/reference/iremotedebugapplication-interface.md)