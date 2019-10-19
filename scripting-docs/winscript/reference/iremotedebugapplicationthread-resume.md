---
title: IRemoteDebugApplicationThread：： Resume |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplicationThread.Resume
apilocation:
- pdm.dll
helpviewer_keywords:
- IRemoteDebugApplicationThread::Resume
ms.assetid: ac290861-515d-4f06-b452-3b96f54e538c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dc9ccb28604d3a185a1919eb8dc288df711630b6
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571955"
---
# <a name="iremotedebugapplicationthreadresume"></a>IRemoteDebugApplicationThread::Resume
繼續執行緒。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT Resume(  
   DWORD*  pdwCount  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pdwCount`  
 脫銷執行緒的暫停計數。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 當此方法繼續執行緒時，它會遞減暫停計數。  
  
## <a name="see-also"></a>請參閱  
 [IRemoteDebugApplicationThread 介面](../../winscript/reference/iremotedebugapplicationthread-interface.md)