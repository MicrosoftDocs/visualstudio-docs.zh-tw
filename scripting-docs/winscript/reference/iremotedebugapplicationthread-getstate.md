---
title: IRemoteDebugApplicationThread::GetState |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplicationThread.GetState
apilocation:
- pdm.dll
helpviewer_keywords:
- IRemoteDebugApplicationThread::GetState
ms.assetid: 44503a78-efa9-4fbf-98be-a5dcfa329c5a
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6534f57c92776dcd3cde9083335becbd66002a32
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62788113"
---
# <a name="iremotedebugapplicationthreadgetstate"></a>IRemoteDebugApplicationThread::GetState
取得這個執行緒的狀態。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetState(  
   DWORD*  pState  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pState`  
 [out]下列執行緒狀態旗標的組合：  
  
|常數|值|描述|  
|--------------|-----------|-----------------|  
|THREAD_STATE_RUNNING|0x00000001|執行緒正在執行。|  
|THREAD_STATE_SUSPENDED|0x00000002|暫止的執行緒。|  
|THREAD_BLOCKED|0x00000004|執行緒已封鎖。|  
|THREAD_OUT_OF_CONTEXT|0x00000008|執行緒是內容之外。|  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 這個方法會取得這個執行緒的狀態。  
  
## <a name="see-also"></a>另請參閱  
 [IRemoteDebugApplicationThread 介面](../../winscript/reference/iremotedebugapplicationthread-interface.md)