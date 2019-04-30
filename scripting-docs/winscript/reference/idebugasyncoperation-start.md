---
title: IDebugAsyncOperation::Start | Microsoft Docs
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
ms.openlocfilehash: b3e02869abab65878412f96b77d5782b9717a1b6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62821924"
---
# <a name="idebugasyncoperationstart"></a>IDebugAsyncOperation::Start
會導致開始非同步作業。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT Start(  
   IDebugAsyncOperationCallBack*  padocb  
);  
```  
  
#### <a name="parameters"></a>參數  
 `padocb`  
 收到這項作業的狀態事件的回呼介面。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
|`E_UNEXPECTED`|作業已暫止。|  
  
## <a name="remarks"></a>備註  
 這個方法會導致`IDebugSyncOperation::Execute`取自執行緒中以非同步方式呼叫`IDebugSyncOperation::GetTargetThread`。 這個方法應該只會從執行緒內呼叫偵錯工具;否則，它不會傳回直到作業完成為止。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugAsyncOperation::Abort](../../winscript/reference/idebugasyncoperation-abort.md)   
 [IDebugAsyncOperation 介面](../../winscript/reference/idebugasyncoperation-interface.md)   
 [IDebugSyncOperation::Execute](../../winscript/reference/idebugsyncoperation-execute.md)   
 [IDebugSyncOperation::GetTargetThread](../../winscript/reference/idebugsyncoperation-gettargetthread.md)