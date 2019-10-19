---
title: IRemoteDebugApplicationThread：：暫止 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplicationThread.Suspend
apilocation:
- pdm.dll
helpviewer_keywords:
- IRemoteDebugApplicationThread::Suspend
ms.assetid: fd5cc874-2970-4092-b1cd-e638775b0e20
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5cb5d4d8c541016de71ee1aabffe0b211f850cb7
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575465"
---
# <a name="iremotedebugapplicationthreadsuspend"></a>IRemoteDebugApplicationThread::Suspend
暫停執行緒。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT Suspend(  
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
 當這個方法暫停執行緒時，它會遞增暫停計數。  
  
## <a name="see-also"></a>請參閱  
 [IRemoteDebugApplicationThread 介面](../../winscript/reference/iremotedebugapplicationthread-interface.md)