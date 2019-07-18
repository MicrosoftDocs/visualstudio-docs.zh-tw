---
title: IDebugApplicationThread::SynchronousCallIntoThread | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplicationThread.SynchronousCallIntoThread
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplicationThread::SynchronousCallIntoThread
ms.assetid: 8a91157f-dade-418a-ad02-5607ce12c95c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f0c9b89332b55a180220820e8ffe1e030d37a848
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62822082"
---
# <a name="idebugapplicationthreadsynchronouscallintothread"></a>IDebugApplicationThread::SynchronousCallIntoThread
提供一個機制，讓呼叫者應用程式執行緒中執行程式碼。  
  
## <a name="syntax"></a>語法  
  
```cpp
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
 [in]第一個參數傳遞至`IDebugThreadCall::ThreadCallHandler`方法。  
  
 `dwParam2`  
 [in]第二個參數傳遞至`IDebugThreadCall::ThreadCallHandler`方法。  
  
 `dwParam3`  
 [in]要傳遞給第三個參數`IDebugThreadCall::ThreadCallHandler`方法。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 這個方法會提供一個機制，讓呼叫者在偵錯工具執行緒中執行程式碼。 語言引擎和主機通常使用這個方法來實作單一執行緒實作之上的無限制執行緒物件。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugApplicationThread 介面](../../winscript/reference/idebugapplicationthread-interface.md)   
 [IDebugThreadCall 介面](../../winscript/reference/idebugthreadcall-interface.md)