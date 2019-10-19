---
title: IDebugAsyncOperation：： Start |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugAsyncOperation.Start
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugAsyncOperation::Start
ms.assetid: a7272364-28e0-48ae-8405-b8bce8a6b9fd
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 485eb34ebe200e7f7898d9338effed37cbf2aa10
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573254"
---
# <a name="idebugasyncoperationstart"></a>IDebugAsyncOperation::Start
導致非同步作業開始。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT Start(  
   IDebugAsyncOperationCallBack*  padocb  
);  
```  
  
#### <a name="parameters"></a>參數  
 `padocb`  
 從此作業接收狀態事件的回呼介面。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
|`E_UNEXPECTED`|作業已暫止。|  
  
## <a name="remarks"></a>備註  
 這個方法會導致 `IDebugSyncOperation::Execute` 在從 `IDebugSyncOperation::GetTargetThread` 取得的執行緒中以非同步方式呼叫。 只有在偵錯工具執行緒內，才會呼叫這個方法。否則，它將不會傳回，直到作業完成為止。  
  
## <a name="see-also"></a>請參閱  
 [IDebugAsyncOperation：： Abort](../../winscript/reference/idebugasyncoperation-abort.md)    
 [IDebugAsyncOperation 介面](../../winscript/reference/idebugasyncoperation-interface.md)   
 [IDebugSyncOperation：： Execute](../../winscript/reference/idebugsyncoperation-execute.md)    
 [IDebugSyncOperation::GetTargetThread](../../winscript/reference/idebugsyncoperation-gettargetthread.md)