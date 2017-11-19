---
title: "IDebugAsyncOperation::Start |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugAsyncOperation.Start
apilocation: pdm.dll
helpviewer_keywords: IDebugAsyncOperation::Start
ms.assetid: a7272364-28e0-48ae-8405-b8bce8a6b9fd
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bd39053e86dce95fa52ba8576814962d13d8b050
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="idebugasyncoperationstart"></a>IDebugAsyncOperation::Start
會導致開始非同步作業。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT Start(  
   IDebugAsyncOperationCallBack*  padocb  
);  
```  
  
#### <a name="parameters"></a>參數  
 `padocb`  
 接收這項作業的狀態事件的回呼介面。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|說明|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
|`E_UNEXPECTED`|作業已暫止。|  
  
## <a name="remarks"></a>備註  
 這個方法會導致`IDebugSyncOperation::Execute`取自執行緒中以非同步方式呼叫`IDebugSyncOperation::GetTargetThread`。 應該只會從呼叫這個方法，在偵錯工具執行緒; 內否則，它不會傳回直到作業完成為止。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugAsyncOperation::Abort](../../winscript/reference/idebugasyncoperation-abort.md)   
 [IDebugAsyncOperation 介面](../../winscript/reference/idebugasyncoperation-interface.md)   
 [IDebugSyncOperation::Execute](../../winscript/reference/idebugsyncoperation-execute.md)   
 [IDebugSyncOperation::GetTargetThread](../../winscript/reference/idebugsyncoperation-gettargetthread.md)