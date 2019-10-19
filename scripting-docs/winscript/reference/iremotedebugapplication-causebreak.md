---
title: IRemoteDebugApplication：： CauseBreak |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplication.CauseBreak
apilocation:
- pdm.dll
helpviewer_keywords:
- IRemoteDebugApplication::CauseBreak
ms.assetid: 6a2c27bb-dca0-475c-9918-bdbb70a50d26
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8107d7f8450df759b53175505c8d7fc2b6bde641
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571491"
---
# <a name="iremotedebugapplicationcausebreak"></a>IRemoteDebugApplication::CauseBreak
導致應用程式以最早的機會中斷偵錯工具。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT CauseBreak();  
```  
  
#### <a name="parameters"></a>參數  
 這個方法不接受任何參數。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 呼叫這個方法並不會立即中斷應用程式。 如果應用程式目前未執行腳本，可能會在應用程式實際中斷之前經過很長的時間。  
  
## <a name="see-also"></a>請參閱  
 [IRemoteDebugApplication 介面](../../winscript/reference/iremotedebugapplication-interface.md)