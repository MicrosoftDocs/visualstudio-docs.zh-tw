---
title: IDebugAsyncOperation::Abort |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugAsyncOperation.Abort
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugAsyncOperation::Abort
ms.assetid: 232541c6-81b8-4eb7-96a7-a8e5fe087b31
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: af8b063f86bd08f293518b1494b41e4f01d61b2c
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2019
ms.locfileid: "54093310"
---
# <a name="idebugasyncoperationabort"></a>IDebugAsyncOperation::Abort
取消作業。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT Abort();  
```  
  
#### <a name="parameters"></a>參數  
 這個方法會接受任何參數。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|S_OK|方法成功。|  
|E_NOTIMPL|無法取消作業。|  
  
## <a name="remarks"></a>備註  
 從偵錯工具執行緒取消沒有回應的作業內通常呼叫這個方法。 這個方法會導致`InProgressAbort`方法`IDebugSyncOperation`要呼叫的物件。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugAsyncOperation 介面](../../winscript/reference/idebugasyncoperation-interface.md)   
 [IDebugAsyncOperation::Start](../../winscript/reference/idebugasyncoperation-start.md)   
 [IDebugSyncOperation::InProgressAbort](../../winscript/reference/idebugsyncoperation-inprogressabort.md)