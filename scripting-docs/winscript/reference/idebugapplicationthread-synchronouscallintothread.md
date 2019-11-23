---
title: IDebugApplicationThread：： SynchronousCallIntoThread |Microsoft Docs
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
ms.openlocfilehash: d545782f8103d10b38f3eb0d2f149c4ef3b9dc95
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574490"
---
# <a name="idebugapplicationthreadsynchronouscallintothread"></a>IDebugApplicationThread::SynchronousCallIntoThread
提供一種機制，讓呼叫者在應用程式執行緒中執行程式碼。  
  
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
 在要呼叫的物件。  
  
 `dwParam1`  
 在要傳遞至 `IDebugThreadCall::ThreadCallHandler` 方法的第一個參數。  
  
 `dwParam2`  
 在要傳遞至 `IDebugThreadCall::ThreadCallHandler` 方法的第二個參數。  
  
 `dwParam3`  
 在要傳遞至 `IDebugThreadCall::ThreadCallHandler` 方法的第三個參數。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 這個方法會提供一個機制，讓呼叫者在偵錯工具執行緒中執行程式碼。 語言引擎和主機通常會使用這個方法，在其單一執行緒的上執行無限制執行緒的物件。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugApplicationThread 介面](../../winscript/reference/idebugapplicationthread-interface.md)   
 [IDebugThreadCall 介面](../../winscript/reference/idebugthreadcall-interface.md)