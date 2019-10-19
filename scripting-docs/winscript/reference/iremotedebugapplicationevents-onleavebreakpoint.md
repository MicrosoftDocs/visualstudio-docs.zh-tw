---
title: IRemoteDebugApplicationEvents：： OnLeaveBreakPoint |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplicationEvents.OnLeaveBreakPoint
apilocation:
- jscript.dll
helpviewer_keywords:
- IRemoteDebugApplicationEvents::OnLeaveBreakPoint
ms.assetid: 00449a23-1f67-4078-ad06-4c426abf7587
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1f4be875f5b420ff96e22ee06cdbeb2929466381
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571948"
---
# <a name="iremotedebugapplicationeventsonleavebreakpoint"></a>IRemoteDebugApplicationEvents::OnLeaveBreakPoint
處理離開中斷點的事件。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT OnLeaveBreakPoint(  
   IRemoteDebugApplicationThread*  prdat  
);  
```  
  
#### <a name="parameters"></a>參數  
 `prdat`  
 在已離開中斷點的應用程式執行緒。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 這個方法會處理用來離開中斷點的事件。  
  
## <a name="see-also"></a>請參閱  
 [IRemoteDebugApplicationEvents 介面](../../winscript/reference/iremotedebugapplicationevents-interface.md)