---
title: "IDebugApplicationThread::SynchronousCallIntoThread |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IDebugApplicationThread.SynchronousCallIntoThread
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplicationThread::SynchronousCallIntoThread
ms.assetid: 8a91157f-dade-418a-ad02-5607ce12c95c
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fdeb57380975f19424f8b7da783846b5aae976ed
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationthreadsynchronouscallintothread"></a>IDebugApplicationThread::SynchronousCallIntoThread
提供應用程式執行緒中執行程式碼呼叫端的機制。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT SynchronousCallIntoThread(  
   IDebugThreadCall*  pstcb,  
   DWORD_PTR          dwParam1,  
   DWORD_PTR          dwParam2,  
   DWORD_PTR          dwParam3  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pstcb`  
 [in]要呼叫的物件。  
  
 `dwParam1`  
 [in]第一個參數傳遞給`IDebugThreadCall::ThreadCallHandler`方法。  
  
 `dwParam2`  
 [in]要傳遞給第二個參數`IDebugThreadCall::ThreadCallHandler`方法。  
  
 `dwParam3`  
 [in]要傳遞給第三個參數`IDebugThreadCall::ThreadCallHandler`方法。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|說明|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 這個方法提供一種機制，在偵錯工具執行緒中執行程式碼呼叫端。 語言引擎，主機通常使用這個方法來實作無限制執行緒的物件，其單一執行緒實作之上。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugApplicationThread 介面](../../winscript/reference/idebugapplicationthread-interface.md)   
 [IDebugThreadCall 介面](../../winscript/reference/idebugthreadcall-interface.md)