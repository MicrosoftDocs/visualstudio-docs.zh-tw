---
title: IRemoteDebugApplicationThread::EnumStackFrames |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplicationThread.EnumStackFrames
apilocation:
- pdm.dll
helpviewer_keywords:
- IRemoteDebugApplicationThread::EnumStackFrames
ms.assetid: 605ce83d-43d2-47ea-b066-ec8f0da50ca6
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 96ca35779ea9f113fc96e485f028f1e74058990a
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2019
ms.locfileid: "58149217"
---
# <a name="iremotedebugapplicationthreadenumstackframes"></a>IRemoteDebugApplicationThread::EnumStackFrames
傳回與這個執行緒相關聯的堆疊框架的列舉值。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT EnumStackFrames(  
   IEnumDebugStackFrames**  ppedsf  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppedsf`  
 [out]這個執行緒相關聯的堆疊框架的列舉值。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 這個方法必須從呼叫內的中斷點。 堆疊框架的列舉程式應傳回框架的堆疊上，從頂端開始從最近推送的框架開始。  
  
## <a name="see-also"></a>另請參閱  
 [IRemoteDebugApplicationThread 介面](../../winscript/reference/iremotedebugapplicationthread-interface.md)